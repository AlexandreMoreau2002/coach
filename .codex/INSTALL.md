# Installing Coach for Codex

## Installation

```bash
git clone https://github.com/AlexandreMoreau2002/coach ~/.codex/coach
mkdir -p ~/.agents/skills
ln -s ~/.codex/coach/skills ~/.agents/skills/coach
```

Restart Codex to discover the skills.

## Verify

```bash
ls -la ~/.agents/skills/coach
```

## Update

```bash
cd ~/.codex/coach && git pull
```

Skills update instantly through the symlink.

## Uninstall

```bash
rm ~/.agents/skills/coach
rm -rf ~/.codex/coach
```
