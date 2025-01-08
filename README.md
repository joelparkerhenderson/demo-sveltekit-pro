# demo-sveltekit-pro

Demo of SvelteKit with our preferred professional options:

* SvelteKit
* Typescript type checking
* Prettier - Opinionated Code Formatter
* ESLint - Opinionated JavaScript Linter
* Vitest - Testing framework powered by Vite
* Playwright - Fast and reliable end-to-end testing for modern web apps
* TailwindCSS - A utility-first CSS framework.
* TailwindCSS Plugins: Typography, Forms, Container Queries
* SvelteKit Adapter + Node - A small plugin that generates output for deployment
* Drizzle + PostgreSQL - ORM to your database and get the benefits of type safety and intellisense.
* Lucia - An open source resource on implementing authentication with JavaScript
* mdsvex - Markdown preprocessor for Svelte. Markdown in Svelte.
* Paraglide JS + ar,cy,de,en,es,eu,fr,hi,ja,sv,ru,zh - internationalization (i18n) library
* Storybook - frontend workshop for building UI components and pages in isolation
* TODO: PostCSS + Autoprefixer
* TODO: DaisyUI


## Prerequisites

Node JavaScript runtime environment:

```sh
node --version
v23.5.0
```

Node Package eXecute:

```sh
npx --version
10.9.2
```

Svelte command line interface:

```sh
npx sv --version
0.6.10
```

Performant Node Package Manager:

```sh
pnpm --version
8.10.5
```

PostgreSQL:

```sh
psql --version
psql (PostgreSQL) 16.6
```

Docker:

```sh
docker --version
Docker version 27.4.0, build bde2b89
```

Docker compose:

```sh
docker-compose --version
Docker Compose version 2.32.1
```

<details>
<summary>Install on macOS via brew</summary>
brew install mise
brew install node
brew install pnpm
brew install postgresql
brew install --cask docker
brew install docker-compose docker-credential-helper

Launch Docker. When Docker is launched in this manner, a Docker whale icon appears in the status menu. As soon as the whale icon appears, the symbolic links for docker, docker-compose, docker-credential-osxkeychain and docker-machine are created in /usr/local/bin.

Docker Compose is a Docker plugin. For Docker to find the plugin, add "cliPluginsExtraDirs" to ~/.docker/config.json:
  "cliPluginsExtraDirs": [
      "/opt/homebrew/lib/docker/cli-plugins"
  ]
</details>

<details>
<summary>Install on macOS via brew and mise</summary>
mise use node
mise use pnpm
mise use docker-compose
brew install gcc readline zlib curl openssl@1.1 ossp-uuid icu4c pkg-config
PKG_CONFIG_PATH="$(brew --prefix)/lib/pkgconfig:$(brew --prefix icu4c)/lib/pkgconfig" \
LDFLAGS="-L$(brew --prefix)/lib" \
CPPFLAGS="-I$(brew --prefix)/include" \
mise use postgres@16 --verbose
brew install docker-compose docker-credential-helper
</details>


## Create a SvelteKit web application

Run the Svelte command line interface:

```sh
npx sv@latest create demo --template minimal --types ts
```

The options mean:

```txt
  --template <type>    template to scaffold (choices: minimal, demo, library)
  --[no-]types <lang>  add type checking (choices: ts, jsdoc)
  --no-install         skip installing dependencies
```

