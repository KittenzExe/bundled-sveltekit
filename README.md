# Bundled SvelteKit

Play on words with Bun SvelteKit along with Tailwindcss.

Designed to save time (or at least, save time for my workflow with svelte).

Enjoy!

## Features

- Bun runtime
- SvelteKit (Adapter Static)
- Tailwindcss
- All files added, edited, and ready to go

## Build yourself

> [!NOTE]
> You will need Bun installed (duh). Download it here: [Bun download](https://bun.sh/)

### Create Svelte

`bun create svelte@latest`

Options:

``` terminal
┌  Welcome to SvelteKit!
│
◇  Where should we create your project?
│    (hit Enter to use current directory)
│
◇  Directory not empty. Continue?
│  Yes
│
◇  Which Svelte app template?
│  Skeleton project
│
◇  Add type checking with TypeScript?
│  Yes, using TypeScript syntax
│
◇  Select additional options (use arrow keys/space bar)
│  none
│
└  Your project is ready!
```

---

### Install Tailwindcss (will also install packages for svelte)

`bun install -D tailwindcss postcss`

---

### Init Tailwindcss

`bun tailwindcss init -p`

---

### Change files for Tailwindcss compatability with Sveltekit

`svelte.config.js`

``` js
import adapter from '@sveltejs/adapter-static';
/** @type {import('@sveltejs/kit').Config} */
const config = {
    kit: {
		adapter: adapter({
			pages: 'build',
			assets: 'build',
			fallback: undefined,
			precompress: false,
			strict: true
		})
	}
};
export default config;
```


(if you want `adapter-auto`, here is the code below)

``` js
import adapter from '@sveltejs/adapter-auto';
import { vitePreprocess } from '@sveltejs/vite-plugin-svelte';
/** @type {import('@sveltejs/kit').Config} */
const config = {
    kit: {
        adapter: adapter()
    },
    preprocess: vitePreprocess()
};
export default config;
```

`tailwind.config.js`

``` js
/** @type {import('tailwindcss').Config} */
export default {
    content: ['./src/**/*.{html,js,svelte,ts}'],
    theme: {
        extend: {}
    },
    plugins: []
};
```

---

### Add files

`/src/app.css`

``` css
@import "tailwindcss/base";
@import "tailwindcss/components";
@import "tailwindcss/utilities";
```

`/src/routes/+layout.svelte`

``` html
<script>
    import "../app.css";
</script>

<slot />
```

---

### Running and building

`bun run dev`

`bun run build`

---

### And you're all set!

With some minor changes to text and the favicon, everything is the same!
