---
layout: post
title: 'Git Stash: Uma ferramenta útil para salvar suas alterações'
date: 2023-08-04 09:00:00 -0300
categories: git
image: 'assets/rubocop-linter/rubocop-cover.png'
description: 'Descubra como essa ferramenta útil possibilita aos desenvolvedores salvar e gerenciar suas mudanças com facilidade, garantindo um fluxo de trabalho contínuo sem commits sujos e confusos.'
---

Olá, colegas desenvolvedores! 👋

Alguma vez você já se viu em uma situação em que estava no meio do trabalho em uma funcionalidade ou corrigindo um bug e, de repente, precisou mudar para outra tarefa? E você ainda não estava pronto para fazer um commit das suas alterações? Apresentamos o git stash - o super-herói do controle de versão!

### O que é o Git Stash?

`git stash` é um comando poderoso e conveniente no Git que permite salvar suas alterações atuais sem fazer um commit. É como uma área de armazenamento temporário para o seu trabalho, que você pode retomar mais tarde. Então, não se preocupe mais em perder o progresso ou fazer commits confusos só para mudar de tarefa!

### Como usar o Git Stash?

Usar o Git Stash é muito fácil. Quando você quiser salvar suas alterações, basta executar em seu terminal:

```bash
git stash
```

Esse comando vai guardar todas as suas modificações, deixando o diretório de trabalho limpo e pronto para a próxima tarefa.

### Recuperando suas alterações guardadas

Quando estiver pronto para continuar trabalhando nas alterações guardadas, não se preocupe! Você pode recuperá-las facilmente com:

```bash
git stash pop
```

Esse comando aplicará o stash mais recente e o removerá da pilha de stashes. Se você quiser manter o stash para uso posterior, pode utilizar:

```bash
git stash apply
```

### Outros comandos úteis do Git Stash

- Para ver a lista dos seus stashes:

```bash
git stash list
```

- Para guardar suas alterações junto com arquivos não rastreados(untrackeds):

```bash
git stash -u
```

- Para dar uma descrição significativa às suas mudanças guardadas (altamente recomendado por questões de clareza!):

```bash
git stash save "Fixing login issue"
```

Atenção: O stash não substitui os commits adequados. Certifique-se de usá-lo apenas para armazenamento temporário e faça commits quando as alterações estiverem prontas para produção.

Portanto, da próxima vez que estiver em um furacão de código e precisar mudar rapidamente de tarefa, lembre-se do seu fiel ajudante git stash para salvar o dia!

### References

- [Git - git-stash Documentation](https://git-scm.com/docs/git-stash)
