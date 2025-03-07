---
title: "Repository Makefiles"
type: docs
---

Most repositories contain a `Makefile` in the root directory. This file allows
us to use the [`make`](https://www.gnu.org/software/make/manual/make.html) tool
to perform common actions in the same way, regardless of the underlying language
tools.

Variants of the `make` tool are available for all major platforms. For
installation instructions, consult your Operating System's package manager.

## Usage

The `make` command must be run in the repository root, and specify the directory
path to act on with the `dir` variable:

```
make lint dir=relative/repo/path
```

## Common Actions

All Makefiles provide the following actions, and some may provide additional
actions. See the repository's `CONTRIBUTING.md` for details about additional
actions.

* `build` : Perform build steps, if any. For non-compiled languages, this may
  run a syntax checker to validate the code, or may install necessary
  dependencies.

* `test` : Run all tests in the given directory. If the repository has multiple
  types of testing (for example, unit and end-to-end tests), this target will
  run all types.

* `lint` : Run available linting and style tooling. This target should
  automatically fix style issues, rather than checking the current style.

* `bootstrap` : **(Optional)** If present, this action creates any cloud
  resources that are required by the tests. It is common practice to create all
  necessary resources as part of the test itself, but for certain types of
  resources this may be impractical. For example, creating and training an
  AI model may be impractical to do ephemerally for each test run.

* `list-actions` : Prints a list of the supported Makefile actions. This is can
  be useful if you forget the name of an action, but the main goal is to help us
  maintain consistent support for Common Actions.
