---
layout: post
title: "Por que você deveria assinar seus commits"
date: 2023-03-12 08:00:00 -0300
categories: git portuguese
description: Você sabia que qualquer um pode fazer commits no git usando seu nome de usuário? Vou ensinar sobre alguns metadados incluídos em cada commit e como alguém pode usá-los para se passar por você.
---

Git é um sistema de controle de versão distribuído que permite aos desenvolvedores gerenciar alterações em seu código ao longo do tempo. Cada vez que um desenvolvedor faz alterações na base de código, ele cria um novo commit, que representa um retrato do código em um ponto específico no tempo. Juntamente com as alterações no código, cada commit também inclui metadados que fornecem informações importantes sobre a aquele commit.

Os metadados de um commit incluem várias informações importantes, como `author`, `committer`, `committer date` e `author date`. O _author_ é a pessoa que originalmente escreveu o código, enquanto o _committer_ é a pessoa que aplicou as alterações no repositório. O [_author date_](https://gustavoaraujo.dev/git/2023/02/28/how-to-hack-github-contributions-graph-specify-the-commit-date.html) refere-se à data, e hora em que o código original foi escrito, enquanto o _committer date_ refere-se à data e hora em que as alterações foram efetuadas no repositório. O _commiter date_ mudará quando você fizer alterações usando `--amend`, um push forçado, um rebase ou outros comandos git.

Em resumo, os metadados de um commit no git fornecem informações críticas sobre o código, incluindo quem o escreveu, quem aplicou as alterações e quando essas alterações foram feitas. Essas informações são essenciais para entender o contexto do código e acompanhar as alterações na base de código ao longo do tempo. Por padrão, o metadado `autor/committer date` é preenchido com a data atual, enquanto o `author/committer` é preenchida com a configuração git `user`, presente no arquivo de configuração git (`~/.gitconfig`).

No git, você pode especificar o autor de um commit, usando o argumento `--author`. Conforme mencionado, o autor padrão é obtido do arquivo de configuração git.

{% include image.html src="/assets/git-sign-commits/authored-commit.png" alt="Um commit especificando o autor" caption="Um commit especificando o autor" %}

Eu criei este commit apenas preenchendo o argumento `--author`, da seguinte forma:

```bash
git commit --author="Lucas Felipe <lpaivareis@users.noreply.github.com>"
```
Como você pode ver, eu defini `lpaivareis` como o autor, mas eu era o responsável pelo commit, então o git me colocou como o committer. Isso aconteceu porque fiz esse commit do meu computador e minha configuração do git tem meu nome de usuário e e-mail.

__Mas o que acontece se eu quiser fingir ser alguém e definir meu arquivo de configuração git com outro nome de usuário e e-mail? Exatamente! Esse é o ponto.__

```bash
git config user.name "Lucas Felipe"
git config user.email "lpaivareis@users.noreply.github.com"
```
Agora, todos os meus commits neste repositório (e em todos, se eu defini-lo globalmente usando o argumento `--global`) vão constar que foram feitos pelo usuário `lpaivareis`:

{% include image.html src="/assets/git-sign-commits/fake-commit.png" alt="Commit indevidamente atribuído a lpaivareis" caption="Commit indevidamente atribuído a lpaivareis" %}

Este é um comportamento esperado do git, você pode fazer commits em nome de outras pessoas, ou apenas colocá-los como autores de um commit, e eles não precisam aceitar nada, nem saberão disso. Neste caso, meu amigo Lucas Felipe ([_lpaivareis_](https://github.com/lpaivareis/)) nem sequer tem acesso ao repositório privado que estou utilizando.

A única maneira de deixar as pessoas confiarem em seus commits, provando que eles realmente vieram de você, é assinando todos os seus commits. Tudo o que você precisa fazer é gerar uma chave GPG, adicioná-la à sua conta GitHub ou GitLab e dizer ao git para assinar todos os seus commits com essa chave:

```bash
git config --global commit.gpgsign true
``````
Assinando seus commits, você ganhará uma linda badge de verificado em todos os seus commits:

{% include image.html src="/assets/git-sign-commits/signed-commit.png" alt="Um commit devidamente assinado" caption="Um commit devidamente assinado" %}

O objetivo deste post é apenas convencê-lo de que você realmente precisa assinar todos os seus commits, e se eu consegui fazê-lo, vou lhe deixar ótimas referências de como fazer isso:

- [Managing commit signature verification - GitHub Docs](https://docs.github.com/en/authentication/managing-commit-signature-verification)
- [Sign commits with GPG - GitLab Docs](https://docs.gitlab.com/ee/user/project/repository/gpg_signed_commits/)
- [Signing Your Work - git Docs](https://git-scm.com/book/en/v2/Git-Tools-Signing-Your-Work)

Obrigado por ler! 

### Referencias
* [git commit](https://mirrors.edge.kernel.org/pub/software/scm/git/docs/git-commit.html#_commit_information)


