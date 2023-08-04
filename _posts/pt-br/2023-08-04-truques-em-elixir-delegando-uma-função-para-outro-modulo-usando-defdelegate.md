---
layout: post
title: "Truques em Elixir: Delegando uma função para outro módulo usando defdelegate"
date: 2023-08-04 08:00:00 -0300
categories: elixir
description: "Melhore a elegância do código com a macro defdelegate do Elixir! Delegue chamadas de função sem esforço, obtendo um código organizado e reutilizável. Simplifique módulos complexos e aprimore a manutenção. Aproveite o potencial da metaprogramação do Elixir para desenvolvimento eficaz!"
---

Às vezes, precisamos escrever funções em Elixir que funcionam como uma ponte entre módulos, permitindo-nos usar funcionalidades específicas de outro módulo, veja o seguinte exemplo:

```elixir
def categories, do: Category.categories
```

A única responsabilidade dessa função é chamar a função categories do módulo Category. Geralmente, os programadores fazem isso para "ocultar" o contexto desnecessário no código. Se estamos falando de "Products" (produtos), fica explicitamente claro o que é uma "Category" (categoria), portanto não é necessário mostrar explicitamente que estamos obtendo isso do módulo Category.

Elixir nos fornece uma macro para ocultar esse contexto, onde podemos delegar funções para outro módulo: defdelegate. Essa macro faz parte do módulo Kernel, portanto, não é necessário importá-la. É uma ferramenta poderosa e conveniente em Elixir que nos ajuda a otimizar nosso código e promover a reutilização de código.

Com defdelegate, podemos facilmente encaminhar chamadas de função para outro módulo, transferindo efetivamente a responsabilidade de lidar com a lógica da função para esse módulo. Isso simplifica nossa base de código e facilita a manutenção, pois as alterações nas funções delegadas podem ser feitas em um só lugar, em vez de espalhadas por vários módulos.

A sintaxe para usar defdelegate é simples. Dentro de um módulo, usamos a macro defdelegate, seguida pelo nome da função que desejamos delegar e especificamos o módulo de destino para o qual a chamada da função deve ser encaminhada. O módulo de destino já deve ter a função delegada implementada, garantindo que a delegação seja válida.

Um exemplo de uso do defdelegate seria o seguinte:

```elixir
defmodule Product do
  defdelegate categories, to: Category
end

defmodule Category do
  def categories, do: ["Apparel and Fashion", "Electronics", "Home and Kitchen"]
end
```

Neste exemplo, o módulo Product delega a função categories para o módulo Category. Agora, se chamarmos Product.categories/0, será encaminhado para Category.categories/0:

```elixir
Product.categories
> ["Apparel and Fashion", "Electronics", "Home and Kitchen"]
```

É importante observar que defdelegate apenas encaminha a chamada da função. Ele não gera automaticamente a documentação da função ou especificações de tipo. Para manter uma documentação clara e especificações de tipo, precisamos fazê-lo explicitamente para a função delegada no módulo que está delegando.

### Referências

- [Hexdocs](https://hexdocs.pm/elixir/1.12/Kernel.html#defdelegate/2)
- [Elixir: defdelegate/2 source code - GitHub](https://github.com/elixir-lang/elixir/blob/v1.15.4/lib/elixir/lib/kernel.ex#L5872-L5927)
