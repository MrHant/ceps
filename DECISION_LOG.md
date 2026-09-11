# Decision log

Deliberate decisions behind the ceps protocol, and the reasoning that is not recoverable from the specification text itself. Each entry records what was chosen, what was rejected, and why.

## `exam` is an intentional name

- **ceps calls its executable evidence an *exam*, not a test, and stores it in `ceps/exams/`.** This is a deliberate choice of an unfamiliar word over a familiar one.
- **The problem it solves.** ceps was tried on projects that already had their own test suites. Implementing agents saw heavy coverage overlap between the project's tests and ceps' tests, concluded it was duplication, and stopped to ask whether the regular tests should be moved into `ceps/tests/`, merged, or deleted. The answer is always no — the two are independent and coexist.

## ceps names only its own artifacts

- **There is no ceps term for the project's own tests, and there will not be one.** Naming them would be ceps defining vocabulary for artifacts it does not own, and any such term is wrong in some project that uses the word differently.
- **The word *test* still appears, narrowed to one meaning.** An exam file is written in a real test framework and contains functions a runner calls tests. That cannot be renamed away, so §4 states the distinction once: *exam* refers to the file and its role as evidence; the framework-level tests inside it are an implementation detail.


## Agents needed a place to write

- **`ceps/assumptions/` and `ceps/answers/` exist because agents were inventing `AGENTS.md` and `CLAUDE.md` to hold what ceps gave them nowhere to put.** Agent behavior required agents to record assumptions and report unresolved issues, while forbidding writes to `ceps/cases/` and `ceps/*.md` — the only writable surfaces. Agents resolved that contradiction by creating files outside the protocol. The write bans were not the problem; the missing destination was.
- **Two folders, not one, because bindingness must be a property of the folder.** An assumption is undecided; an answer is decided by the user. If both lived in one folder an agent would have to read a file to learn whether it must obey it, which is precedence inferred from content rather than stated by the protocol.
- **Assumptions are not a fifth source of evidence.** An agent that could derive behavior from its own assumptions would be writing its own specification, which is what the write bans in agent behavior exist to prevent. They are case-shaped so that accepting one is a move into `ceps/cases/` rather than a rewrite, but the move is the user's decision.
- **An answer outranks only the evidence it names.** §3 states there is no automatic precedence between sources, so a binding source needed an explicit and bounded rank. Unbounded precedence would make `ceps/answers/` a shadow specification quietly outranking `ceps/cases/`. An answer is a record of a resolution; the durable fix is amending the evidence it names.
- **Each rule has one normative home, and other sections point to it.** The folders were described in §2, §3, §6, §7 and the structure diagram at once, including inline diagram comments restating §3's precedence rule non-normatively — a restatement that would silently contradict §3 after any future edit. Descriptive glosses may repeat where an agent first meets a term; a rule may not. Where agent behavior must state an obligation, it names the condition and points at the section defining it.
- **Rejected.** A single `journal/` mixing findings with design rationale: rationale about implementation choices can never become a case, so the protocol does not offer a home for it. A free-form note format: writing assumptions in case format does the work of stating behavior precisely while the agent still has the context, instead of deferring it to whoever promotes it.
