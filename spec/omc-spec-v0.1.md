# Open Model Card Specification

**Version:** 0.1 (Draft)
**Status:** Draft — not yet stable
**Date:** 2026-03-05
**Maintained by:** AlgoBroker (openmodelcard.org)

---

## 1. Introduction

An Open Model Card (`.omc`) is a structured document that describes an AI model from a **practitioner's perspective** — someone evaluating, comparing, tracking, or governing third-party AI models.

This specification defines the file format, field schema, and validation rules for `.omc` files.

### 1.1 Scope

This spec covers:
- The `.omc` file format
- Required, recommended, and optional fields
- The JSON Schema for validation
- Versioning and extension conventions

This spec does not cover:
- How to build or train models
- Model evaluation methodology
- Deployment or packaging

### 1.2 Design Principles

- **Practitioner-first.** Designed for the people using AI models, not the people building them.
- **Self-hosted.** `.omc` files live on your machine. No cloud dependency.
- **Human-readable.** Valid JSON, readable with any text editor.
- **Machine-parseable.** Strict schema, easy to validate and query.
- **Extensible.** Core fields cover the common case. Extension fields cover everything else.

---

## 2. File Format

Open Model Cards use the `.omc` file extension. The contents are valid JSON (UTF-8 encoded).

A single `.omc` file may contain either:
- A **single model card** — a JSON object describing one model
- A **collection** — a JSON object with a `models` array containing multiple model cards

### 2.1 Single Model Card

```json
{
  "$schema": "https://openmodelcard.org/schema/v0.1",
  "id": "gpt-4o",
  "name": "GPT-4o",
  "provider": "OpenAI",
  "description": "OpenAI's flagship multimodal model combining text, vision, and audio."
}
```

### 2.2 Collection

```json
{
  "$schema": "https://openmodelcard.org/schema/v0.1",
  "version": "1.0",
  "models": [
    { "id": "gpt-4o", "name": "GPT-4o", "provider": "OpenAI", "description": "..." },
    { "id": "claude-3-5-sonnet", "name": "Claude 3.5 Sonnet", "provider": "Anthropic", "description": "..." }
  ]
}
```

---

## 3. Fields

### 3.1 Required Fields

Every `.omc` file MUST include these fields:

| Field | Type | Description |
|-------|------|-------------|
| `id` | string | Unique identifier. Lowercase, hyphens only. e.g. `gpt-4o` |
| `name` | string | Human-readable display name. e.g. `GPT-4o` |
| `provider` | string | Organisation that created the model. e.g. `OpenAI` |
| `description` | string | 1-3 sentence description of the model. |

### 3.2 Recommended Fields

These fields are optional but strongly recommended:

| Field | Type | Description |
|-------|------|-------------|
| `version` | string | Model version string. e.g. `2024-11-20` |
| `date` | string | Release or last-updated date. ISO 8601. e.g. `2024-11-20` |
| `url` | string | Link to official model documentation or API page. |
| `modalities` | array | Capabilities: `text`, `image`, `audio`, `video`, `code`, `embedding` |
| `context` | string | Context window size. e.g. `128k tokens` |
| `strengths` | array | Capability tags. e.g. `["reasoning", "vision", "instruction-following"]` |
| `license` | string | License type. e.g. `MIT`, `Apache 2.0`, `Commercial API` |

### 3.3 Optional Fields

#### Pricing

```json
"pricing": {
  "input": 5.00,
  "output": 15.00,
  "unit": "per 1M tokens",
  "notes": "Prices as of 2024-11-20"
}
```

#### Ratings

Subjective ratings on a 1-5 scale, assigned by the practitioner:

```json
"ratings": {
  "reasoning": 5,
  "coding": 5,
  "creativity": 4,
  "speed": 3
}
```

#### Links (relationships between models)

```json
"links": [
  { "id": "gpt-4", "type": "predecessor-of" },
  { "id": "gpt-4o-mini", "type": "related-to" }
]
```

Valid link types: `successor-of`, `predecessor-of`, `fine-tuned-from`, `distilled-from`, `same-family`, `competes-with`, `related-to`

#### Metadata

```json
"metadata": {
  "created": "2025-01-01T00:00:00Z",
  "updated": "2025-06-01T00:00:00Z",
  "bookmarked": true,
  "icon": "🤖",
  "color": "#10a37f"
}
```

---

## 4. Extension Fields

Implementations may add custom fields not defined in this spec. Extension fields MUST be prefixed with `x_` to avoid conflicts with future spec additions.

```json
"x_internal_tier": "approved",
"x_compliance_reviewed": true,
"x_last_reviewed_by": "ml-team"
```

---

## 5. The `$schema` Field

Every `.omc` file SHOULD include a `$schema` field pointing to the spec version it conforms to. This enables validation and tooling support.

```json
"$schema": "https://openmodelcard.org/schema/v0.1"
```

---

## 6. Validation

A JSON Schema for validating `.omc` files is available at:

`schema/omc-schema-v0.1.json`

---

## 7. Versioning

This spec follows semantic versioning.

- Breaking changes (removing or renaming fields) increment the **major** version.
- Additive changes (new optional fields) increment the **minor** version.
- Clarifications increment the **patch** version.

The `$schema` URI encodes the spec version. Implementations SHOULD validate against the version referenced in the file.

---

## 8. Conformance

A conforming `.omc` file:
1. Is valid JSON (UTF-8)
2. Contains all required fields (`id`, `name`, `provider`, `description`)
3. Uses the `x_` prefix for any custom fields not in this spec
4. References a valid `$schema` URI (recommended)

---

## 9. Example

See `examples/frontier-models.omc` for a complete working example.

---

## 10. Changelog

| Version | Date | Notes |
|---------|------|-------|
| 0.1 | 2026-03-05 | Initial draft |
