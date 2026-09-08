# ceps Protocol Specification

Version `0.1`

ceps (`spec` backwards) is a bottom-up executable specification protocol for AI-assisted software development. Behavioral cases, their descriptions, executable tests, and explicit constraints are the evidence from which an implementation is derived.

The key words **MUST**, **MUST NOT**, **SHOULD**, **SHOULD NOT**, and **MAY** are normative.

## 1. Principles

1. **Behavior before implementation.** ceps specifies externally observable behavior. It does not prescribe internal architecture unless an explicit constraint or case requires it.
2. **Evidence before inference.** Agents derive behavior from cases, tests, fixtures, examples, and constraints. They MUST distinguish stated behavior from assumptions.
3. **Tests are executable evidence.** Passing tests is required, but not sufficient when an implementation contradicts a case description or constraint.
4. **Ambiguity is visible.** Contradictions and material gaps MUST NOT be silently resolved.
5. **The smallest coherent solution wins.** Agents SHOULD avoid unsupported features and unnecessary architecture.

## 2. ceps project

A ceps project MUST contain this specification document as `ceps/ceps.md`.
Local copy of `ceps/ceps.md` governs.

`cases` and `tests` folders MUST be located in `ceps/` folder.

A project MAY declare global instruction files in `ceps/*.md`. Typical global instruction file is `ceps/constraints.md`.

A project is **ceps-compliant** when folder structure is valid, every discovered case has a stable identifier and executable test coverage.

ceps-related project structure:
```
ceps/
├── ceps.md
├── *.md      # global instruction files, like constraints.md
├── cases/
└── tests/
```

## 3. Sources of evidence

ceps recognizes four sources of evidence:

1. **Cases** explain intent and observable behavior in natural language.
2. **Executable tests** provide deterministic examples and verification.
3. **Fixtures and test data** provide concrete inputs, outputs, and boundary conditions.
4. **Constraints** state cross-cutting requirements such as platform support, security, performance, dependencies, or public interfaces.

Cases and tests form one specification and MUST agree. There is no automatic precedence between evidence sources. If two sources conflict materially, the project is ambiguous and the agent MUST clarify details with the user before choosing behavior.

Existing implementation code is context, not specification, unless a case or constraint explicitly declares compatibility with it.

## 4. Behavioral cases

Cases MUST be UTF-8 Markdown files. 

Name of the case file without .md extension MUST be treated as `id` - stable case identifier.
Case file MAY be placed in subdirectories of `ceps/cases/`. Subdirectories need to be retained in `id`.

A case's executable coverage lives in a test file, its name is derived from the `id`.
For example:
- `ceps/cases/alpha.md` is covered by `alpha`-derived file in `ceps/tests/`. 
- `ceps/cases/group/beta.md` is covered by `beta`-derived file in `ceps/tests/group/`.

One case MUST have exactly one test file. One test file MAY contain multiple tests belonging to the same case.

Specific naming of test file is dependent on the programming language and test framework.

Naming the file rather than the tests inside it states where coverage belongs without prescribing how many tests express it or what they are called.

The body MUST state the expected behavior precisely enough to interpret the linked tests. It MAY include:

- a behavior-oriented title;
- preconditions or context;
- the triggering action;
- observable outcomes;
- representative examples and important boundaries;
- relevant error behavior.

A case MUST NOT require readers to infer essential behavior solely from its title. Cases SHOULD avoid prescribing classes, functions, algorithms, or storage choices unless those details are part of the public contract.
If logical modules are required in the code - they MUST be named explicitly in domain terms, and used consistently across all the cases.

## 5. Constraints (Optional)

Constraints MAY be included as additional instructions in `ceps/constraints.md` file.
Constraints capture requirements that individual examples cannot express reliably. A constraint MUST be explicit and verifiable where practical. Typical constraints include:

- supported runtimes and operating systems;
- public API or command-line compatibility;
- allowed or forbidden dependencies;
- security and privacy properties;
- performance limits and expectations;
- files or interfaces that must not change.

Agents MUST satisfy constraints even when the linked behavioral cases or tests do not enforce them. Aspirational preferences SHOULD be labeled as non-normative guidance.

## 6. Agent behavior

An agent implementing a ceps project MUST:

1. read all discovered cases (`ceps/cases/`) and additional instructions (`ceps/*.md` other than `ceps/ceps.md`) before implementation;
2. inspect linked tests, fixtures, and relevant existing code;
3. identify contradictions, missing references, and material ambiguity;
4. stop and request clarification when ambiguity could change public behavior, data integrity, security, or compatibility;
5. otherwise record minor assumptions and proceed;
6. implement only behavior supported by ceps evidence;
7. run the tests (`ceps/tests/`);
8. report validation results, assumptions, and unresolved issues.

An agent MUST NOT weaken, delete, skip, or rewrite normative tests merely to make validation pass. It MAY modify tests when explicitly asked to develop or correct the specification, but MUST clearly report those changes.

An agent MUST NOT modify cases unless explicitly asked to do so.
A request to change specified behavior is not ambiguity under step 4. If explicitly asked to modify cases, the agent MUST amend the affected cases before changing the implementation, so that no case contradicts the delivered behavior, and MUST report which cases it changed.

An agent MUST NOT modify instruction files (`ceps/*.md`) unless explicitly asked to do so.

## 7. Completion

An implementation is complete with respect to a ceps project when:

- every discovered case has corresponding executable coverage;
- all tests pass;
- no known behavior contradicts a case or constraint;
- assumptions and remaining limitations are reported to the user.

Passing checks that no case describes does not compensate for a failed described check. Passing all checks does not resolve a known semantic contradiction.

## 8. Versioning

The protocol uses Major.Minor versioning, such as `0.1`.

Any update to the ceps specification MUST be accompanied by a new version number.
