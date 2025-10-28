---
layout: post
title: "Code Review Best Practices: When (and When Not) to Use \"Request Changes\""
date: 2025-10-28 09:00:00 -0300
categories: code-review
description: "Learn code review best practices and why \"Request Changes\" should be used carefully to keep collaboration and trust within your team."
---

A code review is meant to help teams write better code together. But when reviewers misuse the “Request Changes” button, it turns a learning process into a power move, and
code reviews aren’t about control, they’re about collaboration.

When you open a pull request, you’re saying, *"Hey, here’s my idea — what do you think?"* You’re open to feedback (and hopefully expecting it). That’s how teams grow together and keep their codebase healthy.

### **The Real Purpose of Code Reviews**

At their core, code reviews serve two simple principles:

1. **Write code for people, not machines.**
    
    Your teammates should be able to understand your code without decoding your brain.
    
2. **Share knowledge and align understanding.**
    
    Every review is a chance to spread context — not just spot mistakes.
    

If your review doesn’t move the team forward on at least one of these two fronts, it’s probably not doing its job.

### **Not Every Comment Deserves a "Request Changes"**

During a review, you’ll often find things you’d write differently. That’s natural.

We all have preferences — naming styles, indentation, function length, code structure. But your way isn’t always *the* way. And that’s where many reviewers slip into “authority mode.”

When you hit **Request Changes** for something subjective, you stop the flow of collaboration.

You’re not saying *"Here’s an idea to discuss"* — you’re saying *"My way or the highway."*

That button literally blocks the PR from merging until you approve it again. It’s a tool for addressing critical issues, not for expressing opinions.

### **When “Request Changes” Makes Sense**

There are legitimate times to use it:

- The code breaks the build or could harm production.
- There’s a security risk.
- It violates a major architectural rule that needs immediate attention.

In those cases, you’re protecting the system, not your ego.

Use “Request Changes” to safeguard the environment, not to enforce personal taste.

### **For Everything Else: Start a Conversation**

If your feedback is about code design, naming, or readability, explain *why* it matters.

Reference documentation, articles, or past discussions that give your opinion context.

A simple “I’d prefer it this way” doesn’t teach anyone anything.

When feedback feels like an exchange instead of a rejection, it builds trust — and trust leads to better code.

### **Standardize What’s Subjective**

If the same style debates keep coming up, automate them.

Set up linters and formatters in your CI pipeline. That removes bikeshedding from the human layer and frees reviews to focus on what really matters: **logic, architecture, and clarity.**

### **A Small Tip: Try Conventional Comments**

If you want to make your review comments clearer and friendlier, check out [Conventional Comments](https://conventionalcomments.org/).

It helps you structure feedback with prefixes like:

- nit: for small suggestions
- question: for clarifications
- suggestion: for improvements

This format makes your intent explicit and keeps discussions constructive.

### **Final Thought**

Don’t Weaponize the Request Changes buttom in Code Reviews. A good review isn’t about winning an argument, it’s about helping each other write better software.
Avoid “Request Changes” unless the system truly depends on it. Everything else deserves a conversation, not a command.