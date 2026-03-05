# Open Model Card Specification

**OMC — the open standard for AI model documentation.**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Version](https://img.shields.io/badge/spec-v0.1--draft-orange.svg)](spec/omc-spec-v0.1.md)
[![Status](https://img.shields.io/badge/status-draft-yellow.svg)]()

---

## What is an Open Model Card?

An Open Model Card (`.omc`) is a structured JSON document that describes an AI model from a **practitioner's perspective** — someone who is evaluating, comparing, tracking, or deploying third-party AI models.

This is different from existing model card formats, which are designed for model *creators* documenting their own models. OMC is designed for the people *using* those models: data scientists, ML engineers, architects, and technical decision-makers who need to track, compare, and govern the AI models in their organisation.

---

## Why OMC?

There is no open standard for practitioner-facing AI model documentation. Existing formats are:

- **Creator-facing** (Hugging Face YAML, Google's Model Card Toolkit) — designed for the people building models, not using them
- **Infrastructure-facing** (CNCF ModelPack) — designed for packaging and deployment, not documentation
- **Proprietary** (OpenAI system cards, NVIDIA Model Card++) — platform-specific, not interoperable

OMC fills the gap. It is:

- **Open** — the spec is public, MIT licensed, free for anyone to implement
- **Self-hosted** — `.omc` files live on your machine, your data never leaves your control
- **Practitioner-first** — designed for evaluation, comparison, and governance, not model publishing
- **Simple** — valid JSON, readable with any text editor, parseable with any language
- **Extensible** — a core schema with optional extension fields for specific industries or use cases

---

## Specification

The current specification is at [`spec/omc-spec-v0.1.md`](spec/omc-spec-v0.1.md).

The JSON Schema is at [`schema/omc-schema-v0.1.json`](schema/omc-schema-v0.1.json).

**Status: Draft.** This is v0.1. The schema will evolve based on community feedback before a stable v1.0 release.

---

## File Format

Open Model Cards use the `.omc` file extension. The contents are valid JSON conforming to the OMC schema.

---

## Examples

See the [`examples/`](examples/) directory for sample `.omc` files covering:

- A general-purpose frontier model (GPT-4o)
- A reasoning-focused model (Claude 3.5 Sonnet)
- An open-source model (Llama 3)

---

## Reference Implementation

**AI Model Cards** is the reference implementation of the OMC spec — a self-hosted, single-file web application for tracking, comparing, and visualising AI models using `.omc` files.

→ [omc.dev](https://omc.dev)

---

## Contributing

This spec is in early draft. Contributions, corrections, and discussion are welcome.

- Open an issue to propose a new field or flag an error
- Open a PR with a suggested change to the spec
- Join the discussion in GitHub Discussions

Please read [CONTRIBUTING.md](CONTRIBUTING.md) before submitting.

---

## License

The OMC specification is licensed under the [MIT License](LICENSE).

---

## Maintainer

Created and maintained by [AlgoBroker](https://algobroker.com).

Open Model Card specification — [openmodelcard.org](https://openmodelcard.org)
