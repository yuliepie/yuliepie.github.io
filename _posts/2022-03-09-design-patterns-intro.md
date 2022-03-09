---
layout: post
title: Introduction to Design Patterns
tag: Programming
image: https://s3.us-west-2.amazonaws.com/secure.notion-static.com/0ff6515d-acc7-4ed4-9fe0-88843500ccdb/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220309%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220309T084656Z&X-Amz-Expires=86400&X-Amz-Signature=8a368e5ec286fb44b39af1b92352e642efe02b857f77aebabe678ffb4d50eb7f&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject
---
![]({{ page.image | relative_url }})
# What is a Design Pattern?

Design patterns represent **solutions to common problems in software design**. They are like blueprints that work as high level design methodologies for your software. A pattern is not a specific piece of code like a library or an algorithm, but a general concept that you can follow. While an algorithm is like a *cooking recipe* that has exact and clear steps, a design pattern is like a *blueprint* where you can see the overall picture and the outcome, but no specific steps to follow.

A pattern description mostly consists of the **problem** the pattern tries to solve, the **solution**, the **structure of classes** used for the solution and their relationships, and some **code examples**.

Most patterns emerged to solve problems in object-oriented design, but other patterns have emerged continuously.

## Why is a pattern useful?

You can code without knowing a single design pattern, or you might be implementing some patterns without knowing it. However, knowing popular design patterns is useful because:

1. Design patterns are **tried and tested** solutions to common problems in software design. You can have solutions to all sorts of problems under your belt, using principles of object-oriented design.


2. Design patterns can be used as **common language** that you and your teammates can communicate around. When discussing problems, suggesting a design pattern as a solution will immediately make sense to everyone that knows about the pattern beforehand.


3. Optimal design pattern application **prevents the need for refactoring** code, as the application of the design pattern often is an already optimal solution. 


4. Design patterns are built around object-oriented principles and strengthen their advantages, leading to **cleaner code**, less bugs through proper encapsulation etc, more intuitive interface to the client caller.

## Criticism of patterns

- **A workaround for a weak programming language** - Sometimes, the need for patterns comes from using a programming language that lacks necessary featrues or levels of abstractions. For example, the Strategy pattern can be implemented with a simple anonymous (lambda) function in most modern programming languages. This means that sometimes it can be more inefficient to implement a pattern than to choose a language that already implements the pattern.

- **Inefficient solutions** - A pattern can lead to inefficient solutions, especially when they are implemented ‘exactly as the pattern is defined’, without adapting them to the specifc project context. Too much unnecessary overhead can thus occur.
  
- **Unjustified use** - Many novice programmers who have just learned about patterns may try to apply them everywhere, even in situations where simpler code would be better.

# Pattern Types

## By Complexity

Design patterns are very different in their complexity, level of detail, applicability to the entire system. An analogy for different design patterns is where in road construction, you can improve the safety of an intersection by, 1) installing some traffic lights, or 2) building an entire multi-level intersection with underground pedestrian passages.

The most basic and low-level patterns are called **‘idioms’**, and are usually specific to a single programming language. Universal and high-level patterns are called **architectural patterns**, which can be implemented in any language. They are used to design the overall architecture of an entire application.

## By Purpose

Design patterns can be categorized by their purpose, or role in the software. 3 main groups are:

1. **Creational patterns**: provide object creation mechanisms that increase code reusage and flexibility.

2. **Structural patterns**: Provde a way to assemble objects and classes into larger structures in a flexible, efficient manner

3. **Behavioural patterns**: Provide methods of effective communication and assignment of responsibilities between objects.

<figure>
  <img src="https://dotnettekki.com/wp-content/uploads/design-patterns.jpg" alt="drawing" width="auto"/>
  <figcaption style="color:gray;font-style:italic">Patterns as defined by the GoF</figcaption>
</figure>



---


*Reference*:

- [https://refactoring.guru/design-patterns](https://refactoring.guru/design-patterns)
- [https://dotnettekki.com/csharp-design-patterns/](https://dotnettekki.com/csharp-design-patterns/)