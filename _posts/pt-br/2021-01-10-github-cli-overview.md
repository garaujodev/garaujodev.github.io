---
layout: post
title: "GitHub CLI: PRs, Issues e mais do GitHub direto no terminal"
date: 2021-01-10 10:00:00 -0300
categories: ferramentas
description: "Um overview sobre a nova ferramenta do GitHub: PRs, Issues e outros conceitos do GitHub direto no terminal"
---

### O que é?

GitHub CLI (_Command Line Interface_), como o próprio nome sugere, é o GitHub via linha de comando. Com essa ferramenta é possível trazer _pull requests_, _issues_ e outros conceitos do GitHub para dentro do terminal.

Como sugere o [repositório oficial](https://github.com/cli/cli), a CLI do GitHub está disponível para repositórios hospedados em [GitHub.com](http://github.com/) e GitHub Enterprise Server 2.20+, e pode ser instalado em MacOS, Windows e Linux.

### Vale a penar usar?

É uma pergunta bastante relativa, que pode ser respondida levantando dois pontos:

- Você é um amante do Terminal?
- Você já usa o `git` via CLI?

Se a resposta para ambos for sim, talvez vale a pena dar uma olhada mais a fundo.

Com a ferramenta, você consegue abrir um _Pull Request_ pelo mesmo terminal que faz seus _commits_, o que nos poupa bastante tempo, simples e rápido.

### Como instalar

Como não é bem o foco aqui, vou deixar a recomendação de consultar a [própria documentação](https://github.com/cli/cli#installation).

Após instalar, execute o seguinte comando para testar o funcionamento e já verificar todos os comandos:

```bash
$ gh --help
```

- **Lembrando que, `gh` é o próprio binário, não se trata de um _alias_ 🙂.**

### Passos iniciais

O primeiro passo após instalar é autenticar com sua conta do GitHub, para isso basta executar o comando:

```bash
$ gh auth login
```

Existem duas formas de login:

- Via token, que pode ser gerado no GitHub
- Login no navegador

Por questões de praticidade, recomendo a segunda opção. Após autenticado, você pode verificar o status com o comando:

```bash
$ gh auth status
```

Feito isso, caso queira você já pode configurar o seu editor de texto favorito para editar as mensagens de _Pull Requests:_

```bash
$ gh config set editor <editor>
```

Lembrando que, caso não seja atribuído nenhum editor utilizando o comando acima, o `gh` assumirá o padrão definido na variável de ambiente `$EDITOR` (No MacOS e no Linux o editor padrão é o `Nano`, no Windows `Notepad`).

Mais detalhes sobre o comando `gh config` podem ser encontrados na [documentação oficial](https://cli.github.com/manual/gh_config).

## Hands-on - O que é possível fazer?

Abaixo temos algumas das coisas interessantes que essa ferramenta nos permite fazer.

## Pull Requests

- Abrir um _Pull Request_:

  ```bash
  $ gh pr create
  ```

  ![GIF exemplificando o uso do comando](/assets/github-cli/pr_cut_2.gif)

  Algum dos parâmetros interessantes que temos aqui:

  - Com o parâmetro `-B` podemos especificar o base branch, isto é, para qual branch essas alterações serão enviadas após o merge:

  ```bash
  $ gh pr create -B main
  ```

  - Com o parâmetro `-d` podemos especificar que se trata de um _[Draft Pull Request](https://docs.github.com/pt/free-pro-team@latest/github/collaborating-with-issues-and-pull-requests/about-pull-requests#pull-requests-de-rascunho):_

  ```bash
  $ gh pr create -d
  ```

- Fechar/reabrir um _Pull Request:_

  ```bash
  $ gh pr close/reopen
  ```

- Mergear um _Pull Request:_

  ```bash
  $ gh pr merge
  ```

- Listar _Pull Requests:_

  ```bash
  $ gh pr list
  ```

- Ver o _diff_ de um _Pull Request:_

  ```bash
  $ gh pr diff
  ```

- Revisar um _Pull Request_:

  ```bash
  $ gh pr review
  ```

- Verificar os _status checks_ de um _Pull Request_ aberto, como o _CI_:

  ```bash
  $ gh pr checks
  ```

- Verificar seu status de _Pull Requests:_

  ```bash
  $ gh pr status
  ```

  ![GIF exemplificando o uso do comando](/assets/github-cli/prstatus_cut.gif)

## Issues

- Criar uma _Issue:_

  ```bash
  $ gh issue create
  ```

  ![GIF exemplificando o uso do comando](/assets/github-cli/issue_cut.gif)

- Fechar/reabrir uma _Issue:_

  ```bash
  $ gh issue close/reopen
  ```

- Listar _Issues:_

  ```bash
  $ gh issue list
  ```

- Ver uma _Issue:_

  ```bash
  $ gh issue view
  ```

- Verificar seu status de _Issues:_

  ```bash
  $ gh issue status
  ```

  ![GIF exemplificando o uso do comando](/assets/github-cli/issue_status_cut.gif)

### Considerações finais

Com certeza é uma ferramenta sensacional, que, se bem usada nos poupa bastante tempo.

Caso tenham dúvidas, sintam-se a vontade para me contatar via [Twitter](http://twitter.com/garaujodev) 😉
