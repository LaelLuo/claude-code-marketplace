# OpenSpec Workflow Plugin

Automatically enables OpenSpec spec-driven development workflow in Claude Code when working in projects with an `openspec/` directory.

## Features

- **Auto-detection**: Automatically detects OpenSpec projects on session start
- **Workflow guidance**: Provides comprehensive OpenSpec workflow knowledge through skills
- **Smart prompting**: Reminds you to create proposals when appropriate
- **Zero configuration**: No need to run `openspec init` or modify CLAUDE.md

## How It Works

### Session Start Detection
When you start a Claude Code session, the plugin checks if `openspec/project.md` exists. If found, it:
- Notifies Claude that this is an OpenSpec project
- Loads the OpenSpec workflow skill automatically
- Enables spec-driven development patterns

### User Prompt Monitoring
When you mention keywords like "proposal", "spec", "change", "feature", or "breaking", the plugin:
- Reminds Claude to follow OpenSpec workflow
- Suggests creating a change proposal for appropriate scenarios
- Allows direct fixes for bugs, typos, and minor changes

## Components

### Skills
- **openspec-workflow**: Complete OpenSpec workflow knowledge including:
  - Three-stage workflow (Create → Implement → Archive)
  - CLI command reference
  - Spec format and delta operations
  - Common troubleshooting

### Hooks
- **SessionStart**: Detects OpenSpec projects and activates workflow
- **UserPromptSubmit**: Monitors user input for workflow-relevant keywords

## Installation

### For OpenSpec Projects
This plugin is designed to be bundled with OpenSpec. When you run `openspec init`, it will be automatically configured.

### Manual Installation
Copy this plugin directory to your Claude Code plugins location:
```bash
cp -r openspec-workflow ~/.claude/plugins/
```

Or use it project-locally:
```bash
mkdir -p .claude-plugin
cp -r openspec-workflow .claude-plugin/
```

## Usage

Once installed, the plugin works automatically:

1. **Start a session** in an OpenSpec project
2. **Mention features or changes** you want to implement
3. **Claude will guide you** through the OpenSpec workflow

Example:
```
You: I want to add two-factor authentication

Claude: I'll help you create an OpenSpec change proposal for two-factor authentication.
        Let me scaffold the proposal structure...
```

## Requirements

- Claude Code (any recent version)
- OpenSpec CLI installed (`npm install -g @fission-ai/openspec`)
- Project initialized with `openspec init`

## License

MIT
