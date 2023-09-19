---
layout: post
title: "Configurando o Visual Studio Code para Desenvolvimento Elixir"
date: 2023-09-18 08:00:00 -0300
categories: elixir
description: "Se você curte programar em Elixir, tem algumas extensões que ajudam bastante! Neste artigo, vamos dar uma olhada nessas extensões que podem turbinar sua experiência de desenvolvimento em Elixir no VSCode."
---
O VSCode caiu no gosto da galera rapidamente quando o assunto é editor de código, principalmente pela sua capacidade de personalização e interface amigável. Se você curte programar em Elixir, tem algumas extensões que ajudam bastante! Neste artigo, vamos dar uma olhada nessas extensões que podem turbinar sua experiência de desenvolvimento em Elixir no VSCode.

---
### ElixirLS: O Poderoso Servidor de Linguagem Elixir

O ElixirLS é uma extensão para VSCode e serve como uma ferramenta vital para o desenvolvimento em Elixir, graças às suas multifuncionalidades.

**Como Instalar:**

1. Abra o VSCode.
2. No painel lateral esquerdo, selecione o ícone de extensões.
3. Busque por "ElixirLS" e instale a extensão correspondente.

**Funcionalidades e Utilização:**

- **Autocompletar:** Receba sugestões conforme você digita, baseadas na análise estática do código.
    - Comece a digitar uma função, módulo ou variável.
    - Um menu suspenso aparecerá com sugestões baseadas no contexto do seu código.
    - Use as setas do teclado para navegar pelas sugestões e a tecla Enter para selecionar a desejada.
- **Debug:** Integração direta com o VSCode para depurar seu código.
    1. No código, clique na margem esquerda da linha onde você deseja adicionar um ponto de interrupção. Um ponto vermelho aparecerá, indicando o ponto de interrupção.
    2. No painel lateral esquerdo, clique no ícone de "inseto" para acessar a visualização de depuração.
    3. Clique no botão verde "Iniciar Depuração" (ou use F5). Seu código será executado até o ponto de interrupção.
    4. Na mesma visualização, você pode inspecionar variáveis, pilhas de chamadas e usar controles para continuar a execução, avançar passo a passo ou entrar/sair de funções.
- **Diagnostics:** Feedback em tempo real sobre erros e alertas.
    - Ao escrever código, você notará sublinhados em algumas partes do texto (geralmente vermelho para erros e amarelo para avisos).
    - Ao passar o mouse sobre esses sublinhados, uma descrição do problema será exibida.
    - No painel lateral esquerdo, o ícone de "exclamação dentro de um triângulo" mostra uma lista de todos os problemas no projeto. Clique nele para visualizar e navegar pelos problemas.
- **Documentação Inline e Definição:** Acesso direto à documentação de módulos e funções.
    1. Posicione o cursor sobre um módulo ou nome de função.
    2. Pressione **`Ctrl`** + **`Espaço`** para ver um pop-up com uma breve descrição ou documentação.
    3. Para ir à definição de um módulo ou função, clique com o botão direito e selecione "Ir para Definição" ou simplesmente pressione **`F12`**.
