# Motion for Cursor

The official Cursor plugin for [Motion](https://motion.dev), the animation
library for the web. Free, and zero-config: install it and Cursor gets better
at animation immediately.

## What it does

- **Best practices** for Motion and plain CSS, with platform-specific guidance
  for vanilla JS, React, Vue, Base UI and Radix. Covers the things that are
  easy to get subtly wrong: when to use `transform` versus independent
  transforms, where `will-change` helps and where it hurts, how to pick a
  spring that suits the product.
- **Documentation and example search** over the whole Motion codex, delivered
  as MCP resources so full pages cost nothing until they are read.
- **CSS spring and bounce generation** as `linear()` easing curves.
- **The MotionScore performance audit**, which grades every animation in a file
  or a project S through F by its render-pipeline cost, and tells you which
  ones have a real upgrade path. A runtime audit runs locally against any URL
  via `npx motionscore`.
- **Upgrade guidance** between Motion versions, and from `framer-motion` or
  GSAP.

Type `/motion` to invoke it directly, or just animate something — a scoped rule
fires the skill on animation work in any JS, TS, Vue, Svelte, Astro or CSS file.

## Tiers

Everything above works with no account and no configuration.

| | Free | Motion account | [Motion+](https://motion.dev/plus) |
|---|:--:|:--:|:--:|
| Documentation search and full pages | ✅ | ✅ | ✅ |
| Best practices, upgrade guides | ✅ | ✅ | ✅ |
| MotionScore code audit | ✅ | ✅ | ✅ |
| MotionScore runtime audit (`npx motionscore`) | ✅ | ✅ | ✅ |
| CSS spring and bounce generation | ✅ | ✅ | ✅ |
| Example and Motion UI metadata, grades and live demos | ✅ | ✅ | ✅ |
| Saving a runtime audit report (history, trends) | — | ✅ | ✅ |
| Saved transitions | — | ✅ | ✅ |
| Example source code | — | — | ✅ |
| Motion UI source (multi-file) | — | — | ✅ |
| Motion+ documentation | — | — | ✅ |
| Visual transition editor | — | — | ✅ |

To connect an account, ask the agent to sign you in: it calls `motion-connect`
and gives you a link. Nothing is ever pasted into chat.

In CI, or in a client that does not keep a session, set `MOTION_TOKEN` in the
environment instead — the MCP config already reads it. Generate one at
[motion.dev/dashboard/tokens](https://motion.dev/dashboard/tokens).

## Repository layout

```
.cursor-plugin/marketplace.json   marketplace manifest
plugins/motion/
  .cursor-plugin/plugin.json      plugin manifest
  rules/motion.mdc                glob-scoped pointer at the skill
  skills/motion/                  the skill and its capability directories
  agents/motion-reviewer.md       audit subagent for directory-wide scans
  mcp.json                        remote MCP server (mcp.motion.dev)
  assets/logo.svg
```

The MCP server is remote, so there is nothing to install, nothing to keep
updated, and no corpus on disk. Entitlement resolves per request, so buying
Motion+ takes effect on the next call rather than on the next restart.

## Development

```bash
node scripts/validate-template.mjs
```

Run before every submission. To test locally, install the plugin from this
directory in Cursor and confirm `/motion` fires, the rule triggers on a `.tsx`
file without the skill being named, and the MCP server connects anonymously.

To add another plugin, see `docs/add-a-plugin.md`.

## Links

- [Motion](https://motion.dev)
- [Documentation](https://motion.dev/docs)
- [Examples](https://examples.motion.dev)
- [Motion UI](https://motion.dev/ui)
- [MotionScore](https://motion.dev/docs/motionscore)
