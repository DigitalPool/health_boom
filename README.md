Here’s a clean `README.md` you can drop in your repo 👇

```markdown
# HealthBoom Pharmaceuticals — Website

A fast, responsive, static website for **HealthBoom Pharmaceuticals** built with **HTML + Tailwind CSS** (and a sprinkle of vanilla JS).  
Includes core pages (Home, About, Services, Blog, Single Post, Shop, Contact, Privacy, Terms) and a working **Cart** powered by `localStorage`.

**Live demo:** https://health-boom-sand.vercel.app/

---

## Features

- 🔹 Responsive header + mobile hamburger menu
- 🔹 Hero sections with themed imagery
- 🔹 Blog list + single post template
- 🔹 Shop/product cards
- 🔹 **Cart page** with quantities, remove, coupon codes (`HEALTH10`, `FREESHIP`)
- 🔹 Policy pages (Privacy, Terms)
- 🔹 Footer with newsletter input & socials
- 🔹 Zero frameworks, just HTML + Tailwind + a bit of JS

---

## Project Structure (typical)

```

/
├─ index.html
├─ about.html
├─ service.html
├─ blog.html
├─ blog/
│  └─ immune-habits.html  (example single post)
├─ cart.html
├─ contactus.html
├─ privacy.html
├─ terms.html
├─ shop.html
├─ img/
│  └─ ... (site images)
└─ styles/
├─ input.css            (if you rebuild Tailwind)
└─ output.css           (compiled CSS used by the pages)

````

> Pages link `../styles/output.css`. Keep your compiled Tailwind CSS at `styles/output.css`.

---

## Getting Started

### Option A — Use the compiled CSS (quickest)
No build step needed. Open `index.html` in a browser or serve the folder:

```bash
# from project root
npx http-server . -p 5173
# or
python3 -m http.server 5173
````

Visit `http://localhost:5173`.

### Option B — Rebuild Tailwind (if you edit utilities)

1. Install Tailwind locally:

```bash
npm install -D tailwindcss
npx tailwindcss init
```

2. Configure `tailwind.config.js` content paths (edit as needed):

```js
module.exports = {
  content: ["./**/*.html", "./**/*.js"],
  theme: {
    extend: {
      // ensure your brand colors are defined here as 'primary', 'secondary', 'accent'
    },
  },
  plugins: [],
};
```

3. Create `styles/input.css`:

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
/* custom css (optional) */
```

4. Build once (or watch):

```bash
npx tailwindcss -i ./styles/input.css -o ./styles/output.css --minify
# or watch during development
npx tailwindcss -i ./styles/input.css -o ./styles/output.css --watch
```

---

## Cart: how it works

* Data is stored in `localStorage` under key `hb_cart`.
* Each item: `{ id, name, price, img, qty }`.
* Coupons:

  * `HEALTH10` → 10% off
  * `FREESHIP` → free shipping
* Free shipping threshold is ₦50,000 (editable in `cart.html` script).

### Add to Cart (from product cards)

On any product page/button:

```html
<button onclick="addToCart({ id:'vitamin-c-1000', name:'Vitamin C 1000mg', price:3500, img:'/img/f5.png' }, true)">
  Add to Cart
</button>
```

The helper redirects to `/cart.html` when `true` is passed.

---

## Deployment

### Vercel

1. Push to GitHub (ensure `node_modules/` is gitignored).
2. Import the repo on Vercel.
3. **Framework preset:** “Other”.
4. If you’re rebuilding Tailwind on deploy, set the build command to:

   ```
   npx tailwindcss -i styles/input.css -o styles/output.css --minify
   ```

   Otherwise, no build step is required for pure static hosting.

Live preview (already deployed): **[https://health-boom-sand.vercel.app/](https://health-boom-sand.vercel.app/)**

---

## Contributing

1. Create a feature branch: `git checkout -b feat/something`
2. Commit: `git commit -m "feat: add something"`
3. Push: `git push -u origin feat/something`
4. Open a Pull Request.

---

## Housekeeping

* `.gitignore` should include:

  ```
  node_modules/
  .DS_Store
  .env
  .vscode/
  dist/
  .vercel/
  .cache/
  ```
* Do **not** commit `node_modules/`.
  If you did:
  `git rm -r --cached node_modules && git commit -m "remove node_modules" && git push`

---

## License

© HealthBoom Pharmaceuticals. All rights reserved.
