<p align="center">
  <img src="assets/cursor-plugin-card.png" alt="Motion for Cursor" width="100%">
</p>

# Motion

Animation for the web, done properly.

Cursor reaches for `framer-motion` two package names ago, animates `width` when
it means `scale`, and picks spring numbers that feel like nothing in
particular. This plugin fixes that.

## What you get

- **Animations that don't jank.** Cursor learns which properties the browser
  can animate on the compositor and which force a layout every frame.
- **The real API, not a guess.** Every Motion doc, example and UI section is
  searchable from inside the editor, so it builds from the official pattern
  instead of improvising.
- **A performance audit.** Grade any file, folder or URL S to F by what the
  animation actually costs, with the line, the reason and the fix.
- **CSS springs and bounces** as `linear()` curves, ready to paste.
- **Upgrade help** between Motion versions, and away from `framer-motion` or
  GSAP.

Type `/motion` to invoke it, or just animate something.

## What's in here

| Path | What it is |
| --- | --- |
| `rules/motion.mdc` | Fires the skill on animation work in JS, TS, Vue, Svelte, Astro and CSS files, and catches `framer-motion` imports. |
| `skills/motion/` | The skill: best practices, codex search, CSS easing, the MotionScore audit, transition preview. |
| `agents/motion-reviewer.md` | The audit subagent, used for scans bigger than a single file. |
| `mcp.json` | The Motion MCP server at `mcp.motion.dev`. |

## The MCP server

Remote, so there is nothing to install and nothing to keep updated. New
examples and docs are available the day they ship.

Four tools at any tier, five with Motion+:

- `search-motion-codex(platform, searchTerm)`: documentation, examples and
  Motion UI. Returns links; content is fetched only when it is read, so a large
  corpus costs nothing until it is used.
- `generate-css-easing(kind, duration, bounce)`: springs and bounces as CSS
  `linear()` curves.
- `motion-connect`: links the editor to a Motion account. Only appears while
  you are signed out.
- `save-transition(name, transition)`: needs an account.
- `open-transition-editor(...)`: the visual editor, Motion+ only. Falls back
  to a text response in editors that can't render it.

## Why the audit runs in a subagent

Finding every animation in a project means grepping and reading a lot of
source. On one file that is cheap and belongs inline. Across a directory it is
most of a context window, and separate folders don't need to see each other to
be graded. Its voice rules (assign a tier, name the line, no false positives)
also work better as a system prompt than as a section competing for attention
inside a longer skill.

## Links

- [motion.dev](https://motion.dev)
- [MotionScore](https://motion.dev/docs/motionscore)
- [Motion+](https://motion.dev/plus)
