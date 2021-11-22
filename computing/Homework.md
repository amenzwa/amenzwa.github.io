---
title: "Doing STEM Homework using JupyterLab"
tags:
  - mathjax
use_math: true
---

# INTRODUCTION

High school and college students today are required to use the computer for studying, research, writing, laboratory work, the lot. Many students use Microsoft Office, Google Docs, or other similar business applications for the work. These applications are just what the liberal arts and business school students need. But they are less than ideal for STEM students.

Traditionally, STEMers used [$\TeX$ typesetting system](https://en.wikipedia.org/wiki/TeX) written by [Donald Knuth](https://en.wikipedia.org/wiki/Donald_Knuth), the world famous American computer scientist. Most computer science, engineering, and mathematics textbooks are prepared using $\TeX$. In fact, this article was prepared using [Markdown](https://www.markdownguide.org/) and [MathJax](https://www.mathjax.org/), distant descendants of $\TeX$. But $\TeX$ was designed not for word processing but for typesetting, specifically for typesetting mathematics: every sentence and equation must, therefore, be laboriously annotated with formatting command codes. Once printed, the document looks like it was typeset by a textbook publisher. But in the source form, it resembles the HTML source of a web page. Hence, most writers consider the $\TeX$ source document unreadable, and many end up adopting run-of-the-mill word processors. The biggest problem with word processors is that although their text formatting capabilities are acceptable for business use, their mathematical typesetting capabilities are woefully inadequate for STEM use.

Fortunately, we now have [Jupyter](https://jupyter.org/), an interactive programming and document preparation system. Jupyter is a user interface for [literate programming](https://en.wikipedia.org/wiki/Literate_programming), a programming paradigm invented by Knuth in which a programme is a document that contains both the implementation code and the textual description thereof. The document reads like an article that explains the purpose and behaviour of the embedded code. The typesetting system is capable of rendering textbook-quality equations. And this document can be run like an interactive programme that consumes live input data and generates output which is also embedded in the document. When a new set of input data is given, the output immediately reflects the changes. In other words, a Jupyter document, called a notebook, is the ideal medium for preparing technical articles and reports.

The idea of a "live" notebook dates back to Knuth's original implementation in the 1980s. For nearly four decades, the most comprehensive implementation, and indeed the only practical one, was [Mathematica](https://www.wolfram.com/mathematica/). Mathematica is a high-priced commercial software. Very few could afford it, and of those who could afford it, still fewer numbers learned to use it well. With the release of Jupyter in 2015, the notebook concept has been democratised, because it is an open-source software and because it is designed to serve as the frontend to any programming language. The most popular backend is for Python, given its prominence as the language for data science.

Python is unique among programming languages:

- Python is a simple language that beginners can learn quickly. That is, novices with only a few days of experience in the language can use it to accomplish substantive work.
- Python's small set of core features can accomplish almost all ordinary programming tasks, so most Python programmes employ only simple programming concepts. As such, Python programmes are comprehensible to novices.
- Python can be used comfortably to write short programmes that are only a few lines long or large programmes with thousands of modules.
- Python is a full-fledged object-oriented (OO) programming language that supports procedural programming (PP) and functional programming (FP) styles. Seasoned programmers can exploit advanced features of the language to make their large programmes efficient, maintainable, and extensible.
- Python has an extensive list of high quality open-source libraries for every imaginable application domain: system programming, web programming, image processing, numerical analysis, symbolic processing, artificial intelligence—the list is long.
- Python can be stripped down to the essentials and be ported to microcontrollers, like the [BBC micro:bit](https://microbit.org/code/#python).
- Python is an interpreted language that runs with adequate speed: Python programmes are neither the slowest nor the fastest in this category. Where speed is essential, small components can be selectively implemented in C and be accessed from Python programmes.

In short, although Python is not the best in any one aspect, it is above average in the important aspects that programmers care about. For these reasons, I shall use the Python backend for Jupyter.