<details>
<summary>Interaction</summary>
```txt
┌  Welcome to the Svelte CLI! (v0.6.10)
│
◇  Project created
│
◇  What would you like to add to your project? (use arrow keys / space bar)
│  ◼ prettier (formatter - https://prettier.io)
│  ◼ eslint (linter - https://eslint.org)
│  ◼ vitest (unit testing - https://vitest.dev)
│  ◼ playwright (browser testing - https://playwright.dev)
│  ◼ tailwindcss (css framework - https://tailwindcss.com)
│  ◼ sveltekit-adapter (deployment - https://svelte.dev/docs/kit/adapters)
│  ◼ drizzle (database orm - https://orm.drizzle.team)
│  ◼ lucia (auth guide - https://lucia-auth.com)
│  ◼ mdsvex (svelte + markdown - https://mdsvex.pngwn.io)
│  ◼ paraglide (i18n - https://inlang.com)
│  ◼ storybook (frontend workshop - https://storybook.js.org)
│
◇  tailwindcss: Which plugins would you like to add?
│  ◼ typography (@tailwindcss/typography)
|  ◼ forms (@tailwindcss/forms)
|  ◼ container-queries (@tailwindcss/container-queries)
│
◇  sveltekit-adapter: Which SvelteKit adapter would you like to use?
│  ● node (@sveltejs/adapter-node)
│  ○ static (@sveltejs/adapter-static)
│  ○ vercel (@sveltejs/adapter-vercel)
│  ○ cloudflare-pages (@sveltejs/adapter-cloudflare)
│  ○ cloudflare-workers (@sveltejs/adapter-cloudflare-workers)
│  ○ netlify (@sveltejs/adapter-netlify)
│
◇  drizzle: Which database would you like to use?
│  ● PostgreSQL
│  ○ SQLite
│
◇  drizzle: Which PostgreSQL client would you like to use?
│  ● Postgres.JS (recommended for most users)
│  ○ Neon (popular hosted platform)
│
◇  drizzle: Do you want to run the database locally with docker-compose?
│  ○ Yes / ● No
│  
◇  lucia: Do you want to include a demo? (includes a login/register page)
│  ● Yes / ○ No
│
◇  paraglide: Which languages would you like to support? (e.g. en,de-ch)
│  ar,cy,de,en,es,eu,fr,hi,ja,sv,ru,zh
│
◇  paraglide: Do you want to include a demo?
│  ● Yes / ○ No
│
◇  Which package manager do you want to install dependencies with?
│  ○ None
│  ○ npm
│  ○ yarn
│  ● pnpm
│  ○ bun
│  ○ deno
│
◇  Successfully setup add-ons
│
◇  Successfully installed dependencies
│
◇  Successfully formatted modified files
│
╭──────────────────────────────────────────────────────────────────────────────╮
│                                                                              │
│   Storybook was successfully installed in your project!                      │
│   To run Storybook manually, run npm run storybook. CTRL+C to stop.          │
│                                                                              │
│   Wanna know more about Storybook? Check out https://storybook.js.org/       │
│   Having trouble or want to chat? Join us at https://discord.gg/storybook/   │
│                                                                              │
╰──────────────────────────────────────────────────────────────────────────────╯
│
◇  Project next steps ─────────────────────────────────────────────────────╮
│                                                                          │
│  1: cd demo                                                              │
│  2: git init && git add -A && git commit -m "Initial commit" (optional)  │
│  3: pnpm run dev --open                                                  │
│                                                                          │
│  To close the dev server, hit Ctrl-C                                     │
│                                                                          │
│  Stuck? Visit us at https://svelte.dev/chat                              │
│                                                                          │
├──────────────────────────────────────────────────────────────────────────╯
│
◇  Add-on next steps ──────────────────────────────────────────────────╮
│                                                                      │
│  drizzle:                                                            │
│  - You will need to set DATABASE_URL in your production environment  │
│  - Run pnpm run db:start to start the docker container               │
│  - Run pnpm run db:push to update your database schema               │
│                                                                      │
│  lucia:                                                              │
│  - Run pnpm run db:push to update your database schema               │
│  - Visit /demo/lucia route to view the demo                          │
│                                                                      │
│  paraglide:                                                          │
│  - Edit your messages in messages/en.json                            │
│  - Consider installing the Sherlock IDE Extension                    │
│  - Visit /demo/paraglide route to view the demo                      │
│                                                                      │
├──────────────────────────────────────────────────────────────────────╯
│
└  You're all set!
```
</details>


### Deprecated SvelteKit

To create a SvelteKit project, use these command options:

```
npm create @svelte-add/kit@latest my.example.com -- \
--with eslint+playwright+postcss+prettier+tailwindcss+typescript+vitest \
--postcss-autoprefixer \
--tailwindcss-daisyui \
--tailwindcss-forms \
--tailwindcss-typography
```


### Add git

Run:

```sh
cd demo
git init
git add --all
git commit -m "Run npx sv@latest create demo --template minimal --types ts"
```


### Database connection

This demo uses the PostgreSQL database server that must already be running on your system.

Create a new role and database:

```sh
psql -U postgres -c "CREATE ROLE demo_sveltekit_pro_owner WITH LOGIN ENCRYPTED PASSWORD 'secret';"
psql -U postgres -c "CREATE DATABASE demo_sveltekit_pro_development with owner = demo_sveltekit_pro_owner;"
```

