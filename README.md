# windows-screenshots

An [agent skill](https://skills.sh) that teaches AI coding agents where to find your Windows screenshots (Win+PrtScn, Snipping Tool) and how to search them sensibly - from WSL or native Windows shells (Git Bash, PowerShell, cmd).

What it does:

- Locates the screenshots folder via the `SCREENSHOTS` environment variable, with auto-detection guidance when unset.
- Scopes searches to today's screenshots by default - "look at my screenshot" almost never means one from three years ago.
- Picks the "latest" screenshot by filename timestamp within the modern `Screenshot YYYY-MM-DD HHMMSS.png` pattern, avoiding traps from OneDrive mtime churn, legacy `Screenshot_YYYYMMDD_*` names, and hand-renamed files.
- Reads screenshots visually (agents with an image-capable Read tool) instead of just listing filenames.
- Knows the sharp edges: `desktop.ini` noise, OneDrive sync lag, non-standard capture tool naming.

## Install

```bash
npx skills add acfatah/windows-screenshots
```

Or directly for a specific agent, globally:

```bash
npx skills add acfatah/windows-screenshots -a claude-code -g -y
```

## Configuration

The skill requires the `SCREENSHOTS` environment variable to point at your Windows screenshots folder.

WSL - add to `~/.profile` (not below the interactive guard in `.bashrc`, or non-interactive agent shells will not see it):

```bash
echo 'export SCREENSHOTS="/mnt/c/Users/<winuser>/OneDrive/Pictures/Screenshots"' >> ~/.profile
```

Native Windows - one command covers Git Bash, PowerShell, and cmd (new sessions):

```cmd
setx SCREENSHOTS "C:\Users\<user>\OneDrive\Pictures\Screenshots"
```

Tip: if you are unsure of the real folder name, check both `OneDrive\Pictures\Screenshots` and `Pictures\Screenshots` - Windows redirects Pictures into OneDrive when Known Folder Backup is on, and sync conflicts can leave a `Screenshots 1` folder behind. File Explorer may display a localized alias, so verify the on-disk name with `dir` or `ls`.

## License

[MIT](LICENSE)
