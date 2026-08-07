<a id="readme-top"></a>
<div align="center">
  <a href="https://github.com/dev-centr/code-lens/graphs/contributors"><img src="https://img.shields.io/github/contributors/dev-centr/code-lens.svg?style=for-the-badge" alt="Contributors"></a>
  <a href="https://github.com/dev-centr/code-lens/network/members"><img src="https://img.shields.io/github/forks/dev-centr/code-lens.svg?style=for-the-badge" alt="Forks"></a>
  <a href="https://github.com/dev-centr/code-lens/stargazers"><img src="https://img.shields.io/github/stars/dev-centr/code-lens.svg?style=for-the-badge" alt="Stargazers"></a>
  <a href="https://github.com/dev-centr/code-lens/issues"><img src="https://img.shields.io/github/issues/dev-centr/code-lens.svg?style=for-the-badge" alt="Issues"></a>
  <a href="https://github.com/dev-centr/code-lens/blob/main/LICENSE"><img src="https://img.shields.io/github/license/dev-centr/code-lens.svg?style=for-the-badge" alt="License"></a>
  <a href="https://github.com/dev-centr/code-lens/actions/workflows/pages.yml"><img src="https://github.com/dev-centr/code-lens/actions/workflows/pages.yml/badge.svg" alt="Deploy GitHub Pages"></a>

  <h3 align="center">code-lens</h3>
  <p align="center">
    One code snippet, multiple pedagogical lenses — portable JSON5 spec and &lt;code-lens&gt; web component with framework adapters.
    <br />
    <a href="https://dev-centr.github.io/code-lens/"><strong>Live demo »</strong></a>
    <br />
    <br />
    <a href="https://github.com/dev-centr/code-lens/issues">Report Bug</a>
    &middot;
    <a href="https://github.com/dev-centr/code-lens/issues">Request Feature</a>
  </p>
</div>

<details>
  <summary>Table of Contents</summary>
  <ol>
    <li><a href="#about-the-project">About The Project</a></li>
    <li><a href="#installation">Installation</a></li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
  </ol>
</details>

## About The Project

One snippet, multiple pedagogical naming conventions — the real lens for code examples (not a metaphor).

### Delivery model

**In Solid/React/Next you install a component** — e.g. `import { CodeLens } from "@code-lens/solid"`. Under the hood one shared engine powers every framework package; you don't touch that unless you're on plain HTML.

| Layer | Package |
|-------|---------|
| Component (your import) | `@code-lens/solid`, `@code-lens/react`, … |
| Skin | `@code-lens/css` or `@code-lens/tailwind` (planned) |
| Engine | `@code-lens/vanilla` + `@code-lens/core` (pulled in automatically) |

→ [docs/ecosystem.md](docs/ecosystem.md)

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Installation

```bash
pnpm install
pnpm dev          # SolidJS + solid-ui demo (port 5174) — mounts vanilla <code-lens>
```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Usage

```js
import "@code-lens/css";
import { createCodeLens, registerCodeLens } from "@code-lens/vanilla";
import { parseLensBlock, parseThemes, parseUi } from "@code-lens/core";

registerCodeLens();
const el = createCodeLens({
  document: parseLensBlock(blockJson5),
  themes: parseThemes(themesJson5),
  ui: parseUi(uiJson5),
}, "earth");
document.body.appendChild(el);
```

```html
<code-lens theme="earth" appearance="auto"></code-lens>
```

`appearance`: `auto` | `light` | `dark` — independent of pedagogical color theme.

`slotHighlight`: `plain` | `box` — rounded highlight on changeable tokens (default `plain`).

### Portable spec

| File | Role |
|------|------|
| [`spec/examples/*.json5`](spec/examples/) | Aligned token data per lens |
| [`spec/themes.json5`](spec/themes.json5) | Color schemes (light/dark per theme) |
| [`spec/ui.json5`](spec/ui.json5) | Interaction + animation |

- [Ecosystem / delivery model](docs/ecosystem.md)
- [Full specification](docs/specification.md)
- [AI / LLM reproduction spec](docs/ai-reproduction-spec.md) — normative porting detail
- [Glass lens capabilities](docs/glass-lens-capabilities.md)
- [Implementation registry](implementations/REGISTRY.md)

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## License

Distributed under the MIT License. See `LICENSE`.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Contact

DevCentr.org — support@devcentr.org

Project Link: [https://github.com/dev-centr/code-lens](https://github.com/dev-centr/code-lens)

Site: [https://dev-centr.github.io/code-lens/](https://dev-centr.github.io/code-lens/)

<p align="right">(<a href="#readme-top">back to top</a>)</p>
