<a id="readme-top"></a>

[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![License][license-shield]][license-url]
[![Docs | Dev-Centr](https://img.shields.io/badge/docs-Dev--Centr-22c55e)](https://docs.devcentr.org/code-lens/)
[![Deploy GitHub Pages](https://github.com/dev-centr/code-lens/actions/workflows/pages.yml/badge.svg)](https://github.com/dev-centr/code-lens/actions/workflows/pages.yml)

<div align="center">
  <h1>code-lens</h1>
  <p>One code snippet, multiple pedagogical lenses — portable JSON5 spec and &lt;code-lens&gt; web component with framework adapters.</p>
  <p>
    <a href="https://dev-centr.github.io/code-lens/">Live demo</a>
    ·
    <a href="https://docs.devcentr.org/code-lens/">Docs | Dev-Centr</a>
    ·
    <a href="https://github.com/dev-centr/code-lens/issues">Report Bug</a>
    ·
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

→ [Delivery model docs](https://docs.devcentr.org/code-lens/ecosystem.html)

## Installation

```bash
pnpm install
pnpm dev          # SolidJS + solid-ui demo (port 5174) — mounts vanilla <code-lens>
```

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

- [Ecosystem / delivery model](https://docs.devcentr.org/code-lens/ecosystem.html)
- [Full specification](https://docs.devcentr.org/code-lens/specification.html)
- [AI / LLM reproduction spec](https://docs.devcentr.org/code-lens/ai-reproduction-spec.html) — normative porting detail
- [Glass lens capabilities](https://docs.devcentr.org/code-lens/glass-lens-capabilities.html)
- [Implementation registry](implementations/REGISTRY.md)

## License

MIT

## Contact

DevCentr.org - support@devcentr.org

Project Link: https://github.com/dev-centr/code-lens

Site: https://dev-centr.github.io/code-lens/

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- MARKDOWN LINKS & IMAGES -->
[contributors-shield]: https://img.shields.io/github/contributors/dev-centr/code-lens.svg?style=for-the-badge
[contributors-url]: https://github.com/dev-centr/code-lens/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/dev-centr/code-lens.svg?style=for-the-badge
[forks-url]: https://github.com/dev-centr/code-lens/network/members
[stars-shield]: https://img.shields.io/github/stars/dev-centr/code-lens.svg?style=for-the-badge
[stars-url]: https://github.com/dev-centr/code-lens/stargazers
[issues-shield]: https://img.shields.io/github/issues/dev-centr/code-lens.svg?style=for-the-badge
[issues-url]: https://github.com/dev-centr/code-lens/issues
[license-shield]: https://img.shields.io/github/license/dev-centr/code-lens.svg?style=for-the-badge
[license-url]: https://github.com/dev-centr/code-lens/blob/main/LICENSE
