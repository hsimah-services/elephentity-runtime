# elephentity-runtime

Elephentity's runtime contracts: the storage port, the unit of work, verification and
loaders — the small, driver-agnostic surface every adaptor implements and every
generated entity depends on.

```bash
composer require elephentity/runtime
```

## This is a read-only mirror

The source of truth is [`packages/runtime`](https://github.com/hsimah-services/elephentity/tree/main/packages/runtime)
in [`elephentity`](https://github.com/hsimah-services/elephentity). This repository
exists only so `elephentity/runtime` is installable on its own — a WordPress site that
depends on `elephentity/wordpress` should not also pull in the spec compiler.

**Open pull requests against `elephentity`, not here.** A subtree split mirrors
`packages/runtime` into this repository's `main` on every push, and re-tags it whenever
`elephentity` is tagged — so this repo's history and tags always match the state of
`packages/runtime` at the same point in `elephentity`'s. A change made directly here
would be overwritten by the next split.

## What it is not

This package ships to production, but it is not itself a driver. There is no adaptor
here — `Storage\Testing\AdaptorConformance` is the suite any adaptor proves itself
against, and `elephentity/wordpress` and `elephentity/wpgraphql` are the two that do.
A project that wants no platform at all installs neither and writes its own adaptor
against `Storage\StorageAdaptor`, or uses `elephentity/memory`, which still lives in
`elephentity` alongside the compiler.

## Before you commit anything that crosses a repository boundary

**[`.llms/cross-repo.md`](.llms/cross-repo.md) is the closed list of what crosses.** If
you changed something on it, open an issue on each repository it reaches, before or
with the push. [`.llms/README.md`](.llms/README.md) has the rule and
[`.llms/issue-template.md`](.llms/issue-template.md) the shape.
