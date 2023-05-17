---
layout: post
title: "TIL: Evite perder arquivos apagados acidentalmente usando safe-rm"
date: 2023-05-16 08:00:00 -0300
categories: workflow portuguese
description: "Evite perder arquivos apagados acidentalmente pelo terminal utilizando o safe-rm: uma ferramenta que vai mover seus arquivos em vez de apaga-los efetivamente" 

---

Recentemente, assumi uma tarefa desafiadora na SourceLevel, meu trabalho atual. 
Essa atribuição envolveu a elaboração completa da documentação do nosso sistema, abordando aspectos 
como integração e utilização das diversas funcionalidades. Durante o processo, dediquei dois dias 
à redação de uma das páginas, negligenciando, infelizmente, a prática regular de realizar commits a cada hora.

Ao perceber a falha, tomei imediatamente a medida de efetuar os commits para evitar qualquer possibilidade de 
problemas futuros. Entretanto, surgiu a necessidade de remover algumas páginas que não estavam sendo 
utilizadas no projeto em questão, a fim de consolidar as alterações de forma limpa e manter um histórico adequado.

Infelizmente, para minha grande desventura, durante a realização das diversas exclusões dentro do 
editor de texto Vim, mesmo com todos os cuidados tomados, acabei apagando acidentalmente a página na qual 
havia trabalhado intensamente por dois dias. É relevante mencionar que a página não foi movida para a lixeira 
do sistema operacional, pois foi removida internamente através do comando `rm`.

Contudo, acredito firmemente que toda situação, por mais adversa que seja, proporciona lições valiosas. Diante disso, 
decidi buscar por medidas preventivas para evitar a recorrência desse tipo de incidente no futuro. 

Posteriormente, ao buscar por alternativas, descobri uma solução viável que envolve a criação de um alias 
para o comando `rm`. Essa abordagem não resultaria na exclusão permanente do arquivo, mas, em vez disso, 
o moveria para a lixeira. Dessa forma, caso houvesse a necessidade de recuperar o arquivo, bastaria acessar a pasta 
da lixeira e restaurá-lo.

Durante a minha pesquisa, encontrei um projeto bastante interessante 
chamado **[safe-rm](https://github.com/kaelzhang/shell-safe-rm)**, o qual automatiza todo esse processo. Esse projeto 
aceita os mesmos argumentos do comando **`rm`** convencional, porém move os arquivos para uma pasta específica, em vez 
de excluí-los permanentemente. 

Existem duas formas de instalar, sendo:

* Clonar o repositório

```shell
$ git clone git@github.com:kaelzhang/shell-safe-rm.git
$ cd shell-safe-rm
$ sudo sh install.sh) 
```

* Usando npm:

```shell
npm i -g safe-rm
```

Em ambos os casos, você vai precisar criar um `alias` em seu arquivo de configurações do bash (`~/.bashrc`):

```shell
alias rm='safe-rm’
```
Para obter mais informações detalhadas, recomendo consultar o arquivo **`README`** do projeto.

Adicionalmente, caso você use o `ZSH` você pode usar o projeto [zsh-safe-rm](https://github.com/mattmc3/zsh-safe-rm) que 
porta o projeto mencionado acima como um plugin do `ZSH`, facilitando ainda mais sua instalação. Como não é bem o foco aqui, 
não entrarei muito em detalhes, mas caso precise de mais informações, consulte o `README` do projeto.

Agora, todos os arquivos que forem apagados no seu SO usando o comando `rm`, vai na verdade mover esses arquivos pra pasta `~/.Trash`.
Caso necessário recuperar algum arquivo, apenas copie-o utilizando o comando `cp`.

```shell
cp ~/.Trash/my_deleted_file.txt ~/Documents
```

Sempre que necessário, você pode limpar sua lixeira usando o comando padrão `rm`:

```shell
command rm ~/.Trash/*
```

De qualquer forma, essa experiência destacou a importância crucial de adotar medidas preventivas e de se fazer commits 
regulares antes que 
a perda de arquivos importantes e dias de trabalho árduo se concretizem. Portanto, ao implementar essas medidas e 
adotar uma abordagem mais cautelosa em relação à manipulação de arquivos, é possível minimizar o risco de enfrentar 
situações frustrantes como essa no futuro. Afinal, a prevenção é o melhor caminho para preservar nosso trabalho e evitar 
contratempos desnecessários.

