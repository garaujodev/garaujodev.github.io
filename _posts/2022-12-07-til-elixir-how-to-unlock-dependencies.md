---
layout: post
title: "TIL: How to remove unused deps from mix.lock in Elixir"
date: 2022-12-07 10:52:14 -0300
categories: elixir
description: TODAY I LEARNED how to unlock dependencies removing the unused one from your mix.lock file
---

When you add new depencies to your elixir project, and run `mix.deps.get`, it will creates/update the `mix.lock` file, that list all information about the versions of the dependencies you are using, like version, source, etc.

But when you remove specific dependency from your `mix.exs` file, you will need to remove it from the `mix.lock` file to keep the file updated as possible.

But, NEVER update this file mannually, lets `mix` update it to you:

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
**Important note**: This command only unlock dependencies, to remove it completely from the `_build` folder, you can use the following command:

```bash
mix deps.clean --unused --unlock
```
