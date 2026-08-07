# code-lens — Zed extension (scaffold)

Starting point for Zed integration. **Status:** manifest + docs only.

**Upstream:** [github.com/dev-centr/code-lens](https://github.com/dev-centr/code-lens)

## Feasibility (honest)

Zed does **not** currently offer a VS Code–style webview for embedding `@code-lens/vanilla` with full glass-lens DOM animation inline. Practical paths:

| Approach | Feasibility |
|----------|-------------|
| **LSP server** returning inlay hints / code actions with role labels | Best v1 |
| Open external preview (`dev-centr.github.io/code-lens` or local static server) | Easy |
| Native text overlays with morph animation | Blocked on editor APIs |

See [Editor integrations](https://docs.devcentr.org/code-lens/editor-integrations.html).

## Recommended v1: code-lens LSP

Separate crate/package (future `extensions/zed/lsp/` or repo `code-lens-lsp`):

```
textDocument/codeLens / inlayHint
  → analyze range
  → AI or heuristics → lens document
  → return role-labeled inlays + command to open full preview
```

Wire in `extension.toml`:

```toml
[language_servers.code-lens]
name = "code-lens LSP"
language = "..."
```

(Exact Zed LSP registration fields depend on current schema — validate against [Zed extension docs](https://zed.dev/docs/extensions/developing-extensions) when implementing.)

## Install (development)

When implementation exists:

1. Clone [dev-centr/code-lens](https://github.com/dev-centr/code-lens)
2. `zed extensions install file:///path/to/extensions/zed`
3. Or dev link per Zed's extension development guide

## Roadmap

- [ ] Minimal LSP: role inlay hints on selection
- [ ] AI lens generation (shared with VS Code extension)
- [ ] Command: open browser preview with generated JSON5
- [ ] Track Zed APIs for rich inline overlays

## DevCentr

Tracked on DevCentr roadmap as IDE integration for code-lens — see DevCentr Todo & Roadmap.
