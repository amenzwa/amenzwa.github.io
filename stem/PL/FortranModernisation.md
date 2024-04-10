---
title: "A Forlorn Hope of Fortran Modernisation"
tags:
  - mathjax
use_math: true
---

[TOC]

## *a proposal for a dependently typed Fortran*

For decades, people in IT had taken delight in drafting Fortran's obituary. Yet, this old language lives on. But in recent years, the Fortran user community has begun sounding alarms: Fortran shops are having difficulty finding young programmers to replace those who are leaving the workforce, because the young are not willing to devote their careers to this ancient language. At present, no language can rival, let alone surpass, Fortran when it comes to implementing long-lived, large-scale, massively-parallel scientific and engineering applications; not even C and C++. Yet, modern programmers know nothing about Fortran, nor have they any interest in it. Suffice it to say, Fortran has an image problem.

In this article, I explore the causes of Fortran's diminished popularity and discuss potential remedies. The key points I make here are these:

- Fortran is indispensable for scientific parallel computing
- The industry is facing a shortage of Fortran programmers
- The industry has no actionable plans to replenish the ranks

My intended audience include the following groups:

- Computer scientists maintaining the Fortran language standard
- Scientists and engineers who implement scientific software using Fortran
- STEMers interested in parallel processing and scientific programming

Given the breadth and depth of topics involved, the reader is expected to be an experienced parallel programmer in both procedural and functional languages and possess a working knowledge of simple type theory, parametric type theory, and dependent type theory.

