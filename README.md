# 💠 JadeGate Verify Action

[![JadeGate 💠 Origin Verified](https://img.shields.io/endpoint?url=https://jadegate.io/api/badge/JadeGate/jade-core.json)](https://jadegate.io/verify/?repo=JadeGate/jade-core)

> **Pass CI verification → Get your 🔹 Community Verified badge.** The 💠 Origin badge above is root-signed (official projects only).
> **通过 CI 验证 → 获得 🔹 社区验证徽章。** 上方 💠 根签名徽章仅限官方项目。

Verify AI agent skills & MCP servers with JadeGate's 5-layer deterministic security inspection — directly in your CI pipeline.

使用 JadeGate 五层确定性安全检查，在 CI 中验证 AI agent 技能和 MCP 服务器。

## Quick Start / 快速开始

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
          path: ./skills/        # Path to skill JSON files / 技能文件路径
          token: ${{ secrets.JADEGATE_TOKEN }}  # Optional: for badge / 可选：用于徽章注册
```

**👉 Step-by-step guide / 分步教程：[jadegate.io/guide](https://jadegate.io/guide/)**

## Inputs / 输入参数

| Input | Description / 说明 | Required / 必填 | Default / 默认 |
|-------|-------------------|-----------------|----------------|
| `path` | Path to skill JSON file or directory / 技能文件路径 | Yes / 是 | `.` |
| `fail-on-warning` | Fail if warnings found / 有警告时失败 | No / 否 | `false` |
| `badge` | Register with badge API / 注册徽章 | No / 否 | `true` |
| `token` | JadeGate API token / API 令牌 | No / 否 | — |

## Outputs / 输出

| Output | Description / 说明 |
|--------|-------------------|
| `passed` | Number of skills passed / 通过数量 |
| `failed` | Number of skills failed / 失败数量 |
| `result` | `pass` or `fail` / 通过或失败 |

## Badge / 徽章

> 🖥️ **Prefer a visual guide? / 更喜欢可视化引导？** → [jadegate.io/guide](https://jadegate.io/guide/) — Interactive step-by-step verification / 交互式分步盖章教程

After verification passes, add this to your README / 验证通过后，在 README 中添加：

```markdown
[![JadeGate Verified](https://img.shields.io/endpoint?url=https://jadegate.io/api/badge/YOUR_ORG/YOUR_REPO.json)](https://jadegate.io/verify/?repo=YOUR_ORG/YOUR_REPO)
```

![JadeGate Verified](https://img.shields.io/endpoint?url=https://jadegate.io/api/badge/YOUR_ORG/YOUR_REPO.json)

## 5 Layers / 五层检查

| Layer / 层 | Check / 检查内容 |
|------------|-----------------|
| 1. Schema | Structure, required fields, types / 结构、必填字段、类型 |
| 2. DAG | Acyclic, connected, valid entry/exit / 无环、连通、有效入口出口 |
| 3. Security | Network whitelist, sandbox, dangerous patterns / 网络白名单、沙箱、危险模式 |
| 4. Injection | Prompt injection, path traversal, command injection / 注入检测 |
| 5. Crypto | Signature, trust chain, expiry / 签名、信任链、过期 |

No LLM. No probability. Pure math. / 无大模型，无概率，纯数学。

## Trust Levels / 信任级别

| Seal / 印章 | Level / 级别 | Meaning / 含义 |
|-------------|-------------|----------------|
| 💠 | Origin | Signed by JadeGate Root CA / 根 CA 签发 |
| 🔷 | Organization | Signed by authorized org / 授权组织签发 |
| 🔹 | Community | Passed CI verification / CI 验证通过 |

## Get Started / 开始使用

- 📖 **Interactive guide / 交互式引导**：[jadegate.io/guide](https://jadegate.io/guide/)
- 🔍 **Check verification status / 查询验证状态**：[jadegate.io/verify/YOUR_ORG/YOUR_REPO](https://jadegate.io/verify/)
- 📦 **Core library / 核心库**：[jade-core](https://github.com/JadeGate/jade-core)

## License / 许可证

BSL 1.1 — Same as [jade-core](https://github.com/JadeGate/jade-core).
