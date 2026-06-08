# Backdrop GHA

This is currently an experimental repository to explore the feasibility of
using a shared repo for some basic GitHub Actions that can be used by contrib
module maintainers.

Right now only the simplest implementations are included. In the future it may
be expanded to include other options.

## Instructions

To use one of these predefined action, create a directory `.github/workflows/`
in your repository and add a yml file (whatever the name is).

Most below copy-paste examples are the minimal setup (without params) and all
run on pull requests only. You can use all of them in the same repo, but need a
workflow file for each of them.

### Simpletest

Create, for example, a file named:
```
.github/workflows/simpletest.yml
```

Containing the following:
```
name: Simpletest
on: [pull_request]
jobs:
  functional_test:
    timeout-minutes: 10
    runs-on: ubuntu-latest
    steps:
      - name: Run Tests
        uses: backdrop-ops/gha/actions/simpletest@v1
```

Available (optional) parameters:

 - `php_version`: defaults to 8.3
 - `db_version`: defaults to mariadb-10.11
 - `module_dependencies`: default empty; can be set to a comma-separated string

### PHPCS (Changed -- only on modified lines)

Create, for example, a file named:
```
.github/workflows/phpcs_changed.yml
```

Containing the following:
```
name: Coding standards
on: [pull_request]
jobs:
  coding_standards:
    timeout-minutes: 10
    runs-on: ubuntu-latest
    steps:
      - name: Run PHP_CodeSniffer
        uses: backdrop-ops/gha/actions/phpcs_changed@v1
```

Available (optional) parameters:

 - `php_version`: defaults to 8.3

### PHPCS (Full -- on all code in the repo)

Create, for example, a file named:
```
.github/workflows/phpcs_full.yml
```

Containing the following:
```
name: Coding standards
on: [pull_request]
jobs:
  coding_standards:
    timeout-minutes: 10
    runs-on: ubuntu-latest
    steps:
      - name: Run PHP_CodeSniffer
        uses: backdrop-ops/gha/actions/phpcs_full@v1
```

Available (optional) parameters:

 - `php_version`: defaults to 8.3
 - `fail_on_warnings`: defaults to true

