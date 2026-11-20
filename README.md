# MUBO — Cloudflare-ready React storefront

This is the **React source project**. It is not a prebuilt `dist` folder. Cloudflare must build it before it can be served.

## Recommended: Cloudflare Pages via GitHub

1. Extract this ZIP on your computer.
2. Create a GitHub repository and upload the **contents** of the `mubo-storefront` folder (the `package.json`, `index.html`, `src/`, `public/`, etc.). Do not upload the ZIP as a website asset.
3. In Cloudflare Dashboard, open **Workers & Pages → Create application → Pages → Connect to Git**.
4. Select your repository.
5. Set the build configuration:
   - Framework preset: **Vite** (or None)
   - Build command: `npm run build`
   - Build output directory: `dist`
   - Root directory: `/` if the repository contains the project files at its top level. If you put the project inside a subfolder, set that folder as the root directory.
6. Deploy. Cloudflare installs the packages, runs Vite, and publishes `dist`.

The `public/_redirects` file is copied into `dist` and provides SPA fallback routing so direct visits to routes such as `/shop` and `/product/1` work.

## Alternative: Cloudflare Pages Direct Upload

Direct Upload needs the **built output**, not this source ZIP. On a computer with Node.js installed:

```bash
npm install
npm run build
```

Then in Cloudflare choose **Workers & Pages → Create application → Pages → Direct Upload** and upload the contents of the generated `dist` folder (or a ZIP containing the contents of `dist`). Do not upload the project root or `src` folder.

## Alternative: Cloudflare Workers with static assets

This project includes `wrangler.jsonc` for a Workers static-assets deployment. After installing dependencies and building:

```bash
npx wrangler login
npm run deploy:workers
```

This deploys the static Vite build as assets on a Worker. Pages and Workers are separate deployment products; use the Pages instructions above if your goal is a normal website hosted on Cloudflare Pages.

## Local development

```bash
npm install
npm run dev
```

## Included
- Home, Shop, Product Details, Collections, About, Contact, Shopping Bag and Wishlist pages
- Product search, category/type filtering and sorting
- Product size and colour selection
- Add/remove/update bag quantities
- Wishlist saved in localStorage
- Responsive desktop, tablet and mobile layouts
- No payment gateway or checkout processing

## Before commercial launch
The store uses remote Unsplash image URLs as real-photo placeholders. Review each image and its usage rights before commercial publication. Product names, descriptions, prices and contact details are illustrative demo content. Connect real catalogue, inventory, contact/newsletter services, and publish accurate shipping, returns, privacy and terms policies before accepting customers.
