# Installing 404tomb-scan for Codex

## Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/tsesc/404tomb-scan.git ~/.codex/404tomb-scan
   ```

2. **Create the skills symlink:**
   ```bash
   mkdir -p ~/.agents/skills
   ln -s ~/.codex/404tomb-scan/skills ~/.agents/skills/404tomb-scan
   ```

3. **Restart Codex** to discover the skill.

## Updating

```bash
cd ~/.codex/404tomb-scan && git pull
```

## Uninstalling

```bash
rm ~/.agents/skills/404tomb-scan
rm -rf ~/.codex/404tomb-scan
```
