# Installing Coach for Codex

## Installation

```bash
codex plugin marketplace add AlexandreMoreau2002/coach
```

Restart Codex after installation. The plugin is discovered through:

- `.agents/plugins/marketplace.json`
- `.codex-plugin/plugin.json`
- `skills/*/SKILL.md`

## Manual fallback

Use this only if your Codex version does not support `codex plugin marketplace add`.

```bash
git clone https://github.com/AlexandreMoreau2002/coach ~/.codex/coach
mkdir -p ~/.agents/skills
ln -sfn ~/.codex/coach/skills ~/.agents/skills/coach
```

## Verify

```bash
codex plugin marketplace add ~/.codex/coach
```

## Update

```bash
codex plugin marketplace upgrade coach
```

For the manual fallback:

```bash
cd ~/.codex/coach && git pull
```

## Uninstall

```bash
codex plugin marketplace remove coach
```

For the manual fallback, also remove `~/.agents/skills/coach` and `~/.codex/coach`.
