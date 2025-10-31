---
layout: post
title: "Boas práticas de Code Review: quando (e quando não) usar \"Request Changes\""
date: 2025-10-28 09:00:00 -0300
categories: code-review
description: "Aprenda boas práticas de Code Review e por que usar \"Request Changes\" com cuidado para manter a colaboração e a confiança no time."
---

O processo de code review existe para ajudar o time a escrever um código melhor, juntos. Mas quando alguém usa o botão **“Request Changes”** da forma errada, o que deveria ser um processo de aprendizado vira um jogo de poder. E code reviews não são sobre controle, são sobre colaboração.

Quando você abre um pull request, está dizendo *"Ei, aqui está minha ideia — o que você acha?"*. Você está aberto a feedback (e, com sorte, realmente esperando por ele). É assim que times crescem juntos e mantêm uma base de código saudável.

### **O Verdadeiro Propósito dos Code Reviews**

No fundo, o processo de code review tem dois princípios simples:

1. **Escreva código para pessoas, não para máquinas.**
    
    Seus colegas devem conseguir entender seu código sem precisar decifrar sua cabeça.
    
2. **Compartilhe conhecimento e alinhe o entendimento do time.**
    
    Cada review é uma chance de espalhar contexto — não apenas encontrar erros.
    

Se sua review não ajuda o time a evoluir em pelo menos um desses dois pontos, talvez ela não esteja cumprindo seu papel.

### **Nem Todo Comentário Merece um "Request Changes"**

Durante uma review, é comum encontrar trechos que você escreveria de outro jeito. E é natural.

Cada pessoa tem preferências: nomeação, indentação, tamanho de função, estrutura de código. Mas o seu jeito não é *o* jeito. E é aí que muitos revisores escorregam para o modo “autoritário”.

Quando você usa **Request Changes** por algo subjetivo, você interrompe o fluxo de colaboração. Você não está dizendo *"Aqui vai uma ideia para discutirmos"*, está dizendo *"É do meu jeito ou não é."* 

Esse botão literalmente bloqueia o merge do PR até que **você** aprove novamente. É uma ferramenta para tratar **problemas críticos**, não para impor opinião.

### **Quando o "Request Changes" Faz Sentido**

Existem situações legítimas para usá-lo:

- O código quebra o build ou pode causar problemas em produção.
- Há um risco de segurança.
- Viola uma regra arquitetural importante que precisa de atenção imediata.

Nesses casos, você está protegendo o sistema, não o seu ego.

Use o **Request Changes** para garantir segurança e estabilidade, não para reforçar gosto pessoal.

### **Para Todo o Resto: Comece uma Conversa**

Se o feedback é sobre design, nomeação ou legibilidade, explique *por que* isso importa. Deixe referências de documentação, artigos ou discussões anteriores que sustentem sua opinião. Um simples *“eu prefiro assim”* não ensina nada.

Quando o feedback soa como uma troca, e não como uma rejeição, ele constrói confiança, e confiança leva a um código melhor.

### **Padronize o que é Subjetivo**

Se os mesmos debates de estilo continuam aparecendo, automatize.

Configure linters e formatadores no seu pipeline de CI. Isso tira o “bikeshedding” da camada humana e deixa as reviews focarem no que realmente importa: **lógica, arquitetura e clareza.**

### **Dica: Use o Conventional Comments**

Se quiser deixar seus comentários mais claros e amigáveis, dê uma olhada no [Conventional Comments](https://conventionalcomments.org/).

Ele ajuda a estruturar feedbacks com prefixos como:

- nitpick: para pequenas sugestões
- question: para dúvidas
- suggestion: para melhorias

Esse formato deixa a intenção do comentário explícita e mantém a conversa construtiva.

### **Pensamento Final**

Não transforme o botão **Request Changes** em uma arma durante as code reviews. Uma boa review não é sobre vencer uma discussão, é sobre ajudar uns aos outros a escrever software melhor.
Evite usar “Request Changes” a menos que o sistema realmente dependa disso. Todo o resto merece uma conversa, não um comando.