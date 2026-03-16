# Installing 404tomb-scan for Codex

Enable the 404tomb-scan skill in Codex via native skill discovery. Just clone and symlink.

## Prerequisites

- Git

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

   **Windows (PowerShell):**
   ```powershell
   New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.agents\skills"
   cmd /c mklink /J "$env:USERPROFILE\.agents\skills\404tomb-scan" "$env:USERPROFILE\.codex\404tomb-scan\skills"
   ```

3. **Restart Codex** (quit and relaunch the CLI) to discover the skill.

## Verify

```bash
ls -la ~/.agents/skills/404tomb-scan
```

You should see a symlink (or junction on Windows) pointing to your 404tomb-scan skills directory.

## Updating

```bash
cd ~/.codex/404tomb-scan && git pull
```

Skills update instantly through the symlink.

## Uninstalling

```bash
rm ~/.agents/skills/404tomb-scan
```

Optionally delete the clone: `rm -rf ~/.codex/404tomb-scan`.

## Getting Help

- Report issues: https://github.com/tsesc/404tomb-scan/issues
