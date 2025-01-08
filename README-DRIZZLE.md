# Demo SvelteKit: Drizzle

## Database

Previously in this demo, we created a database connection and included the credentials in our .env environment variables.

Setup created a Drizzle configuration file [`drizzle.config.ts`](drizzle.config.ts):

```ts
import { defineConfig } from 'drizzle-kit';
if (!process.env.DATABASE_URL) throw new Error('DATABASE_URL is not set');

export default defineConfig({
	schema: './src/lib/server/db/schema.ts',

	dbCredentials: {
		url: process.env.DATABASE_URL
	},

	verbose: true,
	strict: true,
	dialect: 'postgresql'
});
```


### Schema

Setup created a Drizzle database schema file  [`src/lib/server/db/schema.ts`](src/lib/server/db/schema.ts):

```js
import { pgTable, serial, text, integer, timestamp } from 'drizzle-orm/pg-core';

export const user = pgTable('user', {
        id: text('id').primaryKey(),
        age: integer('age'),
        username: text('username').notNull().unique(),
        passwordHash: text('password_hash').notNull()
});

export const session = pgTable('session', {
        id: text('id').primaryKey(),
        userId: text('user_id')
                .notNull()
                .references(() => user.id),
        expiresAt: timestamp('expires_at', { withTimezone: true, mode: 'date' }).notNull()
});

export type Session = typeof session.$inferSelect;

export type User = typeof user.$inferSelect;
```

### Change id

We prefer the user id to be an integer primary key generated always as identity.

The session id stays as a text primary key because it will be sent to the browser as a cookie.

Change the user section line.

From:

```ts
id: text('id').primaryKey(),
```

Into:

```ts
id: integer('id').primaryKey().generatedAlwaysAsIdentity({ startWith: 1 }),
```

Change the session section line.

From:

```ts
userId: text('user_id')
```

Into:

```ts
userId: integer('user_id')
```


### drizzle-kit generate

Generate the SQL needed to migrate the database:

```sh
npx drizzle-kit generate
```

Output:

```
2 tables
session 3 columns 0 indexes 1 fks
user 4 columns 0 indexes 0 fks

[✓] Your SQL migration file ➜ drizzle/0000_pretty_rockslide.sql 🚀
```


### Change id again

The file [`drizzle/0000_pretty_rockslide.sql`](drizzle/0000_pretty_rockslide.sql):

```sql
CREATE TABLE IF NOT EXISTS "session" (
        "id" integer PRIMARY KEY NOT NULL,
        "user_id" integer NOT NULL,
        "expires_at" timestamp with time zone NOT NULL
);
--> statement-breakpoint
CREATE TABLE IF NOT EXISTS "user" (
        "id" integer PRIMARY KEY NOT NULL,
        "age" integer,
        "username" text NOT NULL,
        "password_hash" text NOT NULL,
        CONSTRAINT "user_username_unique" UNIQUE("username")
);
--> statement-breakpoint
DO $$ BEGIN
 ALTER TABLE "session" ADD CONSTRAINT "session_user_id_user_id_fk" FOREIGN KEY ("user_id") REFERENCES "public"."user"("id") ON DELETE no action ON UPDATE no action;
EXCEPTION
 WHEN duplicate_object THEN null;
END $$;
```

Change the user section line from this…

```sql
"id" integer PRIMARY KEY NOT NULL,
```

…into this:

```sql
"id" integer PRIMARY KEY GENERATED ALWAYS AS IDENTITY,
```


### drizzle-kit migrate

Run the migration:

```sh
npx drizzle-kit migrate	
```

Verify tables:

```sh
psql -d "postgres://demo_sveltekit_owner:secret@localhost:5432/demo_sveltekit_development" \
-c "SELECT table_name FROM information_schema.tables WHERE table_type = 'BASE TABLE' AND table_schema NOT IN ('pg_catalog', 'information_schema');"
```

```txt
      table_name      
----------------------
 __drizzle_migrations
 user
 session
```

Verify tables and columns:

```sh
➜ psql -d "postgres://demo_sveltekit_owner:secret@localhost:5432/demo_sveltekit_development" 
-c "SELECT table_name, column_name, data_type FROM information_schema.columns where table_schema = 'public' order by table_name;"
```

```txt
 table_name |  column_name  |        data_type         
------------+---------------+--------------------------
 session    | id            | integer
 session    | user_id       | integer
 session    | expires_at    | timestamp with time zone
 user       | id            | integer
 user       | age           | integer
 user       | username      | text
 user       | password_hash | text
```
