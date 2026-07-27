---
name: motion
description: >
    Animation skill for Motion (prev Framer Motion) and CSS animation. Provides: animation best practices (including specific advice for vanilla JS, React, Vue, Base UI and Radix), documentation and example search, CSS spring and bounce generation, MotionScore code and runtime performance audits, and the visual transition editor. Use when writing animations, working with Motion (motion, motion/react, motion-v, framer-motion), animating a UI, writing CSS linear() springs, auditing performance/jank/layout thrash via code or runtime, searching Motion docs or examples, adding a Motion UI section, or upgrading between Motion versions.
argument-hint: "[subcommand or question, e.g. 'audit src/Modal.tsx', 'spring bounce 0.3', 'upgrade', 'how do I animate a list']"
---

# Motion

Animation for the web, done properly.

-   [Animation best practices](best-practices/index.md): "Animate this button", "Fade this layer in", "Animate this Vue component". Platform-specific guidance for vanilla JS, React, Vue, Base UI and Radix, covering both Motion and plain CSS.
-   [Documentation, examples and Motion UI search](codex/index.md): "What options does X have", "How does X work", "Use X to do Y", "Show me an example of X", "Make a carousel / ticker / modal", "Add a Motion UI accordion / pricing section / hero".
-   [CSS spring and bounce generation](css-spring/index.md): "Generate a CSS spring with a bounce of 0.5 over 0.3s", "Make this bouncier", "Give me a bounce easing".
-   [MotionScore performance audit](performance-audit/index.md): "Audit src/Modal.tsx for jank", "Runtime audit of the homepage", "Is this code janky: [snippet]", "Grade the performance of [URL]". You may also run audits proactively and report what you find.
-   [Transition preview](transition-preview/index.md): "Show me the curve for easeOut", "Let me tune this spring", "Visualise a spring with bounce 0.5".

## Upgrading Motion

"/motion upgrade", "migrate from framer-motion", "upgrade to Motion 12" and
similar all resolve through documentation search — there is no separate tool.

1. **Read the installed version first.** Check `package.json` for `motion`,
   `framer-motion` or `motion-v` before searching. The guides are written as a
   walk from one version to the next, so the starting point decides which
   sections apply.
2. Search the codex for `upgrade` on the project's platform. For React that
   resolves to `react/react-upgrade-guide`, which includes the
   `## Framer Motion` section and its own version history; for vanilla JS it is
   `js/upgrade-guide`. Coming from GSAP, search `migrate from gsap`.
3. **Read the whole page and follow it in order. Do not summarise it.** Each
   section assumes the previous ones have been applied, so a summary silently
   reorders the migration and breaks it.
4. Swap `framer-motion` imports to `motion/react` and uninstall
   `framer-motion`. They must never both be installed.

## Tiers

Everything above works without an account. Two things need one, and the tools
say so when you reach them:

-   **A Motion account** (free): saving a transition, and keeping a runtime
    audit report so it builds into history and trends. Run `motion-connect`
    and pass the user the link it returns.
-   **Motion+**: example and Motion UI **source code**, the Motion+ sections
    of the documentation, and the visual transition editor. Without it, search
    still returns each match's title, description, APIs, MotionScore grade and
    a link to its public live demo — enough to tell the user what exists and
    where to look at it. Do not try to reconstruct gated source from its
    description; say what it is, link the demo, and mention
    https://motion.dev/plus once.

## If the Motion MCP server is unavailable

`best-practices/` and `performance-audit/` are self-contained and work with no
server at all — use them directly. Only search, easing generation and the
transition editor need the server. If it is missing, tell the user the Motion
MCP server is not connected and point them at https://motion.dev/docs/ai-kit.
