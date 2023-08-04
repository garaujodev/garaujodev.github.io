---
layout: post
title: "Elixir tricks: Delegating a function to another module using defdelegate"
date: 2023-08-04 08:00:00 -0300
categories: elixir
description: "Unlock code elegance with Elixir's defdelegate macro! Seamlessly delegate function calls, promoting clean code and reusability. Simplify complex modules and enhance maintainability. Embrace the power of Elixir's metaprogramming for efficient development!"
---

Sometimes, we need to write functions in Elixir that serve as a bridge between modules, allowing us to use specific functionality from another module, see the following example:

```elixir
def categories, do: Category.categories
```

The only responsibility of this function is to call the `categories` function from the `Category` module. Generally, programmers do that to "hide" unnecessary context in the code. If we are talking about `Products`, is explicitly what a `Category` is, so isn't necessary to explicit show that we are taking it from the `Category` module.

Elixir provides us a macro to hide this context, where you can delegate functions to another module: `defdelegate`. It comes from the `Kernel` module, so isn't necessary to import it. It's a powerful and convenient tool in Elixir that helps us streamline our code and promote code reusability.

With `defdelegate`, we can easily forward function calls to another module, effectively passing the responsibility of handling the function's logic to that module. It simplifies our codebase and makes it easier to maintain, as changes to the delegated functions can be made in one place rather than scattered across multiple modules.

The syntax for using `defdelegate` is straightforward. Within a module, we use the `defdelegate` macro followed by the name of the function we want to delegate and specify the target module to which the function call should be forwarded. The target module must already have the delegated function implemented, ensuring that the delegation is valid.
An example of using `defdelegate` would be as follows:

```elixir
defmodule Product do
  defdelegate categories, to: Category
end

defmodule Category do
  def categories, do: ["Apparel and Fashion", "Electronics", "Home and Kitchen"]
end
```

In this example, the `Products` module delegates the function `categories` to the `Category` module. Now, if we call `Products.categories/0`, it will be forwarded to `Category.categories/0`:

```elixir
Product.categories
> ["Apparel and Fashion", "Electronics", "Home and Kitchen"]
```

It's important to note that `defdelegate` only forwards the function call. It does not automatically generate the function's documentation or type specifications. To maintain clear documentation and type specifications, we need to do it explicitly for the delegated function in the delegating module.

### References

- [Hexdocs](https://hexdocs.pm/elixir/1.12/Kernel.html#defdelegate/2)
- [Elixir: defdelegate/2 source code - GitHub](https://github.com/elixir-lang/elixir/blob/v1.15.4/lib/elixir/lib/kernel.ex#L5872-L5927)
