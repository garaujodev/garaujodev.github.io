---
layout: post
title: "Rubocop: Como instalar e configurar"
date: 2022-01-09 17:11:14 -0300
categories: ruby portuguese
description: Aprenda a instalar e configurar o linter Rubocop, para garantir a consistência e padronização de sua codebase Ruby.
---

Que a qualidade de código é importante todo mundo sabe, mas você tem ou segue um guideline bem definido, para padronizar o seu código?

Fazendo uma introdução bem leve, esse é o intuito de um linter: *uma ferramenta que analisa o código fonte para identificar erros de programação, bugs, erros estáticos e construções suspeitas ([Wikipedia](https://en.wikipedia.org/wiki/Lint_(software)))*

Nos dias atuais é muito difícil manter padronização de código dentro de uma equipe sem o auxilio de um linter, que vai garantir ao máximo que o seu código siga as mesmas regras, de tal forma que pareça que foi escrito por uma única pessoa!

Dentre uma variedade de linters existentes, para as mais diversas linguagens e estilos de código, temos o **[Rubocop](https://github.com/rubocop/rubocop/)**, que é uma [gem](https://rubygems.org/gems/rubocop) (um pacote Ruby) que segue as boas práticas do [guia de estilo Ruby](https://rubystyle.guide/).

Uma vantagem do **Rubocop** (não só do Rubocop, mas qualquer linter diga-se de passagem) é diminuir tempo de revisão de código, pois ele vai evitar muitos problemas como mudanças de estilos ou uma variável não utilizada, fazendo assim com que as revisões de código sejam mais focadas na implementação e requisitos das funcionalidades.

## Instalação

Para instalar o **Rubocop**, é bem rápido e simples. Vamos considerar aqui que todo o seu setup Ruby esteja funcional, então execute o seguinte comando para instalar a última versão disponível:

```bash
$ gem install rubocop
```

_Lembrando que **Rubocop** oficialmente suporta as implementações **MRI 2.5+** e **jRuby 9.2+**.
Você também pode instalar usando o Bundler, adicionando a gem ao seu arquivo `Gemfile` e então execute um `bundle install`._

## Configuração

O comportamento do **Rubocop** pode ser controlado via arquivo `.rubocop.yml` na raiz do projeto onde você deseja executá-lo. É nesse arquivo que você consegue habilitar/desabilitar certas cops (regras) ou alterar seu comportamento.
Todas as cops são agrupadas em departamentos, sendo eles: Style, Layout, Lint, Name, Security, etc. Você pode ler melhores sobre as cops e seus agrupamentos na [documentação](https://docs.rubocop.org/rubocop/cops.html). Você pode ver o arquivo que usamos nos repositórios Ruby na [SourceLevel](https://sourcelevel.io) [neste link](https://github.com/sourcelevel/linters/blob/main/.rubocop.yml).

Um arquivo `.rubocop.yml` tem a seguinte estrutura:

```bash
inherit_from: ../.rubocop.yml

require: rubocop-rails

Style/Encoding:
  Enabled: false

Layout/LineLength:
  Max: 99

...
```

_Nota 1: Usamos o `inherit_from` para usar as cops já definidas de um outro arquivo ou URL. Mais detalhes na [documentação](https://docs.rubocop.org/rubocop/configuration.html#inheritance).
Nota 2: Se você usa **Rails**, é extremamente importante fazer o require do `rubocop-rails`, que é uma extensão do **Rubocop** que vai forçar o uso das convenções de código e [boas práticas definidas pelo Rails](https://rails.rubystyle.guide/)._


Por padrão, o **Rubocop** procura por um arquivo `.rubocop.yml` no diretório atual sempre que executado, caso não encontre, ele vai procurar no seu home path (`~/.rubocop.yml`) e em último caso vai usar o arquivo de configuração padrão. Mais detalhes sobre a configuração do **Rubocop** podem ser encontradas na [documentação oficial](https://docs.rubocop.org/rubocop/configuration.html).

Se você deseja criar seu próprio arquivo de configuração, o que é bem interessante, um bom ponto de partida seria pegar o [arquivo usado](https://github.com/rubocop/rubocop/blob/master/.rubocop.yml) no próprio repositório do **Rubocop**, e assim revisar regra por regra na [documentação](https://docs.rubocop.org/rubocop/cops.html#available-cops) e ver o que funciona melhor pra você e sua equipe. Lembrando que é importante verificar a disponibilidade da cop para a versão do Rubocop que você está utilizando, para isso selecione a versão da gem que está usando na documentação.

Deixando a resalva que regras de estilo que estão no namespace `Style` dos arquivos padrões e mencionados acima, não necessariamente são regras que precisam ser utilizadas. Esse é um estilo de codificação que deve ser observado e discutido pela equipe, e não definido por um único colaborador.

## Uso

Para usar o **Rubocop** é bastante simples, basta ir até o diretório onde deseja rodar o linter, e executa-lo:

```bash
$ rubocop
```

Ou você pode especificar um arquivo/path:

```bash
$ rubocop lib/arquivo.rb
```

É possível também passar uma lista de diretórios e arquivos:

```bash
$ rubocop app spec lib/arquivo.rb
```

Após executar, o **Rubocop** deve lhe reportar os erros encontrados, com base nos cops que foram definidos:

```bash
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

### Autocorreção

Uma feature bem interessante do **Rubocop** é a autocorreção, que corrige automaticamente grande maioria dos problemas que ele encontrar em seu código.

Para usar, você só precisa especificar o argumento na chamada do **Rubocop**:

```bash
$ rubocop -a
# ou
$ rubocop --auto-correct
```

Mas com grandes poderes vem grandes responsabilidades, e recomendo que leia bem sobre a feature antes de usar. Você pode encontrar mais detalhes na [documentação](https://docs.rubocop.org/rubocop/usage/auto_correct.html).

Se você usa o editor **VSCode**, é possível usar uma extensão que praticamente automatiza todo o processo acima. A extensão pode ser encontrada no [Marketplace](https://marketplace.visualstudio.com/items?itemName=misogi.ruby-rubocop). Existe extensão similar para vários outros editores.

Caso tenham alguma dúvida, sintam-se a vontade para me contatar no [Twitter](https://twitter.com/garaujodev). Ficarei feliz em ajudar 🙂
