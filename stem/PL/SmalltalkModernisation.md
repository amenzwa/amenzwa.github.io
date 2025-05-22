---
title: "𝜆aconic"
tags:
  - mathjax
use_math: true
---

## *a proposal for a new Smalltalk*

[TOC]

Smalltalk is an early OO programming language that derives its expressive power from simplicity. When it came out in 1972, its syntax was compact and its semantics simple. But today, five decades later, with many new language design discoveries in CS and many new software development inventions in IT, Smalltalk looks positively stale to the modern eye. But I contend that this classic language has many virtues that are beneficial to modern software development.

First, Smalltalk is purely OO. Everything in Smalltalk is an object, including numbers. Even classes, themselves, are objects. And everything happens when objects interact with one another by sending messages. This uniformity exudes a recursive beauty. And the Smalltalk syntax is so simple that it could be described on 5×7 postcard. This simplicity enabled generations of children to learn to use Smalltalk in classrooms, since the 1970s. Also, Smalltalk was the first practical language with the built-in GUI framework. It was the progenitor of the famous [MVC pattern](https://en.wikipedia.org/wiki/Model–view–controller). In the 1970s and 1980s, when users had to use text terminals to communicate with computers, the GUI was a novelty with genuine utility. And this graphical environment made learning fun for children. The system comes with a complete set of development tools—editor, refactoring tool, performance analyser, debugger, source repository, etc.—which are all coherently integrated and are implemented with intuitive GUIs. But despite its simplicity, and perhaps because of it, Smalltalk is powerful—quietly powerful. Indeed, Smalltalk is capable enough that the language, the compiler, the libraries, the user interface, the operating system, the whole lot, was implemented in itself. And the entire codebase comes with the installation, so the users are able not only to study how the system implementation but also to modify it as they see fit. Despite banking on OO, Smalltalk was heavily influenced by LISP and, as such, it has a comprehensive set of FP facilities. So, Smalltalk spearheaded the modern OO-FP hybrid language trend. Lastly, its VM, which is also the OS, is persistent. That is, objects that were active in the memory when the system was shut down resume their activities when the system starts up again, without no effort from the programmer nor the user. This capability obviates the need for the external database and the awkward object-relational mapping. These qualities make Smalltalk uniquely suited for implementing *small*, *internal-use*, *business* applications in hard, fast, agile development environment. In other words, Smalltalk could have been a DSL for creating what is arguably the largest class of mission-critical business applications.

Yet, Smalltalk always was outshone by one or more industrial languages: FORTRAN, LISP, and COBOL in the 1970s; C in the 1980s; C++ in the 1990s; Java in the 2000s; JavaScript in the 2010s; and Python in the 2020s. The simplicity of its syntax introduces a few quirks, which irked many C programmers. This is analogous to how the simple, abstract syntax tree (AST) shape of the LISP programme causes consternation amongst the throngs of programmers raised on C's blocky syntax. And a VM-borne software, especially in the hardware of the time, was never able to compete with the speed of C.

My goal here is to propose ways to modernise Smalltalk completely—its semantics, its syntax, its implementation, and its usage—while retaining its essential qualities of simplicity, succinctness, clarity, comprehensibility, comprehensiveness. and uniformity. And I argue that neither the blazing speed nor the immense complexity are essential for the class of small business applications that this new language, 𝜆aconic (hereafter, Laconic), targets.

# USAGE

As stated above, Laconic is a DSL for small, internal-use business applications, such as inventory management, asset management, project management, etc., for small- to medium-sized enterprises. In an environment where there is but a small number of users and all users are in-house business experts, features such as cloud infrastructure, web UI, real-time responsiveness, massive scalability, million-user load, and the like are superfluous. In fact, the deployment platform is the collection of staff laptops and the operating infrastructure is the corporate LAN behind the firewall, both of which are under the control of the in-house system administrators.

# IMPLEMENTATION

Smalltalk VM

BEAM VM

Java VM

JavaScript VM

# SYNTAX

same as Haskell

# SEMANTICS

same as Smalltalk

# CONCLUSION

asdf
