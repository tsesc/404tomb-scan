# Installing 404tomb-scan for OpenCode

## Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/tsesc/404tomb-scan.git ~/.config/opencode/404tomb-scan
   ```

2. **Symlink skills:**
   ```bash
   mkdir -p ~/.config/opencode/skills
   ln -s ~/.config/opencode/404tomb-scan/skills ~/.config/opencode/skills/404tomb-scan
   ```

3. **Restart OpenCode.**

## Updating

```bash
cd ~/.config/opencode/404tomb-scan && git pull
```

## Uninstalling

```bash
rm -rf ~/.config/opencode/skills/404tomb-scan
rm -rf ~/.config/opencode/404tomb-scan
```