- **Mix Tasks:** Integração com o Mix para gestão de projetos.
    - Pressione **`Ctrl`** + **`** para abrir o terminal integrado no VSCode.
    - Digite comandos Mix como **`mix test`** ou **`mix compile`**. O ElixirLS detectará e refletirá as alterações no editor conforme você trabalha com tarefas Mix
- **Formatter:** Reformatação do código para seguir padrões de codificação do Elixir.
    1. **Formatação Manual:**
        - Abra o arquivo Elixir que você deseja formatar.
        - Pressione **`Alt`** + **`Shift`** + **`F`**. O código no arquivo atual será imediatamente formatado seguindo as diretrizes padrão do Elixir (ou quaisquer regras personalizadas que você tenha definido).
    2. **Formatação Automática ao Salvar:**
        - Para não ter que se lembrar de formatar manualmente o código cada vez que fizer uma alteração, você pode configurar o VSCode para fazer isso automaticamente sempre que salvar um arquivo.
        - Vá em Configurações (pode ser acessado através de **`Ctrl`** + **`,`**).
        - No campo de pesquisa, digite "format on save" para localizar a opção.
        - Ative a configuração **`editor.formatOnSave`**.
        - Agora, toda vez que você salvar um arquivo Elixir, o formatter será executado automaticamente, mantendo seu código limpo e padronizado.

---
### Phoenix Framework: Realce de Sintaxe para Templates

O Phoenix Framework usa EEx (Embedded Elixir) para seus templates, permitindo aos desenvolvedores embutir código Elixir diretamente no HTML. No entanto, diferentemente do Elixir puro, os templates EEx têm nuances e padrões específicos que podem se beneficiar de um realce de sintaxe personalizado.

**Principais Características:**

- **Syntax Highlighting:** A extensão reconhece padrões EEx e aplica estilos de destaque específicos para eles. Isso torna muito mais fácil distinguir entre código Elixir embutido e HTML padrão, melhorando a legibilidade e reduzindo erros.
- **Suporte para Tags Phoenix:** Além do Elixir embutido, a extensão também destaca as tags específicas do Phoenix, como **`<%= %>`**, facilitando a identificação e edição desses elementos.

**Como Instalar e Usar:**

1. Na seção de extensões do VSCode, busque por "Phoenix Framework" e instale.
2. Após a instalação, sempre que você abrir um arquivo de template (geralmente com a extensão **`.html.eex`** ou **`.leex`** para templates LiveView), a extensão automaticamente aplicará o realce de sintaxe. Seu código Elixir embutido será destacado de forma diferente do HTML, proporcionando uma visualização mais clara do seu template.
3. A extensão pode ser personalizada para se adequar ao seu tema ou preferências de cor. Acesse as configurações do VS Code e ajuste conforme sua necessidade.

---

### Credo: Linter Avançado para Elixir

Para aqueles que buscam elevar ainda mais a qualidade do seu código em Elixir, um linter é uma ferramenta indispensável. Ele age como um verdadeiro guardião da limpeza e da eficiência do código, ajudando os desenvolvedores a seguir as melhores práticas e a evitar erros comuns. Um dos linters mais populares e respeitados para Elixir é o Credo, e, felizmente, há uma extensão dedicada a ele no Visual Studio Code.

O Credo é mais do que apenas um linter. Ele proporciona uma análise profunda do código, destacando problemas de design, refatorações e até questões de legibilidade. Sua capacidade de oferecer feedback em tempo real faz dele uma ferramenta crucial para manter a qualidade e consistência do código em projetos Elixir.

**Características Principais:**

- **Análise Profunda:** O Credo realiza verificações abrangentes em seu código.
- **Feedback Detalhado:** Entenda e corrija problemas identificados com a ajuda das explicações fornecidas pelo Credo.

**Instalação e Uso:**

1. Na seção de extensões do VSCode, busque e instale a extensão "Credo".
2. Adicione o Credo às suas dependências no arquivo `mix.exs` do seu projeto e instale-o executando `mix deps.get`
    
    ```elixir
    defp deps do
      [
        {:credo, "~> 1.7", only: [:dev, :test], runtime: false}
      ]
    end
    ```
    
3. Uma vez ativada, o Credo analisará seu código a cada salvamento, fornecendo feedback imediato.

---

Estas ferramentas não apenas tornam o processo de codificação mais eficiente, mas também promovem a escrita de códigos mais limpos e otimizados. ElixirLS otimiza o desenvolvimento com autocompletar, depuração, diagnósticos e muito mais. A extensão Phoenix Framework melhora a experiência ao trabalhar com templates EEx, enquanto o Credo serve como um vigilante rigoroso da qualidade do código. Em resumo, ao equipar o VSCode com essas extensões, os desenvolvedores de Elixir estarão bem preparados para criar projetos mais robustos e eficientes, e definitivamente ter um ambiente mais profissional e ágil. 

Espero que desfrute bastante do seu novo ambiente Elixir. E caso tenha alguma sugestão ou dúvida, não hesite em me mandar uma mensagem por meio de minhas redes sociais. Um grande abraço!
