# ceps

**ceps** (`spec` backwards) is a bottom-up executable specification protocol for AI-assisted software development.

Instead of beginning with broad requirements and deriving tests later, a ceps project begins with detailed behavioral ceps cases and executable exams. An AI coding agent reads that evidence, infers the required implementation, and validates its work against the same evidence.

Ceps exams live in `ceps/exams/` and are separate from whatever tests the project already has — the two coexist.

> ceps describes observable behavior, not a preferred implementation.

## Status

ceps is experimental. The current protocol version is **0.3**.

## For coding agents

If you are a coding agent asked to implement ceps, read [ceps.md](ceps.md) and ignore the rest of this repository. It is the complete protocol — everything else here is supporting material for maintaining ceps itself, not input to your implementation.

If you are reading this text outside the repository and cannot resolve that path, fetch it from `https://github.com/MrHant/ceps/blob/main/ceps.md`.

## How it works

1. Describe behavior as focused ceps cases.
2. Cover each ceps case with an executable exam.
3. Declare project-wide constraints that exams cannot express well.
4. Give an agent the ceps protocol.
5. The agent implements the smallest coherent solution and runs the verifications.

## For humans

- [ceps.md](ceps.md) — the complete protocol and agent workflow
- [DECISION_LOG.md](DECISION_LOG.md) — architectural decision log

## License

[MIT](LICENSE)