Setup created a file Edit file [`.env`](.env):

```sh
# Replace with your DB credentials!
DATABASE_URL="postgres://user:password@host:port/db-name"
```

Change the line to:

```sh
DATABASE_URL="postgres://demo_sveltekit_pro_owner:secret@localhost:5432/demo_sveltekit_pro_development"
```


### Launch

Run:

```sh
pnpm run dev -- --open
```


### Optional copy

To copy old files from a old demo project:

```sh
cp old/.env demo/
cp old/src/lib/{Header,Footer}.svelte demo/src/lib/
cp old/src/app.css demo/src/
cp old/src/routes/+layout.svelte demo/src/routes/
cp old/src/lib/server/db/schema.ts demo/src/lib/server/db/
```


### Verify

You may wish to verify the new configuration files:

```sh
ls -1 *.config.ts
drizzle.config.ts
eslint.config.js
playwright.config.ts
postcss.config.js
svelte.config.js
tailwind.config.ts
tsconfig.json
vite.config.ts
```


## Configure static site - optional

If the project is a static site:

* https://kit.svelte.dev/docs/adapter-static

```sh
pnpm i -D @sveltejs/adapter-static
```

If the project is a static site on Vercel then use the default adapter.

Edit file `svelte.config.js`:

```js
import adapter from '@sveltejs/adapter-static';
import { vitePreprocess } from '@sveltejs/kit/vite';

/** @type {import('@sveltejs/kit').Config} */
const config = {
	// Consult https://kit.svelte.dev/docs/integrations#preprocessors
	// for more information about preprocessors
	preprocess: [vitePreprocess({})],

	kit: {
		// adapter-auto only supports some environments, see https://kit.svelte.dev/docs/adapter-auto for a list.
		// If your environment is not supported or you settled on a specific environment, switch out the adapter.
		// See https://kit.svelte.dev/docs/adapters for more information about adapters.
		adapter: adapter()
	}
};

export default config;
```

Add our preferred settings for prerender and trailing slash.

Create the file `src/routes/+layout.ts`:

```ts
export const prerender = true;
export const trailingSlash = 'always';
```


## Tailwind

Setup installed Tailwind and its dependencies.


```sh
cat src/app.css
```

```js
@import 'tailwindcss/base';
@import 'tailwindcss/components';
@import 'tailwindcss/utilities';
```

### PostCSS

Setup created a PostCSS configuration file:

```sh
cat postcss.config.js
```

```js
export default {
        plugins: {
                tailwindcss: {},
                autoprefixer: {}
        }
};
```

You can write PostCSS syntax in the style lang="postcss" blocks in Svelte files.

You can write PostCSS syntax in the file `src/app.css`.

This is your global stylesheet because it will be active on every page of your site.


### Edit application styles

Edit file [`app.css`](app.css) to add any of your own preferred application styles, such as for typical web page HTML tags.

Example:

```css
@layer base {
    h1 {
        @apply text-3xl;
    }
    p {
        @apply my-4;
    }
    a {
        @apply text-blue-600 underline;
    }
    ol {
        @apply list-decimal;
    }
    ul {
        @apply list-disc;
    }
    li {
        @apply my-4;
    }
}
```


### Layout

Setup create a layout file [`src/routes/+layout.svelte`](src/routes/+layout.svelte) that includes TypeScript, internationalization, Paraglide, and more.


```svelte
<script lang="ts">
	import { i18n } from '$lib/i18n';
	import { ParaglideJS } from '@inlang/paraglide-sveltekit';
	import '.app.css';
	let { children } = $props();
</script>

<ParaglideJS {i18n}>
	{@render children()}
</ParaglideJS>
```


## Create components

Create some Svelte components that are simple placeholders, such as for a header and footer. Create the components with some simple HTML tags and some simple Tailwind CSS classes.

Create file [`src/lib/Header.svelte`](src/lib/Header.svelte):

```html
<header class="mb-2 border-b-2 border-2">
    <nav class="p-2">
        <a class="no-underline" href="/">Home</a>
    </nav>
</header>
````

Create a Svelte component that is a simple placeholder footer.

Create file [`src/lib/Footer.svelte`](src/lib/Footer.svelte):

```html
<footer class="mt-2 border-t-2 border-2">
    <nav class="p-2">
        <a class="no-underline" href="/">Home</a>
    </nav>
