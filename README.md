# ceps

**ceps** (`spec` backwards) is a bottom-up executable specification protocol for AI-assisted software development.

Instead of beginning with broad requirements and deriving tests later, a ceps project begins with detailed behavioral ceps cases and executable exams. An AI coding agent reads that evidence, infers the required implementation, and validates its work against the same evidence.

Ceps exams live in `ceps/exams/` and are separate from whatever tests the project already has — the two coexist.

> ceps describes observable behavior, not a preferred implementation.

## Status

ceps is experimental. The current protocol version is **0.2**.

## How it works

1. Describe behavior as focused ceps cases.
2. Cover each ceps case with an executable exam.
3. Declare project-wide constraints that exams cannot express well.
4. Give an agent the ceps protocol.
5. The agent implements the smallest coherent solution and runs the verifications.

## Start here

- [ceps.md](ceps.md) — the complete protocol and agent workflow

## License

[MIT](LICENSE)
