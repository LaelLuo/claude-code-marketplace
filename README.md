# OpenSpec Marketplace

Official plugin marketplace for OpenSpec spec-driven development tools.

## About

This marketplace provides Claude Code plugins that enhance the OpenSpec workflow, making spec-driven development seamless and intuitive.

## Available Plugins

### openspec-workflow

Automatically enables OpenSpec spec-driven development workflow in projects with `openspec/` directory.

**Features:**
- Auto-detection of OpenSpec projects
- Comprehensive workflow guidance (Create → Implement → Archive)
- Intelligent prompting for proposal creation
- Complete CLI command reference
- Spec format and troubleshooting guides

**Installation:**
```bash
# Add this marketplace to Claude Code
# Edit ~/.claude/plugins/known_marketplaces.json and add:
{
  "openspec-marketplace": {
    "source": {
      "source": "github",
      "repo": "Fission-AI/openspec-marketplace"
    },
    "installLocation": "~/.claude/plugins/marketplaces/openspec-marketplace"
  }
}

# Then install the plugin
cc plugin install openspec-workflow
```

## Using This Marketplace

### For Users

1. **Add marketplace to Claude Code:**

   Edit `~/.claude/plugins/known_marketplaces.json`:
   ```json
   {
     "openspec-marketplace": {
       "source": {
         "source": "github",
         "repo": "Fission-AI/openspec-marketplace"
       },
       "installLocation": "~/.claude/plugins/marketplaces/openspec-marketplace",
       "lastUpdated": "2026-01-12T00:00:00.000Z"
     }
   }
   ```

2. **Browse available plugins:**
   ```bash
   cc plugin list --marketplace openspec-marketplace
   ```

3. **Install a plugin:**
   ```bash
   cc plugin install openspec-workflow
   ```

### For Plugin Developers

Want to add your OpenSpec-related plugin to this marketplace?

1. **Fork this repository**
2. **Add your plugin** to `plugins/` directory
3. **Update** `.claude-plugin/marketplace.json` with your plugin entry
4. **Submit a pull request**

**Plugin requirements:**
- Must be OpenSpec-related
- Must follow Claude Code plugin standards
- Must include comprehensive documentation
- Must pass validation tests

## Marketplace Structure

```
openspec-marketplace/
├── .claude-plugin/
│   └── marketplace.json      # Marketplace configuration
├── plugins/
│   └── openspec-workflow/    # Plugin directory
│       ├── .claude-plugin/
│       │   └── plugin.json
│       ├── skills/
│       ├── hooks/
│       └── README.md
└── README.md                 # This file
```

## Plugin Categories

- **development**: Development workflow tools
- **productivity**: Productivity enhancements
- **documentation**: Documentation tools
- **validation**: Validation and quality tools

## Support

- **Issues**: https://github.com/Fission-AI/OpenSpec/issues
- **Discord**: https://discord.gg/YctCnvvshC
- **Documentation**: https://github.com/Fission-AI/OpenSpec

## License

MIT License - see individual plugins for their licenses.
