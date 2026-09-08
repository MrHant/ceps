# ceps

**ceps** (`spec` backwards) is a bottom-up executable specification protocol for AI-assisted software development.

Instead of beginning with broad requirements and deriving tests later, a ceps project begins with detailed behavioral cases and executable tests. An AI coding agent reads that evidence, infers the required implementation, and validates its work against the same evidence.

> ceps describes observable behavior, not a preferred implementation.

## Status

ceps is experimental. The current protocol version is **0.1**.

## How it works

1. Describe behavior as focused ceps cases.
2. Cover each case with executable tests.
3. Declare project-wide constraints that tests cannot express well.
4. Give an agent the ceps protocol.
5. The agent implements the smallest coherent solution and runs the verifications.

## Start here

- [ceps.md](ceps.md) — the complete protocol and agent workflow

## License

[MIT](LICENSE)
