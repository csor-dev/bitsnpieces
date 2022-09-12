# Configuring Nuxt 3 with Tailwind Css



https://frontendshape.com/post/how-to-install-tailwind-css-3-in-nuxt-3

Start by creating a new Nuxt 3 project named `hello-tailwind-3` with the following command:

```
npx nuxi init hello-tailwind-3
```

Install Tailwind CSS as a development dependency with the following command:

- `npm install -D tailwindcss`

Create your `tailwind.config.js` file with the following content:

- `npx tailwindcss init`

Open up `tailwind.config.js` and add the paths to all of your template files under content:

```js
module.exports = {
  content: [
    "./components/**/*.{js,vue,ts}",
    "./layouts/**/*.vue",
    "./pages/**/*.vue",
    "./plugins/**/*.{js,ts}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

Create a new file `assets/css/tailwind.css` and add the following add the @tailwind directives for each of Tailwind’s layers:

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

Open up `nuxt.config.js` and add the following:

```tsx
import { defineNuxtConfig } from 'nuxt'

// https://v3.nuxtjs.org/docs/directory-structure/nuxt.config
export default defineNuxtConfig({
  build: {
    postcss: {
      postcssOptions: {
        plugins: {
          tailwindcss: {},
          autoprefixer: {},
        },
      },
    },
  },
  css: [
    "~/assets/css/tailwind.css"
  ],
})
```
