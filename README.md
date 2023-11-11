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
