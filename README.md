### Changes
Compared to the upstream version this fork allows you to customize the allowed commit types. This lets you allow types like `enh`.

# Conventional Commits GitHub Action

A simple GitHub action that makes sure all commit messages are following the [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0-beta.2/) specification.

![Screenshot](/docs/screenshot.png)

Note that, typically, you would make this check on a pre-commit hook (for example, using something like [Commitlint](https://commitlint.js.org/)), but those require extra configuration and can theoretically easily be skipped, hence this GitHub action.

## Basic usage

```yml
name: Conventional Commits

on:
  pull_request:
    branches: [ master ]

jobs:
  build:
    name: Conventional Commits
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2

      - uses: gentleseal/action-conventional-commits@master
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}
```
This will use the default allowed types of:

```
[
    "feat",
    "fix",
    "docs",
    "style",
    "refactor",
    "test",
    "build",
    "ci",
    "chore",
    "revert",
    "merge",
    "wip",
]
```
## Customizing the commit types
```yml
name: Conventional Commits

on:
  pull_request:
    branches: [ master ]

jobs:
  build:
    name: Conventional Commits
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2

      - uses: gentleseal/action-conventional-commits@master
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}
          valid-commit-types: >
            [
              "feat",
              "fix",
              "docs",
              "style",
              "refactor",
              "test",
              "build",
              "ci",
              "chore",
              "revert",
              "merge",
              "wip",
              "enh"
            ]
```
