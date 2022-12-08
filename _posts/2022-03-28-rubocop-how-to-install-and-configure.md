---
layout: post
title: "RuboCop: How to install and configure"
date: 2022-03-28 10:52:14 -0300
categories: ruby
description: That Code quality is important, and any high-performing team knows it, but do you follow a guideline to standardize your codebase and make sure that everyone is going and looking in the same direction? Learn how to install and configure Rubocop linter.
---

That Code quality is important, and any high-performing team knows it, but do you follow a guideline to standardize your codebase and make sure that everyone is going and looking in the same direction?

Making a brief introduction, this is the goal of a linter: A tool that analyzes your source code to identify programming errors, bugs, and suspicious constructions *([Wikipedia](https://en.wikipedia.org/wiki/Lint_(software))).*

The main objective is to ensure that your code follows the same rules and practices, to look like the entire code was written by the same person.

In a large variety of linters from Ruby, we have **[RuboCop](https://github.com/rubocop/rubocop/)** (available as a gem) that follows the best practices described in [The Ruby Style Guide](https://rubystyle.guide/).

One of the advantages of using a linter is to save time reviewing code because it prevents small issues like inconsistent variable names and practices during the development process. With that, the code review is more efficient, and it can be focused on implementations and features requirements.

Starting using RuboCop is very straightforward and doesn’t depend on anyone else to setup it. You can install the gem and run it immediately during your workflow.

## Installation

To install the RuboCop, it’s quick and easy. Let's consider here that all your Ruby environment is working, so just execute the following command to install the latest RuboCop version available: 

```bash
$ gem install rubocop
```

RuboCop officially supports the **MRI 2.5+** and **jRuby 9.2+** implementations. You can also install directly in the project using Bundler, adding the gem to your `Gemfile`, and then run `bundle install`.

## Configuration

The RuboCop behavior can be controlled in the `.rubocop.yml` file in the root path where you want to execute it. In this file, you can enable/disable certain cops (rules) or change their behavior.

All cops are grouped into departments: **Style**, **Layout**, **Lint**, **Naming**, **Security**, **Metrics**, **Migration**, **Bundler,** and **Gemspec**. You can read about the cops and their departments in the [documentation](https://docs.rubocop.org/rubocop/cops.html). For reference purposes, check the configuration file that we use in [SourceLevel](https://sourcelevel.io/) in our [linter’s configuration repository](https://github.com/sourcelevel/linters/blob/main/.rubocop.yml).

The `.rubocop.yml` file has the following structure:

```yaml
inherit_from: ../.rubocop.yml

require: rubocop-rails

Style/Encoding:
  Enabled: false

Layout/LineLength:
  Max: 99

...
```

*Note 1: We’re using `inherit_from` to inherit all defined cops in the other file. See more in the [documentation](https://docs.rubocop.org/rubocop/configuration.html#inheritance).
Note 2: If you’re using **Rails**, it’s important to require the `rubocop-rails` extension (remember to add it to your `Gemfile`), which will force RuboCop to follow the [conventions and good practices](https://rails.rubystyle.guide/) defined by the Rails community.* 

By default, when executed, the RuboCop looks for `.rubocop.yml` in the current directory, then in your home path (`~/.rubocop.yml`), and in the last case it will use the defaults. More details about RuboCop’s configuration file can be found on the [documentation](https://docs.rubocop.org/rubocop/configuration.html).

If you want to create your configuration file, which I encourage, a good starting point is to use the [configuration](https://github.com/rubocop/rubocop/blob/master/.rubocop.yml) available in the RuboCop repository as a reference. You can review cop by cop and configure what suits you. Just remember to check the cop availability for the version of RuboCop that you’re using.

Keep in mind that style rules that belong to the `Style` namespace are configurable and optional. A good recommendation is that these rules need to be discussed and defined with the entire team, not by a single person.

It’s nice to mention that you can write your own cops, called **Custom Cops**. With that, you can create your own rules, defining your practices to ensure that they will be followed. You can find more information about this process in [documentation](https://docs.rubocop.org/rubocop/development.html).

## Usage

To use the RuboCop you just need to navigate to the directory where you want to run the linter, and execute:

```bash
$ rubocop
```

You can specify a file/path too:

```bash
$ rubocop lib/file.rb
```

It’s possible to specify a list of directories and files:

```bash
$ rubocop app/ spec/ lib/file.rb
```

After running RuboCop, you’ll get an output with offenses, like:

```ruby
Offenses:

test.rb:1:1: C: Style/FrozenStringLiteralComment: Missing magic comment # frozen_string_literal: true.
def badName
^
test.rb:1:5: C: Naming/MethodName: Use snake_case for method names.
def badName
    ^^^^^^^
test.rb:2:3: C: Style/GuardClause: Use a guard clause instead of wrapping the code inside a conditional expression.
  if something
  ^^
test.rb:2:3: C: Style/IfUnlessModifier: Favor modifier if usage when having a single-line body. Another good alternative is the usage of control flow &&/||.
  if something
  ^^
test.rb:4:5: W: Layout/EndAlignment: end at 4, 4 is not aligned with if at 2, 2.
    end
    ^^^

1 file inspected, 5 offenses detected
```

### Autocorrecting

A great thing about RuboCop is the autocorrecting feature. This option fix automatically all possible offenses in your code, based on defined rules. In our case, we use `-a` that fix safe offenses, but you can be more optimistic and use `-A` to fix all offenses (including unsafe), but you need to use it with caution.

To use them, you just need to run RuboCop with this autocorrecting argument:

```bash
$ rubocop --auto-correct
# or
$ rubocop -a
```

You can check all **RoboCop’s** arguments using the `--help`:

```bash
$ rubocop --help
```

Just for linking purposes, you can check the [documentation](https://docs.rubocop.org/rubocop/usage/auto_correct.html) to know more about autocorrect.

## Integrating with other tools

RuboCop integrates with many other tools. You may integrate it into your code editor to run it every time you save a file, and you'll immediately get its insights. 

For a list of currently supported code editors, you can check [this page](https://docs.rubocop.org/rubocop/integration_with_other_tools.html#editor-integration) on documentation, and if your favorite is not listed, it’s a great opportunity to contribute to RuboCop implementing an integration.

Another great usage is creating a [Git Hook](https://git-scm.com/book/en/v2/Customizing-Git-Git-Hooks) to run RuboCop before every commit. You can also setup RuboCop to be run into your Continuous Integration service (such as GitHub Actions) to have some insights for every commit. In all cases, more details can be found in the [documentation](https://docs.rubocop.org/rubocop/integration_with_other_tools.html#git-pre-commit-hook-integration-with-pre-commit).

I hope you enjoyed the content, and thank you for reading.
