# elephentity-runtime

Read [README.md](README.md) first — this file assumes it.

## Do not edit `src/` or `tests/` here

This repository is a **read-only subtree mirror** of `packages/runtime` in
[`elephentity`](https://github.com/hsimah-services/elephentity). Any change to the
runtime's actual behaviour — the storage port, unit of work, verification, loaders —
belongs there, in `packages/runtime/`. A commit made directly to `src/` or `tests/`
here will be silently overwritten the next time the split workflow runs.

What legitimately changes in *this* repository: `composer.json`'s `require-dev`
versions, the CI/tooling scaffold (`.docker/`, `tools/php`, `phpstan.neon.dist`,
`.php-cs-fixer.dist.php`), the `.llms/` trio, and this file and `README.md`.

## Working in this repository

There is no local PHP. Everything runs in a container:

```bash
./tools/php composer ci          # style, static analysis, tests
./tools/php composer style:fix
./tools/php vendor/bin/phpunit --filter SomeTest
```

`composer ci` must pass before committing. PHPStan runs at **level max** with no
baseline exclusions.

## Before you commit anything that crosses a repository boundary

**[`.llms/cross-repo.md`](.llms/cross-repo.md) is the closed list of what crosses.** If
you changed something on it, open an issue on each repository it reaches, before or
with the push. [`.llms/README.md`](.llms/README.md) has the rule and
[`.llms/issue-template.md`](.llms/issue-template.md) the shape.
