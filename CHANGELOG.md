# Changelog

## 1.0.57 — 2026-06-17

### Changed

- **Branch connectors default** — `├─` `└─` `│` use **fixed rgb(72)** unless you set `/cc-tools branch theme` or a custom gray. `/cc-tools branch reset` restores that default.

### Fixed

- **Resume / session switch theme mix** — on `session_start` (especially `resume`, `new`, `fork`), rebind tool chrome from the active pi theme (palette cache bust, Shiki light/dark, branch epoch, full UI invalidate) plus deferred passes so other extensions can `setTheme` in the same tick without cross-package coupling.
- **Hidden thinking summary** sticks on "Thinking…" when `thinking_end` lands on the same frame as Pi's `updateContent` — per-message active/duration flags plus a deferred UI refresh so "Thought for Ns" appears right away.
- **Spinner footer** applies the same deferred sync on thinking start/end so "thought for Ns" shows immediately when thinking finishes.

### Changed

- **Unified container chrome** — user message box, tool outline rules, rounded code fences, and branch connectors share one theme-derived color (`dim` → `muted` → `borderMuted`) so light themes do not get harsh dark user borders or overly bright branches.
- **User message fill** — strip nested `Box` → `Markdown` backgrounds so the framed user row stays transparent and matches terminal chrome (fixes dark slabs inside the border).
- **Light-theme branch chrome** — when the active theme has a light panel, outline/branch colors are attenuated toward mid-gray so `├─` `└─` `│` and user borders are not washed-out bright; `/cc-tools status` no longer implies theme mode uses fixed gray 72.

## 1.0.56 — 2026-06-17

### Fixed

- **Theme-adaptive tool chrome** re-derives when the active pi theme’s resolved colors change (fingerprint of `success`, `borderMuted`, `accent`, etc.), not only when the theme object identity changes. Fixes stale borders/dots/diffs after external theme sync (e.g. Ghostty) without coupling to other extensions.

### Changed

- Palette cache tracks `theme.name` plus color fingerprint; removed cross-extension global bust symbols.

## 1.0.55 — 2026-06-17

- Internal: theme name in cache key (superseded by 1.0.56 fingerprint).

## 1.0.54 — 2026-06-17

### Changed

- **Branch connectors** (`├─` `└─` `│`): default **`theme`** mode (was fixed gray). Uses **dim → muted → thinkingText**, same family as thought/gray prose.
- **Pending tool dots** (○): use theme **dim** when theme-adaptive; grouped counts use the same pending color.

### Fixed

- `/cc-tools branch reset` restores theme-following default, not fixed rgb(72).

## 1.0.53 — 2026-06-17

### Fixed

- **Light theme edit/write diffs**: auto-select Shiki `github-light` vs `github-dark`; light panel tint base; Shiki contrast normalization for light backgrounds.
- **Light theme tool status chrome**: pending ○ / blink uses softer `borderMuted` instead of heavy `muted`; grouped tool pending counts match.

## 1.0.52

- Theme-adaptive diff and branch tooling updates.