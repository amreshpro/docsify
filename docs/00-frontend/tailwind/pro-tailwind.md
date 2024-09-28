# Tailwind Config

#### Installation

```sh
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
```

`tailwind.cofig.js`

```js
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: [
    "./app/**/*.{js,ts,jsx,tsx,mdx}",
    "./pages/**/*.{js,ts,jsx,tsx,mdx}",
    "./components/**/*.{js,ts,jsx,tsx,mdx}",

    // Or if using `src` directory:
    "./src/**/*.{js,ts,jsx,tsx,mdx}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
};
```

Add below code in `global.css`

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

### Media Queries

Add this code in `tailwind.cofig.js`

```js
 theme: {
    screens: {
      "2xl": { max: "1535px" },
      xl: { max: "1279px" },
      lg: { max: "1023px" },
      md: { max: "767px" },
      sm: { max: "639px" },
      xsm: { max: "339px" },
    },
  },
```
