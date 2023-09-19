---
layout: post
title: "Configurando o Neovim para Desenvolvimento Elixir"
date: 2023-09-19 10:00:00 -0300
categories: elixir
description: "O Neovim é um poderoso editor que pode ser transformado em uma IDE completa para Elixir com a adição de algumas ferramentas e extensões. Neste guia, vamos explorar como montar um ambiente otimizado para desenvolvimento Elixir no Neovim."
---

O Neovim é um poderoso editor que pode ser transformado em uma IDE completa para Elixir com a adição de algumas ferramentas e extensões. Neste guia, vamos explorar como montar um ambiente otimizado para desenvolvimento Elixir no Neovim.

---
## Pré-requisitos:

- Neovim instalado.
- Git instalado (para clonar plugins).

Esses são os requisitos funcionais obrigatórios. Porém outras ferramentas são necessarias para tirar total proveito do Lazyvim. Recomendo que acesse a página oficial: [Lazyvim - Requirements](https://www.lazyvim.org/#%EF%B8%8F-requirements)
## 1. Instalação do Lazyvim

Eu já perdi muito tempo configurando todos os plugins da minha forma. Isso te dá muito controle sobre como você monta seu setup, porém você sempre vai ter algum problema de um plugin descontinuado ou coisa parecida, o que dá muito trabalho de manter atualizado e funcional. Por esse motivo, nos dias de hoje, eu tanto uso quanto encorajo a usar ferramentas como o Lazyvim, que já trás toda uma suite de plugins configurados, além da própria comunidade fazer uma curadoria e ser ativa no sentido de manter todos os plugins que fazem parte da suite estarem funcionais e ativos. 

A instalação é bastante simples, você só vai precisar clonar um template inicial:

```bash
git clone https://github.com/LazyVim/starter ~/.config/nvim
```

É altamente recomendável que você apague a pasta `.git` desse repositorio, assim, você pode adicionar seu próprio repositório e versionar suas configurações:

```bash
rm -rf ~/.config/nvim/.git
```

Para mais detalhes, você pode acessar a [documentação do Lazyvim](https://www.lazyvim.org/installation).

Agora, abra seu Neovim usando `nvim` e aguarde o download de todos os plugins. Recomendo executar `:checkhealth` para obter um relatório completo, para garantir que todos os requisitos da suite Lazyvim estão satisfeitos.

Daqui em diante, abordaremos duas formas diferentes de se instalar os plugins, sendo via comando, e via arquivo. Eu particularmente lhe recomendo instalar via arquivo, que é interessante caso você queira versionar todo o seu setup de ambiente no git. Feito isso, para subir o mesmo setup do seu neovim em outro computador, você só precisa clonar seu repositório no diretorio de configurações do neovim, assim como fez com o starter-template do Lazyvim.

## 2. Configurando o Language Server Protocol (LSP) para Elixir

O Lazyvim usa o [Mason](https://github.com/williamboman/mason.nvim), que é um gerenciador de pacotes portavel que permite que você instale servidores LSP, DAP, Linters e Formatters de forma rápida e fácil. O que é um trabalho bastante chato de se fazer na mão, se torna fácil usando o Mason.

### Instalando via comando

  Você pode instalar usando a interface do próprio Mason, que é acessada usando `:Mason` (navegue usando o vim-way de navegação, `k` ou `j` e use `i` para instalar). Você pode consultar a seção de ajuda usando `g?`.

### Instalando via arquivo

Outra forma de instalacão, um pouco mais pragmatica, é fazendo isso via arquivo de plugin. Crie um arquivo com qualquer nome no diretório `~/.config/nvim/lua/plugins/` com a extensão `.lua`. Nesse caso, iremos adotar `elixir.lua`:

  ```bash
  nvim ~/.config/nvim/lua/plugins/elixir.lua
  ```

  Dentro desse arquivo, cole o seguinte trecho:

  ```lua
  return {
    {
      "williamboman/mason.nvim",
      opts = function(_, opts)
        vim.list_extend(opts.ensure_installed, {
          "elixir-ls",
        })
      end,
    },
  }
```

Como você pode ver, extendemos a funcionalidade do Mason, adicionando o `elixir-ls` a lista do `ensure_installed` que vai garantir que esse plugin esteja instalado quando iniciarmos o neovim. Você pode adicionar outros plugins, caso queira. Salve o arquivo e reinicie o seu neovim.

Lembrando que o ElixirLS já nos oferece a funcionalidade de formatter, portanto quando você salvar seu código, ele vai automaticamente formata-lo.

## 2. Configurando o TreeSitter para Syntax Highlight

Para syntax highlight usaremos o [treesitter](https://github.com/nvim-treesitter/nvim-treesitter), que é auto-definido como uma ferramenta de gerenciamento de parsers. A configuração segue a mesma linha do LSP, onde você pode instalar via comando, ou via arquivo, sendo esse último mais recomendado em caso de versionamento de sua configuração neovim.

### Instalando via comando

  Para instalar via comando, você só precisa executar o seguinte comando:

  ```jsx
  :TSInstall elixir
  ```

  Lembrando que o TreeSitter tem uma infinidade de parsers para várias linguagens, que pode ser consultada no [repositório oficial](https://github.com/nvim-treesitter/nvim-treesitter#supported-languages).

### Instalando via arquivo

  Abra novamente o arquivo `~/.config/nvim/lua/plugins/elixir.lua` e adicione o seguinte trecho após as aspas de fechamento do primeiro bloco, do LSP (`},`):

  ```lua
  {
      "nvim-treesitter/nvim-treesitter",
      opts = function(_, opts)
        vim.list_extend(opts.ensure_installed, {
          "elixir",
          "heex",
          "eex",
        })
      end,
    },
  ```

  Você pode criar um novo arquivo `.lua` dentro da pasta `/plugins` com o nome que desejar. Fica totalmente a seu critério.

  O arquivo final (`elixir.lua`), com a configuração do LSP e do syntax highlight deve ficar assim:

  ```lua
  return {
    {
      "williamboman/mason.nvim",
      opts = function(_, opts)
        vim.list_extend(opts.ensure_installed, {
          "elixir-ls",
        })
      end,
    },
    {
      "nvim-treesitter/nvim-treesitter",
      opts = function(_, opts)
        vim.list_extend(opts.ensure_installed, {
          "elixir",
          "heex",
          "eex",
        })
      end,
    },
  }
  ```

## 3. Interação com testes: Configurando o Neotest

O Neotest é um framework extensível para interagir com testes dentro do NeoVim. Seu uso permite listar os testes existentes, bem como executa-los e obter seu status sem precisar sair do seu editor. Você vai ter acesso a um sumário listando todos os testes que passaram, quais falharam, bem como os outputs dos testes que falharam, dentre outras.

  ![Interface do Neovim utilizando neotest](/assets/configurando-neovim-para-elixir/lazyvim-neotest.png)

O Lazyvim já nos oferece o neotest como um extra. Você só precisa habilita-lo. Abra o arquivo `~/.config/nvim/lua/config/lazy.lua` e adicione o seguinte extra:

  ```lua
  { import = "lazyvim.plugins.extras.test.core" },
  ```

Sua sessão `spec` deve se parecer a algo como isso:

  ```lua
  spec = {
      -- add LazyVim and import its plugins
      { "LazyVim/LazyVim", import = "lazyvim.plugins" },
      -- import any extras modules here
      -- { import = "lazyvim.plugins.extras.lang.typescript" },
      -- { import = "lazyvim.plugins.extras.lang.json" },
      -- { import = "lazyvim.plugins.extras.ui.mini-animate" },
      { import = "lazyvim.plugins.extras.test.core" },
      -- import/override with your plugins
      { import = "plugins" },
    },
  ```

Caso queira saber mais sobre os extras que o Lazyvim possui, você pode consultar o menu lateral “Extras” diretamente no [site oficial](https://www.lazyvim.org/).

Agora, vamos instalar o adapter `neotest-elixir` para ser possível interagir com a suite de testes Elixir. Abra seu arquivo `~/.config/nvim/lua/plugins/elixir.lua` (ou crie um novo) e vamos adicionar mais uma seção:

  ```lua
    { "jfpedroza/neotest-elixir" },
    {
      "nvim-neotest/neotest",
      opts = { adapters = { "neotest-elixir" } },
    },
  ```

Salve o arquivo, e reinicie seu Neovim. 

Agora você vai conseguir interagir com seus testes, como executar todos os testes, executar um teste específico, e até mesmo visualizar o ouput de sua suite. Para isso, aperte `leader` e depois `t`. Lembrando que, por padrão, a `leader` no Lazyvim é a tecla `space`.

## 4. Linter: Interagindo com o Credo no Neovim

Até o presente momento, eu tenho utilizado [null-ls](https://github.com/jose-elias-alvarez/null-ls.nvim) para injetar o credo dentro dos diagnosticos do Neovim. Porém, enquanto escrevia, percebi que o projeto foi arquivado e não faz muito sentido usar a ferramenta agora devido a possíveis futuras falhas de funcionamento. Ainda estou verificando as possibilidades, possivelmente usar o [nvim-lint](https://github.com/mfussenegger/nvim-lint/) ou até mesmo o [ALE](https://github.com/dense-analysis/ale/). Quando tiver algo concreto e usável, atualizo esse post.

___

### Resultado final

Esse é o arquivo final do nosso setup, o nosso `elixir.lua`

```lua
return {
  {
    "williamboman/mason.nvim",
    opts = function(_, opts)
      vim.list_extend(opts.ensure_installed, {
        "elixir-ls",
      })
    end,
  },
  {
    "nvim-treesitter/nvim-treesitter",
    opts = function(_, opts)
      vim.list_extend(opts.ensure_installed, {
        "elixir",
        "heex",
        "eex",
      })
    end,
  },
	{ "jfpedroza/neotest-elixir" },
  {
    "nvim-neotest/neotest",
    opts = { adapters = { "neotest-elixir" } },
  },
}
```

Espero que desfrute bem de seu novo ambiente de desenvolvimento Elixir. E caso tenha alguma sugestão ou dúvida, não hesite em me mandar uma mensagem por meio de minhas redes sociais. Um grande abraço!
