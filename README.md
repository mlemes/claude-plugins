# mlemes Claude Code marketplace

Claude Code plugins by Marcus Lemes. Each plugin lives in its own repository; this repository contains the shared catalog.

| Plugin | Purpose | Source |
| --- | --- | --- |
| `quotaline@mlemes` | Subscription quota usage in the Claude Code status line | [quotaline](https://github.com/mlemes/quotaline) |
| `ml-referee@mlemes` | Seal ML holdouts, audit leakage, and record budgeted evaluations | [ml-referee](https://github.com/mlemes/ml-referee/tree/release/claude-plugin-0.1.0) |

## Add the marketplace

```bash
claude plugin marketplace add mlemes/claude-plugins
```

Install either plugin independently.

## Quotaline

```bash
claude plugin install quotaline@mlemes
```

Run `/quotaline:install` inside Claude Code, then restart it. See [requirements and setup](https://github.com/mlemes/quotaline#requirements).

## ML Referee

Python 3.11 or later is required. Install the Python package from the same commit pinned in the catalog:

```bash
python3 -m venv ~/.venvs/ml-referee
source ~/.venvs/ml-referee/bin/activate
python -m pip install 'git+https://github.com/mlemes/ml-referee.git@e9f3f49633c61e474a9727440abd052003f04378'
claude plugin install ml-referee@mlemes
```

Keep that environment active when launching Claude Code from your ML project. Follow the [project setup and sealing instructions](https://github.com/mlemes/ml-referee/blob/release/claude-plugin-0.1.0/README.md) before training. The plugin retains its guard and recorder hooks; catalog installation alone does not install Python dependencies or seal data.

## Existing marketplace users

Run `claude plugin marketplace add mlemes/claude-plugins` to switch an existing registration to this repository. Claude Code updates the source without changing installed plugin identifiers. To roll back, add your previous source again.

If Claude Code reports that the source conflicts with `extraKnownMarketplaces` in your user settings, change only `extraKnownMarketplaces.mlemes.source` in `~/.claude/settings.json` to the following, then rerun the add command:

```json
{"source": "github", "repo": "mlemes/claude-plugins"}
```

Keep the other settings unchanged. If the declaration is managed by your organization, ask its administrator to update it.

The older catalog at `mlemes/quotaline` remains available for compatibility. The marketplace name stays `mlemes`, so plugin identifiers do not change. This repository is the canonical catalog for future updates.

## Maintaining the catalog

Update the relevant GitHub source commit in `.claude-plugin/marketplace.json` after reviewing a plugin release. When updating ML Referee, also update the matching Python installation commit above. Validate with:

```bash
claude plugin validate --strict .claude-plugin/marketplace.json
```

## License

MIT. See [LICENSE](LICENSE).
