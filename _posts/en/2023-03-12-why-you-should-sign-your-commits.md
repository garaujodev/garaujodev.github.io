---
layout: post
title: "Why you should sign your git commits"
date: 2023-03-12 08:00:00 -0300
categories: git 
description: Did you know that anyone can make git commits using your username? I will teach you about some metadata included in each commit, and how someone can use them to impersonate you.
---

Git is a distributed version control system that allows developers to manage changes to their code over time. Each time a developer makes changes to the codebase, they create a new commit, which represents a snapshot of the code at a specific point in time. Along with the changes to the code, each commit also includes metadata that provides important information about the commit.

The metadata of a commit includes several key pieces of information, such as the `author`, `committer`, `committer date`, and `author date`. The author is the person who originally wrote the code, while the committer is the person who applied the changes to the repository. The [author date](https://gustavoaraujo.dev/git/2023/02/28/how-to-hack-github-contributions-graph-specify-the-commit-date.html) refers to the date, and time when the original code was written, while the committer date refers to the date and time when the changes were committed to the repository. The commit date will change when you make changes by using `--amend`, a force push, a rebase, or other git commands.

In summary, the metadata of a commit in git provides critical information about the code, including who wrote it, who applied changes to it, and when those changes were made. This information is essential for understanding the context of the code and tracking changes to the codebase over time. By default, the `author/committer date` information is filled with the current date, and the `author/committer` is filled with the `user` configuration from the git configuration file (`~/.gitconfig`).

In a git commit, you can specify the author of a commit, using the `--author` argument. As mentioned, the default author is taken from the git configuration file.

{% include image.html src="/assets/git-sign-commits/authored-commit.png" alt="A commit specifying the author" caption="A commit specifying the author" %}

I created this commit just providing an author argument:

```bash
git commit --author="Lucas Felipe <lpaivareis@users.noreply.github.com>"
```
As can you see, I set `lpaivareis` as the author, but I was responsible for the commit, so the git put me as the committer. This happen because I did this commit from my computer, and my git configuration has my username and email.

__But what happens if I want to impersonate someone, and set my git configuration file with another username and email? Exactly! This is the point.__

```bash
git config user.name "Lucas Felipe"
git config user.email "lpaivareis@users.noreply.github.com"
```
Now, all my commits in this repository (and all of them, if I set it globally using the `--global` argument) will seem that come from `lpaivareis`:

{% include image.html src="/assets/git-sign-commits/fake-commit.png" alt="An misattributing commit impersonating Lucas" caption="An misattributing commit impersonating Lucas" %}

This is an expected behavior from git, you can make commits in name of others, or just put them as the author of a commit, and they don't need to accept anything, they won't even know about it. In this case, my friend Lucas Felipe ([_lpaivareis_](https://github.com/lpaivareis)) nor have access to the private repository that I'm using.

The only way to let people trust in your commits, proving they really came from you, is signing all your commits. All that you will need to do, is generate a GPG key, add them to your GitHub or GitLab account, and tell to git sign all of your commits with that key:

```bash
git config --global commit.gpgsign true
``````
Signing your commits, you'll get a beautiful verified badge in all of your commits:

{% include image.html src="/assets/git-sign-commits/signed-commit.png" alt="A signed commit" caption="A signed commit" %}

This post's purpose is just to convince you that you really need to sign all of your commits, and if I was successful in my mission, I'll give you great references to do that:

- [Managing commit signature verification - GitHub Docs](https://docs.github.com/en/authentication/managing-commit-signature-verification)
- [Sign commits with GPG - GitLab Docs](https://docs.gitlab.com/ee/user/project/repository/gpg_signed_commits/)
- [Signing Your Work - git Docs](https://git-scm.com/book/en/v2/Git-Tools-Signing-Your-Work)

Thanks for reading! 

### References
* [git commit](https://mirrors.edge.kernel.org/pub/software/scm/git/docs/git-commit.html#_commit_information)


