# code-lens GitHub Pages demo

Marketing + live demo site for [code-lens](https://github.com/dev-centr/code-lens), deployed to GitHub Pages via [`.github/workflows/pages.yml`](../.github/workflows/pages.yml).

**Stack:** [SolidJS](https://www.solidjs.com) · [solid-ui](https://www.solid-ui.com) (Kobalte + Tailwind) · `@code-lens/solid` · `@code-lens/vanilla`

## Develop locally

From the repo root:

```bash
pnpm install
pnpm dev
```

Opens Vite on port **5174**. The demo loads spec JSON5 from `../spec/` and renders the live `<code-lens>` block through the Solid wrapper.

## Build

```bash
pnpm --filter @code-lens/core build
pnpm --filter @code-lens/vanilla build
pnpm --filter @code-lens/demo build
```

Output: `demo/dist/` (uploaded by CI).

## solid-ui components

UI primitives live under `src/components/ui/` — copied from the [solid-ui](https://github.com/stefan-karger/solid-ui) registry (same copy-paste model as shadcn/ui). Config: `ui.config.json`.

To add more components (when the CLI works in your environment):

```bash
cd demo
pnpm dlx solidui-cli@latest add dialog tabs
```

## GitHub Pages URL

Published from the `dev-centr/code-lens` repository at **https://dev-centr.github.io/code-lens/**.
Product documentation lives on the Dev-Centr docs portal: **https://docs.devcentr.org/code-lens/**.

`vite.config.ts` uses `base: "./"` so asset paths work under a subdirectory.