</footer>
````

Add these components to the layout file [`src/routes/+layout.svelte`](src/routes/+layout.svelte):

```svelte
<script lang="ts">
	import { i18n } from '$lib/i18n';
	import { ParaglideJS } from '@inlang/paraglide-sveltekit';
	import '.app.css';
    import Header from "$lib/Header.svelte";
    import Footer from "$lib/Footer.svelte";
	let { children } = $props();
</script>

<ParaglideJS {i18n}>
    <Header />
	{@render children()}
    <Footer />
</ParaglideJS>
```


## Test

Vitest provides unit testing.

Playwright provides end-to-end testing. 


### Vitest

Vitest provides unit testing.

Setup created a unit test file [`src/demo.spec.ts`](src/demo.spec.ts):

```ts
import { describe, it, expect } from 'vitest';

describe('sum test', () => {
	it('adds 1 + 2 to equal 3', () => {
		expect(1 + 2).toBe(3);
	});
});
```


### Playwright

Playwright provides end-to-end ("e2e") testing. 

Before you run Playwright the first time, you need to install any browser updates.

Run:

```sh
pnpm exec playwright install   
```

Setup created an e2e test file [`e2e/demo.test.ts`](e2e/demo.test.ts):

```ts
import { expect, test } from '@playwright/test';

test('home page has expected h1', async ({ page }) => {
	await page.goto('/');
	await expect(page.locator('h1')).toBeVisible();
});
```


### Test the application

Run:

```sh
pnpm test
```

Output:

```txt
✓ src/demo.spec.ts (1)
   ✓ sum test (1)
     ✓ adds 1 + 2 to equal 3

 Test Files  1 passed (1)
      Tests  1 passed (1)
   Start at  20:20:42
   Duration  304ms (transform 26ms, setup 0ms, collect 14ms, tests 1ms, environment 0ms, prepare 86ms)


> demo@0.0.1 test:e2e
> playwright test

[WebServer] "serial" is imported from external module "drizzle-orm/pg-core" but never used in "src/lib/server/db/schema.ts".
[WebServer] .svelte-kit/generated/client-optimized/app.js (29:28): "transport" is not exported by "src/hooks.ts", imported by ".svelte-kit/generated/client-optimized/app.js".

Running 1 test using 1 worker

  ✓  1 demo.test.ts:3:1 › home page has expected h1 (475ms)

  1 passed (10.1s)
```


### Unit test a custom file

Create a file [`src/lib/sum.js`](src/lib/sum.js):

```js
export function sum(a, b) {
  return a + b
}
```

Create a file [`src/lib/sum.test.js`](src/lib/sum.test.js):

```js
import { expect, test } from 'vitest'
import { sum } from 'sum.js'

test('adds 1 + 2 to equal 3', () => {
  expect(sum(1, 2)).toBe(3)
})
```

Run:

```sh
pnpm test
```


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

We prefer the id to be an integer primary key generated always as identity.

Change each of the lines from…

```ts
id: text('id').primaryKey(),
```

…into:

```ts
id: integer('id').primaryKey().generatedAlwaysAsIdentity({ startWith: 1 }),
```

Change from this…

```ts
userId: text('user_id')
```

…into this:

```ts
userId: integer('user_id')
```


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

Change each of the lines from this…

```sql
"id" integer PRIMARY KEY NOT NULL,
```

…into this:

```sql
"id" integer PRIMARY KEY GENERATED ALWAYS AS IDENTITY,
```

Run the migration:

```sh
npx drizzle-kit migrate	
```

Verify tables:

```sh
psql -d "postgres://demo_sveltekit_pro_owner:secret@localhost:5432/demo_sveltekit_pro_development" \
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
➜ psql -d "postgres://demo_sveltekit_pro_owner:secret@localhost:5432/demo_sveltekit_pro_development" 
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


## Demo route

Setup created a demo route for Lucia and Paraglide:

* http://localhost:5173/demo


## Lucia authentication

Setup created a Lucia demo directory: [`src/routes/demo/lucia/`](src/routes/demo/lucia/)

```txt
demo/src/routes/demo/lucia/
demo/src/routes/demo/lucia//+page.server.ts
demo/src/routes/demo/lucia//+page.svelte
demo/src/routes/demo/lucia//login
demo/src/routes/demo/lucia//login/+page.server.ts
demo/src/routes/demo/lucia//login/+page.svelte
```

Browse: http://localhost:5173/demo/lucia/login


### Display error messages

The Lucia login and registration code is in the file [`src/routes/demo/lucia/login/+page.server.ts`](src/routes/demo/lucia/login/+page.server.ts).

We prefer Lucia to display error messages that originate from the database and ORM.

Change this line from…

```ts
			return fail(500, { message: 'An error has occurred' });
