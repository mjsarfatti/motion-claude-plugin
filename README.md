<p align="center">
  <img src="plugins/motion/assets/cursor-plugin-card.png" alt="Motion for Cursor" width="100%">
</p>

# Motion for Cursor

Cursor is good at most code. It is not good at animation. It reaches for
`framer-motion` two package names ago, animates `width` when it means `scale`,
and picks spring numbers that feel like nothing in particular.

This plugin fixes that. It is free, it installs in one click, and there is
nothing to configure.

## What you get

**Animations that don't jank.** Cursor learns which properties the browser can
animate on the compositor and which force a layout on every frame. It stops
reaching for `top` and `left`, and it knows when `will-change` helps and when
it is just burning memory.

**The real API, not a guess.** Every Motion doc, example and UI section is
searchable from inside the editor, so Cursor builds a carousel from the
official pattern instead of improvising one that half works. It searches before
it writes, not after you've read the diff.

**A performance audit, on demand.** Ask it to audit a file, a folder or the
whole project and you get every animation graded S to F by what it actually
costs the browser, with the specific line, the reason, and a fix. Point it at a
running URL and it opens a real browser to measure the page for you:

```
> audit src/components for animation performance
```

```
Rank: B     S ████████████████░░░░░░░  9 · 45%
            A █████████░░░░░░░░░░░░░░  5 · 25%
            C ██████░░░░░░░░░░░░░░░░░  4 · 20%
            D ██░░░░░░░░░░░░░░░░░░░░░  2 · 10%

src/Sheet.tsx:34 — Tier D
What:     `height` transition on `.sheet-panel`
Why:      height triggers layout, then paint, then composite, every frame
Upgrade:  Motion's `layout` prop (B) or a `scaleY` transform (S)
```

**CSS springs, without the calculator.** Ask for a spring that lasts 0.3
seconds and is quite bouncy, and get a `linear()` curve you can paste into a
stylesheet. Same for bounce easings, which is the one people always write by
hand and always get slightly wrong.

**No more `framer-motion`.** A scoped rule catches the import in any file you
touch and offers to migrate it, and the upgrade guides walk the versions in
order rather than dumping a summary that silently reorders the steps.

## Install

Find **Motion** in the Cursor Marketplace and install it. That's the whole
setup.

Type `/motion` to talk to it directly, or just animate something and it will
show up on its own.

## Motion+

Everything above is free and always will be. Two things sit behind an account,
and Cursor tells you when you reach them.

**A free Motion account** keeps a runtime audit report so it builds into
history, and remembers transitions you've tuned so they get offered again on
your next project.

**[Motion+](https://motion.dev/plus)** adds paste-ready source for every
example and Motion UI section, the Motion+ documentation, and a visual editor
for tuning a transition against a live preview instead of guessing at numbers.
Without it you still see what exists, what it uses, how it scores and a link to
the live demo, so you always know what's there.

Ask Cursor to sign you in and it hands you a link. Nothing gets pasted into
chat.

## What's in here

```
plugins/motion/
  rules/            fires the skill on animation work, blocks framer-motion
  skills/motion/    best practices, docs search, CSS easing, the audit
  agents/           the audit subagent, for scans bigger than one file
  mcp.json          the Motion MCP server
```

The MCP server is remote, so there's no package to install and nothing to keep
up to date. New examples and docs appear the day they ship.

## Links

- [motion.dev](https://motion.dev)
- [Documentation](https://motion.dev/docs)
- [Examples](https://examples.motion.dev)
- [Motion UI](https://motion.dev/ui)
- [MotionScore](https://motion.dev/docs/motionscore)

---

Adding another plugin to this repo: see `docs/add-a-plugin.md`. Run
`node scripts/validate-template.mjs` before submitting.
