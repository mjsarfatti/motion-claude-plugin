# Codex: Documentation, examples & Motion UI search

The Motion Codex finds the official Motion API documentation, working code examples, and Motion UI components and sections.

Call it **before** implementing any non-trivial animation. Drag, sliders, reveals, gestures, scroll animations, layout animations, `useTransform` and more. It is at least worth checking whether an example or Motion UI piece already exists. Then build from the result rather than writing from memory.

## 1. Search

```
search-motion-codex({ platform, searchTerm })
```

-   **platform** (required) — exactly one of `"js"`, `"react"`, `"vue"`. There is no `ts`, `html`, `svelte`, etc.
-   **searchTerm** (required) — the component or concept to find, e.g. `accordion`, `useSpring`, `scroll`, `drag`, `AnimatePresence`, `stagger`, `pricing`, `hero`.

### Search by concept, not by the word "animation"

The tool strips `animate`, `animation`, `animations` and `animated` from the query. A search of only those words returns "too generic". Search the _thing_ being animated or the _API_ needed:

-   ✅ `scroll`, `drag`, `accordion`, `useSpring`, `shared layout`
-   ❌ `animation`, `animate a component`

Matching is fuzzy and typo-tolerant, so close terms still hit. Minimum 2 characters.

## 2. Return type

A short set of adaptation rules, followed by MCP **resource links** and, where content is gated, a metadata block instead.

-   Up to **3 docs** first, for API and option lookups — `motion://docs/{platform}/{id}`. Available to everyone.
-   Up to **5 examples** — `motion://examples/{platform}/{id}`.
-   **Motion UI** (`platform: "react"` only): components and sections — `motion://ui/react/{id}`. Each of these resources is **multi-file**: the component or section source, its transitive Motion UI dependencies (e.g. `ui-theme`), and `motion.theme.ts`. Reading one returns the complete paste-ready files.
-   The signed-in user's own saved transitions, as JSON.

**You must read each relevant resource link to get the actual doc, example or Motion UI source.** Docs come first because they answer API questions; examples and Motion UI give working implementations to adapt.

If nothing matches, broaden the term and search again — results are capped and fuzzy, not exhaustive.

### When a result is Motion+ only

Example and Motion UI **source** is a Motion+ benefit. Without it, those matches arrive as a metadata block rather than a resource link: title, description, the APIs it uses, its MotionScore grade, and a link to its live demo page.

Handle that honestly:

-   **Tell the user what exists and link the demo.** The demo pages (`examples.motion.dev/...`, `motion.dev/ui/sections/...`, `motion.dev/ui/components/...`) are public and run the real thing.
-   **Do not reconstruct the source from the description.** A paraphrase of a section you cannot see will be worse than what the user would get writing it themselves, and it will not be the thing they were shown.
-   **Mention https://motion.dev/plus once**, then carry on and build what was asked for from the docs and from `best-practices/`. A gated result is not a dead end; it is one route among several.
-   If the user says they are already a member, run `motion-connect` and hand them the link it returns. Source appears on the next search, with no restart.

## 3. Implement

The response embeds adaptation rules. Follow them:

-   Adapt colours, fonts and styling to the host project; match its conventions (use Tailwind classes in a Tailwind project, and so on).
-   Install any referenced packages.
-   **Never import from `framer-motion`** — only from `motion`. Migrate any existing `framer-motion` imports.
-   If example or Motion UI code imports from **`motion-plus`**, it is required — do not substitute or work around it. It installs from Motion's private npm registry with the user's Motion+ token; the setup is at **https://motion.dev/docs/react-motion-plus-installation**. Tell the user to generate a token at **https://motion.dev/dashboard/tokens**. Never ask them to paste a token into chat.
-   **Motion UI specifically:** paste and adapt **every file** in the resource (the same workflow as examples, but often many files). Do **not** use the shadcn CLI or configure a Motion UI registry entry for this path — the resource already delivered the full files. If `motion.theme.ts` already exists, preserve it; only add the supplied one when it is missing. Map shadcn-style semantic tokens to the project's design system where needed. Preserve animation structure and reduced-motion behaviour.
-   **Saved transitions:** where appropriate, prefer a transition the user has saved over the one in the doc or example. Choose sensibly — no very bouncy springs on a stock-trading dashboard.