```

…into:

```ts
			return fail(500, { message: 'An error has occurred: ' + (e instanceof Error ? e.message : 'unknown error') });
```

Browse: http://localhost:5173/demo/lucia/login

Now if you try username "alice" and password "secret", you should see this error message: 

* An error has occurred: cannot insert a non-DEFAULT value into column "id".

The error is because we changed the primary key type. We'll fix this next.


### Create a user via SQL

To create a user via SQL, look at the Lucia login file [`src/routes/demo/lucia/login/+page.server.ts`](src/routes/demo/lucia/login/+page.server.ts).

This line shows the password hash algorithm is argon2:

```ts
import { hash, verify } from '@node-rs/argon2';
```

This line converts plain text into a password hash:

```ts
const passwordHash = await hash(password, {
```


This line validates the database record user's password hash with the web browser user's password form field plain text:

```ts
const validPassword = await verify(existingUser.passwordHash, password, {
```

To generate a password using a command line node repl, we can use the same kind of code.

Run:

```sh
node
```

Run:

```js
const { hash, verify } = await import("@node-rs/argon2");
let plainText = "secret";
console.log(plainText);
let cryptText = await hash(plainText, {
    memoryCost: 19456,
    timeCost: 2,
    outputLen: 32,
    parallelism: 1
});
console.log(cryptText);
let isValid = await verify(cryptText, plainText, {
    memoryCost: 19456,
    timeCost: 2,
    outputLen: 32,
    parallelism: 1
});
console.log(isValid);
```

Output:

```
secret
$argon2id$v=19$m=19456,t=2,p=1$3fZkYOfXgvvRwEpZtT3tQQ$VqF4vlH5yDaFxabiFpZXXBfE2tJyuBujsci2EJrG7no
true
```


## Demo Paraglide

Setup created a demo route for Paraglide:

* http://localhost:5173/demo/paraglide


## Create helper tools

For some of our projects, we create helper tools, such as typical shell scripts.

Our naming convention is to put these tools here:

```sh
mkdir bin
```


### markdown-reader-to-headline

File <bin/markdown-reader-to-headline>:

```sh
grep -m1 '^##*[[:space:]][[:space:]]*[^[:space:]]' "$@" |
sed 's/^#*[[:space:]]*//; s/[[:space:]]*#*[[:space:]]*$//;'
```


### clean

For some of our projects, we create a helper tool that we name `clean`.

The tool aims to reset the project to its original state.

For example, the code below deletes all normal routes, yet does not affect any special routes that start with a plus character.

File <bin/clean>:

```sh
#!/bin/sh
set -euf
find .src/routes -type f ! -name '+*' -exec rm {} \;
```

This tool enables us to quickly clean up routes.

Example before:

```
src/routes/+layout.svelte
src/routes/+page.svelte
src/routes/alfa.bravo
src/routes/charlie.delta
```

Example after:

```
src/routes/+layout.svelte
src/routes/+page.svelte
```


### slugs

For some of our projects, we create a helper tool that we name `slugs`.

For example, the code below searches a pre-existing git repository, that contains a directory named `topics`, that contains pre-existing subdirectories, that each contain a markdown content file named `index.md`. The tool parses the directories into web-friendly slugs.

File <bin/slugs>:

```sh
GIT_TOP_DIR="$(git rev-parse --show-toplevel)"
DIR="$GIT_TOP_DIR/topics"
find "$DIR" -name 'index.md' -type f -exec dirname {} \; |
sort | cut -c $(( ${#DIR} + 2 ))-
```

Example input pre-existing directory structure:

```txt
my-project/topics/alpha/index.md
my-project/topics/bravo/index.md
```

Example output slugs:

```txt
alpha
bravo
```
