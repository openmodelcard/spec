# Contributing to Open Model Card

Thank you for your interest in contributing to the OMC specification.

## How to Contribute

### Proposing a new field

Open an issue with the label `field-proposal`. Include:
- The field name (following the naming conventions in the spec)
- The type and allowed values
- Why it belongs in the core spec vs. as an extension field
- One or more example use cases

### Reporting an error or ambiguity

Open an issue with the label `spec-bug`. Quote the relevant section and describe the problem clearly.

### Submitting a pull request

1. Fork the repository
2. Create a branch: `git checkout -b your-change-description`
3. Make your changes
4. Open a pull request with a clear description of what you changed and why

### Principles

When evaluating contributions, we ask:

- **Is this practitioner-facing?** OMC is designed for people using AI models, not building them.
- **Is this broadly applicable?** Core fields should apply across model types and providers. Use extension fields (`x_`) for anything narrower.
- **Does it stay simple?** The spec should be readable by a non-technical stakeholder.
- **Is it self-hostable?** Nothing in the spec should require a network call or external service.

## Code of Conduct

Be direct. Be respectful. Disagree on ideas, not people.

## Questions

Open a GitHub Discussion for anything that is not a bug or a proposal.
