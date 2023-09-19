---
layout: post
title: "Configurando o Alchemist no Emacs para Desenvolvimento Elixir"
date: 2023-09-18 08:00:00 -0300
categories: elixir
description: "Se você é um profissional ou entusiasta do Elixir e utiliza o Emacs como sua principal ferramenta de edição, a ferramenta Alchemist é essencial para otimizar sua experiência de desenvolvimento. Este guia detalha o processo de instalação e uso do Alchemist no ambiente Emacs."
---

Se você é um profissional ou entusiasta do Elixir e utiliza o Emacs como sua principal ferramenta de edição, a ferramenta Alchemist é essencial para otimizar sua experiência de desenvolvimento. Este guia detalha o processo de instalação e uso do Alchemist no ambiente Emacs.

--- 
### **Pré-requisitos:**

Assegure-se de atender aos seguintes requisitos antes de prosseguir:

1. O Emacs deve estar instalado em seu dispositivo.
2. As ferramentas Elixir e Mix devem estar presentes e operacionais.

### **Instruções de Instalação:**

### **Configuração do Package Manager do Emacs (MELPA):**

Caso ainda não tenha o MELPA configurado, siga os passos abaixo:

1. Insira o código a seguir no seu arquivo `.emacs` ou `init.el`:

    ```elixir
    (require 'package)
    (add-to-list 'package-archives
                '("melpa" . "<https://melpa.org/packages/>") t)
    (package-initialize)

    ```

2. Salve as alterações e reinicie o Emacs.
3. Para instalar o Alchemist:
   - Utilize o comando `M-x` (Meta + x; Meta geralmente corresponde à tecla `Alt` ou `Esc`).
   - Execute `package-refresh-contents` para atualizar a lista de pacotes.
   - Novamente, utilize o comando `M-x`.
   - Execute `package-install`, seguido de `alchemist`.
4. Para garantir que o Alchemist seja ativado sempre ao abrir um arquivo `.ex` ou `.exs`, insira no seu arquivo `.emacs` ou `init.el`:

    ```elixir
    (add-hook 'elixir-mode-hook 'alchemist-mode)

    ```

### **Spacemacs:**

Para usuários do Spacemacs:

1. Abra o arquivo `.spacemacs`, comumente localizado no diretório home.
2. Localize e adicione `elixir` à função `dotspacemacs-configuration-layers`.
3. Salve as alterações e reinicie o Spacemacs. Uma combinação útil é `SPC q r`.
4. Após o reinício, o Spacemacs instalará o layer Elixir, incluindo o Alchemist e outras funcionalidades relacionadas.

### **Doom Emacs:**

Para usuários do Doom Emacs:

1. Abra o arquivo localizado em `~/.doom.d/init.el`.
2. Encontre o módulo `elixir` e descomente a linha associada.
3. Salve o arquivo.
4. Execute o comando `doom sync` no terminal.
5. Finalmente, reinicie o Doom Emacs.

---

### **Funcionalidades Principais:**

Com o Alchemist instalado, você agora tem acesso a diversas funcionalidades poderosas, incluindo:

1. **Autocompletar:** O Alchemist fornece autocompletar para módulos, funções, variáveis e muito mais.
   - Ao digitar seu código, pressione **`M-TAB`** para ativar a sugestão de autocompletar.
2. **Documentação Inline:** Você pode acessar rapidamente a documentação de qualquer módulo ou função diretamente no Emacs.
   - Coloque o cursor sobre um módulo ou nome de função e pressione **`M-?`**. Uma janela pop-up mostrará a documentação relevante.
3. **Navegação:** O Alchemist permite que você navegue rapidamente para a definição de qualquer módulo ou função.
   - Posicione o cursor sobre um módulo ou nome de função e pressione **`M-,`**. Isso o levará diretamente à definição do módulo ou função.
4. **Execução de Testes:** O ambiente Emacs agora pode executar testes Elixir.
   - Para executar todos os testes do projeto, pressione **`M-x`** e digite **`alchemist-mix-test`**.
   - Para executar um teste específico, navegue até o teste desejado, pressione **`M-x`** e digite **`alchemist-mix-test-at-point`**.
5. **Integração REPL:** Uma integração perfeita com o REPL `iex` do Elixir permite testes de código em tempo real e muito mais.
   - Para iniciar uma sessão **`iex`** através do Alchemist, simplesmente pressione **`M-x`** e digite **`alchemist-iex-run`** e pressione Enter. Isso iniciará uma nova janela Emacs com uma sessão **`iex`** ativa.
   - Se você deseja iniciar o **`iex`** junto com sua aplicação Phoenix (se estiver trabalhando com o framework Phoenix), pode usar o comando **`alchemist-phoenix-server-run`**. Isso iniciará tanto o servidor Phoenix quanto a sessão **`iex`** associada.
   - Quando desejar encerrar a sessão **`iex`**, simplesmente digite **`exit()`** no REPL ou feche a janela do Emacs associada à sessão **`iex`**.

Espero que tire bastante proveito do seu novo caldeirão e crie bons Elixires! E caso tenha alguma sugestão ou dúvida, não hesite em me mandar uma mensagem por meio de minhas redes sociais. Um grande abraço!