It would seem that trying to shore up this mid-century language for the grind of the 21st Century verges on insanity. Not so. I contend that Fortran modernisation is worthwhile and necessary. I admit, though, that refreshing Fortran for the 2020s is but a [forlorn hope](https://en.wikipedia.org/wiki/Forlorn_hope#:~:text=A%20forlorn%20hope%20is%20a,to%20save%20a%20retreating%20army%2C), at present.

Before we delve into the subject, here is some background on my connection to Fortran. Like other electrical engineering undergraduates in the 1980s, I learned FORTRAN in college. I used FORTRAN 1977 on the DEC VAX-11/780. FORTRAN was then the primary language for performing [electronic circuit simulation](https://en.wikipedia.org/wiki/Electronic_circuit_simulation), [digital signal processing](https://en.wikipedia.org/wiki/Digital_signal_processing) (DSP), [finite element method](https://en.wikipedia.org/wiki/Finite_element_method) (FEM), [computational fluid dynamics](https://en.wikipedia.org/wiki/Computational_fluid_dynamics) (CFD), and other engineering computations, so we were required to learn the language.

But in those days, most of us STEMers tried to learn every programming language we could get our hands on. There were only a few languages in popular use in science and engineering: LISP, FORTRAN, C, Pascal, ML, and Prolog; good compilers for these languages were available only on minicomputers; and the only place where we could gain access to these large, expensive machines was at the university computer centre. Scarcity drives demand, I suppose. I did most of my work in my preferred languages: LISP, C, and ML. So, my FORTRAN experience was limited to class assignments.

Later, in computer science graduate school, my research work led me back to Fortran 90 on a CRAY [Y-MP](https://en.wikipedia.org/wiki/Cray_Y-MP) with an attached [T3D](https://en.wikipedia.org/wiki/Cray_T3D). My professional association with Fortran ended, when I left academia for industry in the mid 1990s. Even in those days, no one in IT was using Fortran. But out of personal interest, I kept up with Fortran's evolution, through the years. So, my views presented here are born of dated hands-on experience with older Fortran, present awareness of modern Fortran's predicament, and decades-long hands-on experience with several modern programming languages. And I admit that although I am no fan of Fortran at a practical level, I truly admire Fortran at an intellectual level, for its originality, longevity, and history.

Now, let us crack on.

## *yesterday*

The concept of modern computer was conceived in the minds of mathematicians the late 1930s. Then, in the mid 1940s, the implementation of modern computer was realised in the hands of electrical engineers. Initially, programming was done by wiring up the circuits. This was followed by entering binary words into registers using hardware switches. Later, symbolic assembly languages were invented. And in 1957, [Backus](https://en.wikipedia.org/wiki/John_Backus), a computer scientist extraordinaire, and his colleagues at IBM created the world's first high-level programming language, [FORTRAN](https://en.wikipedia.org/wiki/Fortran). Its purpose was to enable scientists to implement scientific applications using their native tongue, the mathematical notation, instead of in a foreign tongue, the assembly language.

Over the past 70 years, Fortran continued to evolve, incorporating the advances through the decades. There have been numerous standardised versions of Fortran: 1966, 1977, 1990, 1995, 2003, 2008, 2018, and 2023. The latest standard version as of this writing in early 2024, the Fortran 2023 (draft), is a thoroughly modern language with strong static type system, user-defined types, tail-call eliminating recursions, objects, modules, garbage collection, and built-in [partitioned global address space](https://en.wikipedia.org/wiki/Partitioned_global_address_space) (PGAS) parallel programming to boot. To date, Fortran is the only standardised language with built-in parallel processing facilities. Despite its age, despite the decades of additions, Fortran remains essentially a simple language that non-programmers could quickly learn to use. In that sense, Fortran is easy to use, like Python. But unlike Python, Fortran is fast—faster than even the mighty C—when it comes to scientific parallel computing.

Today, modern Fortran is still the primary language of choice in large-scale, massively-parallel applications which are the bread-and-butter of scientific and engineering computations. A few elite engineering colleges round the world still teach Fortran to their engineering undergraduate students, even if their computer science students may have never heard of the language. There simply is no modern language that can compete with Fortran, when it comes to performing scientific computations on [supercomputers](https://en.wikipedia.org/wiki/Supercomputer). The same is true of modern Cobol. Although no undergraduate students would ever learn it in college, many large financial institutions still rely heavily on Cobol for handling massive amounts of transactions. No modern language can compete with Cobol, when it comes to high-throughput processing of financial transaction in real-time on [mainframes](https://en.wikipedia.org/wiki/Mainframe_computer).

The first generation high-level programming languages emerged in the late 1950s and early 1960s: FORTRAN (1957) the first high-level language specifically designed for scientific computing; LISP (1958) the first functional programming (FP) language designed to automate theorem proving; ALGOL (1958) the first procedural programming (PP) language; COBOL (1959) the first purpose-built business computing language; Simula (1962) the first object-oriented (OO) programming language. These [OG](https://en.wikipedia.org/wiki/O.G._Original_Gangster) (original gangsta) languages live on in one form or another. Modern FORTRAN is [Fortran 2023](https://wg5-fortran.org/f2023.html). Modern LISP is [Common Lisp 2005](https://www.lispworks.com/documentation/HyperSpec/Front/index.htm). Modern ALGOL is essentially all modern PP languages, the exponent among them is [C 2023](https://www.open-std.org/jtc1/sc22/wg14/). Modern COBOL is [Cobol 2023](https://www.iso.org/obp/ui/#iso:std:iso-iec:1989:ed-3:v1:en). Modern Simula is all modern OO languages, the best known one being [C++ 2023](https://isocpp.org/std/the-standard).

LISP was immensely popular during the heyday of rule-based artificial intelligence (AI) in the 1970s and 1980s. Today, its primary use is as the scripting language for the inimitable [Emacs](https://en.wikipedia.org/wiki/Emacs) editor. And being the first FP language, all modern FP languages, like OCaml and Haskell, are its spiritual descendants. ALGOL never escaped academia, but its influence is seen in the design of all PP languages that followed, including Pascal, C, and other modern systems programming languages like Rust, Odin, and Zig. C is still being used heavily in systems programming—compilers, libraries, operating systems, etc. Its most famous use is in the implementation of the Linux kernel. Simula, too, was primarily an academic research language. But it heavily influenced Smalltalk and C++. Smalltalk, in turn, was influential to Objective-C and Java. C++ combined C's efficiency and Simula's objects, thereby injecting many useful OO concepts into the traditionally PP domain of systems programming. Today, C++ is used in almost every application domain where speed is essential. Hence, LISP, ALGOL, and Simula live on, albeit in very different guises.

FORTRAN and COBOL, however, have remained essentially unchanged for almost seven decades. Their standard committees opted to maintain full backward compatibility. For example, Fortran 2023 compiler can still compile the FORTRAN 1977 code, without modification. Note that the original stylised name "FORTRAN" changed to the modern style "Fortran" with the publication of the Fortran 1990 standard. By the way, FORTRAN stands for "formula translator", which hints at its mathematical heritage.

The advantage of backward compatibility is dependability, both in terms of longevity and of reliability. Most bugs had been eradicated over time, and the institutions can depend on the continued existence of these long-lasting languages. The disadvantage of backward compatibility, of course, is that newer concepts that had emerged decades after the birth of these old languages had to be shoehorned into their designs, yielding a rather ectopic feel, syntactically and semantically. As such, linguistic extensions for these languages, like modules and objects, though modern, feel dated and awkward, nonetheless. Consequently, FORTRAN and COBOL look and feel stale.

From this point forward, the discussions will focus on Fortran. But the arguments and the conclusions proffered apply equally to Cobol, by analogy.

## *today*

There is no denying that modern Fortran suffers from the image problem. Young programmers entering IT rightly perceive this pioneering language as old. That perception reflects the reality. But these youngsters wrongly assume that this old language had remained in its infantile form, that there is no future for them in Fortran, and that they must learn the newest language currently popular in the industry. That assumption is not merely incorrect, it is the opposite of the reality.

IT became a speciality in the 1950s, with the advent of modern digital computers. But modern IT, as we now know it, did not come about until the 1970s, when [minicomputers](https://en.wikipedia.org/wiki/Minicomputer) from DEC, Data General, IBM, and other manufacturers became affordable, due to the widespread use of integrated circuits (ICs). This rapid expansion of IT coincided with the rise of PP languages. C was introduced in the early 1970s. And by the early 1980s, it had established itself as the dominant language in the industry, and its reign continued well into the late 1980s. C++ eventually wrested away the crown in the early 1990s. Java emerged almost overnight less than a decade later, and took the top spot by the early 2000s. The 2010s saw the meteoric rise of JavaScript, fuelled by Web 2.0. Today, in the 2020s, Python is king, due to its popularity in machine learning (ML) and data science. It appears that the reign of a popular industrial language is about as long as that of a Roman emperor.

This is in stark contrast to Fortran's trajectory. Since the rise of C more than 50 years ago, the popularity of Fortran had been in steady decline. This decline accelerated in the mid 1980s, when the [free software](https://en.wikipedia.org/wiki/Free_software) movement became mainstream and quality compilers for many new languages became freely available. Also, the rise of [home computers](https://en.wikipedia.org/wiki/Home_computer) around this time hatched throngs of new programmers who were seeking new languages to learn. And even at its peak of popularity, Fortran occupied a narrow, but deep, specialised domain of scientific computing. Those specialised applications were inseparable from supercomputers, which were inaccessible to most universities and corporations. The combination of these factors conspired to deplete Fortran's popularity. Yet, it remains firmly established in scientific computing.

And therein lies the rub: those organisations that depend on Fortran can no longer find young programmers who are willing to devote their careers to this old language that offends their delicate Pythonic sensibilities. Also, most programmers today have never seen a supercomputer; colleges no longer operate traditional computer centres because every student owns a laptop, a tablet, and a mobile. These factors militate against the students' exploration into the Fortran ecosystem. Today, those organisations that rely on Fortran for their mission can no longer find new programmers to replace the dwindling population of aging programmers, who are about to leave the workforce or have already left it.

## *tomorrow*

If the decline of Fortran's popularity continues to accelerate, soon there will no longer be enough programmers to maintain the massive amounts of existing mission-critical code. The "tomorrow" in the section title is no hyperbole; this problem is imminent.

And despite the industry leaders' increasing concerns about this problem for the past three decades, there had been no concerted effort to remedy it. Indeed, there are no actionable plans in existence. Transitioning away from an entrenched, long-lasting language like Fortran would take at least a couple of decades. Hence, this situation is insupportable.

There are only a handful of possible courses of action, but ignoring the problem and maintaining the status quo is not sensible:

- Manually translate Fortran into a new language
- Automatically translate Fortran into a new language
- Embrace Fortran by systematically promoting it in academia and in industry
- Create new, future-proof languages that target Fortran
- Thoroughly modernise Fortran and shed all emotional attachments to the days of yore

We shall now explore these options, in depth.

# OPTIONS

This document was written with a design to promote discussion, but it is not a design document for a new Fortran. In other words, the recommendations given here are fragments of ideas, not fully formed dicta. My aim is to lay the foundation upon which to think, talk, and teach about the looming gloom of Fortran code rot.

## *translate manually*

It is possible to translate manually a Fortran programme into a modern language, say C++, Java, Python, or something else. After all, an algorithm is an algorithm, whatever the implementation language.

But such a manual translation is not only uneconomical, it is downright perilous. Most Fortran programmes in use were first implemented decades ago, and the scientists and engineers who designed the programme had long left the workforce, and with them went the institutional knowledge of requirements and designs. Such programmes grew out of someone's research or experiment, and were never designed to grow so large and last so long. As such, the code and the system are usually undocumented. Given the specialist nature of their domain, most Fortran programmers are an insular lot; they do not know, or if they do know are not proficient in, newer languages that would be necessary to reimplement those massive, complex, parallel scientific applications. Conversely, most C++ and Java programmers have never seen a piece of Fortran code. And a typical Fortran code is highly optimised for parallel execution, but modern programmers have no experience with parallel programming. Moreover, modern languages do not have standardised, built-in parallel processing facilities. As such, the lead programmer must research, experiment, and select one parallel API from among the many: MPI, OpenMP, OpenCL, OpenACC, Vulkan, CUDA, Metal, and countless others, not to mention the implementation language itself. Also, parallel code is usually encrusted with layers of data distribution and control synchronisation protocols that obscure the underlying algorithm. These algorithms—even in their simpler, sequential form—are so specialised and sophisticated that IT coder, who do not possess the requisite science and engineering background, have no chance of comprehending.

Hence, the only people who could understand large, complicated Fortran codebase are those old scientists and engineers who are on the verge of departing the workforce. But in the twilight of their careers, they have no impetus to switch to newer, far-less-capable languages which would only hinder their work. And the only people who could reimplement those Fortran programmes in newer languages are those typical IT coders, who have no desire to devote a decade of their careers trying to master Fortran. This is a classic [Catch-22](https://en.wikipedia.org/wiki/Catch-22).

## *translate automatically*

A more realistic alternative to manual translation is automatic translation by leveraging existing Fortran compilers. For instance, the ever-popular [GNU Fortran compiler](https://gcc.gnu.org/fortran/), a free software to boot, can translate FORTRAN 1977 code into C. However, although it can compile modern, parallel Fortran code, it cannot translate that newer code into C, mainly because C is an unashamedly sequential language. Hence, even the state of the art compilers automatically convert only the old, sequential FORTRAN 1977.

The other possible path is to use a [large language model](https://en.wikipedia.org/wiki/Large_language_model) (LLM), which was first published in 2017. In late 2022, when ChatGPT was released, it shook the IT sector and the world at large. Today, IT is abuzz with LLMs: code generation, automated chat, text summarisation, spreadsheet analysis, image annotation, and the like. Of late, LLMs have all but swamped the field of AI research. At present, they are arguably the most capable, and the most adaptable, ML algorithms for text manipulation.

There are many LLMs that specialise in programming languages. They are trained on trillions of lines of code written in tens of thousands of languages. But even the most advanced LLMs could do no more than generate isolated code snippets of known algorithms. There are also some LLMs that are able to translate code snippets into a variety of different languages. But they, too, are limited to translating only small amounts of code. As of today, the most capable LLM translators falter when presented with a few thousand lines of code in any language they purportedly know. And they know nothing of parallel programming.

Beyond all that, there is a fundamental weakness of LLMs that may prove to be difficult, if not impossible, to overcome. Like all neural networks, nondeterminism is innate to LLMs. Moreover, LLMs are prone to [hallucinations](https://arxiv.org/abs/2311.05232), which maybe amusing in chat applications but unacceptable in scientific applications. The bottom line is that there is no direct statistical measure for assessing the accuracy of LLMs' code generation and translation capabilities. Hence, even if LLMs are capable of mass translation of parallel Fortran code into some new language, there is no way to guarantee that the semantics of the translated code is identical to the original Fortran code. And it is a well known fact that automated testing is insufficient to offer even an acceptable level of correctness guarantee, let alone $100\%$ accuracy, when life and limb are at risk.

It may well be that in the future, AI could perform machine translation of programmes. But that may take a few decades, yet. By then, it is unlikely that machine translation of high-level languages would be necessary at all, because AI programmers do not need high-level programming languages. It would then be economically nonsensical to employ human programmers. So, if AI were to be used to program machines in a distant future—a distinct possibility—it is an eminently more sensible use of resources to focus on creating AI that programs the hardware directly in machine language. So, AI translation of Fortran is also a Catch-22.

## *embrace fortran*

When I was an undergraduate electrical engineering student in the early 1980s, Fortran was the only programming language we were required to learn. Indeed, it was the only language scientists and engineers used in those days. Soon, C took over large swathes of Fortran's traditional hunting ground. And today, the majority of scientists and engineers use Python, exclusively. Meanwhile, Fortran continued to evolve quietly, incorporating modern programming language concepts and, most significantly, parallel programming facilities collectively known as [coarray](https://en.wikipedia.org/wiki/Coarray_Fortran). Coarray Fortran (CAF) originated in the early 1990s, and it was eventually incorporated into the Fortran 2008 standard.

Coarray parallel programming offers an unparalleled, as it were, comfort and convenience in implementing massively parallel code. No other language, to date, has managed to offer such a cultured parallel programming experience. Coarray has distinct advantages over other methods: it is syntactically and semantically bound to Fortran, a language specifically designed for high-performance scientific computing, a language that caters to the way scientists and engineers think about computing, a language that has been in sustained use for seven decades in scientific computing. Also, Fortran employs the [partitioned global address space](https://en.wikipedia.org/wiki/Partitioned_global_address_space) (PGAS) model of parallel programming. Of the many parallel programming models, PGAS is generally considered the most natural and intuitive to use. Thus, CAF is not only natural for programmers to use, it also enjoys field-proven reliability and stability. It is no surprise that Fortran continues to thrive today in scientific parallel computing.

But as explained above, Fortran's popularity in broader academia and industry faded a long time ago. That the scientific computing community has ignored the impending problem of Fortran programmer shortage for such a long time is regrettable. The simplest and the most realistic way to remedy this problem is to reintroduce Fortran into broader STEM undergraduate curricula.

At the moment, however, Python occupies that sacred spot in STEM education. Indeed, it would be highly unpopular to foist the crusty old Fortran upon the STEM undergraduates, when most of them have already achieved familiarity with Python even back in high school. It does not help Fortran's cause that it is used primarily on supercomputers and supercomputers are inaccessible to most universities.

But there is hope. All computers, including the mobile phones are multicore, shared-memory machines, these days. That is, they are parallel computers. But these powerful parallel machines currently run single-threaded applications written in sequential programming languages, because parallel programming has not caught on in IT. It takes considerable knowledge, skills, and effort to implement parallel code using the current stock of industrial languages. Even though no web developer would ever take up Fortran, it is not inconceivable that some science and engineering undergraduates could be coaxed into using CAF on their GPU-equipped, multicore laptops say, to implement and train AI models with greater efficiency, especially given that this code would run much, much faster on supercomputers, without requiring any modifications. And the same educational initiatives could be pursued in the industry, especially with the backing of current power users of Fortran: nVIDIA, IBM, NASA, NOA, DoD, and the like.

Put crudely, this approach is nothing more than a marketing campaign to restore Fortran's tarnished reputation to its former lustre. But it is as easy to accomplish as it is crude. All it would take is a few years. Moreover, familiarity with Fortran's parallel processing concepts will help young programmers immensely in their future career where the only type of computing resources available will be multicore, multiprocessor machines. This could be a win-win scenario, both for the Fortran shops and for the young programmers—if the marketing campaign can convince the youngsters to give Fortran a change against the tide of six-figure Python jobs. And that is a big "IF".

## *create new languages*

I recall, when I began my career in computing some decades ago, we used to quibble with our colleagues over the code format: whether to use tabs or spaces when indenting, the number of spaces to use for each indentation, the number of blank lines to retain between blocks of code, the column at which to place the inline comment, and much, much more. Many toes were stepped on; many feelings hurt; many friendships strained. The triviality of each argument is surpassed only by its convoluted, circular reasoning. But we sure did enjoy those hearty fights over a big nothing. Today, the disagreement over code formatting is moot, thanks to automatic formatting tools baked into [integrated development environments](https://en.wikipedia.org/wiki/Integrated_development_environment) (IDEs), almost all of which are free, open-source software. Recently, many IDEs have begun to incorporate LLMs to aid the programmer with code generation, refactoring, testing, debugging, performance monitoring, deploying, and so on.

It appears that programming tools will continue their arc of rapid improvement, at least in the foreseeable future. So, I contend that it may not be long before we have IDEs that can parse a high-level language, say Java, into its [abstract syntax tree](https://en.wikipedia.org/wiki/Abstract_syntax_tree) (AST), then use the AST to generate code in another related high-level language, say C# or C++. The disputes over which language is better will disappear, just like those conflicts over which code format was superior.

Today, a common practice in programming language design is to target "low-enough" high-level languages, instead of the machine language. The first C++ compiler from the 1980s, called the AT&T Cfront, transpiled C++ down to C, then invoked the platform's C compiler to produce the native binary. Nim, a new PP language, also transpiles down to C. Elm, the effervescent, purely-functional, web front-end domain specific language (DSL), transpiles down to JavaScript, the assembly language of the Web. So, it is in keeping with the current industry trends to design new, parallel programming DSLs that transpile down to Fortran.

It is important to note, though, that transpilation is not bidirectional: transpiling a low-abstraction language, like C, up to a high-abstraction language, like Haskell, is a practical impossibility, whereas transpiling Haskell down to C is far simpler by comparison. This is because down-transpilation is abstraction lossy. One way to mitigate abstraction loss is to inject metadata into the AST from which the high-level abstractions can be recovered. But those techniques are neither foolproof nor optimal. Within a paradigm, however, it is straightforward to translate between languages that are semantically proximate, say between C and Pascal, between Java and C#, or between OCaml and Reason. Fortran is a low-abstraction language, compared to modern FP languages. And Fortran's domain, scientific computing, is intensely mathematical. Hence, existing FP languages, like Haskell, OCaml, and F#, could target Fortran with relative ease. In fact, these languages already target C and JavaScript, so down-transpilation is not a foreign practice to them.

Programmers always chase new languages with elegant syntax and cogent semantics. So, they would have no objections to learning fresh, new scientific programming languages that target Fortran, even if they have to work within the mouldy, old Fortran ecosystem. This, too, could be a win-win situation. But it is not without challenges.

Designing a brand new language is not for the faint of heart. I would also caution against anointing the canonical language. DoD's efforts with the [High Order Language Working Group](https://en.wikipedia.org/wiki/High_Order_Language_Working_Group) that culminated in Ada; DARPA's efforts with [High Productivity Computing Systems](https://en.wikipedia.org/wiki/High_Productivity_Computing_Systems) that produced X10, Chapel, and Fortress; and other similar efforts have proved conclusively that languages developed by government-sponsored committees inevitably fails, not because the language is poor, but because the bureaucracy that surrounds it is poisonous and, more importantly, programmers detest being forced to use the sacred language forced upon them by government officials and corporate executives. It is better to take a gentler approach and leave language evolution to the [marketplace of ideas](https://en.wikipedia.org/wiki/Marketplace_of_ideas).

## *modernise fortran*

Throughout its long existence, Fortran has staunchly adhered to those original design concepts and philosophies that gave it life way back in the 1950s. Indeed, all modern Fortran compilers can still compile FORTRAN 1977 code. This level of backward compatibility is a remarkable achievement on the part of those who curated and guided the series of language standards, through the years.

But much has changed in computing, since 1957. As explained above, backward compatibility is a double-edged blade. Fortran's single-minded pursuit of backward compatibility extended its longevity: despite being the first ever high-level programming language, it is still being used actively, today. But this design choice also made Fortran verbose and stale. In the early days, English-like verbosity was valued for its perceived comprehensibility. Back then, no one really knew what high-level programming languages were supposed to look like. Also, hardware limitations constrained programmes to be no larger than a few hundred lines of code, making them essentially one-time-use tools. But today, when projects routinely exceed the million-line mark and last a few decades, verbosity severely diminishes comprehensibility and maintainability. So, the verbose nature of Fortran makes it unpalatable to modern programmers, in whose eyes modern Fortran is anything but modern.

Despite the successive standards' attempts to modernise Fortran and to expand its application domain, there is no denying that Fortran is not a [general-purpose language](https://en.wikipedia.org/wiki/General-purpose_programming_language) (GPL), a systems language, an enterprise language, a web development language, nor a mobile development language; it is a scientific programming language, through and through. Indeed, it is the only standardised programming language with parallel programming facilities baked into the syntax. Fortran is, thus, the ultimate scientific [domain-specific language](https://en.wikipedia.org/wiki/Domain-specific_language) (DSL).

All modern software development projects employ several different programming languages, each put to a particular purpose. For instance, the following division of labour amongst the languages would be entirely normal in any large scientific computing project, today: use HTML and JavaScript, TypeScript, or ReScript for web UI; use industrial-strength high-level languages that target WebAssembly for front-end background services and back-end remote services; use Python and Jupyter for interactive data analysis; use C, C++, Rust, or Zig for systems integration; use GraphQL for data wrangling; use SQL for data warehousing; and use Fortran for scientific parallel programming. In this scenario, Fortran's core could be excised of the inessentials that it had acquired through the decades, and be restored to its former svelte self, and its syntax will be overhauled to reflect modern thinking in language design. Much of Fortran's present bloat came from attempts to keep pace with modernity and to turn it into a GPL. Accepting Fortran's lot in life as the ultimate scientific DSL will make the language more compact, thereby making it better suited to its original purpose, once again.

Trimming the verbose syntax and the extraneous features of Fortran is not only feasible, it is also the most sensible option. This new Fortran, as it were, will employ the syntax and semantics of modern FP languages, like Haskell, OCaml, and F#, and incorporate features from modern proof assistants, like Agda, Idris, and Lean. But it will retain Fortran's array manipulation and parallel programming facilities. Yet, it is but a thin veneer of palatable, alternative syntax atop the Fortran 2023 syntax. In terms of syntactic differences, this effort is analogous to what [Reason](https://reasonml.github.io/) is to [OCaml](https://ocaml.org/). And in terms of semantics, it is like what [Agda](https://agda.readthedocs.io/en/latest/index.html) is to [Haskell](https://www.haskell.org). The compiler transpiles this new, higher-abstraction language down to Fortran, then invokes the Fortran compiler to produce the native binary. And just as C++ is able to interact natively with the existing C binaries, this new language will interact with the existing Fortran binaries.

After this modernisation, the resultant language is still Fortran in essence—a scientific DSL with built-in parallel programming facilities—but without the decades-old crust. And it provides familiar modern comforts and accoutrements that young programmers adore.

# MODERNISATION

Unique among modern programming languages, Fortran is religiously backward compatible. A 50-year-old piece of code is still a valid modern Fortran code, along with tonnes of other syntactic extensions that had been added during that time. This obsession with full backward compatibility makes Fortran revolting to modern programmers.

Surely, language designers and maintainers do make mistakes from time to time; it is human nature. The purpose of design updates is to remedy those mistakes, not to amplify them. Staunchly maintaining backward compatibility with a decades-old design, no matter what, is a monstrous mistake, in hindsight. It is senseless to enable application owners who slothfully or parsimoniously avoid updating their ancient, but still mission-critical, codebase. The continued use of a mission-critical code that no one understands any longer endangers that very mission. This behaviour must be deterred. Fortran's historical crud must, therefore, be cleansed by following the usual planned obsolescence path, and by embracing modern programming concepts without continuing to strut that tired mid-century chic.

There have been examples of languages dramatically altering their syntactic appearance without altering their semantic core. The difference between C 1978 and C 1989 was stark, but planned obsolescence smoothed out the transition. Python 2 to Python 3 transition was considerably messier, but it was done, eventually. The most recent language to have a plastic surgery was Scala, a popular FP language. Scala was released in 2004, at the height of Java's fame. As such, Scala 1 syntax was nearly identical to Java. By the time Scala 3 was released in 2021, though, Python was burning hot, and the syntax has been altered significantly to resemble Python, whose syntax is undeniably cleaner than that of Java. Twenty years is almost an eternity in the life of a programming language. The designers of Scala opted to evolve the language to ensure its continued success, instead of holding on to the old ideas that were not aging gracefully. At some point, a clean break with the past is warranted. If Fortran were to continue to attract new programmers, it, too, must undergo a similar plastic surgery.

To the programmer, the syntax is the intimate touchpoint with a language. So, programmers grow emotionally attached to a language, mainly for its attractive, intuitive syntax. Of course, semantics is important to programmers, too, to do the job right. During the three-quarters of a century over which high-level programming languages have been in use, a handful of design philosophies and implementation practices have emerged as dominant ones. Modern languages must adhere to those good principles, both to promote execution efficiency and to eliminate programmer misunderstanding. It is, therefore, important to modernise both the crusty syntax and the antiquated semantics of Fortran.

In this section, I present a modernised Fortran syntax that resembles the syntax of the ML family of FP languages. This choice is deliberate. First, the ML family uses the clutter-free offside rule (meaningful whitespace) of [ISWIM](https://en.wikipedia.org/wiki/ISWIM), a seminal FP research language. Although Python is of the OO lineage, it follows the offside rule. Marks for Python, there. Secondly, Fortran leans heavily towards mathematics, much like FP languages, and the most established languages in the FP paradigm belong to the ML family. Thirdly, the offside rule, together with a few other simple conventions, yield a clean, clear, cogent syntax without parentheses, braces, commas, semicolons, and other syntactic noises, as demonstrated by Hope, Clean, Miranda, Haskell, Agda, Idris, and other ML family members.

The syntactic and semantic modifications proposed in this section, like all such proposals, are always susceptible to being dismissed as "mere preferences". The conversation, then, quickly devolves into a fight over tastes. To avoid that, I have provided my reasoning behind every proposal, so that it could be subjected to a reasoned critique. However, rejecting a proposal by saying, "We reject the *new*, because we have always done it the *old* way" is neither reasonable nor valid. Also, the proposal to remove the unnecessary, irrelevant, old syntax cannot be countered with, "We want that", because wants are not needs. And earlier, I have already refuted the claimed supremacy of absolute backward compatibility.

## *scrub the crud*

***remove fixed format***—Modern Fortran continues to support the 1950s code formatting convention developed for the [teleprinter](https://en.wikipedia.org/wiki/Teleprinter), called the [fixed format](https://people.cs.vt.edu/~asandu/Courses/MTU/CS2911/fortran_notes/node4.html). Stringent backward compatibility demands modern Fortran compilers to support this obsolete convention. Yet, in modern programming practice, this format is arbitrary, onerous, and irrelevant. Hence, this format must be replaced with the [offside rule](https://en.wikipedia.org/wiki/Off-side_rule).

***remove implicit none***—The [`implicit none`](https://fortranwiki.org/fortran/show/implicit%20none) statement appears in every modern Fortran code. It disables the old FORTRAN feature, which automatically assigned all identifiers that begin with `I`, `J`, `K`, `L`, `M`, and `N` to the `INTEGER` type, and all other variables to `REAL`. In the days of the teleprinter, this implicit typing feature was a desirable keystroke saver. But it grates against the strong, static typing philosophy of modern programming languages, including modern Fortran. As such, every modern Fortran code begins with this incantation to disable implicit typing.

This feature should have been excised long ago through the planned obsolescence process employed by countless other languages, including C and C++. For instance, the original C syntax that appeared in *[The C Programming Language](https://en.wikipedia.org/wiki/The_C_Programming_Language)*, 1ed (1978) continued to be used well into the early 1990s, but it is no longer accepted by modern C compilers in the early 2020s—as they ought not. Indeed, most modern C programmers cannot understand the 1970s style C code any more. But the irrational adherence to absolute backward compatibility obliges modern Fortran programmers to inject `implicit none` into every module.

The `implicit none` is an instance of the many poor design decisions that littered Fortran's long trek to modernity. Disabling implicit typing should have been cued off a file name extension (`.f90` for instance) or a compiler flag (say `--ImplicitNone`), and it should have been excised from the language a long time ago. But the designers opted to keep this superfluous feature in perpetuity and to force the programmer manually to disable implicit typing in every single module. Consequently, this statement is almost as prevalent in code as `do` and `if`, yet it performs no substantive work. Such pointless and arcane incantations not only make modern Fortran verbose, they also diminish its legibility, without offering any countervailing benefits.

## *trim the bloat*

***trim type definitions***—To make programmes readable, it is necessary to eliminate verbosity from the syntax. Modern Fortran supports user-defined product types, which it calls *derived type*. It is not uncommon to see bloated code like the following.

```fortran
type :: point3d
  integer, parameter :: k8 = selected_real_kind(8)
  real(kind=k8) :: x
  real(kind=k8) :: y
  real(kind=k8) :: z
end type point3d

type(point3d) :: p

p = point3d(3.0, 2.0, 1.0)
```

This verbosity is gratuitous, tedious, confusing, illegible, and error-prone. The above code could be reduced to the following Haskell-like syntax in our new language.

```
Point3D : Point3D {x, y, z : ℝ} ## declare a record type
p = Point3D {3.0, 2.0, 1.0} ## define a record value
```

In the above declaration `Point3D : Point3D {x, y, z : ℝ}`, the left-side `Point3D` is the type constructor and the right-side `Point3D` is the data constructor that takes a record of the shape `{x, y, z : ℝ}`. For simplicity, this same syntax is used for type aliases, too. In the second line, the data constructor `Point3D` is applied to the data value `{3.0, 2.0, 1.0}` to construct the record `p`. The fields of this record are accessed as `p.x`, `p.y`, and `p.z`.

***remove kinds***—For historical reasons, Fortran supports several different number representations via a convoluted, and convulsive, mechanism it calls *kind selection*. In the `point3d` example above, `selected_real_kind(8)` is used to defines an 8-byte floating-point kind selector named `k8`, whose type is `integer`, and `k8` in turn is used to define three double-precision floating-point variables named `x`, `y`, and `z` . This syntax is excessive, to say the least. The main purpose of this mess is to allow the programmer to choose the smallest number of bytes necessary for the desired precision, thereby conserving memory use. But allowing multiple representations for a number type could create incompatibilities across different hardware platforms. And these byte-level concerns are superfluous in modern programming practice, where memory conservation is no longer the utmost priority.

Moreover, the word "kind" is a term of art in modern type theory. It means the "type of a type" in Haskell. That is, just as values are classified by their types, types are classified by their kinds. Hence, using the term "kind" to refer to number representations should be abandoned, along with the practice of allowing multiple, incompatible representations for one number type.

***remove bit twiddling***—Systems programming languages like C, C++, Odin, and Zig need to manipulate bits, but a scientific DSL like Fortran does not need bit twiddling operators like `&`, `|`, `~`, and the like. Bits are, after all, hardware-level concepts.

***remove objects***—A scientific DSL like Fortran has no need for OO. Modules, sum types, product types, functions, and functionals are more than capable of modelling mathematical and scientific concepts. Objects are commonly used to model massive tangles of interacting business processes and for hiding their convoluted, mutual mutations of each other's states. Objects are convenient (that is, expedient) for representing concepts and organising code that implements a large, sequential business application running on a uniprocessor. But objects' very nature—their propensity to hide interacting mutations—make them unsuited to implementing a large, parallel scientific application running on a multiprocessor.

The key feature introduced by the Fortran 2003 standard was objects. OO was the dominant paradigm in the early 2000s. Today, though, it is well established that hidden state mutations of OO are detrimental to comprehensibility and parallelism of code. In my view, Fortran's adoption of OO was a mistake. Fortran has never been known for its OO prowess, unlike Simula, Smalltalk, Objective-C, C++, Java, Python, and loads of other proper objective languages. Moreover, just including objects does not make the language OO; the syntax must make creating and manipulating objects convenient and effortless. Smalltalk and Python excel in that, but Fortran fell way short. Be that as it may, given Fortran's mathematical propensities, FP is the superior suitor for Fortran than OO ever could be.

***trim variable declarations***—The following is a way to declare and define a two-dimensional, floating-point array in modern Fortran.

```fortran
real, dimension(:, :), allocatable :: a ! declare a matrix

allocate(a, 2, 3) ! allocate an uninitialised 2x3 matrix
```

The following is an equivalent array defined in the new syntax, using the standard library's [dependently typed](https://en.wikipedia.org/wiki/Dependent_type) `Matrix ℝ 2 3` (aliased as`[ℝ 2 3]`), which is parameterised with the element type $ℝ$ and is doubly indexed with size values of type $ℕ$. Note that in the code snippet below, the elements of the matrix `y` are automatically initialised to $0.0$.

```
y : [ℝ 2 3] ## define an ℝ type 2x3 matrix initialised to 0.0
```

***trim function definitions***—The following is an implementation of [quicksort](https://en.wikipedia.org/wiki/Quicksort) in modern Fortran. For simplicity, this implementation uses a naïve double recursion and accepts as argument an array of integers, only.

```fortran
recursive function qsort(x) result(y)
  integer, dimension(:), intent(in) :: x
  integer, dimension(1:size(x)), intent(out) :: y
  if (size(x) > 1) then
    y = (/ qsort(pack(x(2:), x(2:) < x(1))), &
           x(1), &
           qsort(pack(x(2:), x(2:) >= x(1))) /)
  else
    y = x
  end if
end function qsort
```

As can be seen above, there is much crud in the syntax of this simple function. By contrast, the following equivalent implementation in the new syntax is succinct and, more importantly, legible and comprehensible.

```
qsort : (n : ℕ) ⇒ [ℤ n] → [ℤ n]
  | [] → []
  | x:xx → qsort [l | l ← xx, l < x] + [x] + qsort [g | g ← xx, g ≥ x]
```

The type declaration `qsort : (n : ℕ) ⇒ [ℤ n] → [ℤ n]` states that the function `qsort` takes an integer vector of size `n` as argument and returns an integer vector of the same size. Here, `[ℤ n]` is the shorthand syntax for the dependent type `Vector ℤ n`. And the double-arrow syntax `(n : ℕ) ⇒` constrains the type of `n` to be $\mathbb{N}$. Hence, this vector type, which is defined in the standard library, is parameterised with the type $ℤ$ and is indexed with the value of the variable `n` whose type is $\mathbb{N}$​. This single line not only replaces three lines of rather busy Fortran code.

In fact, the type system can automatically infer the type of this function, so the type declaration could be omitted, altogether. Thus, a minimalist implementation of `qsort`, shown below, consists of just two clauses: the base case and the recursive step.

```
qsort [] → []
qsort x:xx → qsort [l | l←xx, l<x] + [x] + qsort [g | g←xx, g≥x]
```

In this `qsort` implementation, the formal parameter `[]` in the first clause pattern matches an empty vector argument. Since a sorted version of an empty vector is just an empty vector, the first clause simply returns the value `[]`. The formal parameter `x:xx` in the second clause pattern matches a non-empty vector argument, with the variable `x` bound to the first element, and the variable `xx` bound to the rest of the elements. The `[l | l ← xx, l < x]` is the vector comprehension syntax that is an analogue of the [set comprehension](https://en.wikipedia.org/wiki/Set-builder_notation) notation in mathematics. This phrase dynamically constructs a vector that holds the filtered elements of `xx` that are less than `x`. Likewise, the vector `[g | g ← xx, g ≥ x]` holds the filtered elements of `xx` that are greater than or equal to `x`. Then, the sorted lesser vector, the singleton vector  `[x]` that contains the pivot element `x`, and the sorted greater vector are concatenated into the resultant vector using the `+` operator, and this result is returned. This version of `qsort` reads like a mathematical description of the algorithm. Proximity to mathematical discourse, not hardware bits, is the driving force behind FP languages.

The overloaded operator `:`, when used in the context of vector operations, is not acting as the typing operator. Instead, it is aliased to the standard library vector constructor function `cons`. Applying this function to the element `x` and the vector `xx`, as in `cons x xx`, prepends `x` to the head of `xx`. Because this construction occurs frequently in FP, we have the shorthand syntax `x:xx` for it. Also, the overloaded operator `+` is aliased to the standard library vector concatenation function `cat`. Hence, `cat u v` is the same as `u + v`. We pronounce `:` as *cons* (per LISP tradition) and `+`  as *cat* (per UNIX tradition), when these symbols appear in the context of vector operations.

As can be seen above, the quicksort algorithm immediately pops out at the reader in our new syntax, without him having to traipse over Fortran's syntactic spikes.

## *let go of old memories*

***remove manual memory management***—Manual memory management has long been known to be the primary source of runtime errors. Manual memory management was essential in the days before the advent of modern, efficient [garbage collection](https://en.wikipedia.org/wiki/Garbage_collection_(computer_science)) (GC) techniques, when the high-level programming languages were just a thin coating atop assembly language and when computers had but a few kilobytes of memory. Note that LISP was the first to employ a GC. But it was not until the 1990s that GCs became fast enough to be used with mainstream industrial languages.

Today, though, most languages, including Haskell, Java, C#, Kotlin, Go, Swift, and the like, have automatic memory management by GC. The only languages that still rely on manual memory management—out of necessity—are systems programming languages, like C, Odin, and Zig. Nim has automatic memory management, but it allows the programmer to take control, if desired. Rust's [ownership model](https://doc.rust-lang.org/book/ch04-01-what-is-ownership.html), which is based on the [linear type system](https://en.wikipedia.org/wiki/Substructural_type_system), requires the programmer manually to provide hints in the code to enable the compiler automatically to ensure that objects are always owned (referenced) by one owner. Hence, the compiler can automatically free up the objects that are no longer being used.

In some ways, Fortran's present approach to memory management is similar to that of Nim's. But I argue that it is time for Fortran to go a step further: abandon manual memory management, completely. First, Fortran is not a systems programming language, so it ought not muck about with hardware-level concerns like memory management. Secondly, the memory access patterns of large business applications are driven by external events and hence are random, whereas the memory access patterns of large scientific applications are driven by internal logic and thus are ordered. Such simple patterns of memory use can readily be optimised by modern compilers and GCs. Thirdly, modern automatic memory management techniques have advanced to the point where the GC could out perform hand-tweaked memory management code.

***remove pointers***—Careless programmers routinely kill programmes. Their chosen crime scene is the arena of manual memory management. Their preferred murder weapon is the needle-sharp pointer, which has been popular with programme assassins since antiquity.

Pointers are immensely useful in systems programming. In the hands of skilled programmers (a small minority), pointers are perhaps the most expedient tool for efficient memory access. But ordinary programmers (a vast majority) are not skilled enough to extract that last little bit of efficiency from the hardware, and they usually cannot outperform even the run-of-the-mill compilers, when it comes to optimisation. The gain-loss balance of manual pointer manipulations is tipped substantially towards loss. As such, most modern languages have done away with pointers. So should Fortran. Besides, pointers are an afterthought in Fortran. In fact, the use of pointers can slow down the code in Fortran!

I urge that modern Fortran programmers alter their view of computation, at a fundamental, philosophical level. They should discard the ancient "systems approach" to programming and adopt the modern "functional approach". FP programmers went through this perspective shift in the 1970s and 1980s; today, they are better off for it, because the hardware technology and the software techniques have caught up with their aspirations. Fortran programmers, too, must become comfortable with relinquishing control over the myriad hardware-level concerns, such as memory conservation and pointer manipulation. Their time and efforts are more profitably allocated to the design of superior parallel algorithms that are orders-of-magnitude faster, albeit with some memory consumption overhead. In return for giving up the control over memory use, they gain programming convenience, code clarity, software maintainability, and runtime safety.

The most obvious alternative to explicit pointers is, of course, implicit references. Most modern languages take this approach.

## *embrace modernity*

***use modern comment styles***—Delimit a documentation comment with `#<` and `#>`; `<` and `>` are evocative of open books. Delimit a block comment with `#{` and `#}`; `{` and `}` remind one of C code blocks. Note that both the open- and the close-comment markers begin with the `#` symbol; this is for consistency. And begin an in-line comment with `##`. Doubling the `#` symbol makes it stand out visually against the backdrop of code and it also makes all comment symbols twin characters, another mark of consistency.

Also, avoid superfluous, in-your-face comments. The shouting comment shown below may well be impossible to ignore, but it imparts no insightful information to the reader.

```fortran
!*********************************************************************
!* FILE: QUICKSORT.F90                                               *
!* This function sorts an input array using the quicksort algorithm. *
!* It accepts a 1D array and returns a sorted 1D array.              *
!*********************************************************************
```

Subtly is a virtue. When it comes to commenting code, it is better to cite a readily accessible, authoritative source of the algorithm in the module's block comment, without cramming in a incomprehensible, perfunctory description thereof.

```
#< GraphSearch.f
This module implements bread-first and depth-first
graph searching algorithms as described in
Chapter 20 Elementary Graph Algorithms of
"Introduction to Algorithms", 4ed (2022), Cormen et al. #>
```

***use common primitive types***—Many modern high-level languages use only these primitive types: boolean, character, integer, natural number, and floating-point number. The boolean is a one-byte quantity, the character is a variable-byte quantity represented using Unicode, the natural number is an unsigned 64-bit quantity represented using binary, the integer is a signed 64-bit quantity represented using 2's compliment binary, and the floating-point number is a 64-bit quantity represented using the IEEE 754 format. These primitive data types suffice for scientific applications. We shall call them `Bol`, `Chr`, `Nat`, `Int`, and `Flt`, respectively. Larger data types with greater precisions are defined in the standard library: infinite-precision integer as `Integer`, 128-bit integer as `Int128`, and 128-bit floating-point number as `Flt128`. The types `Nat`, `Int`, `Int128`, `Integer`, `Flt`, and `Flt128` belong to the number class `Num`.

The standard library defines some type aliases for convenience. $\mathbb{N}^+$ is the type of non-zero natural numbers (counting numbers).  $\mathbb{Z}^-$ is the type of non-zero negative integers. $\mathbb{Z}^+$ is the type of non-zero positive integers. $\mathbb{Z}^\pm$ is the type of non-zero integers.

```
ℕ+ : (n : ℕ) > 0
ℤ- : (n : ℤ) < 0
ℤ+ : (n : ℤ) > 0
ℤ± : (n : ℤ) ≠ 0
```

The [rational](https://en.wikipedia.org/wiki/Rational_number), [complex](https://en.wikipedia.org/wiki/Complex_number), and [quaternion](https://en.wikipedia.org/wiki/Quaternion) data types are implemented as records in the standard library.

```
Rational : Rational {n : ℤ, q : ℤ±}
ℚ : Rational

Complex :
  | Rectangular {x, y : ℝ}
  | Polar {r, 𝜑 : ℝ}
ℂ : Complex

Quaternion :
  | Rectangular {a : ℝ, v : [ℝ 3]}
  | Polar {m, 𝜃 : ℝ, n : [ℝ 3]}
ℍ : Quaternion
```

Above, we defined the type `Rational` as an alias of the record `{n : ℤ, q : ℤ±}`, representing the mathematical quantity $n/d$, where $n ∈ \mathbb{Z}$ and non-zero $d ∈ \mathbb{Z}^\pm$. The left-side `Rational` is the type constructor, and the right-side `Rational` is the data constructor that takes a record of the shape `{n : ℤ, q : ℤ±}`. The type `Complex` is defined to be the sum of two product types, the `Rectangular` and the `Polar`. That is, `Complex` is a sum-of-products type. Likewise, the type `Quaternion`.

For convenience and concision, the following shorthand type aliases are provided: $\mathbb{B}$ for `Bol`, $\mathbb{U}$ for Unicode `Chr`, $\mathbb{N}$ for `Nat`, $\mathbb{Z}$ for `Int`, $\mathbb{Q}$ for `Rational`, $\mathbb{R}$ for `Flt`, $\mathbb{C}$ for `Complex`, $\mathbb{H}$ for Hamiltonian `Quaternion`, $\mathbb{V}$ for `Vector`, $\mathbb{M}$ for `Matrix`, and $\mathbb{T}$ for `Tensor` of three or more dimensions. The `unsigned` types, though useful for bit manipulation in a systems GPL like C, are useless in a scientific DSL like Fortran, except to represent natural numbers $\mathbb{N}$ and counting numbers $\mathbb{N}^+$. Our new language supports both natural numbers and counting numbers, but not the `unsigned` type modifier, as C does.

The Unicode symbols can be used in the code for identifier names: $\pi$, $\sigma$, $\le$, $\ge$, $\sqrt{}$, $\infty$, $\bot$, $\lnot$, $\land$, $\lor$, $\emptyset$, $\otimes$, $\oplus$, etc. These symbols are entered using standard [$\LaTeX$](https://en.wikipedia.org/wiki/LaTeX) commands, as is done in Agda. IDEs can provide keyboard shortcuts.

***rename derived type***—Calling a user-defined product type a "derived type" is courting trouble, because it is a term of art in OO, and most newcomers to Fortran today would already know OO quite well. Instead, simply call the user-defined product type a "record", just like every other modern language. Redefining buzzwords just to be different causes confusion without offering benefits.

***remove case insensitivity***—Modern Fortran, like other mid-century languages, is case insensitive. This is not in keeping with modern programming language conventions. Case insensitivity, more precisely the use of all-caps characters, was the norm in the early days of computing, because teleprinters could only print capital letters. Today, though, all-caps are shunned, due to their illegibility.

***standardise naming conventions***—There is no consistent, industry-wide naming convention for Fortran. So, we shall adopt a consistent naming convention for our new Fortran. For legibility, we adopt the naming convention similar to Smalltalk, Java, and Haskell. This convention has proven itself over the decades by being concise, consistent, cogent, and comprehensible.

- Avoid using `-` separators, `_` separators, ALL_CAPS, and other noisy naming conventions; instead, use the more legible PascalCase and [camelCase](https://en.wikipedia.org/wiki/Camel_case)
- Use PascalCase for type names: `Vector`, `Matrix`, `Point2D`
- Use lower-case single Greek letter for type variable names: `Point2D (𝛼 : Num)` where 𝛼 could be substituted with a number type in the class `Num` comprising the types `Nat`, `Int`, `Int128`, `Flt`, `Flt128`, or `Integer`
- Use camelCase for variable names and function names
- Use PascalCase for file names, and module names will be automatically given the name of the file
- Retire the tired FORTRAN 1977 fixed format
- Reclaim the `.f` file name extension for the new language

***standardise formatting***—When indenting, use 2 spaces, not 4, not tabs. Modern IDEs show vertical lines that demarcate indented code, so the traditional, deeper indentations are no longer necessary for legibility. Avoid blank lines as much as possible. They do not aide clarity; they just rob screen real estate.

These guidelines help contract the code in both the horizontal and the vertical directions, thus fitting more code per screen. Being able to see more code on the screen at once improves cognition and reduces the need for scrolling.

***allow user-defined symbolic operators***—As the first high-level language, Fortran invented arithmetic, relational, and logic operators, but it employed `.LT.` for `<`, `.EQ.` for `==`, `.GT.` for `>`, and so on. These dotted operators may look strange to modern eyes, but they were necessary, because early teleprinters had no support for mathematical symbols. In due course, languages converged on the modern, symbolic conventions for operators. Even Fortran eventually had to abandon its old style dotted operators and adopt modern symbolic operators.

Many languages today allow programmers to define their own symbolic operators. In Haskell, for example, many standard operators are not baked into the language, but are defined in standard library modules, like the famous monad `bind` operator and its symbolic alias `>>=`. But Fortran insists upon using the old convention of the dotted words for user-defined operators, which is verbose, unnecessarily constraining, and offers no real benefits.

In our new language, an operator is introduced using the Agda-style [mixfix](https://agda.readthedocs.io/en/latest/language/mixfix-operators.html) syntax. Here, the `_` symbol represents an argument placeholder.

```
Bol :
  | False
  | True
𝔹 : Bol

¬_ : 𝔹 → 𝔹 → 𝔹
  | False → True
  | True → False

_∧_ : 𝔹 → 𝔹 → 𝔹
  | False ∧ _ = False
  | True ∧ b = b

_∨_ : 𝔹 → 𝔹 → 𝔹
  | False ∨ b = b
  | True ∨ _ = True

p, q : 𝔹
...
¬ p
p ∧ q
p ∨ q
```

Above, we defined the prefix operator $\neg$ and the infix operators $\land$ and $\lor$. And we can implement the postfix factorial user-defined operator `!` like so.

```
_! : ℕ → ℕ
  | 0 → 1
  | n → n * (n - 1)!
```

***access record fields using the . operator***—Use the de facto industry standard `.` operator to access a record's fields, not the `%` operator as Fortran does. In modern languages, the `%` symbol represents the modulo operator. Besides, the Fortran syntax `object%field%subfield` is an eyesore, compared to the common syntax `object.field.subfield`.

***use row-major ordering***—All popular, modern languages use the [row-major ordering](https://en.wikipedia.org/wiki/Row-_and_column-major_order) for multi-dimensional arrays. That is, the rightmost index of a multi-dimensional array changes the fastest, in a similar way the rightmost digit of an odometer changes the fastest or the cursor on a terminal moves across the screen horizontally first and vertically thereafter.

Fortran's adherence to its old, column-major ordering—which harkens back to the early days when there were no established memory arrangement conventions in computing—is a source of confusion for newcomers who are already fluent in modern languages that employ row-major ordering.

## *fixate on functions*

***remove imperative***—One of the most important aspects of an FP language is its support for pure, side-effect-free expressions, from which pure functions are constructed. It has long been established that pure functions are easier to understand for programmers and are easier to parallelise for compilers. Effectful, imperative statements must be shunned, for they do not play well with effect-free, declarative expressions.  Fortran's imperative control statements must be converted into expressions, and its imperative looping constructs must be replaced with recursion. And `goto`, that ultimate imperative construct, must go to the bin.

***embrace declarative***—In his 1977 ACM [Turing award acceptance lecture](https://cs.wellesley.edu/~cs251/s19/notes/backus-turing-lecture.pdf), Backus, the father of FORTRAN which is a perennial imperative language, said that for programming to advance to a higher plane, we must abandon the imperative PP and adopt the declarative FP. This was also the year the second standard, FORTRAN 1977, was published. Yet, after 50 years, Fortran remains resolutely PP, while most modern languages have already migrated to FP, either partially or fully.

***support functionals***—Embracing FP means supporting higher-order functions (functionals): functions that accept and return functions as first-class values. An ordinary function $f : x \to y$ accepts and returns *ordinary values* $x$ and $y$, which can be primitives, tuples, records, or enumerations. And a functional $h : f \to g$ accepts and returns *function values* $f$ and $g$. In calculus, for example, applying the differential operator $\frac{d}{dx}$ to the $sin(x)$ function yields as the result the $cos(x)$ function. The differential operator, which takes some function and returns another function, is a functional.

Anonymous functions that are created on-the-fly (𝜆 functions) are also an integral part of FP. Likewise, function composition operators—pipe-left `<|` (same as mathematical composition operator `∘`), and pipe-right `|>` (same as Unix shell pipe operator `|`)—are essential parts of the FP idiom. The following code shows the use of the 𝜆 function construct supported by our new language. The fold-left standard library functional `foldl` takes a 𝜆 function, an initial value, and a vector. The 𝜆 function takes as arguments the accumulator `a` and the element `x`.

```
foldl (𝜆 a x → a + x) 0 [3, 5, 7, 4, 9] ## returns 28
```

Note the function application syntax shown above. The function `foldl` is applied to three arguments: a 𝜆 function, the initial value `0`, and the vector `[3, 5, 7, 4, 9]`. No parentheses are needed when applying a function to its arguments. So, whereas in mathematics function application is written $f(x)$, in Haskell it is written `f x`. This syntax is clear, succinct, and quiet. By the way, the vector, the initial value, and the 𝜆 function, together, form an algebraic structure called a *[monoid](https://en.wikipedia.org/wiki/Monoid)*.

The `<|` and `|>` composition operators as used as follows.

```
g <| f x ## same as g ∘ f, which is read "g after f"
f x |> g ## same as f ; g, which is read "f then g"
```

Fortran, too, supports passing functions as arguments—well, sort of. The Fortran `pack` procedure is an analogue of the `filter` functional of FP languages. Note that the name "pack" reflects the compaction of memory occupied by the result array, which ordinarily would be smaller than the original argument array. This undue obsession with hardware-level concerns is unbecoming of a scientific DSL. The following is a Fortran code for filtering (selecting) from an array the elements whose values are greater than $5$.

```fortran
integer :: xx(:) = (/ 9, 1, 6, 3, 7, 4, 8, 5, 2, 0 /)
integer, allocatable :: packed(:)
packed = pack(xx, xx > 5) ! returns (/ 9, 6, 7, 8 /)
```

And this is the equivalent code in the new syntax. The `filter` standard library functional takes a 𝜆 function and a vector. The 𝜆 function takes an argument `x`, which is an element sequentially pulled from the vector `xx`.

```
xx = [9, 1, 6, 3, 7, 4, 8, 5, 2, 0] ## inferred type is [ℕ 10]
filtered = filter (𝜆 x → x > 5) xx ## returns [9, 6, 7, 8]
```

As a scientific DSL, our new language must support FP, fully. So, it provides concise and convenient syntax for defining (abstracting) and calling (applying) functions. Fortran's current support for FP, though, leaves much to be desired: no support for lambda abstraction, no support for function composition operators, and what little functional facilities supported is syntactically burdensome.

***support clausal functions***—Functions can also be defined by multi-clause pattern matching in the new language.

```
modulus : ℂ → ℝ
  | Rectangular {x, y} → √ (x^2 + y^2)
  | Polar {r, _} → r
```

The standard library aliases the operator `√` to the function `sqrt`. Since we do not need to use the $\phi$ field of the `Polar` record in the second clause above, we ignore it using the `_` symbol.

The code for `modulus` can be read as follows:

- The function `modulus` takes an argument of type $\mathbb{C}$, and returns a value of type $\mathbb{R}$
- If the argument is in the `Rectangular` form $x + iy$, the result is $\sqrt{x^2 + y^2}$
- But if the argument is in the `Polar` form $r\angle{\phi}$, the result is $r$

The `modulus` function is an example of a multi-clause function. It could also be shortened as follows, by letting the type system infer its type as $\mathbb{C} \to \mathbb{R}$.

```
modulus Rectangular {x, y} → √ (x^2 + y^2)
modulus Polar {r, _} → r
```

The `id` function defined below is an example of a uni-clause function. Although there is but one clause here, we nevertheless use the begin-clause symbol `|`, for visual consistency of function definitions.

```
id : 𝛼 → 𝛼
  | x → x
```

Here, too, we could shorten this code like this, and the type system would infer its type as $𝛼 \to \alpha$.

```
id x → x
```

***support pure functions***—Fortran does allow marking functions with the `pure` keyword. In the new language, all functions are pure, by default.

***support inner functions***—Fortran also provides a way to define inner functions, which are useful for avoiding polluting the namespace with small functions. In Fortran, inner functions are called *internal procedures*. But its internal procedure syntax is more trouble than it is worth. The following concocted example shows how an internal function is defined and called in Fortran.

```fortran
pure function external(i) result(o)
  real, intent(in) :: i
  real, intent(out) :: o
  o = g(i) - 2.0

  contains
    pure function internal(x) result(y)
      real, intent(in) :: x
      real, intent(out) :: y
      y = x**3.0
    end function internal
end function external
```

Compare that grotesque, bloated Fortran code to the equivalent, svelte code in the new language.

```
external : ℝ → ℝ
  | i → internal i - 2.0 where internal x → x^3.0
```

The type system can automatically infer the type of the function `internal` to be $\mathbb{R} \to \mathbb{R}$ based on its implementation and its usage within the body of the function `external`, so there is no need explicitly to provide the type of the function `internal`. The `where` clause in this code is analogous to the $where$ clause in mathematics—it provides a succinct way to create local definitions. The scope of the function `internal` is the body of the function `external`.

The type system can also infer the type of the function `external` as $\mathbb{R} \to \mathbb{R}$, so we could further contract the above code like this.

```
external i → internal i - 2.0 where internal x → x^3.0
```

Note that, instead of the `where` clause, the `let-in` construct can be used to introduce the `internal` function.

```
external i → let internal x → x^3.0 in internal i - 2.0
```

The differences between `let-in` and `where` are these:

- `let-in` creates a new block within the current scope, and the scope of the local definitions introduced is that new block.
- `where` can only be used inside functions, and the scope of the local definitions introduced is the entire body of the function.

***mark impure functions***—As mentioned, all functions are pure by default in our new language. But impure functions that exchange data between various data structures is a common programming practice in scientific computing. So, our new language supports impure functions. But since they reduce parallelisation, impure functions should be used only sparingly.

Impure functions—those with side effects—must be marked with the `!` symbol, which hints at the surprising (unpredictable) nature of such effectful functions. This is a convention in Scheme, but it is mandatory in our new language: if the programmer left out the `!` symbol at the end of an impure function, the compiler automatically appends it. Below, the `print!` function causes a side effect by printing a message to the console. And the `time!` function causes a side effect by returning `Time` object representing the current time, because time changes from call to call and, hence, is a side effect by definition. The `now!` function that calls these impure functions also becomes tainted by association.

```
time! : () → Time
  | () → ...

now! : () → IO ()
  | () → time! () |> show |> print!

now! () ## current time appears on the console
```

The type expression `() → IO ()` of the function `now!` means that the function takes an argument of the unit type and returns a value of the type `IO ()`. The [unit type](https://en.wikipedia.org/wiki/Unit_type) has only one occupant, the unit value; both the type and the value are written as `()`, by FP convention. Its analogue in PP languages is the C `void` type. The unit value cannot be manipulated. That is, it cannot be used to perform meaningful computation. Its only use is to cause side effects. The return type `IO ()`—the `IO` type parameterised with the unit type—represents an I/O side effect. Thus, the type expression `() → IO ()` states that the function `now!` takes no meaningful argument and it does not return a useful value but causes an I/O side effect, which in this case is to print today's date to the console. A function, like `now!`, that takes the unit value `()` as the argument is invoked thus: `now! ()`.

***mark predicate functions***—Predicate functions—those that check a condition on the argument and return a $\mathbb{B}$ value—must be marked with the `?` symbol, which indicates the interrogatory nature of predicate functions. This, too, is a convention in Scheme, but it is mandatory in our new language. Visually, it is more succinct and more distinctive than naming predicate functions with the `is...` prefix, which is the convention in most languages.

The following is a declaration for the predicate function `prime?` that checks if the argument `n` of dependent type `(n : ℕ) > 1` (a natural number greater than $1$) is a prime number.

```
prime? : (n : ℕ) > 1 → 𝔹
```

This predicate can be used in an `if-then-else` conditional.

```
n = 7
...
if prime? n then ... else ...
```

## *depend on dependent types*

***support dependent types***—In an FP language, functions are first class, so functions can be held in variables and be manipulated by other functions. In a language with [dependent types](https://en.wikipedia.org/wiki/Dependent_type), types are first class, so types can be held in variables and be manipulated by functions.

In a [parametric type](https://en.wikipedia.org/wiki/Parametric_polymorphism) system, types can be parameterised with other types. That is, types can depend on other types: `Vector 𝛼` means "an arbitrary-length vector of $𝛼$-typed elements"—in other words, a list. In a dependent type system, types can additionally depend on values: `Vector 𝛼 n`, where `n` is a value of type $\mathbb{N}$, means "a size-$n$ vector of $𝛼$-typed elements". By convention, we name type parameters of a dependent type using Greek letters $\alpha$, $\beta$, etc., and values indices of a dependent type using English letters `m`, `n`, etc.

Our new language uses the operator `:` to assign types to variables, instead of using `::` as in Fortran and Haskell. In dependently typed languages, types are first-class values and there are many expressions involving types. As such, we use the less noisy `:` for type assignment. This convention is common among dependently typed languages, including Coq, Agda, and Idris.

We use a strong, static, dependent, inferencing type system based on dependent type theories, such as Martin-Löf's [Intuitionistic Type Theory](https://en.wikipedia.org/wiki/Intuitionistic_type_theory), Girard's [System F](https://en.wikipedia.org/wiki/System_F), or Coquand's [Calculus of Constructions](https://en.wikipedia.org/wiki/Calculus_of_constructions). The standard library `Vector` type is an example of a dependent type.

```
Vector 𝛼 (n : ℕ) : [𝛼 n]
```

In the above type declaration, the type constructor `Vector` on the left side is parameterised with the type variable $𝛼$ for the element type and is indexed by the numeric value `n` for the size. Here, $𝛼$ is an unconstrained type parameter, and `n` is a value of the natural number type $ℕ$. The data constructor `[𝛼 n]` on the right side takes a concrete type and a size value. Invoking this data constructor creates a vector of size $n$. The $i$-th element of a vector `x` is written `x[i]`, where $i ∈ [0, n)$, and the type of that element is $𝛼$. Passing $0$ for `n` to the data constructor creates a size-$0$ (empty) vector `[]`.

Using the `Vector` dependent type, we can define a size-$3$ vector of $\mathbb{R}$-typed elements that are automatically initialised to $0.0$, like this.

```
x = [ℝ 3] ## elements automatically initialised to 0.0
```

We may declare a vector concatenation operator `+` as follows.

```
_+_ : [ℝ m] → [ℝ n] → [ℝ (m + n)]
```

The above dependently typed function declaration enables the compiler to make a guarantee that concatenating a vector of size $m$ and a vector of size $n$ yields a vector of size $m + n$​; the programme need not include runtime size checks.

We may define the `head` and `tail` vector functions as follows.

```
head : (n : ℕ+) ⇒ [𝛼 n] → 𝛼
  | x:_ → x

tail : [𝛼 n] → [𝛼 (n - 1)]
  | [] → []
  | _:xx → xx
```

In simply typed languages like ML, OCaml, or Haskell, the `head` function throws a $\bot$ at runtime, when passed an empty list `[]`. But in our dependently typed language, the type of `head` prevents the user from passing an empty vector `[]` during compilation. Let us see how this works.

In the definition of the vector type above, the index variable `n` is zero-based, because its type is natural number $\mathbb{N}$. But the double-arrow type constraint syntax `(n : ℕ+) ⇒` in the type expression of `head` locally alters the type of `n` to be non-zero natural number $\mathbb{N}^+$. As such, passing a zero-size vector to `head` is a type error, since that makes the size value $n = 0 ∉ \mathbb{N}^+$. Since the compiler has already guaranteed the argument vector `[𝛼 n]` passed to `head` is non-empty, `head` can safely extract the first element `x` from the argument vector without a runtime size check. This is an example of using dependent types to specify precisely the *precondition* of functions.

Similarly, the type of the `tail` function guarantees that if the argument vector is of size $n$, the result vector will be of size $n - 1$. This is an example of using dependent types to specify precisely the *postcondition* of functions.

There is a finer point about the way the standard library defines the primitive type $\mathbb{N}$ and its subtraction operator `-`. The definition of $\mathbb{N}$'s  `-` operator clamps the minimum result to $0$. Hence, $0 - k = 0$, by definition. That means applying `tail` to an empty vector `[]` type checks: the type of the argument vector is `[𝛼 0]` where $n = 0$, and the type of the result vector is also `[𝛼 0]` where $n - 1 = 0 - 1 = 0$ by the definition of the `-` operator.

Next, using the `Matrix` dependent type from the standard library, we can define a $2 \times 3$ matrix of $\mathbb{R}$-typed elements that are automatically initialised to $0.0$, as follows.

```
Matrix 𝛼 (m, n : ℕ) : [𝛼 m n]

y = [ℝ 2 3] ## elements automatically initialised to 0.0
```

The transpose `⊤` and the addition `+` matrix operators are declared this way.

```
_⊤ : [𝛼 m n] → [𝛼 n m]
_+_ : [𝛼 m n] → [𝛼 m n] → [𝛼 m n]
```

The compiler can verify that transposing a matrix `y` of size $m \times n$, as in `y⊤`, yields a matrix of size $n \times m$. And the compiler will ensure that the element types and the sizes of the argument matrices are matched for the matrix addition expression `y1 + y2`. But in languages with simple type systems, these verifications can only be performed by runtime size checks.

A dependent type system additionally provides advanced types that a simpler type system like the [Hindley-Milner](https://en.wikipedia.org/wiki/Hindley%E2%80%93Milner_type_system) cannot. A [dependent product type](https://en.wikipedia.org/wiki/Dependent_type#%CE%A0_type) (dependent function type) $\Pi$ corresponds to universal quantification $∀$ of predicate logic. A [dependent sum type](https://en.wikipedia.org/wiki/Dependent_type#%CE%A3_type) (dependent pair type) $\Sigma$ corresponds to existential quantification $∃$ of predicate logic. The $\Pi$ type is a function whose result type depends on (indexed by) the argument value: $f : (x : \alpha) \to \beta[x]$. The $\Sigma$ type is a pair whose right-element type depends on (indexed by) the left-element value: $((x : \alpha), \beta[x])$. These advanced types allow the programmer to state specifications with a high level of precision, and the type system automatically guarantees that the code that type checks meets these specifications.

Note that some types in Fortran have a tinge of dependent types. Its fixed-size arrays, for instance, can be seen as dependently typed. In the definition `real, dimension(3) :: x`, the variable `x` is a size-$3$ array that holds elements of type `real`.

The modern trend in programming languages is a gradual shift toward typefulness. Types are no longer simple classifications of values that prohibit mixing a value of one type with a value of another type; types are now deeply enmeshed with all aspects of programming: code completion, code refactoring, correctness verification, runtime safety, and performance optimisation. As such, we programmers must change our perspective about types: we must no longer view types as combative *guards* who restrain our freedom and diminish our productivity, but instead learn to depend on them as helpful *guides* who help us produce faster, safer, verified software that are easier to comprehend and to maintain.

***support algebraic data types***—We discussed above the record and the tuple product types and the enumeration sum type. Because the product type and the sum type can be interpreted as algebraic operations on types, they are called [algebraic data types](https://en.wikipedia.org/wiki/Algebraic_data_type) (ADTs).

***support pattern matching***—The term "pattern matching" in FP means using the structure of the ADTs to dissect (analyse ) a data structure into its constituent components. If we consider data structures to be "alive" at runtime, then runtime pattern matching is not a dissection, but a vivisection, of data.

Our new language should support structural pattern matching via the `case` control construct.

```
c : ℂ
...
case c
  | Rectangular {x, y} → ...
  | Polar {r, 𝜑} → ...
```

Another use of pattern matching is for record field extraction, as shown below.

```
c = Rectangular {x = 2.0, y = 3.0}
...
{x, y} = c ## c is destructured; x is bound to 2.0 and y to 3.0
```

Sometimes, it is convenient to be able to refer by name the whole of the pattern matched data structure. This is called the as-pattern, and we use the `@` symbol for it.

```
f (x:xs) @ v → ... ## whole vector v can be used in body of f
```

***support type classes, not classes***—Fortran is a scientific DSL, and dependent algebraic data types are more than adequate for modelling scientific data. As such, there is no need for Fortran to provide object modelling facilities. Instead of classes with fine-grained visibility modifiers, such as private, protected, and public, we rely on coarser but simpler alternative: modules containing selectively exported types and values. And instead of object inheritance, we support Haskell-style type classes.

A type class roughly corresponds to Java `interface`. It defines a collection of functions (behaviours) which can be reused (inherited) by making a type an instance of the desired type class. Below, we declare the `Show` type class whose primary behaviour is to convert a value of some type $\alpha$ to a Unicode string representation.

```
Show 𝛼 :: ## declare Show type class
  show : 𝛼 → 𝕌 ## declare show function
```

We now make the complex number type $\mathbb{C}$ an instance of the `Show` type class, and implement the `show` function that converts a complex value to a formatted string representation. This mechanism is conceptually similar to Java `implements`. Note the syntax: just as we use the single-colon syntax `value : Type` to assign a value to a type, we use the double-colon syntax `Type :: Class` to make a type an instance of a type class. This forms a type hierarchy: $value ∈ Type ∈ Class$.

```
ℂ :: Show ## make ℂ type an instance of Show type class
  show : ℂ → 𝕌 ## implement show function for complex type
    | Rectangular {x, y} → "Rectangular " + strOf(x) + "+𝒾" + strOf(y)
    | Polar {r, 𝜑} → "Polar " + strOf(r) + "∠" + strOf(𝜑)

log! : ℂ → IO ()
  | c → show c |> print! ## formatted complex value appears on the console
```

Note that Fortran supports polymorphism. Parametric polymorphism in Fortran is called *generics*. For example, using the `selected_real_kind()` procedure, the programmer may select the floating-point precision for a data structure or a procedure. Ad hoc polymorphism in Fortran is called *overloading*. It is comparable to C++ operator overloading. And with the addition of OO in the Fortran 2003 standard, it is now possible in Fortran to implement something akin to C++ *inheritance*, which is an OO way of implementing polymorphic sum type ADTs. Nevertheless, polymorphism was retrofitted into Fortran in a convoluted manner, making it rather clunky to use.

***remove mandatory explicit typing***—Just about every Fortran programmer today knows at least one other modern language, so they are no strangers to modern programming concepts and practices. Hence, there should be no philosophical objections against discarding explicit typing and adopting a strong, static, dependent type system that automatically infers types, thereby alleviating the burden of manual typing.

## *provide container types*

***containers***—From the very beginning, FP languages relied on sequences, represented with the list data structure. Indeed, LISP stands for "list processor". But FORTRAN has always relied on sequences, which it calls *arrays*. At the hardware level, an array is a contiguous sequence of memory cells. Array data structures are friendly to caches and vector processors. In scientific programming, almost all data are represented as sequences; complicated record hierarchies endemic to business computing are rare used, if at all, in scientific computing. Consequently, array processing is the central tenet of Fortran. Our new language, too, embraces sequence processing.

But unlike Fortran that uses arrays exclusively and unlike other FP languages that use lists exclusively, we use fixed-size vectors exclusively to represent sequences. Vectors naturally extend to matrices and tensors, and all three data structures are commonly used throughout scientific computing. Our sequence data structures are fixed size, per the FP ethos of immutability.

***vectors***—A vector is a fixed-size 1D sequence of values. The `Vector` dependent type is defined in the standard library. It is parameterised with a type variable $𝛼$ and it is indexed with size `n`. A zero-sized vector is written as `[]`, similar to the empty list in other FP languages. And in keeping with the FP tradition, we add elements to the head of the vector with the syntax `x:xx`, where `x` is the new element and the `xx` is the existing vector of the same element type.

```
Vector 𝛼 (n : ℕ) : [𝛼 n]
𝕍 : Vector
```

The following is the literal syntax for creating a vector. The type system infers the type of the variable `x` to be `[ℝ 3]` or `𝕍 ℝ 3`, a $1 \times 3$ row vector of $\mathbb{R}$-typed elements. Note that a 1D sequence is viewed as a column vector in mathematics, but modern programming languages treat such a sequence as a row vector.

```
e0, e1, e2 : ℝ
...
x = [e0, e1, e2]
```

We may declare `inner` and `outer` vector product functions like this. Both functions take as arguments two size-$n$ vectors of $\alpha$-typed elements. The result of `inner` is a scalar of type $𝛼$, and the result of `outer` is an $n \times n$ matrix of $\alpha$-typed elements.

```
inner : (𝛼 : Num) ⇒ [𝛼 n] → [𝛼 n] → 𝛼
outer : (𝛼 : Num) ⇒ [𝛼 n] → [𝛼 n] → [𝛼 n n]
```

Note the type constraint `(𝛼 : Num) ⇒`. The the declaration of the `Vector` type, the type parameter $\alpha$ is unconstrained. But in these functions, $\alpha$ is constrained to be a type in the `Num` class. Since the type parameter $𝛼$ is unconstrained in the vector data constructor `[𝛼 n]`, it is possible to create a vector of non-numeric elements. But the compiler will raise a type error, when the user attempts to pass a non-numeric vector to `inner` or `outer`, which expects the argument to be vectors of numeric elements.

Array processing languages, like Fortran, APL, and Matlab support convenient syntax for accessing ranges and elements. Python, Julia, Mojo, and other modern languages have adopted this array access syntax. So do we. Our 1D sequence access syntax is shown below.

```
x[i] ## ith vector element where n is size of x and i ≤ n-1
x[-i] ## (n-1-i)th vector element where i ≤ n-1
x[ia..ib] ## subvector of elements from x[ia] to x[ib]
x[i..] ## subvector of elements from x[i] to the last
x[..i] ## subvector of elements from x[0] to x[i]
```

***matrices***—A matrix is a fixed-size 2D grid of values.

```
Matrix 𝛼 (m, n : ℕ) : [𝛼 m n]
𝕄 : Matrix
```

The literal syntax for a matrix extends the vector literal syntax. For real-valued elements, the inferred type of the variable `y` in the example below is `[ℝ 2 3]` or `𝕄 ℝ 2 3`, a $2 \times 3$ matrix of $\mathbb{R}$-typed elements.

```
y = [ [e00, e01, e02] ## vector [e00 .. e02]
    , [e10, e11, e12] ] ## matrix [e00 .. e12]
```

Our 2D sequence access syntax is as follows.

```
y[i, *] ## ith row vector where m is row-size of y and i ≤ m-1
y[-i, *] ## (m-1-i)th row vector where i ≤ m-1
y[ia..ib, *] ## submatrix of elements from y[ia, *] to y[ib, *]
y[*, j] ## jth column vector
y[*, -j] ## (n-1-j)th column vector
y[*, ja..jb] ## submatrix of elements from y[*, ja] to y[*, jb]
y[i, j] ## matrix element
y[-i, -j] ## matrix element
```

***tensors***—A tensor is a fixed-size, multi-dimensional sequence of values. A 3D cube tensor is defined thus.

```
Tensor3 𝛼 (l, m, n : ℕ) : [𝛼 l m n]
𝕋3 : Tensor3
```

A 3D tensor literal can be defined as follows. The inferred type of the variable `z` is `[ℝ 3 3 3]` or `𝕋3 ℝ 3 3 3`, a $3 \times 3 \times 3$ tensor of $\mathbb{R}$-typed elements.

```
z = [ [ [e00, e01, e02]
      , [e10, e11, e12]
      , [e20, e21, e22] ]
    , [ [f00, f01, f02] ## 1x3 vector [f00 .. f02]
      , [f10, f11, f12]
      , [f20, f21, f22] ] ## 3x3 matrix [f00 .. f22]
    , [ [g00, g01, g02]
      , [g10, g11, g12]
      , [g20, g21, g22] ] ] ## 3x3x3 tensor [e00 .. g22]
```

An element of a 3D tensor is accessed as follows. Because the tensor access syntax is just a natural extension of the matrix access syntax, it need not be further elaborated.

```
z[2, 1, 0] ## element g10
```

It is important to note that we are using the comma-separated  `[..., ...]` syntax in two distinct senses: sequence literal constructor and sequence element accessor. In the constructor sense, we use the symbols `[` and `]` to delimit the dimensions and the symbol `,` to separate the dimensions as well as the elements within each dimension. In the accessor sense, we use the symbols `[` and `]` to group the dimensional indices and the symbol `,` to separate the dimensional indices. Our syntax is less noisy and more legible than C's `z[2][1][0]` syntax. Recall that, in contrast to Fortran, we follow the row-major element order, which is employed by all popular languages, today.

The sequence syntax extends to higher dimensions. For example, a 6D tensor is defined as follows.

```
Tensor6 𝛼 (i, j, k, l, m, n : ℕ) : [𝛼 i j k l m n]
𝕋6 : Tensor6
```

***tuples***—A tuple is an unnamed product type that holds ordered, unlabelled fields of varying types. For example, a duple type is `(𝛼, 𝛽)` and a triple type is `(𝛼, 𝛽, 𝛾)`.

A musical note can be represented with a tuple literal as follows. The first element is the name of the note (`"C4"` for middle C), the second is the frequency ($261.624$ Hz), and the third is the MIDI number ($60$).

```
Note : (𝕌, ℝ, ℕ) ## musical note; name, freq, MIDI
...
c4 = ("C4", 261.624, 60) ## middle C
...
freq = c4(1) ## 261.624 Hz
...
(name, freq, midi) = c4 ## name="C4", freq=261.624, midi=60
```

Tuples are a convenient way to pack a few pieces of data into a small bundle. For instance, a tuple can be used to return multiple values from a function. In mathematics and in FP, functions can return only one value, so to return multiple results, we must bundle those disparate values into a tuple. But trying to squeeze tens of values into a tuple is tickling danger. In such a case, a record is the better type to use.

***records***—A record is a named product type that holds unordered, labelled fields of varying types. The `Rectangular` and the `Polar` product types defined above are examples of records. The fields of a record are accessed using the `.` operator, as in `p.𝜑`. A new record can be created from an existing one using the record update syntax `{... | ...}`.

```
c = Rectangular {x = 2.0, y = 3.0} ## c is 2.0+𝒾3.0 of type ℂ
...
c' = {c | y = -c.y} ## c' is complex conjugate is 2.0-𝒾3.0
```

***enumerations***—An enumeration (disjoint union) is a named sum type. For example, the boolean $\mathbb{B}$ type is a sum type with nullary data constructors `True` and `False`: `𝔹 : False | True`. On the other hand, the complex $\mathbb{C}$ type is a sum type with data constructors `Rectangular` and `Polar`, each taking a record product type: `ℂ : Rectangular{x,y:ℝ} | Polar{r,𝜑:ℝ}`. More precisely, $\mathbb{C}$ is a sum-of-products type. Enumerations are frequently used in conjunction with records to form sum-of-product types. The data elements of an enumeration are accessed by pattern matching.

```
case b
  | False → ...
  | True → ...
```

***hashes***—A hash is a collection of pairs. Each such pair comprises a value `v` associated with a unique key `k`: `<k:𝛼 # v:𝛽>`. Here, the key type is $𝛼$ and the value type is $𝛽$. The symbol `#` separates the key and its value. The elements of a hash are accessed by key indexing, as in `h<k>` for the value associated with the key `k`, or by pattern matching, as in `x#xx = h` with `x` bound to the first key-value pair in `h` and the rest of the collection bound to `xx`.

## *leverage modules*

***hold one module per file***—A module is a container of closely related types and values. Every cohesive unit of code is a module. Many modern languages allow the programmer to define multiple modules in one file. This could be convenient when implementing large, complex business data structures built out of many substructures. But scientific data are far simpler. As such, a straightforward one module per file approach is used for our new language. For added simplicity, the name of the module is the same as the name of the containing file. Recall the naming conventions defined earlier.

***support abstract data types***—An [abstract data type](https://en.wikipedia.org/wiki/Abstract_data_type) (also confusingly called "ADT", but is a wholly distinct concept from algebraic data types) is a data structure whose international representation is hidden and can be manipulated only through a collection of published interface functions. An abstract data type is implemented using the module construct.

The PP module-based abstraction mechanism was the precursor to the OO class-based abstraction mechanism. As IT grew rapidly in the 1980s, the complexity of business applications began to eclipse the abstraction powers of abstract data types, and classes became the standard abstraction mechanism in enterprise software development. But scientific applications have far humbler abstraction needs, and module-based abstract data types are well matched for those simpler needs.

***use implicit export***—In most modern programming languages, the declarations and definitions contained in a module are hidden by default, and the programmer must manually mark the specific items he wishes to export. The alternative, of course, is to export by default.

In imperative PP languages, this hide-by-default behaviour is safer than the export-by-default behaviour, because it prevents users of the module from directly mutating the internal data representations of the abstract data type. But in declarative FP languages, data structures are not only simpler, they are also immutable. Immutability obviates the need obsessively to hide the representations of data structures. Hence, in the new language, we shall employ the implicit export behaviour, so as to minimise cluttering the code with `export` markers sprinkled throughout the module. If a particular declaration or definition must be hidden, we explicitly mark it with the `--` symbol, as shown below.

```
#< Distance.f
This module implements distance measures. #>

-- 𝛿 = 0.0001 ## a module-internal constant

## check if a and b are near each other
near? : ℝ → ℝ → 𝔹
  | a b → |b - a| < 𝛿
_≈_ : `near?`
```

The code above is contained in the file `Distance.f`, and the associated module is automatically given the name `Distance`. Hence, there is no `module ModuleName` construct in our language; it is unnecessary. The constant $\delta$ is defined for use by the module implementer but it is hidden from the module users, since it is marked with the `--` symbol. But the export-by-default behaviour of modules makes available to the users the predicate function `near?`, which checks if the absolute distance between the measures `a` and `b` is less than $\delta$, and hence the two measures are deemed to be near each other. The mixfix operator `_≈_` is aliased to the back-quoted version of `near?`. In Haskell, a binary function `f a b` can be converted to an infix operator by back-quoting.

```
f a b → ...
...
m `f` n ## same as f m n
```

The `Distance` module is used from the main module as follows.

```
#< Main.f #>

use Distance

main! : () → IO ()
  | () → if a ≈ b then "near" else "far "| print!
         where a = -3.2; b = 6.8
```

The `use` construct imports all non-hidden declarations and definitions from the designated module into the current module. But this could cause name collisions. So, the as-module construct can be used to give a name to the imported module. Here, again, we use the `@` symbol. If a module is imported using the as-module construct, we must use the `.` operator to access its contents.

```
use Distance @ D
...
if D.near? a b then ... else ...
```

## *promote parallelism*

***hardware***—Over the past 70 years, countless varieties of parallel processing hardware had been designed and equally many parallel programming models targeting these machines had been created. Most of these parallel programming models were incorporated into sequential programming languages. The reason is that although parallelism is innate to nature, it is unnatural to computing. It turns out that parallel computing is a notoriously difficult, both hardware and software. So, despite all the technical advances over the years, much of modern computing is still based on the original sequential processing template from 1945, the [von Neumann architecture](https://en.wikipedia.org/wiki/Von_Neumann_architecture).

Since the birth of modern digital computers in the 1950s, CPU designers have managed to extract more and more performance out of the sequential architecture by integrating increasing number of gates on the chip and by cranking up the clock speed. For decades, gate count kept increasing as predicted by [Moore's law](https://en.wikipedia.org/wiki/Moore's_law) (which states that transistor count doubles every two years), and clock speed kept rising in accordance with [Dennard scaling](https://en.wikipedia.org/wiki/Dennard_scaling) (which states that the power consumption of the transistor decreases in proportion to its on-chip area). Eventually, physics crashed the party: Dennard scaling ended in the 2000s, and Moore's law faded in the 2010s. In order to create for the consumers the appearance of continually increasing capabilities, chip manufacturers started to cram in more and more cores onto a single chip.

The multicore approach is simpler and cheaper than other advanced techniques. For instance, stacking silicon wafers (thereby turning a traditional 2D chip into a 3D chip) dramatically increases the gate density of CPUs, but it also creates a host of other problems, including heat dissipation. As such, unless physicists and engineers dream up an entirely new set of design and manufacturing techniques, the multicore CPU shall remain the workhorse of consumer-grade parallel processing, in the foreseeable future. [Flynn's taxonomy](https://en.wikipedia.org/wiki/Flynn%27s_taxonomy) classifies parallel processing architectures as follows:

- SISD—single instruction, single data
  -  [Single-core processors](https://en.wikipedia.org/wiki/Single-core) on which one instruction operates on one data element
- SIMD—single instruction, multiple data
  - [Pipelined processors](https://en.wikipedia.org/wiki/Instruction_pipelining) and [vector processors](https://en.wikipedia.org/wiki/Vector_processor) on which a single instruction is executed against multiple data elements on separate processing elements within one processor
- MISD—multiple instruction, single data
  - Independent processors process a single stream of data and vote on the result; used in safety-critical, real-time control systems, like the Space Shuttle [Primary Avionics Software System](https://ntrs.nasa.gov/api/citations/20110014946/downloads/20110014946.pdf) (PASS)
- MIMD—multiple instruction, multiple data
  - [Multicore processors](https://en.wikipedia.org/wiki/multicore_processor) and [distributed computers](https://en.wikipedia.org/wiki/Distributed_computing) that perform parallel processing at multiple levels (instruction level, thread level, or process level) on multiple processing resources (multiple cores on a processor, multiple processors on a machine, or multiple machines in a network)

***software***—Traditionally, parallel processing was the domain of supercomputers, and parallel programming was the province of specialist programmers with PhDs in science or engineering. These programmers used parallel programming extensions baked into custom compilers made by the supercomputer manufacturers. But with the recent advent of cheap multicore CPUs brought parallel processing down to consumer-grade computers, such as desktops, laptops, tablets, phones, and even single-board computers. That means parallel programming is no longer a rarified task for a few specialists, but a workaday task for all programmers. As such, programming language designers should incorporate parallel programming facilities into the languages in ways that are intuitive and simple to use.

Parallel programming can be summarised as the programmer-visible aspects of parallel processing. Today, compilers are sophisticated enough to automate SIMD type instruction-level parallelism, so modern parallel programmers focus on MIMD type application-level parallelism. And the essence of MIMD is to coordinate data distribution and control coordination via some communication mechanism. [Parallel programming models](https://en.wikipedia.org/wiki/Parallel_programming_model) are classified as follows:

- CPP—centralised parallel processing with shared memory
  - Under the *shared memory* model, several programmes running on a *single computer* collaborate (that is, communicate and coordinate) via a designated area of the memory address space managed by the OS. The shared memory model is a form of *centralised* parallel processing.
  - Traditional [Unix processes](https://en.wikipedia.org/wiki/Process_(computing)) concurrently execute on a conventional single-core processor. In the late 1960s, the concept of processes emerged as a way to provide the interactive computing alternative to the then-prevalent batch computing. The process system call interface provides a coarse-grained control over parallelism. Because this approach is very simple and natural for programmers to use, it is still quite popular today.
  - Then, [POSIX Threads](https://en.wikipedia.org/wiki/Pthreads) standard came out in 1995, as a way to unify the different threading approaches being promoted by various computer manufacturers. Threads are independent execution paths that run within the address space of a single process. The threading library provides a fine-grained control over parallelism, but it places the burden on the programmer to ensure a correct collaboration amongst the threads.
  - The open multi-processing [OpenMP](https://en.wikipedia.org/wiki/OpenMP) standard was published in 1997. It is a multithreading facility that provides higher-level parallel processing abstractions and more advanced collaboration mechanisms than POSIX Threads, and it implements these facility using a combination of compiler pragmas and library calls. OpenMP is as complicated to use as it is powerful. And it tends to produce ugly code littered with pragma markups.
  - Threaded shared memory parallel programming facilities emerged in the mid 1990s. This was also the time when consumer-grade, shared-memory, multiprocessor machines first appeared on the market.
- DPP—distributed parallel processing via message passing
  - Initially, the *message passing* model was intended to enable multiple programmes running on *different computers* (mostly single-core machines, then) to collaborate by passing message over the network. This is called *distributed* parallel computing, a coarse-grained, application-level MIMD.
  - When multicore computers became commonplace, message passing became the dominant model of parallel processing, because the same code that performs distributed parallel processing on networked machines runs on a single multicore computer, with little or no modifications. The current trend is to use message passing and shared memory approaches together on one large multicore, multiprocessor machine. This coarse-grained distributed parallelism provides a good balance between capability and complexity.
  - The message passing interface ([MPI](https://en.wikipedia.org/wiki/Message_Passing_Interface)) is the best known facility for distributed parallel computing. When it was published in 1991, the MPI standard was intended to be the communication and coordination substrate for compilers targeting distributed parallel hardware. But given the slow pace of compiler develop in those days, programmers started using the library directly in their application code, and this practice is now the norm.
  - The synchronously communicating sequential processes ([CSP](https://en.wikipedia.org/wiki/Communicating_sequential_processes)) employed by Go and the asynchronously communicating [actor model](https://en.wikipedia.org/wiki/Actor_model) used by Lisp are also quite popular in their respective communities. But these facilities are use primarily on a single multicore computer, relying on the shared memory as the collaboration mechanism. Nevertheless, this form of computing qualifies as distributed parallel processing, since the collaborating programmes run on different cores within the same computer.
- SPMD—single programme, multiple data
  - Under the [SPMD](https://en.wikipedia.org/wiki/Single_program,_multiple_data) model, the same programme runs on multiple cores. When the cores are on the same multicore computer, the collaboration mechanism is typically shared memory. And when the cores are on different computers, the collaboration mechanism is typically message passing. A single piece of code manages data distribution and control coordination across multiple cores by cueing off core IDs. SPMD, as a concept, emerged in 1983, at the dawn of networked [workstations](https://en.wikipedia.org/wiki/Workstation)—single-core machines, but were quite capable for the time. This was the birth of distributed parallel processing.
  - Note that MPI is often used as the collaboration substrate for a network-distributed form of SPMD. In that case, the same programme is distributed to different machines on the network. On the other hand, when MPI is used in the MIMD-style distributed sense, different programmes, each specialising on one task, are involved.
  - Partitioned global address space ([PGAS](https://en.wikipedia.org/wiki/Partitioned_global_address_space)), as the name suggests, employs a shared, global address space across different cores, with each core being assigned a partition of the address space. So, PGAS is a *hybrid* of the centralised (shared memory) and the distributed (message passing) forms of parallel computing. That is, the PGAS abstraction works uniformly regardless of whether the underlying computing infrastructure is one multicore processor, one multiprocessor computer, many distributed computers, or a mixture thereof. And PGAS is SPMD in the sense that a single programme runs on multiple cores.
  - The [Coarray Fortran](https://en.wikipedia.org/wiki/Coarray_Fortran), [Unified Parallel C](https://en.wikipedia.org/wiki/Unified_Parallel_C), [SHMEM](https://en.wikipedia.org/wiki/SHMEM) (not the same as the system-level shared memory facility described above), and many other approaches for many different languages exist. Of those, Coarray Fortran (CAF) seems the most mature and the best put-together.
- FAP—fully automatic parallelisation by the compiler
  - In computing, processor architecture and compiler design progress in lockstep, mutually propelling each other forward and the same practitioners working in both fields. Together, these two fields have reached a point where the compiler can analyse a small piece of sequential code and automatically generate a parallel executing code, in some circumstances. But the compiler's ability automatically to parallelise the whole programme is very limited, given the data dependencies and other hurdles prevalent in all large programmes.
  - For about 50 years now, the FP community has recognised the importance of pure functions in parallelising code. But even the sophisticated compilers of powerful, established FP languages, like ML, Haskell, and OCaml, have not been successful in automatically extracting full parallelism from the sequential code. The rapid pace of hardware development also makes this task much more difficult. Hence, the parallel processing facilities in these FP languages still require programmers to use language features (types, monads, pragmas, etc.) to aid the compilers parallelise the code. Nevertheless, this is a hot, fertile research area.

There are about as many parallel programming models as there are parallel processing architectures. But above, we grouped the parallel programming concepts into broad categories: CPP, DPP, and SPMD. It is evident, however, that there are no distinct boundaries among these models, especially when diving down to low levels of implementation details. In due course, PGAS and MPI have emerged as the favourites among programmers, since they both support centralised and distributed forms of parallelism and both offer significant capability with appreciable simplicity. MPI's advantage over PGAS is that, as an external library, it can be used with any existing sequential programming language. And PGAS's advantage over MPI is that by integrating parallel programming constructs directly into the programming language syntax, it offers a more natural way to do parallel programming. In that sense, PGAS is arguably the most elegant and the most programmer-friendly approach to parallel programming. So, we shall incorporate the CAF-style coarray variant of SPMD in our new syntax.

***coarrays***—In programming, aesthetics matter, perhaps not as much as correctness, but about as much as performance. The design of the [coarray](https://en.wikipedia.org/wiki/Coarray_Fortran) parallel programming facility is imbued with elegance, pragmatism, and efficiency. It was created by CRAY's Fortran compiler team, [Numrich](https://dl.acm.org/profile/81337492153) et al., in the early 1990s, and was incorporated into the Fortran 2008 standard. The key feature of coarray design is to provide an array-centric parallel programming constructs that are tightly integrated into the syntax of Fortran, an array programming language. In other words, coarray is a natural extension of the sequential array processing syntax of Fortran with parallel array processing semantics. In classic Fortran, arrays are accessed as `a(i)`, where `a` is a 1D array indexed by an integer `i`. In CAF, this array access syntax is extended with `a(i)[p]`, where the `[p]` references a copy of the array element `a(i)` in the programme that is running on the $p$th core. The coarray syntax generalises naturally to scalar values as well as multi-dimensional arrays. For instance, `s[p]` is the value of the scalar variable `s` in the programme running on the $p$th core, and `m(i, j)[p]` is the value of the matrix element `m(i, j)` in the programme run by the $p$th core. The syntax also allows the cores to be arranged in multiple dimensions. Hence, `s[p, q]`refers to the value of the scalar `s` in the programme running on the core $(p, q)$ in a 2D grid of cores. CAF also provides built-in facilities for data distribution and control coordination, like `sync all` and `sync p`.

In our new language, we use the `@[p]` syntax to index processor cores.

```
c@[p] ## scalar variable c in programme running on core p
x[i]@[p] ## ith element of vector x on core p
x[*]@[*] ## the vector x on all cores
x[i]@[p, q] ## ith element of vector x on core (p, q) in grid of cores
c@[p, *] ## scalar variable c on row p of cores in grid of cores
c@[*, q] ## scalar variable c on column q of cores in grid of cores
```

Our version of the coarray syntax is compact and natural. Python-style indexing also works for all primitive and structured data types distributed across the cores: scalars, vectors, matrices, tensors, tuples, records, enumerations, and such.

Remote data can be received into a local variable using the left double-arrow operator `⇐`. Note that `c[*]` refers to all the copies of the scalar variable ` c` on all the processors. When used without the coarray index, as in `c`, it refers to its local value.

```
c ⇐ c@[p] ## retrieve the scalar value c from core p
```

Local data can be sent to a remote variable using the right double-arrow operator `⇒`.

```
c ⇒ c@[*] ## distribute the local scalar value c to all other cores
```

Control coordination is performed by the `sync` construct.

```
sync@[*] ## synchronise all cores running programmes
sync@[p] ## synchronise local core with remote core p
sync@[p..q] ## synchronise local core with remote cores in range p..q
```

Do note that the coarray facility can be transparently extended to support GPUs and TPUs. The compiler can be instructed to target those coprocessors by automatically generating coprocessor-specific instructions.

## *value verification*

***formal proofs***—In mathematics, the term "formal proof" does not mean a proof written in stodgy King's English by a tuxedo-clad mathematician; it means a fully worked out proof that does not skip any steps. Formal proofs are tedious and error prone for humans, but computers can easily verify large formal proofs. For this reason, computer scientists have obsessed over formalising mathematics, since the birth of high-level programming languages. Indeed, the creation of LISP was, in part, motivated by the desire to automate formal, mathematical proofs. But fully automated proofs are but the stuff of dreams, for now. So, proof assistants were created as a practical alternative. Proof assistants provide the means to automate the tedious, mechanical aspects of proof writing and rely on human intuition and creativity to guide the partially automated proof towards its goal. Proof assistants, like Coq, Lean, Agda, Idris, etc., are also dependently typed functional programming languages, thanks to [Curry-Howard correspondence](https://en.wikipedia.org/wiki/Curry%E2%80%93Howard_correspondence) between logic and computing: propositions are types and proofs are values of those types. For a more details discussion of this important idea, see the *ML concepts* section of my article [*Programming Paradigms*](./Paradigms.md).

Our new, dependently typed Fortran, too, is a programming language and a proof assistant. That means we can write both the algorithm and the formal proof that verifies its correctness in the same piece of code. There are two kinds of formal verifications: internal and external. In internal verification, the proof is built into the code that implements the algorithm, whereas in external verification, a separate proof code accompanies the algorithm implementation.

The vector `head` function mentioned above is an example of internal verification. The type `(n : ℕ+) ⇒ [𝛼 n] → 𝛼` encodes the specification that `head` does not accept zero-length vectors.

```
head : (n : ℕ+) ⇒ [𝛼 n] → 𝛼
  | x:_ → x
```

And the following is an example of external verification. The numeric `+` operators computes the addition of numbers. The proof of associativity, `+assoc◻`, and proofs of other properties accompany the implementation of `+` in the standard library. The symbol $\square$ at the end of the proof name is mandatory. If the programmer neglects to append this symbol to the proof name, the compiler will. It stands for "quod erat demonstrandum" ([QED](https://en.wikipedia.org/wiki/Q.E.D.)), which appears at the end of a proof in mathematics. The symbol $\forall$ means "for all", as usual. The symbol $\equiv$ stands for [propositional equality](https://en.wikipedia.org/wiki/Type_theory#Equality_types) in type theory.

```
_+_ : (𝛼 : Num) ⇒ 𝛼 → 𝛼 → 𝛼
  | ...
+assoc◻ → ∀ (x, y, z : ℕ) → x + (y + z) ≡ (x + y) + z
```

Using dependent types, it is possible to express programme specifications with a very high degree of precision. This, then, is the foundation upon which verified software can be built. But both the type theory and software verification are broad, deep subjects well outside the bounds of this short article on Fortran modernisation. See the end of this article for some references on these subjects.

# CONCLUSION

The [Jaguar D-Type](https://en.wikipedia.org/wiki/Jaguar_D-Type) won the [1957 24 Hour of Le Mans](https://en.wikipedia.org/wiki/1957_24_Hours_of_Le_Mans) race. The D-Type was at the pinnacle of motorsport in 1957, the year FORTRAN was born. But no racing team would enter this car in a modern Le Mans race. Jaguar surely could build another Le Mans winning prototype race car today, complete with a diesel-electric hybrid engine, CFD-simulated sculpted aerodynamic surfaces, multiple embedded computers connected via a [CAN bus](https://en.wikipedia.org/wiki/CAN_bus), and tonnes of other fancy technologies. But they would not reuse the D-Type chassis; they would instead design a modern carbon fibre [monocoque chassis](https://en.wikipedia.org/wiki/Monocoque) upon which to build the new car. Maintainers of modern Fortran should have follow this common engineering practice of keeping up with technological progress. Instead, their design decisions are analogous to building a new Le Mans race car with hyper-modern components haphazardly bolted onto the old D-Type chassis. At some point, the old design, no matter how illustrious it once was, must be replaced with a wholly new design that reflects modern thinking.

Fortran is indispensable, and there are no viable contenders, at present, who could usurp its parallel processing throne. Fortran was born several years before I was, and it will surely out live me by several decades. Still, there is no denying that Fortran suffers from the image problem among the younger set whose opinion of Fortran is that it is 70 years old, it is rotten, it has no future. And while it maybe unkind, it is not untrue to say that Fortran standard is stuck in the 1980s concepts and Fortran codebase is stuck in the 1970s practices. As such, no sensible young programmer would willingly learn Fortran today, let alone devote his career to wrangling FORTRAN 1977 code.

Clearly, the most practical remedy to Fortran's image problem is the multi-pronged, parallel approach: simultaneously embrace Fortran in both academia and industry and rejuvenate its image, encourage the design of new parallel programming languages that seamlessly interoperate with Fortran, and rescue Fortran from its mid 20th Century cage by modernising it syntactically and semantically. This approach gives the organisations the freedom to continue using traditional Fortran, transition to the modernised Fortran syntax, or target Fortran using new languages that interoperate with it, all without incurring undue risks and without being harried by the sense of impending doom.

Permit me to recapitulate. Fortran is here to say; there is no better DSL for parallel, high-performance, scientific computing. But Fortran cannot rest upon its laurels, counting on the fact that it still works exactly as it was originally designed nearly 70 years. A language's maturity and stability are necessary, but not sufficient; modernity and appeal are just as important for it to survive and thrive.

## *references*

### FORTRAN

- *[Modern Fortran Explained](https://www.amazon.com/Modern-Fortran-Explained-Incorporating-Mathematics/dp/0198876580/ref=sr_1_fkmr0_1?crid=1DEXYAH8TUOGA&dib=eyJ2IjoiMSJ9.6a3Rwxif2LMU3_e-R0D5tngh9ETcM1pW1zbc4F7IvSVkNe5mMXi-NElPr9KtoJx4.4Hm8yGghlRypFn3sxYpE8EYglXf797xYn8VO5m0NeGU&dib_tag=se&keywords=metcalfe+fortran&qid=1712266956&sprefix=metcalf+fortran%2Caps%2C58&sr=8-1-fkmr0)*, Metcalf
- *[Parallel Programming with Coarrays](https://www.amazon.com/Parallel-Programming-Co-arrays-Chapman-Computational-ebook/dp/B07HGGK9XS/ref=sr_1_5?crid=29Z4WY15VFASS&dib=eyJ2IjoiMSJ9.83EdggKMXCDCxiuB7OPMzZonPk7FyDhusQSSmK-7N1aHKNF3ptKcEaKWD-81Yp1Td3PqoXjd1gvOEmrl8QqUqRqZXpfLdUfZVPJMNWO9B5YRDfEvXGEGuuvc8R2hN3oSs-A1RI-IV6poyZ6B8AIxAOaXAqN7enIh27jJvI2lP-JgOecGyEQhGK3topBbgtaD.88ht4QQGAvwFIqpvScb9g4CQ_PTX3Fz3RGUUtEcbQ74&dib_tag=se&keywords=Coarray+Fortran+for+Parallel+Programming&qid=1712266905&sprefix=%2Caps%2C60&sr=8-5)*, Numrich
- *[Modern Fortran: Building Efficient Parallel Applications](https://www.amazon.com/Modern-Fortran-Building-Efficient-Applications/dp/1617295280/ref=sr_1_1?crid=2PABKLJAG0NB3&dib=eyJ2IjoiMSJ9.ZZ8Gi0ZQRNtvol7rlw6YbCBTHNYKtWXlqB3wFBScWGtTBuJlkBYbCnpnv-5oGyLTCKbNCVdPx80lxu8vWQUWFWsvg2cAZRItnkjgKWGMC4D3p6V0tKMRIug2sugkMkS4LmuCCXeFryJhVhiQGuqIGogfHd4YWE4qKsCWgfTz_YH2vNH6ROHIbNz3Z7PgOgpb8hSWwjVm5ny-CDwR1CiGfuzKnUl7F9NeMqxXZQRcPA4.hbtwTWli6jfDhut3EphTaW68y_XuZjeNfpDYcQry5Fw&dib_tag=se&keywords=Modern+Fortran%3A+Building+Efficient+Parallel+Applications&qid=1712267035&sprefix=modern+fortran+building+efficient+parallel+applications%2Caps%2C61&sr=8-1)*, Curcic

## PROOF ASSISTANTS

- Agda
  - *[Agda User Manual](https://my-agda.readthedocs.io/_/downloads/en/latest/pdf/)*, Agda Team
  - *[Dependently Typed Programming in Agda](https://www.cse.chalmers.se/~ulfn/papers/afp08/tutorial.pdf)*, Norell
  - *[Verified Functional Programming in Agda](https://www.amazon.com/Verified-Functional-Programming-Agda-Books/dp/1970001240)*, Stump
- Idris
  - *[Idris 2 Documentation](https://idris2.readthedocs.io/en/latest/)*, Idris Team
  - *[Type-Driven Development with Idris](https://www.amazon.com/Type-driven-Development-Idris-Edwin-Brady/dp/1617293024/ref=sr_1_1?crid=19GOORD0L4Y5H&dib=eyJ2IjoiMSJ9.T7dj4Z08iIESjdfzWqIVoivGwZI4-RKyBbc6Wv51fug.oVzgB3C9tubrP6iIdZEHV-ajicwou-PY2My-yq2gL4E&dib_tag=se&keywords=Type-Driven+Development+with+Idris&qid=1712267255&s=books&sprefix=type-driven+development+with+idris%2Cstripbooks%2C45&sr=1-1)*, Brady
  - *[Type-Driven Development of Concurrent Communicating Systems](https://www.type-driven.org.uk/edwinb/papers/tdd-conc.pdf)*, Brady
- Coq
  - *[The Coq Reference Manual](https://coq.inria.fr/doc/V8.19.0/refman/)*, Coq Team
  - *[Certified Programming with Dependent Types](https://www.amazon.com/gp/product/0262026651/ref=as_li_tf_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=0262026651&linkCode=as2&tag=adamchli-20)*, Chlipala
  - *[Verified Software Toolchain](https://vst.cs.princeton.edu/)*, Appel
- Lean
  - *[The Lean 4 Theorem Prover and Programming Language](https://lean-lang.org/papers/lean4.pdf)*, de Moura
  - *[Programming in Lean](https://avigad.github.io/programming_in_lean/programming_in_lean.pdf)*, Avigad
  - *[Theorem Proving in Lean](https://leanprover.github.io/theorem_proving_in_lean/theorem_proving_in_lean.pdf)*, Avigad

### TYPE THEORY

- *[Basic Simple Type Theory](https://www.amazon.com/Simple-Cambridge-Theoretical-Computer-Science/dp/0521054222)*, Hindley
- *[A Theory of Type Polymorphism in Programming](https://courses.engr.illinois.edu/cs421/sp2013/project/milner-polymorphism.pdf)*, Milner
- *[Programming in Martin-Löf ’s Type Theory](https://www.cse.chalmers.se/research/group/logic/book/book.pdf)*, Nordstrom
