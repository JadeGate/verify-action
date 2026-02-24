# 💠 JadeGate Verify Action

Verify AI agent skills & MCP servers with JadeGate's 5-layer deterministic security inspection — directly in your CI pipeline.

## Usage

```yaml
# .github/workflows/jadegate.yml
name: "💠 JadeGate Security Check"

on: [push, pull_request]

jobs:
  verify:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Verify skills
        uses: JadeGate/verify-action@v1
        with:
          path: ./skills/        # Path to skill JSON files
          token: ${{ secrets.JADEGATE_TOKEN }}  # Optional: for badge registration
```

## Inputs

| Input | Description | Required | Default |
|-------|-------------|----------|---------|
| `path` | Path to skill JSON file or directory | Yes | `.` |
| `fail-on-warning` | Fail if warnings found | No | `false` |
| `badge` | Register with badge API | No | `true` |
| `token` | JadeGate API token | No | — |

## Outputs

| Output | Description |
|--------|-------------|
| `passed` | Number of skills that passed |
| `failed` | Number of skills that failed |
| `result` | `pass` or `fail` |

## Badge

After verification passes, add this badge to your README:

```markdown
[![JadeGate Verified](https://jadegate.io/badge/YOUR_ORG/YOUR_REPO)](https://jadegate.io/verify/YOUR_ORG/YOUR_REPO)
```

Example:

![JadeGate Verified](https://img.shields.io/badge/JadeGate-🔹_Verified-10b981?style=flat-square)

## What gets checked

Every skill goes through 5 deterministic layers:

| Layer | Check |
|-------|-------|
| 1. Schema | Structure, required fields, types |
| 2. DAG | Execution graph: acyclic, connected, valid entry/exit |
| 3. Security | Network whitelist, sandbox level, dangerous patterns |
| 4. Injection | Prompt injection, path traversal, command injection |
| 5. Crypto | Signature verification, trust chain, expiry |

No LLM. No probability. Pure math — same input, same result, every time.

## Trust Levels

| Seal | Level | Meaning |
|------|-------|---------|
| 💠 | Origin | Signed by JadeGate Root CA |
| 🔷 | Organization | Signed by an authorized org |
| 🔹 | Community | Passed CI verification |

## License

BSL 1.1 — Same as [jade-core](https://github.com/JadeGate/jade-core).
