# windows-screenshots - moved

This skill now lives in my skills monorepo:

**https://github.com/acfatah/skills**

This repository is archived and no longer receives updates.  The `SKILL.md` here
is left in place at its final version (v1.0.0) so existing installs keep working,
but it will not be maintained.

## Install from the new location

```bash
npx skills add acfatah/skills -s windows-screenshots
```

Or directly for a specific agent, globally:

```bash
npx skills add acfatah/skills -s windows-screenshots -a claude-code -g -y
```

## Already installed from here?

Your lockfile still points at this archived repository, so `npx skills update`
will never see new versions.  Remove and re-add from the monorepo:

```bash
npx skills remove windows-screenshots -g -y
npx skills add acfatah/skills -s windows-screenshots -a claude-code -g -y
```

## License

[MIT](LICENSE)
