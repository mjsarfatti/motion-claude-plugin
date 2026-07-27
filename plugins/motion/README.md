# Motion

Animation for the web, done properly.

This plugin makes Cursor good at animation: the official Motion and CSS
patterns, search across the whole Motion documentation and example catalogue,
CSS spring generation, and a performance audit that grades every animation by
what it actually costs the browser.

## Components

| Path | What it is |
| --- | --- |
| `rules/motion.mdc` | Glob-scoped rule. Fires the skill on animation work in JS, TS, Vue, Svelte, Astro and CSS files, and blocks `framer-motion` imports. |
| `skills/motion/` | The skill. Best practices, codex search, CSS easing, the MotionScore audit, transition preview. |
| `agents/motion-reviewer.md` | Audit subagent. Used for directory- and project-wide scans, so discovery does not fill the main context. |
| `mcp.json` | The remote Motion MCP server at `mcp.motion.dev`. |

## The MCP server

Remote, so there is nothing to install and nothing to keep updated. Four tools
at any tier, five with Motion+:

- `search-motion-codex(platform, searchTerm)` — documentation, examples and
  Motion UI. Returns resource links; content is fetched on read, so a large
  corpus costs nothing until it is used.
- `generate-css-easing(kind, duration, bounce)` — springs and bounces as CSS
  `linear()` curves.
- `motion-connect` — links the editor to a Motion account. Only appears while
  unauthenticated.
- `save-transition(name, transition)` — account tier and above.
- `open-transition-editor(...)` — the visual editor, Motion+ only. Degrades to
  a text response in hosts that do not render MCP Apps.

## Why the audit is a subagent

Discovery greps and reads a lot of source. On a single file that is cheap and
belongs inline; across a directory it is most of a context window, and separate
areas do not need to see each other to be graded. The agent's voice rules
(decisive, tier-assigning, no false positives) also work better as a system
prompt than as a section competing for attention inside a longer skill.

## Links

- [Motion](https://motion.dev)
- [MotionScore](https://motion.dev/docs/motionscore)
- [Motion+](https://motion.dev/plus)
