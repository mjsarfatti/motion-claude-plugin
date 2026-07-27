# Add a plugin

Add a new plugin under `plugins/` and register it in `.claude-plugin/marketplace.json`.

## 1. Create plugin directory

Create a new folder:

```text
plugins/my-new-plugin/
```

Add the required manifest:

```text
plugins/my-new-plugin/.claude-plugin/plugin.json
```

Example manifest:

```json
{
  "name": "my-new-plugin",
  "displayName": "My New Plugin",
  "version": "0.1.0",
  "description": "Describe what this plugin does",
  "author": {
    "name": "Your Org"
  }
}
```

## 2. Add plugin components

Add only the components you need, at the plugin root (never inside `.claude-plugin/`):

- `skills/<skill-name>/SKILL.md` (YAML frontmatter required) — model-invoked, use this for anything that should apply automatically based on context
- `agents/*.md` (YAML frontmatter required)
- `commands/*.(md|mdc|markdown|txt)` (frontmatter recommended) — flat, user-invoked `/name` skills; prefer `skills/` for new plugins
- `hooks/hooks.json` and `scripts/*` for automation hooks
- `.mcp.json` for MCP server definitions
- `assets/logo.svg` — not a recognized `plugin.json` field in Claude Code, but harmless to keep for other tools or future use

Claude Code has no equivalent to Cursor's glob-triggered `rules/*.mdc` files. Fold any "always apply this guidance" instructions into the relevant skill's `description` (so it's picked up by skill-matching) or body instead.

## 3. Register in marketplace manifest

Edit `.claude-plugin/marketplace.json` and append a new entry:

```json
{
  "name": "my-new-plugin",
  "source": "./plugins/my-new-plugin",
  "description": "Describe your plugin"
}
```

`source` is the relative path from the repository root to the plugin folder.

## 4. Validate

```bash
node scripts/validate-template.mjs
claude plugin validate .
```

Fix all reported errors before committing.

## 5. Test locally

```bash
claude --plugin-dir ./plugins/my-new-plugin
```

Or install from this repo as a marketplace:

```bash
/plugin marketplace add ./
/plugin install my-new-plugin@motion
```

## 6. Common pitfalls

- Plugin `name` not kebab-case.
- `source` path in marketplace manifest does not match folder name.
- Missing `.claude-plugin/plugin.json` in plugin folder.
- Missing frontmatter keys (`name`, `description`) in skills, agents, or commands.
- Using `mcp.json` instead of `.mcp.json` (leading dot) for MCP server definitions.
- Putting `skills/`, `agents/`, `commands/`, or `hooks/` inside `.claude-plugin/` instead of at the plugin root.
- Broken relative paths for `logo`, `hooks`, or `mcpServers` in manifest files.
