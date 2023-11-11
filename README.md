# demo-sveltekit-pro

Demo of SvelteKit with our preferred professional options:

* SvelteKit 4
* ESLint
* Playwright
* PostCSS + Autoprefixer
* Prettier
* TailwindCSS + DaisyUI + Forms + Typography
* Typescript
* ViTest


## Create a SvelteKit web application

To create a new SvelteKit web application with our preferred professional options, you can use our helper script:

Run:
```
npm create @svelte-add/kit@latest my.example.com -- \
--with eslint+playwright+postcss+prettier+tailwindcss+typescript+vitest \
--postcss-autoprefixer \
--tailwindcss-daisyui \
--tailwindcss-forms \
--tailwindcss-typography

cd my.example.com
git init && 
git add -A && 
git commit -m "Run npm create @svelte-add/kit@latest …"
pnpm run dev -- --open
```

### Or use sveltekit-create

You can optionally do the same by running this script:

<https://github.com/sixarm/sveltekit-create>

Run:

```sh
sveltekit-create my.example.com
```

### Verify

You may wish to verify the new configuration files:

```
./playwright.config.ts
./postcss.config.cjs
./svelte.config.js
./tailwind.config.cjs
./tsconfig.json
./vite.config.ts
```


## Configure Tailwind

Setup installed Tailwind and its dependencies.

Setup added the Tailwind directives to your CSS by using this PostCSS file:

File `./app.postcss`:

```postcss
/* Write your global styles here, in PostCSS syntax */
@tailwind base;
@tailwind components;
@tailwind utilities
```

The app uses PostCSS, not plain CSS, so do not create a Tailwind directives file such as `./src/app.css`.


### Edit application styles

Edit tile `./app.postcss` to add any of your own preferred application styles, such as for typical web page HTML tags.

Example:

```postcss
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

* <src/app.postcss>


## Create helper tools

For some of our projects, we create helper tools, such as typical shell scripts.

Our naming convention is to put these tools here:

```sh
mkdir bin
```


### clean

For some of our projects, we create a helper tool that we name `clean`.

The tool aims to reset the project to its original state. 

For example, the tool deletes all normal routes, yet does not affect any special routes that start with a plus character.

File <bin/clean>:

```sh
#!/bin/sh
set -euf
find src/routes -type f ! -name '+*' -exec rm {} \;
```

This tool enables us to quickly clean up routes.

  
### slugs

For some of our projects, we create a helper tool that we name `slugs`.

The tool searches a pre-existing directory that contains pre-existing subdirectories that contain markdown content files, each named `index.md`. The tool parses the directories into web-friendly slugs.

File <bin/slugs>:

```sh
top=$(git rev-parse --show-toplevel)
dir="$top/topics"
find "$dir" -name 'index.md' -type f -exec dirname {} \; | 
cut -c $(( ${#dir} + 2 ))-
```
