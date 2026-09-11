This document describes development of ceps protocol itself. 
Projects implementing ceps - doesn't need current document.

# Working on ceps

ceps is a language-independent protocol, not an implementation framework. Read `ceps.md` before changing protocol behavior.

## Repository map

- `ceps.md`: complete normative specification and agent workflow
- `DECISION_LOG.md`: deliberate design decisions and the reasoning behind them

## Change rules

- Maintain all the significant logic within `ceps.md`.
- Use MUST/SHOULD/MAY only for normative protocol requirements.
- Keep ceps independent of programming language, test framework, and AI vendor.
- Do not add behavior that requires an agent to infer hidden precedence.
