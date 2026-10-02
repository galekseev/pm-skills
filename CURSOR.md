# Installing in Cursor

This fork adds Cursor plugin manifests next to the Claude Code ones, so the plugins install into Cursor with their slash commands, not only as loose skills.

- `.cursor-plugin/marketplace.json` at the root lists the plugins packaged for Cursor.
- Each listed plugin has a `.cursor-plugin/plugin.json`; its `skills/` and `commands/` folders are discovered automatically.

Packaged plugins: `pm-product-discovery`, `pm-product-strategy`, `pm-execution`. The other plugins are unchanged from upstream and can still be used as skills by copying their `skills/*` folders into `.cursor/skills/`.

## Install

- **IDE**: Customize → Plugins → From GitHub Repository → `https://github.com/galekseev/pm-skills`, then install the plugins you need (project or user scope).
- **Team marketplace** (Teams/Enterprise): Dashboard → Plugins & MCPs → Team Marketplaces → Add Marketplace → Import from Repo with the same URL.
- **CLI**: `agent plugin marketplace add https://github.com/galekseev/pm-skills`, then install from `/plugin`.
- **Local development**: copy a plugin folder into `~/.cursor/plugins/local/<plugin>/` and run "Developer: Reload Window".

## Commands in Cursor

The command files use only `description` and `argument-hint` in their frontmatter; Cursor reads `description` and ignores `argument-hint`. Text typed after the command (`/write-prd Protocol fee switch`) is passed along as the rest of the message. Chained workflows such as `/discover` pause at the same checkpoints as in Claude Code.

## Keeping in sync with upstream

Upstream is [phuryn/pm-skills](https://github.com/phuryn/pm-skills). The Cursor manifests live only in `.cursor-plugin/` folders and this file, so merging upstream `main` should not conflict.
