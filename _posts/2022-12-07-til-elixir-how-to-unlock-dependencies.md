---
layout: post
title: "TIL: How to remove unused deps from mix.lock in Elixir"
date: 2022-12-07 10:52:14 -0300
categories: elixir
description: Today I Learned how to unlock dependencies removing the unused ones from your mix.lock file to keep your .lock file always updated
---

When you add new dependencies to your elixir project and run `mix deps.get`, it will create/update the `mix.lock` file, that list all information about the versions of the dependencies that you are using, such as version, source, etc.

But when you remove a specific dependency from your `mix.exs` file, you will need to remove it from the `mix.lock` file to keep the file as updated as possible.

But, NEVER update this file manually, let `mix` do it for you:

```bash
mix deps.unlock NAME
```

This command supports some arguments:

```bash
--all - unlocks all dependencies
--filter - unlocks only deps matching the given name
--unused - unlocks only unused dependencies (no longer mentioned in the mix.exs file)
--check-unused - checks that the mix.lock file has no unused dependencies. This is useful in pre-commit hooks and CI scripts if you want to reject contributions with extra dependencies
```

So to keep your `mix.lock` file updated, just run:

```bash
mix deps.unlock --unused --check-unused
```
**Important note**: This command only unlocks dependencies, to remove it completely, including build artifacts and fetched sources, you can use the following command:

```bash
mix deps.clean --unused --unlock
```
