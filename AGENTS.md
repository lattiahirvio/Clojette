# AGENTS.md

## Scope

These instructions apply to the entire repository.

## Project

Clojette is a Clojure-inspired Lisp for GreyHack. The runtime is written in GreyScript/MiniScript (`.gs`); macros, the self-hosted standard library, tests, and examples use Clojette (`.clj`). Do not assume JVM Clojure, Leiningen, Clojure CLI, or Node tooling.

## Repository layout

- `src/clojette.gs`: runtime entry point; imports the runtime components.
- `src/clojette-core.gs`: lexer, parser, evaluator, and special forms.
- `src/clojette-env.gs`: environments, bindings, and namespace state.
- `src/clojette-stdlib.gs`: GreyScript-hosted built-ins and guards.
- `src/clojette-interop.gs`: GreyHack native-function registration.
- `src/clojette-repl.gs`: development REPL and optional test loading.
- `src/macros.clj`: core macros.
- `src/stdlib.clj`: preferred self-hosted standard library.
- `src/tests.clj`: regression suite.
- `DOCS/`: language, library, guard, and example documentation.
- `all.gs`: packaged stable release. Do not edit it directly; make source changes under `src/`.

## Build and run

There is no repository-defined shell build command. Development is performed in GreyHack; Greybel is optional.

For a source build:

1. Copy the files from `src/` into GreyHack, using `.src` for GreyScript source files.
2. Replace `<user>` paths in `clojette.src` and `<path-to-runtime>` in `clojette-repl.src`.
3. Build `clojette.src` as importable and install it as `/lib/clojette.so`.
4. Copy `macros.clj` and `stdlib.clj` to `/lib/clojette/`.
5. Build and run `clojette-repl.src`.

For the packaged release, copy and build `all.gs` with GreyHack's `CodeEditor.exe` or `build` command.

## Tests

No host-side test runner or CI is configured. Copy `src/tests.clj` to `/lib/clojette/tests.clj`, enable `clojette.tests` in the development runtime, and run the development REPL. A successful run ends with `All tests passed!` and zero failures.

Run the full suite after runtime, macro, or standard-library changes. Per `CONTRIBUTING.md`, test-only changes must be validated against a stable release and should not share a pull request with runtime code changes. If GreyHack is unavailable, state that tests were not run; do not invent a local command.

## Conventions

- GreyScript names use `camelCase`.
- Clojette names use `kebab-case`; predicates end in `?` and mutating operations in `!`.
- Dereference GreyScript function references with `@` whenever storing or passing them.
- Runtime objects use `classID` and the `@__runtimeTag__` sentinel.
- When distinguishing runtime objects from ordinary maps, check the runtime tag; do not rely on `isa map` alone.
- Return structured `lispError` values and propagate guard or evaluation errors instead of allowing runtime crashes.
- Do not commit temporary `print()` debugging.
- Preserve existing GPLv3-with-linking-exception headers.
- Prefer implementing portable library behavior in `src/stdlib.clj`; use `src/clojette-stdlib.gs` for host integration.
- Update relevant files in `DOCS/` when changing public syntax, behavior, or library APIs.
- No formatter or linter is configured, so follow nearby formatting and keep diffs focused.
