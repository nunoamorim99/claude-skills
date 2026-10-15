# nunoamorim99 — Claude Code plugins

One marketplace for all of Nuno Amorim's Claude Code plugins. Each plugin keeps its own repository, history and README; this repo only holds the catalog that points to them.

## Add the marketplace

```
/plugin marketplace add nunoamorim99/claude-skills
```

Then install only what you need:

| Plugin | What it does | Install |
|---|---|---|
| [**Agile-Ledger**](https://github.com/nunoamorim99/agile-ledger) | Scrum backlog, sprints, board, velocity and releases in plain Markdown | `/plugin install agile-ledger@nunoamorim99` |
| [**Cartographer**](https://github.com/nunoamorim99/cartographer) | Stakeholder documentation generated from your repositories | `/plugin install cartographer@nunoamorim99` |
| [**Idea-Ledger**](https://github.com/nunoamorim99/idea-ledger) | Capture ideas, track how each evolves, and version what ships, in two Markdown files | `/plugin install idea-ledger@nunoamorim99` |
| [**Fortify**](https://github.com/nunoamorim99/fortify) | Protection assessment against reverse engineering, cracking, scraping and cloning | `/plugin install fortify@nunoamorim99` |

Update everything later with `/plugin marketplace update nunoamorim99`.

## Team-wide

Commit this to a project's `.claude/settings.json` so everyone who opens the project gets the marketplace (enable the plugins you want):

```json
{
  "extraKnownMarketplaces": {
    "nunoamorim99": {
      "source": { "source": "github", "repo": "nunoamorim99/claude-skills" }
    }
  },
  "enabledPlugins": {
    "fortify@nunoamorim99": true
  }
}
```

## Adding a new plugin

1. Build it in its own repo with the plugin in `plugins/<name>/` (with `.claude-plugin/plugin.json`).
2. Add an entry to [`.claude-plugin/marketplace.json`](.claude-plugin/marketplace.json):
   ```json
   {
     "name": "<name>",
     "source": { "source": "git-subdir", "url": "https://github.com/nunoamorim99/<repo>.git", "path": "plugins/<name>", "ref": "main" },
     "description": "..."
   }
   ```
3. Push. Users get it with `/plugin marketplace update nunoamorim99`.

Plugin repos should **not** ship their own `.claude-plugin/marketplace.json` named `nunoamorim99` — marketplace names must be unique, so this repo is the only one.
