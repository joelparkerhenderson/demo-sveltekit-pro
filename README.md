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
* SvelteKit Adapter + Vercel - A small plugin that generates output for deployment
* Drizzle + PostgreSQL + Docker - ORM to your database and get the benefits of type safety and intellisense.
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

Performant Node Package Manager:

```sh
pnpm --version
8.10.5
```

Svelte command line interface:

```sh
npx sv --version
0.6.10
```

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
◆  Project created
│
◇  What would you like to add to your project? (use arrow keys / space bar)
│  [x] prettier
|  [x] eslint
|  [x] vitest
|  [x] playwright
|  [x] tailwindcss
|  [x] sveltekit-adapter
|  [x] drizzle
|  [x] lucia
|  [x] mdsvex
|  [x] paraglide
|  [x] storybook
│
◇  tailwindcss: Which plugins would you like to add?
│  [x] typography
|  [x] forms
|  [x] container-queries
│
◇  sveltekit-adapter: Which SvelteKit adapter would you like to use?
│  vercel
│
◇  drizzle: Which database would you like to use?
│  PostgreSQL
│
◇  drizzle: Which PostgreSQL client would you like to use?
│  Postgres.JS
│
◇  drizzle: Do you want to run the database locally with docker-compose?
│  Yes
│
◇  lucia: Do you want to include a demo? (includes a login/register page)
│  Yes
│
◇  paraglide: Which languages would you like to support? (e.g. en,de-ch)
│  ar,cy,de,en,es,eu,fr,hi,ja,sv,ru,zh
│
◇  paraglide: Do you want to include a demo?
│  Yes
│
◇  Which package manager do you want to install dependencies with?
│  pnpm
│
◆  Successfully setup add-ons
│
◆  Successfully installed dependencies
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
pnpm run dev -- --open
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

Edit file `./svelte.config.js`:

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


## Configure Tailwind

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

You can write PostCSS syntax in the file `./src/app.css`.

This is your global stylesheet because it will be active on every page of your site.


### Edit application styles

Edit tile `./app.css` to add any of your own preferred application styles, such as for typical web page HTML tags.

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

Our file is here:

* <src/app.css>


### Layout

Setup create a layout file that includes TypeScript, internationalization, Paraglide, and more.

```sh
cat ./src/routes/+layout.svelte
```

```svelte
<script lang="ts">
	import { i18n } from '$lib/i18n';
	import { ParaglideJS } from '@inlang/paraglide-sveltekit';
	import '../app.css';
	let { children } = $props();
</script>

<ParaglideJS {i18n}>
	{@render children()}
</ParaglideJS>
```


## Create components

Create some Svelte components that are simple placeholders, such as for a header and footer. Create the components with some simple HTML tags and some simple Tailwind CSS classes.

Create file `./src/lib/Header.svelte`:

```html
<header class="mb-2 border-b-2 border-2">
    <nav class="p-2">
        <a class="no-underline" href="/">Home</a>
    </nav>
</header>
````

Create a Svelte component that is a simple placeholder footer.

Create file `./src/lib/Footer.svelte`:

```html
<footer class="mt-2 border-t-2 border-2">
    <nav class="p-2">
        <a class="no-underline" href="/">Home</a>
    </nav>
</footer>
````

Add these components to the layout.

```svelte
<script lang="ts">
	import { i18n } from '$lib/i18n';
	import { ParaglideJS } from '@inlang/paraglide-sveltekit';
	import '../app.css';
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
find ../src/routes -type f ! -name '+*' -exec rm {} \;
```

This tool enables us to quickly clean up routes.

Example before:

```
./src/routes/+layout.svelte
./src/routes/+page.svelte
./src/routes/alfa.bravo
./src/routes/charlie.delta
```

Example after:

```
./src/routes/+layout.svelte
./src/routes/+page.svelte
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

```
my-project/topics/alpha/index.md
my-project/topics/bravo/index.md
```
```

Example output slugs:

```
alpha
bravo
```
