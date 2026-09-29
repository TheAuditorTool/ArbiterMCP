# Arbiter

**The command center above your AI tools.**

Arbiter is a local orchestration layer for dispatching, supervising, and governing AI clients, agents, terminals, and supporting tools. It gives one operator a durable control plane without binding the workflow to a single model provider or coding client.

## Release status

Arbiter is a working product entering IP hardening, licensing, and public packaging preparation.

This repository is the official release and product-information channel. It does not currently contain distributable software.

## What it changes

- **Provider and client independence:** Coordinate different models and agent clients through one control plane.
- **Durable supervision:** Preserve run state and make interrupted work visible for recovery.
- **Cost-aware routing:** Send work to an appropriate capability tier instead of defaulting every task to the most expensive model.
- **Approval-aware operations:** Keep consequential actions visible to the operator.
- **Local coordination:** Use operating-system-native local communication without requiring a public control port.
- **Ecosystem integration:** Work alongside the other Code Reality Labs tools (TheAuditor, Curator, Warden) and third-party clients as separate, optional capabilities.

## Follow development

- Product: [arbitermcp.com](https://arbitermcp.com)
- Engineering journal: [blog.arbitermcp.com](https://blog.arbitermcp.com)
- Made by: [Code Reality Labs](https://coderealitylabs.com)

## License

Arbiter is proprietary software. Copyright (C) 2026 Code Reality Labs. All rights reserved.

See [LICENSE](LICENSE) for terms. Commercial licensing and partnership inquiries:
[Code Reality Labs](https://coderealitylabs.com).
