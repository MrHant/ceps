# Decision log

Deliberate decisions behind the ceps protocol, and the reasoning that is not recoverable from the specification text itself. Each entry records what was chosen, what was rejected, and why.

## `exam` is an intentional name

- **ceps calls its executable evidence an *exam*, not a test, and stores it in `ceps/exams/`.** This is a deliberate choice of an unfamiliar word over a familiar one.
- **The problem it solves.** ceps was tried on projects that already had their own test suites. Implementing agents saw heavy coverage overlap between the project's tests and ceps' tests, concluded it was duplication, and stopped to ask whether the regular tests should be moved into `ceps/tests/`, merged, or deleted. The answer is always no — the two are independent and coexist.

## ceps names only its own artifacts

- **There is no ceps term for the project's own tests, and there will not be one.** Naming them would be ceps defining vocabulary for artifacts it does not own, and any such term is wrong in some project that uses the word differently.
- **The word *test* still appears, narrowed to one meaning.** An exam file is written in a real test framework and contains functions a runner calls tests. That cannot be renamed away, so §4 states the distinction once: *exam* refers to the file and its role as evidence; the framework-level tests inside it are an implementation detail.

