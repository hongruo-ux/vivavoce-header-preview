# Viva Voce header component — live preview

**Live preview: https://hongruo-ux.github.io/vivavoce-header-preview/**

The site at the repo root is a static build published via GitHub Pages, so anyone
with the link can click through it — no local setup needed.

The React source lives in [`source/`](source). Built from the five supplied JSX
exports and Figma references, using the supplied local photographs, Sharp Earth
and GT Alpina fonts, and original Figma logo/icons.

## Run the source locally

```sh
cd source
npm install
npm run dev
```

`npm run build` generates `dist/`. `npm run preview` previews the production build.

## Updating the live preview

The root-level `index.html`/`assets/`/`fonts/` are a built snapshot, not rebuilt
automatically. After making changes in `source/`, rebuild and copy the output back
to the repo root:

```sh
cd source
npx vite build --base=/vivavoce-header-preview/ --outDir ../dist-out
cd ..
rm -rf assets fonts index.html
mv dist-out/* . && rmdir dist-out
git add -A && git commit -m "Update preview build" && git push
```

## Components

- `source/src/VivaVoceHeader.jsx`: standalone responsive header with five mega menus, hover/click disclosure, Escape/outside-click dismissal, arrow-key navigation, search, and small-screen accordion navigation.
- `source/src/menuData.js`: menu labels, cards, stories, and default route generation.
- `source/src/header.css`: plain CSS and local font declarations.
- `source/src/main.jsx`: minimal preview. Clothing is initially expanded to match the reference. Same-origin links show a destination placeholder; replace this preview with your store app.

Use `<VivaVoceHeader />` for an initially closed header, or pass `initialMenu="Clothing"`. Use `getHref(label, section)` to map menu links to your real routes, and `onNavigate(label)` for optional integration. Utility links use conventional store paths; the search form submits `q` to `/search`. Commerce, account, and search-result pages are outside this header component.

Breakpoints: large desktop >=1280px, compact desktop 1024–1279px, small <1024px. The supplied exports describe desktop layouts; the small accordion layout is an adaptation. At 1280–1399px desktop spacing tightens to retain the full menu without overflow.

Source wording is preserved, including the dresses size label “6X - 6X” and accessories card caption “Linen Looks”. Change these in `menuData.js` if desired.
