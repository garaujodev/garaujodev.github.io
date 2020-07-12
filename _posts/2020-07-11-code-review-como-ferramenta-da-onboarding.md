---
layout: post
title: Code Review como ferramenta de onboarding
date: 2020-07-11 17:11:14 -0300
categories: [code review]
description: Nesse post, compartilho como foi minha experiência ao entrar na SourceLevel, aprendendo melhor sobre a codebase, com base em histórico de Pull Requests e outras discussões.
---

O processo de onboarding sempre é uma etapa difícil para desenvolvedores e empresas.
Para o desenvolvedor, é um momento de conhecer pessoas novas, outra cultura, práticas e
se adequar a arquitetura utilizada. Para a empresa, é um momento de integrar alguém a equipe,
contextualizá-lo sobre como as coisas funcionam, compartilhar aspectos culturais.
É nesse momento que buscamos nos alinhar com o time.

Entrando como desenvolvedor na SourceLevel, não foi diferente.
Em um primeiro momento, percebi que teria bastante dificuldade, pois a empresa nesse momento
já adotava uma cultura que eu ainda não tinha vivenciado pelos lugares onde passei.
Por ser uma startup com um produto voltado à qualidade de código e aprimoramento contínuo de
equipes, faz mais que sentido ela adotar boas práticas internas, tanto de desenvolvimento quantos
culturais (inclusive esse foi o motivo de eu me candidatar para a vaga).

Eu já havia desenvolvido aplicações em Rails (SourceLevel usa Ruby como linguagem principal),
porém cada aplicação Rails tem suas particularidades. Mesmo recebendo acompanhamento de alguém que
já está familiarizado com o código nesse processo de onboarding, a melhor forma de você se
contextualizar com o que é praticado é lendo o código. Ele é o resultado final.
De nada adiantam várias reuniões internas para ajustar questões culturais e técnicas, se no
final das contas isso não é transcrito para o código. Portanto, ele sempre vai ser sua melhor referência.

Quando preciso mexer em uma base de código que não conheço, vou explorando os
arquivos - abrindo cada um - e lendo, procurando compreender o contexto de cada classe, e como
o código foi escrito. Mas essa é uma prática que pode ser acelerada se você analisar as discussões
que geraram tal código, as melhorias sugeridas, bem como o código era anteriormente, em outras
palavras, como ele evoluiu com o passar dos tempos.

Quando o produto ainda se tratava de uma ferramenta interna da extinta Plataformatec, e ainda
chamado Ebert, os desenvolvedores já utilizavam boas práticas. Eram bastante alinhados em questões
culturais e faziam revisão de código, mesmo com uma equipe pequena. Muitos consideram como algo
desnecessário para equipes pequenas, mas no meu onboarding foi fundamental, pois eu tinha a disposição
todo um histórico de discussões e alterações, o que permitiu me contextualizar melhor com as
metodologias usadas, o porquê de cada mudança, e qual o contexto em que ela se aplicava.

Então fui abrindo todos os Pull Requests antigos, analisando cada mudança, olhando o diff, vendo a
evolução do código, qual a motivação, qual a nomenclatura usada nas branches. Nessas discussões
relacionadas à melhoria de código, consegui aprender bastante sobre a forma como o código atual é
estruturado, quais padrões deveria seguir, as mudanças de arquiteturas, e com base nesse histórico, saber
como deveria escrever o código hoje. Estava tudo ali, devidamente registrado. Cada mudança tinha uma
explicação da motivação, e qual era a solução proposta. Isso foi fundamental para mim, e acelerou bastante
o meu processo de onboarding, que inclusive foi notado por todos.

Foi uma atividade bem proveitosa, pois consegui até mesmo aprender algumas coisas novas, o que me
possibilitou me sentir à vontade no time, sugerir mudanças, discutir soluções e melhorias, sem medo de
errar, sem medo de ser julgado.

Quando comecei a contribuir com código, percebi que sempre tinha por ali pessoas interessadas em me
ensinar e a aprender, as revisões nos meus Pull Requests eram sempre proveitosas.
Tínhamos (ainda temos na verdade) diversas discussões, que sempre acrescentavam bastante à qualidade do
código que eu escrevo.

Quando era minha vez de revisar o Pull Request dos outros desenvolvedores, com mais familiaridade
com o código e com mais tempo de estrada, eu sempre me sentia retraído, achava que eu não tinha
muito a acrescentar, mas isso foi mudando conforme algumas de minhas sugestões estavam sendo
aceitas e apreciadas. Portanto, independente se você é um desenvolvedor sênior, pleno ou junior,
o processo de revisão de código é sempre enriquecedor, para todos. Como diz a velha frase do matemático
e filósofo Blaise Pascal:

> “Ninguém é tão sábio que não tenha algo pra aprender e nem tão tolo que não tenha algo pra ensinar”

Hoje, consigo navegar no código e contribuir com clareza, me sinto à vontade para solicitar e ceder revisões, e sei o quão produtiva é a revisão de código em um processo de onboarding. Certamente incluiria essa prática nos próximos onboardings que eu participar e recomendo que todos façam o mesmo.

