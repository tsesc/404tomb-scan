# Installing 404tomb-scan for OpenCode

## Prerequisites

- [OpenCode.ai](https://opencode.ai) installed
- Git installed

## Installation Steps

### 1. Clone the repository

```bash
git clone https://github.com/tsesc/404tomb-scan.git ~/.config/opencode/404tomb-scan
```

### 2. Register the Plugin

Create a symlink so OpenCode discovers the plugin:

```bash
mkdir -p ~/.config/opencode/plugins
rm -f ~/.config/opencode/plugins/404tomb-scan.js
ln -s ~/.config/opencode/404tomb-scan/.opencode/plugins/404tomb-scan.js ~/.config/opencode/plugins/404tomb-scan.js
```

### 3. Symlink Skills

Create a symlink so OpenCode's native skill tool discovers 404tomb-scan skills:

```bash
mkdir -p ~/.config/opencode/skills
rm -rf ~/.config/opencode/skills/404tomb-scan
ln -s ~/.config/opencode/404tomb-scan/skills ~/.config/opencode/skills/404tomb-scan
```

### 4. Restart OpenCode

Restart OpenCode. The plugin will automatically inject 404tomb-scan context.

Verify by describing a startup idea — the skill should trigger automatically.

## Usage

### Finding the Skill

Use OpenCode's native `skill` tool to list available skills:

```
use skill tool to list skills
```

### Loading the Skill

Use OpenCode's native `skill` tool to load the skill:

```
use skill tool to load 404tomb-scan/404tomb-scan
```

## Updating

```bash
cd ~/.config/opencode/404tomb-scan
git pull
```

## Troubleshooting

### Plugin not loading

1. Check plugin symlink: `ls -l ~/.config/opencode/plugins/404tomb-scan.js`
2. Check source exists: `ls ~/.config/opencode/404tomb-scan/.opencode/plugins/404tomb-scan.js`
3. Check OpenCode logs for errors

### Skill not found

1. Check skills symlink: `ls -l ~/.config/opencode/skills/404tomb-scan`
2. Verify it points to: `~/.config/opencode/404tomb-scan/skills`
3. Use `skill` tool to list what's discovered

### Tool mapping

When the skill references Claude Code tools:
- `WebFetch` → your native HTTP/fetch tool
- `Read`, `Write`, `Edit`, `Bash` → your native tools
- `Skill` tool → OpenCode's native `skill` tool

## Getting Help

- Report issues: https://github.com/tsesc/404tomb-scan/issues
