---
layout: post
title: "Ruby + VSCode: Unlocking Advanced Features with an LSP"
date: 2024-02-18 09:00:00 -0300
categories: ruby
description: "This guide introduces the integration of Solargraph and Shopify's Ruby LSP with Visual Studio Code, providing a streamlined setup for advanced code completion, auto-formatting, real-time feedback, and efficient navigation. Perfect for Rubyists seeking to enhance productivity and code quality."
---

In the realm of software development, efficiency, and productivity are not just goals but necessities. For Ruby developers, this means leveraging the best tools and practices to streamline coding processes. One pivotal advancement in this area is the adoption of the Language Server Protocol (LSP), which revolutionizes how developers write, navigate, and understand code. LSPs provide a bridge between your code editor and the programming language, offering features like auto-completion, code navigation, linting, and real-time feedback. These features not only enhance coding efficiency but also significantly improve code quality and developer satisfaction.

Visual Studio Code (VSCode), with its versatile ecosystem and support for a wide array of programming languages, has become a preferred Integrated Development Environment (IDE) for many Ruby developers. Its extensibility through extensions allows for a highly customizable development environment. Among these extensions, Language Server Protocol (LSP) implementations for Ruby, such as Solargraph and Shopify's Ruby LSP, stand out by offering tailored support that meets the unique needs of Ruby development.

Solargraph provides a comprehensive suite of features for Ruby development, including documentation lookup, code completion, and in-depth analysis of code quality. On the other hand, Shopify's Ruby LSP, crafted with the challenges of large codebases in mind, offers an optimized experience designed to enhance performance and scalability.

In this guide, we'll dive into how to set up and configure both Solargraph and Shopify's Ruby LSP in VSCode. Whether you're building a complex Ruby on Rails application or working on a Ruby gem, integrating these LSPs into your development workflow can lead to more productive coding sessions and a deeper understanding of your codebase.

You can make your own choice about which you will use, you won't need both (and not recommended). But firstly, let me mention that Solargraph works well with **Ruby 2.5** or higher, while Shopify's LSP needs **Ruby 3** or newer to work properly. You can do some workarounds to make Shopify's LSP work with an older version of Ruby, as described [here](https://github.com/Shopify/vscode-ruby-lsp?tab=readme-ov-file#ruby-version-requirement). You can read more about the motivation to require **Ruby 3** [in this issue](https://github.com/Shopify/vscode-ruby-lsp/issues/948#issuecomment-1867024912).

## Getting Started with Solargraph

Solargraph was created by Fred Snyder, over Castwide company, with its first release making its way to the Ruby community in 2017. Developed out of a need for a robust, Ruby-specific language server protocol (LSP) solution, Solargraph aimed to fill the gap by offering a rich suite of features tailored for Ruby developers. 
With its rich feature set, including code completion, diagnostics, and inline documentation, Solargraph has quickly become a must-have for Ruby developers. Here's how to get started:

### Step 1: Install the Solargraph Gem
To begin, install the Solargraph gem through your terminal:

```bash
gem install solargraph
```
This command ensures the Solargraph server is available on your machine, setting the stage for its integration with VSCode.

### Step 2: Integrate Solargraph with VSCode

After installation, proceed to VSCode and install the "Solargraph" extension from the marketplace. This extension facilitates the connection between VSCode and the Solargraph gem installed on your system. A quick restart of VSCode activates the extension, unlocking the full potential of Solargraph in your development environment.

### Step 3: Configure Solargraph (Optional)

For the most part, Solargraph works out of the box. However, tweaking a few settings can tailor the experience to your needs. To adjust Solargraph's settings:

1. Open the Command Palette (with `Ctrl+Shift+P` For Windows/Linux and `Cmd+Shift+P` for MacOS).
2. Type `Preferences: Open Settings (JSON)` and press enter.
3. Add or modify Solargraph settings in your `settings.json`. For example:
```json
"solargraph.autoformat": true,
"solargraph.diagnostics": true,
"solargraph.formatting": true,
```

These settings enable automatic formatting, diagnostics for code issues, and document formatting. You can disable one or more of them, by just setting the value to `false`. You can check more configurable options on the [official extension's repository](https://github.com/castwide/vscode-solargraph?tab=readme-ov-file#extension-settings), so feel free to explore other settings based on your preferences.

### Troubleshooting
If you encounter any issues, such as the LSP not starting, ensure Solargraph is correctly installed by running in your terminal:
```bash
solargraph -v
```
If the problem persists, consult the Solargraph documentation or the VSCode extension page for further troubleshooting tips.

## Getting Started with Shopify Ruby LSP

Born out of Shopify's extensive experience with Ruby, Shopify's Ruby LSP is tailored for performance and efficiency, particularly beneficial for large Ruby and Rails projects. It's described as **An opinionated language server for Ruby**.

### Integrate Shopify Ruby LSP with VSCode
Shopify's Ruby LSP is designed for performance, offering a streamlined setup process in VSCode that avoids manual gem installations:

1. **Add the Shopify Ruby LSP Extension to VSCode**: Instead of installing a gem, simply add Shopify's Ruby LSP extension from the VSCode marketplace. This approach ensures you have the latest features and updates without manual gem management.
2. **Note on Manual Installation**: It's important to highlight that for VSCode users looking to leverage Shopify's Ruby LSP, manual installation of the gem is not recommended. The VSCode extension handles all necessary configurations, ensuring seamless integration and optimal performance.

### Configure Shopify Ruby LSP (Optional)
After integrating Shopify's Ruby LSP, there might be additional optional configurations you can explore to tailor the LSP to your project's needs. These configurations can enhance your development workflow further, but the default setup provided by the extension will suffice for most users.

If you want to customize a specific feature, you just need to open the language status center right next to the language mode Ruby and select `Manage` right next to enabled features.

{% include image.html src="https://github.com/Shopify/vscode-ruby-lsp/blob/main/extras/ruby_lsp_status_center.png?raw=true" alt="Shopify's Ruby LSP Configuration Menu" caption="Shopify's Ruby LSP Configuration Menu" %}

For more information, check out the official [README](https://github.com/Shopify/vscode-ruby-lsp?tab=readme-ov-file#ruby-lsp-vs-code-extension) of the extension.

### Troubleshooting
Encountering issues while setting up or using Shopify's Ruby LSP in VSCode? Here are a few tips to help you troubleshoot common problems:

* **Extension Not Working**: Ensure you have restarted VSCode after installing the Shopify Ruby LSP extension. Sometimes, a simple restart can resolve integration issues.

* **Conflicts with Other Extensions**: If you have multiple Ruby-related extensions installed, try disabling others temporarily to check for conflicts affecting Shopify's Ruby LSP functionality.

* **Check for Updates**: Both VSCode and the Shopify Ruby LSP extension are regularly updated. Ensure you're using the latest versions of both to benefit from recent fixes and features.

## Conclusion

Integrating with an LSP is a game-changer for developers, offering a suite of powerful tools that significantly enhance coding efficiency and enjoyment. These integrations not only improve code quality but also save you time through features like auto-formatting, advanced code completion, and real-time feedback. 

By adopting these tools, you're investing in a smarter coding process and joining a forward-thinking community dedicated to advancing Ruby development. Happy coding!
