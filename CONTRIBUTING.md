# Contributing to vidformer

Thank you for your interest in contributing to vidformer.

This repository contains the Rust core library, the Python package, the `vidformer-igni` server, and the project documentation. Please keep contributions focused, documented, and reproducible.

## Before you start

- Review the [README](./README.md) for project overview and documentation links.
- Use a short-lived branch for each change.
- Open or reference an issue when the change needs design discussion or project tracking.

## Local setup

The repository's CI workflow installs native and Python dependencies with the provided scripts before building and testing.

### CI-style dependency setup

```bash
bash ./scripts/deps_ci.sh
```

### Development container setup

```bash
bash ./scripts/deps_devcontainer.sh
```

The development-container script also installs the editable Python package and downloads the sample media used by tests and examples.

## Build and test

Run the existing project commands that match the area you changed:

```bash
cargo build
cargo build --release
cargo test --verbose
pip3 install ./vidformer-py
pytest -vv
bash ./scripts/valgrind_test.sh
```

The Python tests run from `snake-pit/`:

```bash
cd snake-pit
pytest -vv
```

## Documentation changes

If you change documentation, validate the relevant docs build when practical:

```bash
cargo doc --no-deps -p vidformer
cd docs && mdbook build
cd ../vidformer-py && pdoc vidformer/ -o ../target/doc/vidformer-py/
```

## Contribution expectations

Please aim to:

- keep pull requests scoped to one logical change;
- update docs when behavior, setup, or interfaces change;
- preserve reproducibility by documenting new dependencies or sample assets;
- avoid committing generated files, credentials, or large local-only artifacts.

## Commit and pull request guidance

- Prefer descriptive, atomic commits.
- Conventional Commit prefixes such as `feat:`, `fix:`, `docs:`, and `chore:` are welcome.
- Include a clear pull request summary and note any validation you ran.

## Questions and conduct

By participating in this project, you agree to follow the [Code of Conduct](./CODE_OF_CONDUCT.md).
