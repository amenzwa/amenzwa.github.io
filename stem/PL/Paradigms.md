---
title: "Programming Paradigms"
tags:
  - mathjax
use_math: true
---

[TOC]

# INTRODUCTION

To be an efficient programmer, one must master the art of software design and the science of computing (CS). To be an effective thinker, he must learn multiple programming languages from different programming paradigms. In the article *[Programming Languages](ProgrammingLanguages.md)*, I described the different programming paradigms and enumerated a representative list of languages to learn within each paradigm. That article gave a broad overview of programming languages that are currently popular in the IT industry. In this article, I show a way to go beyond merely knowing a few programming languages to mastering various programming paradigms. My goal is to provide programmers with the rudiments of programming paradigms so as to enable them to learn any new programming language.

Note that this article is about exploring, learning, and mastering various programming paradigms. It is a study guide, a roadmap as it were, to learning various programming paradigms, not a tutorial on particular programming languages. Being that this is a high-level, conceptual presentation of programming paradigms, code examples are used sparingly, only where a specific syntax promotes presentation clarity. The reader is expected to study the cited source materials for details of the languages and the paradigms. To put it another way, this guide is written for advanced programmers who wish to expand their theoretical, paradigmatic knowledge and practical, programming skills, in order to bolster their software development careers; it is not written for novices who are merely seeking to learn a language in order to secure a programming job.

The secondary audience is CS students who are interested in programming language design. All CS undergraduates are introduced to multiple programming paradigms. This article provides self-study tips to these students on how to go beyond the introductions and master the programming paradigms.

There are many programming languages in popular use, and there are equally many ways to learn these languages. But knowing a language does not make one an expert in the paradigm. Indeed, there is but one way to master a programming paradigm: by repeatedly using the design idioms of the paradigm and by writing many programmes in a canonical language of that paradigm.

A novice programmer learns his first programming language this way:

- Study the language manual written by the language designer, focusing on the syntax
- Implement small programmes in the end-of-chapter exercises that were assigned by the professor

The goal of a novice, at this early stage, is to learn how to use the language, especially the syntactic elements of the language. This practical knowhow, alone, will not make him a good programmer, however. To become a well-rounded programmer, the novice must additionally study CS theories: discrete mathematics, algorithms, complexity theory, computer architecture, and so on. Those interested in CS education may read my article, *[Computer Science Curriculum](CSCurriculum.md)*.

An experienced programmer picks up a new programming language in a very different way:

- Study the language manual written by the language designer, focusing on the semantics
- Implement small projects, either from the exercises or from his repertoire of favourite problems
- Apply the language in a commercial setting, thereby deepening his understanding

When a conscientious programmer studies a new programming language, he not only learns the static, syntactic structures of the language, but also absorbs the dynamic, semantic behaviours of the paradigm to which this language belongs. And he takes in a bit of historical background of both the paradigm and the language. He reads the texts (yes, plural) that have been written about that language, preferably by the one who designed the language or by those who are active in that community. He does the end-of-chapter exercises in the texts. His reading list includes definitive textbooks, academic papers, and official online documentation. For a more effective learning, he additionally employs the paradigm's prescribed design concepts and the language's preferred implementation idioms to solve a few pet problems that are substantive but not too complicated, for instance, graph algorithms, neural network algorithms, computer graphics algorithms, or comparable ones. This is the most effective, proven way, regardless of whether one is learning the language in a formal, classroom setting or in an informal, bedroom setting.

An expert programmer masters a programming paradigm as follows:

- Study the underlying theories of the paradigm, and identify the concepts that distinguish the paradigm
- Study a canonical language of the paradigm, focusing on the language's support for the key concepts
- Implement small projects to master the implementation practices of the language
- Implement a large project to master the design theories under the paradigm

One learns a programming language for these reasons: because it is commercially *successful* in the industry; because it is intellectually *influential* in academia among programming language designers; or because it is *both* influential and successful. Below, I suggest a way to master four languages in four paradigms. These four paradigms are the ones used extensively in the IT industry. And these languages are canonical languages in their respective paradigms, all have been successful, and all continue to be influential. Absorbing these languages and their respective paradigms will equip one with the fundamentals necessary to pick up any language—either existing or yet to be invented—in those paradigms.

Before we proceed, I would like to reemphasise the following oft-overlooked, but important, points. Knowing how to use a language is not the same as understanding how to use it well. To use a language properly in an application domain (scientific, engineering, business, etc.), one must have done these in advance:

- Learn the language's idioms
- Master the paradigm's concepts
- Grasp the domain's drivers

# PARADIGMS

There are two predominant programming paradigms: the *imperative* paradigm, which reflects the way the computing hardware performs its work, and the *declarative* paradigm, which reflects the way the computer scientist thinks about his work. To look at it another way, whereas an imperative programme's meaning can only be understood by executing the code in the reader's mind, a declarative programme's meaning is patent in the code.

***imperative paradigm***—Within the [imperative paradigm](https://en.wikipedia.org/wiki/Imperative_programming), there are three divisions: machine programming (MP) languages, procedural programming (PP) languages, and object-oriented (OO) languages.

*MP* languages are realisations of [Turing Machine](https://en.wikipedia.org/wiki/Turing_machine), a theoretical model of computation. MP languages are the assembly languages for various instruction set architectures, be they actual hardware or virtual machines. Today, very few programmers read, let alone write, in assembly. Only compiler writers regularly deal with assembly. The most prominent MP languages at present are ARM, Intel, JVM, and CLR.

As for *PP*, the classic languages of this paradigm include FORTRAN, COBOL, ALGOL, C, and Pascal. Of these, only C remains in extensive use. But the linguistic innovations that originated in ALGOL live on in most languages that are popular today, including C. Hence, ALGOL is considered an influential language, although it never attained the commercial success of its contemporaries, FORTRAN and COBOL.

Classic *OO* languages are Simula and Smalltalk. Both are all but dead, but their intellectual descendants include C++, Java, C#, and just about every new language that emerged in the past decade or two. OO is, by far, the most successful programming paradigm in the industry. The persnickety nature of MP is quelled by the high-level constructs of PP languages, and PP's laissez-faire attitude toward code organisation and data management is tamed by the OO concepts of class, inheritance, objects, and methods. It could be said that OO is the most evolved expression of the imperative paradigm.

***declarative paradigm***—The [declarative paradigm](https://en.wikipedia.org/wiki/Declarative_programming), too, comprises three divisions: functional programming (FP) languages, relational programming (RP) languages, and logical programming (LP) languages.

*FP* languages are realisations of [λ-calculus](https://en.wikipedia.org/wiki/Lambda_calculus), another theoretical model of computation, an equivalent of Turing Machine. FP languages emphasise creation, application, and manipulation of functions as values. Classic FP languages include LISP, ISWIM, and ML. LISP lives on in popular, modern languages like Racket and Clojure. ML is still used extensively in academia as the introductory language for first-year CS students.  Through the decades, there have been many great ML textbooks written by prominent FP researchers and professors. ML is the only language in popular use that has a comprehensive theoretical description. And ML's type system, syntax, and semantics appear in most new languages that came about over the past several years, including Haskell, OCaml, Rust, Kotlin, and Swift. Hence, ML is highly influential intellectually, though not as successful commercially. ISWIM is a conceptual language. Although it was never implemented, the concepts it pioneered were adopted by ML and the descendants of ML. As such, ISWIM is indeed the most influential FP language.

In set theory, a relation is a generalisation of a function. Compared to a function, a relation has less stringent mathematical constraints. This laxity endows the relation with more expressive power, as well as with more theoretical pitfalls, than the function. Loosely speaking, functions describe the transformation of the input set (domain) to the output set (co-domain), and relations describe the connection between the left-hand set and the right-hand set. *RP* is based on relational theory. It is a generalisation of FP. RP emphasises creation and manipulation of relations, which are commonly referred to by practitioners as tables. The only RP language in popular use today is SQL. It has been in a sustained, intense use in the industry for five decades. In a way, SQL is about as successful as C. But unlike C, SQL has evolved and mutated, extensively and frequently. And just as C's domain is system programming, SQL's domain is database programming. Almost all non-trivial, modern web and mobile applications use SQL to store and manipulate data. An application typically uses embedded SQL, directly. Alternatively, an application may use an ORM API or a REST API, and the API in turn uses embedded SQL.

*LP* is even more theoretical than RP and FP. LP is based on formal logic, a foundation of computation, philosophy, law, and several other fields. LP emphasises definition, derivation, and evaluation of logic rules. A well-written LP programme is capable of performing automatic logical proofs. Proofs have always been the Holy Grail of AI research. It could be said that LP is the highest expression of the declarative paradigm. As with RP and SQL, the only LP language that remains in use today is Prolog and, not surprisingly, only in academia.

***different but equivalent***—Programming paradigms provide different, but equivalent, ways to solve problems. All paradigms are equivalent in that they are all designed to aid in the production of software. But they are different in that each paradigm espouses a unique philosophy. The right choice of paradigm and language depends on the problem at hand.

Let us compare the data manipulation philosophies. An imperative programme mutates its state. The programme initialises the central data structure by loading the input data into it, and evolves this programme state by mutating it using various procedures. On the other hand, a declarative programme incrementally evolves its state, without maintaining a mutable central data structure. The programme passes the input data through a pipeline of functions where each function incrementally computes its output based on its input but without mutating that input. At the end of execution, however, both programmes produce the same results from the same set of inputs. Typically, software that are close to the computing hardware are written in imperative languages, and software that are close to the human mind are written in declarative languages.

Today, PP is used almost exclusively in system programming. OO is predominant in business computing, but its use is widespread in system programming, too. Until recently, FP was used primarily in academic research and scientific computing but, of late, FP has become the IT industry's darling of the day. It took the industry four decades to appreciate all that FP has to offer. As mentioned above, RP is used in the industry only for database programming. But since all modern enterprise applications use databases, RP is significant. MP is used exclusively for hardware-proximate uses, such as operating systems, games, and microcontroller, and even in those domains, only sparingly. In the heyday of AI in the 1980s LP, especially Prolog, was nearly as prominent as LISP. But now, LP is confined to academia. Since this article is aimed mainly at enterprise programmers working in the IT industry, I shall discuss only PP, OO, FP, and RP paradigms.

# PROCEDURAL

C is the quintessential PP language, which is now more than half-a-century old. Indeed, C is the most successful PP language still in heavy use. Despite its age, C has remained essentially unaltered over time, because its design, from the very beginning, matched its purpose: for creating software that hugs the hardware, such as infrastructure application, operating system (OS), device driver, digital signal processing (DSP), etc.

The newer Nim language has a clean syntax, a static type system, and a customisable garbage collector. It compiles to C first, then uses the C compiler to generate the executable. As such, Nim programmes run anywhere C programmes run, and they perform about as fast as C programmes. Like C, Nim is purely PP, but supports OO and FP, naturally. Hence, for business, scientific, and system programming on an enterprise scale, Nim is the better choice over C. Due to its simplicity, Nim is also well suited to novices. However, C remains the gold standard for PP languages. As such, all programmers should learn C, at some point in their careers.

To master C and the PP paradigm, study these:

- The de facto industry standard C compiler has long been the GNU `gcc`, which comes with macOS, a modern UNIX, and Linux. To prevent developing mental disorders in the future, one should not learn C programming on Windows.
- Study computer architecture fundamentals, such as CPU microarchitecture, instruction set architecture, computer organisation, and the like.
  - *[Learning Computer Architecture with Raspberry Pi](https://www.amazon.com/Learning-Computer-Architecture-Raspberry-Pi/dp/1119183936/ref=sr_1_12?dchild=1&keywords=computer+architecture&qid=1634399945&sr=8-12)*, Upton (Raspberry Pi SoC designer)
- Read a UNIX user guide to learn about processes, file system, devices, command-line tools, etc. Do realise that UNIX was the 1970s version of the IDE. UNIX was designed by programmers as an integrated programming environment to be used by programmers via a text terminal.
  - *[The Unix Programming Environment](https://www.amazon.com/Unix-Programming-Environment-Prentice-Hall-Software/dp/013937681X/ref=sr_1_8?dchild=1&keywords=kernighan&qid=1634400385&sr=8-8)*, Kernighan (Bell Labs UNIX/C team member)
- Read the definitive C programming manual to learn the syntax and the idioms of the language.
  - *[C Programming Language](https://www.amazon.com/Programming-Language-2nd-Brian-Kernighan/dp/0131103628/ref=sr_1_4?dchild=1&keywords=kernighan&qid=1634400385&sr=8-4)*, Kernighan (Bell Labs UNIX/C team member)
- After having gained a basic knowledge of architecture, UNIX, and C, study these advanced textbooks.
  - *[Computer Architecture: A Quantitative Approach](https://www.amazon.com/Computer-Architecture-Quantitative-Approach-Kaufmann/dp/0128119055/ref=sr_1_5?dchild=1&keywords=computer+architecture&qid=1634399945&sr=8-5)*, Hennessy (Stanford MIPS CPU designer)
  - *[The Design of the UNIX Operating System](https://www.amazon.com/Design-UNIX-Operating-System/dp/0132017997/ref=sr_1_3?dchild=1&keywords=unix+operating+system&qid=1634400445&sr=8-3)*, Bach (Bell Labs UNIX/C team member)
- To learn advanced hardware-level programming, experiment with SoCs and MCUs.
  - [Raspberry Pi 4](https://www.raspberrypi.com/products/raspberry-pi-4-model-b/)—SoC with ARM Cortex-A72 CPU (A-profile for high-performance application)
  - [STM32F411VE](https://www.st.com/en/evaluation-tools/32f411ediscovery.html)—MCU with ARM Cortex-M4 CPU (M-profile for low-power microcontroller)

## *PP concepts*

In PP, the key organising principle is the procedure. A *procedure* is a named sequence of statements. Ordinarily, a procedure, by its constituent statements, accesses and mutates some global data. This behaviour is referred to as *side effect*. The behaviour of a procedure can be controlled by providing it a set of input parameters. Although a return value is not mandatory, a procedure can return a result.

Outwardly, a procedure resembles a function. But a mathematical *function* does not have side effects; its behaviour is entirely defined by its set of input parameters. And a mathematical function always returns a meaningful value.

A PP programme is designed by grouping reusable behaviours into procedures. At runtime, the distinguished main procedure first initialises the global data structure, then invokes other procedures. These procedures, in turn, invoke other procedures in still lower tier. Programme execution proceeds, procedure-by-procedure, statement-by-statement. When the global data structure has been manipulated into its final desired form, the programme execution is deemed complete.

Large PP programmes often use modules as the next higher level of programme organisation. A *module* contains its own data and procedures, which other modules may use.

## *C concepts*

C is a small, simple language; it can be learned in a day. But it takes an ordinary programmer a couple of years to master the language. The reason for this difficulty is that although the language is simple, it is very close to the hardware. As such, the programmer is exposed to the intricacies of the hardware. The programmer must develop a mechanical sympathy for the computer. He must first acquaint himself with the computer's architecture, before he could wield C's power. My article, [*How 8-bit Computers Work*](../ComputingHistory/How8bitComputersWork.md), explains the structure and the behaviour of 1980s 8-bit home computers, including component organisation, CPU architecture, instruction set architecture, and assembly programming. It aims to help high-level language programmers develop a deeper understanding of low-level computing concepts. One who wishes to learn to program in C must learn these basic, hardware concepts, first.

C is armed with a low-level facility call *pointers*, which are numerical values that represent memory addresses in the underlying hardware. Pointers are unheard of in modern programming languages, but C without pointers is unthinkable. Through pointers, a programme can directly access and control hardware resources—CPU registers, RAM, ROM, graphics card, hard disc, network port, etc.—as through they are memory addresses. The concept of pointers has haunted many generations of young C programmers, because these novices usually try to learn C without first studying computer architecture. The above-mentioned introductory books on architecture and UNIX help a novice to develop a high-level mental picture of how the memory is organised, how the CPU addresses a memory location, how the CPU accesses contents of a memory location, how the C compiler allocates the memory, and how UNIX enforces fair sharing of memory amongst processes. Once these concepts have been absorbed, pointers become second nature to the hardware-minded programmer.

C's high-level abstraction facilities are `union`, `struct`, function, and module. In category theory terms, a `union` is a sum type; a `struct` is a product type; and function, too, is a product type, because $f: X → Y$ is equivalent to $X \times Y$. They are used to group primitive data types, like `char`, `int`, `float`, etc., into compound data types. A common technique for structuring a data hierarchy is to create a top-level compound data structure, which contains several lower-level compound data structures. For time and space efficiency, higher-level data structures typically contain pointers to, not copies of, lower-level data structures.

A *function*, which is C's term for PP's procedure, can accept primitive data types, compound types, and pointer types. A function can also return those types. C has no support for higher-order function, but a C function can accept and return a function pointer. With care, this ability can be used to simulate some of the behaviours of higher-order functions.

Primitive and compound data types are sometimes referred to as *concrete data types*, in a sense that the data they contain are tangible and can be manipulated directly by client code. In contrast, *abstract data types* hide the internal representations of their constituent data; only the associated operations (functions) that create and manipulate them are visible to client code. The client code that uses an abstract data type does not know, nor does it care, how the constituent data are represented and manipulated internally; the client code accesses an abstract data type only through the published operations.

A typical C programme is divided into *modules*. Physically, a module is a file. Conceptually, a module represents an abstract data type. Only those variables and functions expressly exported (using `extern` keyword in the `.h` header file) can be accessed from outside the module. So, C modules are a rudimentary, but effective, data-hiding abstraction mechanism. This simple technique originated with the [Modula](https://www.research-collection.ethz.ch/handle/20.500.11850/68669) programming language. All modern languages now support modules, both as a means of data abstraction and of code organisation.

C employs a static type system, but a rather weak one at that: it provides no substantive type safety. Programmers, thus, rely on an elaborate set of conventions and idioms as a form of manual type safety protocol. A weak type system and a permissive, pointer-based memory manipulation techniques, together, make C programmes prone of many kinds of runtime errors, which invariably result in the all-too-familiar UNIX console message, `Segmentation fault (core dumped)`. This message means that the programme had somehow trampled upon a region of memory not allotted to it, and as a consequence UNIX has forcibly terminated it and has preserved its memory state in a file named `core` for later examination by the programmer using [low-level debugging tools](https://wolfram.schneider.org/bsd/7thEdManVol2/adb/adb.pdf), such as `adb`. Modern C programmers do not use such low-level tools; instead they use a sophisticated, GUI-driven IDE with an integrated debugger.

***purpose of C***—It is important to recognise that C was created to implement operating systems at a time when [the most powerful computer](https://en.wikipedia.org/wiki/IBM_System/360) had a 32-bit CPU and 1 MB RAM, and [a typical business computer](https://en.wikipedia.org/wiki/PDP-11) had only a 16-bit CPU and 16 KB of RAM. The ability directly to manipulate the hardware was of paramount importance to the designers of C. So, they did not equip C with sophisticated high-level abstraction facilities, because such features were unnecessary for the intended purpose and they would only have bloated the language. Viewed in this light, it is understandable, and indeed quite forgivable, that C's static type system does not perform any runtime checks, since all safety features have associated performance costs.

Although C was used on many enterprise-scale projects in the 1980s, it was clear to everyone that this was not the application domain that suited C. OO thus came to the fore. Today, C has returned to its roots: small-scale, hardware-level programming. Hence, an experienced programmer who wishes to learn C should familiarise himself with at least one microcontroller architecture, such as the popular [ARM Cortex-M](https://developer.arm.com/ip-products/processors/cortex-m) family.

To be precise, C the language is eminently capable of handling any level of software complexity; it is the average C programmer who cannot. For this reason, only a few large projects use C, these days. The Linux kernel is one of those few. This famous open-source project admits into their midst only the most proficient of C programmers.

# OBJECTIVE

In the 1990s, the IT industry was consumed by an almost-irrational enthusiasm for OO. There were many reasons why the industry adopted OO wholesale, but the primary motivator was the desire to manage the rampant increase in software complexity.

OO concepts were pioneered by Simula in the early 1960s, as an OO extension of ALGOL, a PP language. Simula's forte was discrete event simulation, which was an ideal playground for OO. Theoretical developments trickled in during the 1970s and 1980s. By the early 1990s, OO had matured, theoretically and practically. OO's coming of age coincided with the advent of RISC, which represented a massive jump in hardware sophistication. This hardware revolution empowered software to do much more than was possible, previously.

The 1990s saw the rise of distributed computing protocols, like Sun's [RPC](https://en.wikipedia.org/wiki/Sun_RPC), OSF's [DCE](https://en.wikipedia.org/wiki/Distributed_Computing_Environment), OMG's [CORBA](https://en.wikipedia.org/wiki/Common_Object_Request_Broker_Architecture), and most importantly, CERN's [HTTP](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol). These advances accelerated the growth of software complexity. The most dominant language of the time, the hardware-centric C with its casual attitude toward software abstractions, was unequal to the task of coping with this increased complexity. The industry looked to OO as the means to manage software complexity, and OO delivered in spades.

Although Simula is rightly credited as the progenitor of OO, it was Smalltalk, with the backing of a corporate giant Xerox, that popularised OO in the industry, in the 1970s. And by the mid 1980s, C was being used extensively in the industry on a large scale. Soon, C was found to be lacking in its ability to handle enterprise-scale software complexity. Objective-C was created by melding Smalltalk and C.

The NeXTSTEP OS adopted this little-known language in the late 1980s, and propelled Objective-C into the pantheon of modern languages. NeXT was to be "Apple 2.0", and the original MacOS was the embodiment of Smalltalk's legendary MVC GUI. Naturally, NeXTSTEP was powered by Objective-C and MVC.

Around the same time, Bell Labs hatched C++ by injecting Simula's OO concepts into C, in order to create a more modern system simulation language. C++'s OO support was appealing to C programmers struggling with enterprise applications that were becoming larger and more complex. By the early 1990s, C++ was already being used for desktop GUI, business software, scientific computing, system programming, operating system, device driver, game development, and everything else.

Together, Objective-C and C++ dominated the software development industry throughout the 1990s. Today, Objective-C is still used on the modern macOS, the descendant of NeXTSTEP, but it is rapidly bing displaced by Apple's new language, Swift, a derivative of ML, Smalltalk, and C. And C++ is still used extensively throughout the industry, especially in performance-critical applications like VR games.

Smalltalk is now all but confined to a few remaining legacy business applications. Nevertheless, Smalltalk is considered by OO aficionados as the definitive OO language. After all, Smalltalk inspired Objective-C, Java, C#, Scala, Ruby, and loads of other OO languages in popular use, at present. Although most modern programmers are aware that Smalltalk is OO, not many know that Smalltalk has a decent FP support, owing to its LISP influence:

- Smalltalk, like LISP, has a weak, dynamic type system
- Smalltalk `#xyz` symbol is LISP `'xyz` quote
- Smalltalk `[ ... ]` block is LISP `lambda` function
- Smalltalk `collect:` method is LISP `map` functional
- Smalltalk `select:` method is LISP  `filter` functional
- Smalltalk `inject:into:` method is LISP `foldl` functional
- Smalltalk `currentDo:` method is LISP `call/cc` continuation
- Smalltalk reflection is the dynamic version of LISP macro

Despite its pedigree and power, Smalltalk, as the name suggests, is a small, simple language endowed with a clean, cogent syntax. This makes Smalltalk a very good first language, even for young children. The compact syntax is easy to learn, and the pure OO nature is quick to grasp. Experienced programmers in the industry cannot escape OO, and they cannot shrug their responsibility to teach the less experienced. Smalltalk simplifies the teacher's job, when teaching OO concepts to novices.

To master Smaltalk and the OO paradigm, study these:

- Download Pharo, a modern implementation of Smalltalk.
  - [Pharo](https://pharo.org/)
- Read the language manual for Pharo to learn the syntax and the idioms of the language.
  - *[Pharo by Example](https://github.com/SquareBracketAssociates/PharoByExample80/releases/download/continuous/PBE8-wip.pdf)*, Ducasse
- Having learnt the fundamentals, read a more advanced language manual.
  - *[Smalltalk by Example](https://thelackthereof.org/docs/library/cs/smalltalk/Sharp,%20Alex:%20Smalltalk%20by%20Example.pdf)*, Sharp
- For those who want to know how experienced Smalltalkers perform their work, this book is the one.
  - *[Smalltalk Best Practice Patterns](https://www.amazon.com/Smalltalk-Best-Practice-Patterns-Kent-ebook/dp/B00BBDLIME/ref=sr_1_1?dchild=1&keywords=smalltalk&qid=1634482789&sr=8-1)*, Beck
- For historical background, read the definitive programming manual for the original Xerox Smalltalk.
  - *[Smalltalk-80: The Language and its Implementation](http://stephane.ducasse.free.fr/FreeBooks/BlueBook/Bluebook.pdf)* (Blue Book), Goldberg (Smalltalk team member)

## *OO concepts*

The state of an entire PP programme is held inside a large, global data structure. Any procedure can access this data structure, at will. In large, complex programmes, this unrestrained mutation of global data leads to chaos.

OO strives to tame this chaos by holding portions of the programme state inside various objects with distinct responsibilities. The central idea of OO is quite simple: ensconce a piece of data inside an *object*, and let the object guards its data against undisciplined access by outsiders. The object allows other objects to access to its internal data only via some well-defined methods. This concept is called *encapsulation*.

Without the concept of classes, there will be no objects. A *class* is a static template from which many identical copies of dynamic objects are created and are subsequently customised to suit their individual runtime behaviours.

Classes represent the static side of OO, and objects its dynamic side. At runtime, the programme state is smeared across the myriad active objects. These objects interact and collaborate with one another by sending messages. When an object receives a message, it invokes its method that the message specifies. This method accesses or mutates the associated object's internal state, as necessary. In this way, the dispersed programme state advances in lockstep amongst the objects.

The other big idea of OO is *inheritance*. A class can inherit structure and behaviour from another class, and augment what was inherited with its own specialised functionality. C++ is a multiple-inheritance OO language; it allows a child class to inherit from multiple parent classes. But Smalltalk is a single-inheritance OO language. That means a child class may inherit only from one parent class. Smalltalk's static inheritance hierarchy of classes is a tree, the root of which is the distinguished class called `Object`. At runtime, though, the dynamic hierarchy of objects can take on an arbitrary graph structure to suit the needs of a running application.

A category theory point of view simplifies the matter: a class is a product type, and inheritance is a means by which to create a sum type from existing classes.

Designing an OO programme is a matter of finding discrete concepts, naming them, and creating classes for them. A banking simulator, for example, would have classes like `Bank`, `Teller`, `Queue`, `Customer`, `Account`, and so on.

Despite the humble beginnings, however, OO has, over the years, amassed an exasperatingly unwieldy amount of glossy theories and swanky idioms, like SOLID principle, covariance, contravariance, patterns, and anti-patterns. But all theories and idioms can be viewed as mere practical conventions for deciding what responsibility to assign to which class, in order to ensure software remains maintainable as its design ages.

## *Smalltalk concepts*

The core concepts of Smalltalk are inheritance, class, object, method, and message, which are the fundamental OO concepts familiar to modern programmers; nothing special there. What makes Smalltalk special, however, is the understated way in which it achieves express power: clear vision, pure purpose, simple design, and harmonious philosophy.

The unifying principle in Smalltalk is that everything is an object. Primitive values like characters and numbers are objects. Even classes are objects. For instance, to create a new object of the class `Stratocaster`, one sends the `new` instance creation message to the global object that represents this class which, incidentally, is named `Stratocaster`:

```Smalltalk
redStrat := Stratocaster new
  model: 'Fender Custom Shop';
  color: 'Fiesta Red'
```

Likewise, sending the `subclass:` message to an existing class (which is an object) creates a derived class (a new object) with the specified name:

```Smalltalk
MusicalInstrument subclass: #Guitar

Guitar subclass: #AcousticGuitar
AcousticGuitar subclass: #GibsonL5
AcousticGuitar subclass: #MartinD28

Guitar subclass: #ElectricGuitar
ElectricGuitar subclass: #FenderTelecaster
ElectricGuitar subclass: #FenderStratocaster
```

Computation is performed by sending messages to objects. For example, `5 factorial` computes $5! = 120$. Here, the receiver is the `Integer` object `5` and the message is `factorial`.

The conditional expression, too, is implemented as a message:

```Smalltalk
b
  ifTrue: [ csq ]
  ifFalse: [ alt ]
```

Here, the receiver `b` is an object of the `Boolean` class, the message is `ifTrue:ifFalse:`, and the message parameters `[ csq ]` and `[ alt ]` are the consequent and the alternative blocks. If `b` evaluates to a `true` value, the `[ csq ]` block is evaluated, and otherwise, the `[ alt ]` is evaluated.

A count-up loop over integers is written as follows:

```Smalltalk
1 to: 10 do: [ :i | i print ]
```

Here, the receiver is the `Integer` object `1`, the message is `to:do:`, and the message parameters are the `10` and the `[ ... ]` block. Each time through the loop, the receiver's current value is passed to the block as the argument `i`, and the receiver is then automatically incremented. An equivalent loop in C is this:

```c
for (int i = 1; i <= 10; i++) printf("%d\n", i + 1);
```

Yes, Smalltalk uses the human-centric 1-based counting scheme, unlike C, which uses the machine-centric 0-based counting. The condition method and the loop method above are analogous to higher-order functions in FP, and the blocks are analogous to λ functions. Other FP influences in Smalltalk include  `collect:`, `select:`, `inject:into:`, whose FP equivalents are `map`, `filter`, `foldl`. It is not only possible, but also quite idiomatic, to program in Smalltalk using λ functions and the standard higher-order functional operators.

***advice***—In the late 1980s, I had the opportunity to observe, up-close, the many struggles that experienced PP programmers faced when adopting OO. They were my colleagues. They were C experts. They read the excellent [*The C++ Programming Language, 1ed*](https://stroustrup.com/1st.html) (Brown Book) by Stroustrup, as we all did, in those days. C++ was but a small extension of C then, having only classes, multiple inheritance, and operator overloading. For a Smalltalking, C hacker like me, adopting C++ (and Objective-C) was a simple matter of learning a few syntactic quirks. But my C-is-a-god colleagues went through a year-long ordeal. They learned easily the syntactic elements, but they struggled with OO design concepts; they kept falling back into familiar C idioms, and ended up writing C programmes in C++ syntax.

Like my colleagues, I was versed in C and assembly, when I learned Smalltalk a few years before they began learning C++. However, when I learned OO in Smalltalk, I did not experience that shocking ordeal my colleagues had to endure, because Smalltalk was a small, simple, strictly OO language, without pointers, `goto`, and other PP paraphernalia to distract and derail me. And because, by the time I began learning Smalltalk, I had already learnt LISP, I was able to recognise, and exploit, Smalltalk's FP idioms, which blended naturally with the core OO idioms of the language. Learning OO was by no means an easy transition for me, but it certainly was an enjoyable learning process, not an ordeal.

This experience taught me that when learning something new and distinct, it is best to check one's prejudices and predilections, and that early exposure to different perspectives is vital in one's continuing intellectual development. Learning is an exercise in assiduity while being receptive. Humility is the trait from which both hard work and open mind sprang. Do not be seduced by the "my way is the only way" mentality. The arrogance born of "my best way" sways in the blistering winds of trend and it is soon buried under the wind-blown sands of time; humility, however, is unburdened and it glides above tempests of trends. So, strive to be humble. Learn, continuously.

# FUNCTIONAL

Fortunes of FP seem to wax and wane in decennial cycles. LISP, the world's second high-level language (after FORTRAN) and the first FP language, came out in the 1950s. Naturally, there was much enthusiasm for both FORTRAN and LISP, because most programmers at the time were programming in various assembly languages.

But by the 1960s, COBOL held the business computing market and FORTRAN the scientific computing market, the two largest applications of computers in those early days. Programming language researchers in academia were preoccupied with ALGOL, then. This was not FP's time to shine.

The 1970s saw the rebirth of LISP as the definitive language for the AI expert system, which was the IT industry's obsession of the day. ML emerged during this period, too. Its strong, static type system with inferencing ([Hindley-Milner type system](https://en.wikipedia.org/wiki/Hindley–Milner_type_system)), its clean syntax, and its theoretical foundations seduced many CS university programmes into adopting ML as their teaching language. It appears FP was on the rise again, both in academia and in industry.

In the 1980s, though, C took the computing world by storm. C was especially popular in business computing, which up till then was occupied by COBOL. C is generally regarded as a much more powerful language than COBOL, and for good reasons, too. The enthusiasm for C in the industry was keen, then, and university CS programmes that leaned toward the industry dropped ML altogether, and the lot of them went C-razy. Moreover, the hype surrounding AI expert systems in the decade prior did not yield dividend. LISP was forever tied to the downfall of expert systems. Consequently, many derided LISP in those days; some referred to it as "Lost In Stupid Parentheses".

Again, FP returned in the 1990s, in the guises of OCaml and Haskell, both descendants of ML. OCaml successfully combined its academic FP core with the industry OO hype, which was in full swing, by then. The existence of Scala, F#, Reason, and other popular languages is a vindication of OCaml's hybrid OO-FP approach. Haskell, however, took a completely different approach. It was designed by a committee of CS professors to serve as "the standard" language for pure FP research. Many theoretically-inclined university CS programmes, thus, adopted Haskell as their teaching language.

However, the 2000s were undoubtedly the age of Java. Almost overnight, Java displaced C++ in enterprise computing. Indeed, the original Web was fuelled by Java: web programmes ran on instances of Java VM, and web programmers ran on cups of Java. Java gave birth to C# and Scala directly, and it indirectly influenced many modern languages, including Kotlin and Swift.

In the 2010s, JavaScript did to Java what Java did to C++, a decade prior. But JavaScript is Java only syntactically; semantically JavaScript is a derivative of Self and Scheme. Self is a dialect of Smalltalk, and Scheme a dialect of LISP. Owing to its adoption of Self's class system and prototype-based inheritance, JavaScript is known in the industry as an OO language. But JavaScript possesses a LISP-influenced FP core, due to its Scheme lineage:

- JavaScript, like LISP, has a weak, dynamic type system
- JavaScript `Symbol` class is LISP `quote` function
- JavaScript `⇒` function is LISP `lambda` function
- JavaScript `map` method is LISP `map` functional
- JavaScript `filter` method is LISP `filter` functional
- JavaScript `reduce` method is LISP `foldl` functional
- JavaScript  `async`-`await` concurrency is LISP `call/cc` continuation
- The much-maligned JavaScript  `eval` function is LISP `eval` function

This period also saw the resurgence of interest in FP due, in part, to many JavaScripters having adopted functional reactive programming (FRP) as a means to control the complexities associated with HTTP-based distributed computing. This renewed interest in FP, in turn, heightened the industry's awareness and respect for existing FP languages like OCaml, Haskell, Scala, and Clojure, and additionally created a demand for new FP-inspired languages, like Rust, Kotlin, and Swift. If the 2000s were the era of the OO hype, the 2010s were certainly the time of the FP hype.

Now, in the 2020s, new languages are cropping up seemingly every few hours. The designers of these new languages keep injecting FP facilities into their languages, but it is plain to see that most programmers continue to use the OO facilities with which they are familiar. It is too early to say whether FP will be snubbed by the industry, again, in this decade.

For the time being, though, much enthusiasm for FP permeates the industry, especially in domains such as mathematical computing, parallel computing, and FRP. Hence, it is advisable for an experienced programmer to take up the FP paradigm.

In truth, any new language in popular use today can be used to study FP, because they all support FP, to varying degrees. But there are scant few academic textbooks for these languages. Many new languages do not have books written about them. Some have blogs. Some have a README. Some have only undocumented, uncommented, buggy code. Although a few have books, they are written by, and for, those who view programming as a trade, not a mathematical, intellectual pursuit. This situation makes it rather difficult to acquire deep insight into FP, while trying to learn one of those newfangled languages.

On the other hand, OCaml, Haskell, and especially Standard ML, have extensive collection of books written by CS professors and IT practitioners alike. These books span the gamut: gentle introductions, heavy-duty industrial applications, compiler constructions, explorations of category theory, the lot.

Haskell has a reputation for being difficult to learn and even more difficult to teach. Indeed, one cannot write a "Hello, World!" in Haskell, unless one understands the concept of *monad*, which is a rather high bar for novice FP programmers.

OCaml is easier to learn, but its OO facilities may distract novices who are endeavouring to learn FP. And both Haskell and OCaml are large, complex languages that are continually evolving.

But Standard ML, the version of ML that was [standardised in 1997](https://www.smlnj.org/sml97.html), is stable and its core is comparatively tiny. And it has been around for a long time, and is used extensively in academia as a teaching language. As such, there are many more textbooks on Standard ML that are accessible to FP novices. Practically speaking, since OCaml, Haskell, and almost every modern FP language either descended from or was inspired by ML, it is fairly straightforward for an ML programmer to pick up those newer languages. For these reasons, Standard ML is considered by many to be the best language in which to learn FP. From a philosophical viewpoint, Standard ML is a still-vibrant, seminal language that gave birth to almost all modern FP languages. For that reason alone, Standard ML deserves to be studied.

To master Standard ML and the FP paradigm, study these (NB—all texts in this list were written by famous personalities in CS who are active in the FP community):

- Download SML/NJ, a modern implementation of Standard ML. There are several Standard ML implementations. SML/NJ is the most popular one.
  - [SML/NJ](SML/NJ)
- Read a Standard ML language manual. This is arguably the most accessible textbook of its kind for FP novices.
  - *[ML for the Working Programmer](https://www.amazon.com/ML-Working-Programmer-2nd-Paulson/dp/052156543X/ref=sr_1_1?dchild=1&keywords=ML+for+the+Working+Programmer&qid=1634436011&sr=8-1)*, Paulson
- Study the authoritative textbook on FP. This is, far and away, the best introductory textbook for FP novices. It is based on Miranda, the mother of Haskell. But the concepts presented in this textbook are applicable to all FP languages. And since Miranda descended from ML, this book is accessible to ML programmers.
  - *[Introduction to Functional Programming](https://archive.org/details/introductiontofu0000bird)*, Bird
- Read the classic paper that presents a convincing argument for why FP matters to programmers. This paper is based on Haskell, but it is accessible to ML programmers.
  - *[Why Functional Programming Matters](https://www.cs.kent.ac.uk/people/staff/dat/miranda/whyfp90.pdf)*, Hughes
- Read the famous paper that focuses on the `fold` operator to gain a deeper insight on its properties and applications. This paper is based on Haskell, but it is accessible to ML programmers.
  - *[A tutorial on the universality and expressiveness of fold](http://www.cs.nott.ac.uk/~pszgmh/fold.pdf)*, Hutton
- Study category theory to learn the deep, sublime mathematical concepts that underlie computation in general and FP in particular. This book is based on Haskell, and uses more advanced features of the language. But the mathematical ideas presented in it are accessible to all FP programmers.
  - *[Category Theory for Programmers](https://github.com/hmemcpy/milewski-ctfp-pdf/releases/download/v1.3.0/category-theory-for-programmers.pdf)*, Milewski

## *FP concepts*

From the perspective of state management, OO is but a gloss on PP. PP holds all programme state in a global data structure. Computation progresses when procedures mutate the global data. Of course, the procedures can mutate that global data, without restraint. On the other hand, OO apportions the programme state amongst autonomous objects who guard their own pieces of data. Computation progresses when objects exchange messages amongst themselves, which result in controlled, coordinated mutation of the disparate pieces of programme state. Despite these outward differences, both PP and OO propel computation by mutating programme state.

FP eschews the store-and-mutate way of working. Instead, FP propels computation by applying functions to input data and by producing transformed output data to be passed to the next function in the pipeline. The programme state is whatever the result happens to be at a particular moment, be it intermediate or final. If necessary, copies of the sequence of intermediate states could be saved, say for "undo" operations.

From the programme design point of view, the whole FP programme is just a function. This top-level function accepts input data, and passes the data to other functions which it invokes, and these functions in turn invoke other lower-tier functions. The bottom tier consists of functions that implement simple expressions.

The key concepts behind FP are simple, minimalist. But FP derives immense expressive powers by composing these simple, individual concepts in a uniform way. This readily composable nature of concepts distinguishes FP from other programming paradigms, when things get complicated.

Objects in OO are designed to be assembled. But object assembly is different in kind form function composition. Functions compose like the connected individual stations in an assembly line. So long as the next station is equipped to accept the output of the previous station, the assembly line works smoothly. The arrival of the input animates a station into action. There is a unified sense of timing and flow. The traversal time through the assembly line is *linearly* proportional to the number of stations in the assembly line. By contrast, objects assemble and organise themselves rather like a group of people mingling and chatting at a party. People are autonomous; their individual actions are governed by their internal motivations. But in a crowd, individuals endeavour to regulate their actions and to coordinate with one another, in accordance with local social norms. There is no unified sense of timing and flow. In the absence of an external ordering, a social order emerges organically to aid collaboration. However, the need for coordination is a form of overhead—a collaboration overhead. And this overhead grows *exponentially* with the number of people involved in the conversation.

Another way to look at this is that FP abstracts synchronised flow, whereas OO abstracts spontaneous coordination. Abstracting something hides the details and simplifies the associated task. FP hides the low-level details associated with function *composition*, thereby simplifying the task of composing large systems out of functional forms. But because OO hides the low-level details associated with inter-object *coordination*, it simplifies the task of configuring object interactions. Interactions contribute to the exponential growth of system's runtime complexity as the number of active objects increases. Since OO abstracts interactions, however, this costly growth of runtime complexity remains invisible to the programmer.

Now, let us turn our attention to some FP terms. FP takes delight in giving ornate names to simple concepts. Below, I shall peel the arcane FP terms to reveal the simple concepts they denote.

***purity***—Mathematical functions mutate neither their input arguments nor external values. This property of functions is referred to as *purity*. Purity guarantees that FP functions will not mutate data sneakily—no side effects. By contrast, PP procedures often have side effects, usually in the form of global data mutation.

***immutability***—Because functions are pure and they do not mutate data structures, when a a function makes a modification to a data structure, it always produces a new copy of the data structure containing that modification. This property of FP data structures is known as *immutability*.

***transparency***—Functions do not maintain internal data that they covertly mutate through hidden computations. That is, a function's behaviour is transparent and is defined entirely by the input parameters. The same input always yields the same output: if a function $f$ applied to an input value $x$ yields an output value $y$, as in $y = f(x)$, then the value $y$ can always be used in place of the function application $f(x)$, and vice versa. This property of functions is called *referential transparency*.

***first-class functions***—Functions are values, just like characters, integers, reals, lists, tuples, records, etc. As such, a function $f$ can be passed as an argument to another function $g(f)$, and a function $f$ can be returned as a result from another function $f = h(x)$. This property of functions is known as *first-class*.

***local functions***—Since in FP functions are values, a function can be declared inside another function, and such local functions, like local variables, are visible only inside the enclosing function.

***higher-order functions***—In FP, a function can accept another function as its argument value and a function can return another function as its result value. This property of functions is called *higher-order* functions. Higher-order functions can abstract away the low-level recursions, thereby making the task of the programmer more convenient and, more importantly, less error-prone.

Higher-order functions are also called *functionals*. The term "functional programming" is a respectful nod to this key concept of FP.

***recursion***—Because in FP state maintenance is forbidden, counting loops are forbidden, too. The `for` loop construct in PP, for instance, maintains the loop count, which is a state. Instead, FP performs repetition with *recursion*. A recursive function is one that invokes itself, as part of its operation. Many problems in CS are hierarchically structured. At the top level, there is the original problem. This problem can be expressed in terms of smaller, self-similar sub-problems.

Let us examine the algorithm for computing the length of a list. A *list* is the tail sublist $tl[⊡]$ with the singleton head element $hd[⊡]$ tacked on at the front: a list $l = hd[l] + tl[l]$. The tail, being a sublist, can be split further in the same manner. Using this hierarchical, self-similar representation, the algorithm computes the length of the list in two cases, as follows:

<div>
$$
len(l) =
\begin{cases}
  0 & \text{if l = ∅} \\
  len(hd[l]) + len(tl[l]) & \text{otherwise}
\end{cases}
$$
</div>

The algorithm states that the length of an empty list is $0$, and that the length of a non-empty list is the length of the singleton head element (which is $1$) plus the length of the tail (which is computed recursively on the smaller sublist $tl[l]$). As the algorithm proceeds down the tail, the tail shortens to the empty list. The resultant length is $1 + 1 + ... + 0$, where the $1$s stand for each element of the list, and the $0$ for the terminating empty list.

The above equation is not merely logical; it is downright intuitive. This comprehensibility and simplicity are the consequences of the hierarchical, self-similar representation, which epitomises the divide-and-conquer problem solving technique employed throughout CS. And the structure of a typical list processing solution like this matches that of the mathematical induction proof method, which means such an algorithm can be proved correct by a direct appeal to induction.

The technique we used in list processing algorithms can be extended to handle trees. A *tree* is constructed of two types of nodes: a branch and a leaf. A tree also has a distinguished node called the root, which is the ancestor of all other nodes. Branches provide a means for structuring the tree, and leaves serve as containers for values held in the tree. A tree, too, has a hierarchical, self-similar structure: any node within the tree can be viewed as the root of a smaller subtree.

Just as trees are generalisations of lists, graphs are generalisation of trees. A graph is a collection of vertices connected with edges. Vertices contain values held in the graph, and the edges represent the relationships between these values. A graph has a hierarchical, self-similar structure: any collection of vertices and edges within the graph, called a subgraph, resembles the parent graph.

In programming, lists are used to represent sequential data. Trees are used to represent hierarchical data. Graphs are used to represent networked data. A database table is a list of records. A JSON data structure is a tree. A road network is a graph. Any complex data can be represented using a combination of these three recursive data structures.

***bottom***—A computation that does not yield a result (for example, infinite recursion) or one that terminates due to a fatal error (for example, divide by zero) is called *bottom*, written $⊥$.

***strictness***—A function that returns a $⊥$ as the result when given a $⊥$ as an argument is referred to as a *strict* function. Otherwise, that function is deemed *non-strict*.

***laziness***—FP languages use either the eager evaluation strategy or the lazy evaluation strategy. The *eager evaluation* strategy reduces every expression to its value, before proceeding with the computation. When using paper and pencil to evaluate a complex arithmetic expression, one instinctively begins the reduction from the innermost subexpression, and works outward until the entire expression is reduced to a number. This is an example of eager evaluation. ML is an eager language.

The *lazy evaluation* strategy reduces an expression to its value, only if that value is needed in the subsequent computation. Evaluating a complex expression by beginning with the outermost subexpression and proceeding inward only when necessary is an example of lazy evaluation. Lazy evaluation proceeds only up to a point when the immediate needs have been satisfied. It does not evaluate the entire expression to its logical end. This approach enables lazy evaluation to support infinite data structures, whose values are computed only when the need arises and only up to a point when such need has been satisfied. A distinguishing feature of lazy evaluation is memoisation. Every evaluated result is cached by the language, and this cached value is reused in all subsequent accesses to the expression. Haskell is a lazy language.

The *delayed evaluation* strategy looks similar to lazy evaluation, but it is very different. Modern languages do not use it, but modern applications do. That is, it is no longer a language facility but now a programming technique. It is known in the web application world as "future". A delayed evaluation is but a suspension of computation for a future evaluation. When the suspended computation is eventually resumed, the whole expression is reduced to its values, in one go. Delayed evaluation is often used to postpone expensive computations until the point when the CPU time becomes available. Large media files and large JavaScript modules embedded in web pages are often loaded using the application code that employs the delayed evaluation strategy. Delayed evaluation, by definition, does not memoise the results. Every access to the expression recomputes it. Of course, the programmer may, on his own, augment his delayed evaluation code with memoisation.

I mentioned delayed evaluation here because it was once a language feature, it is commonly used in modern applications, and most people confuse it with lazy evaluation because both appear to "delay" the computation. But they are different. Lazy evaluation is a compiler-level behaviour, incremental, and memoising. Delayed evaluation is a programme-level behaviour, non-incremental, and non-memoising.

***parameter passing***—When calling a function, there are a few different strategies the language designer can choose: call-by-value, call-by-reference, call-by-name, call-by-need.

The *call-by-name* parameter passing strategy, by far the most popular with language designers, reduces the arguments to their values before passing them into the function. Eager languages use this approach. It is natural. In C, all primitive values are passed by value.

The *call-by-reference* strategy is an optimisation technique used by eager languages. Instead of passing by value the entire copies of large objects, the language passes only the pointers to those pre-evaluated objects, and coats the bitter pointers with syntactic sugar, so the programmer need not grapple with pointer dereferencing. C++ supports passing pointers, as well as references, to objects. Python always passes objects by reference.

The *call-by-name* strategy have been used in only a few languages in the history of high-level programming languages. Under the call-by-name strategy, the language passes the arguments, unevaluated, into the function. The function receives just names (references) to the arguments. Only when the function accesses the argument, its expression is reduced, all in one go, to its value. Moreover, every time the argument is accessed, its expression is reevaluated, which leads to inefficiencies. The call-by-name parameter passing is employed by ALGOL 60 and a few others that use the delayed evaluation strategy. It is not popular with modern language designers.

The *call-by-need* strategy is used in lazy languages. The language passes argument expressions into to the function without evaluation. Only when the function accesses the argument, its expression is reduced, and even then, only incrementally up to the values needed. And the evaluated argument is memoised, so the next time it is accessed, the memoised value is returned. Haskell and its lazy siblings pass by need.

Say, a function $f : x, y → z$ is called as $f(a, b)$ and $b = 1/0$, but $f$ only accesses $b$ based on the value of $a$. If the value of $a$ is such that $b$ is never accessed by $f$, then computation will proceed normally in Haskell and its lazy siblings. But in just about every modern, eager language, the call $f(a, b)$ will go to $\bot$, when $b$ is evaluated just before $f$ is invoked.

***partial functions***—In mathematics, a *total* function is one that is defined for the entirety of its domain. A *partial* function is a function that is not defined for the entirety of its domain. In other words, if a partial function is given a value on which it is not defined, the computation goes to the $⊥$.

***currying***—Currying is a technique for transforming a multi-argument function into a single-argument version. When the compiler sees the function $f : x, y → z$, it transforms the function into $g : x → h$ where $h : y → z$. That is, the multi-argument function $f(x, y)$ is automatically transformed into a single-argument function $g(x)$ that returns another single-argument function $h(y)$ which has value $x$ baked into its body. This transformation is known as *currying*. When the function $h$ is applied to value $y$, it uses both $x$ and $y$ to compute the result $z$. In FP, a multi-argument function may always be thought of as a pipeline of curried, single-argument functions.

***partial application***—A partial application of a multi-argument function is a consequence of currying. In the currying example above, the function $h$ is a partially applied version of the original function $f$. Applying the dyadic $f(x, y)$ to only $x$ is referred to as a *partial application* of $f$ to $x$. When $f$ receives only $x$, it knows that it cannot complete the computation, and instead returns $h(y)$, which accepts $y$ and already has $x$ in its body. When $h$ is given $y$, it becomes the fully applied, so it uses both $x$ and $y$ in its computation, and returns the final result $z$.

Note that many programmers confuse the term "partially applied function" with "partial function"; these two concepts are unrelated. A partial application is analogous to the situation in which a painter is handed a 1 L can of paint and is told to paint a wall that requires 5 L to cover. He would paint as much of the wall as he can cover, but it is impossible for him to complete the job, until he is supplied with an adequate amount of paint. On the other hand, a partial definition is like a painter renowned for his intense hatred of white paint. If he were to be handed a can of white paint, he would surely blow his top in rage and, instead of painting the wall, would burn down the house.

***sections***—A *section* is a partially applied dyadic operator. For instance, when the $+$ operator is partially applied to only one value, as in $(+1)$, it automatically returns a function $g : x → x + 1$. When $g$ is applied to value $3$, it returns  $3 + 1 = 4$. The function $g$ could be used as the increment operator.

## *ML concepts*

***recursion***—ML uses recursion for repetition. Let us examine the factorial function. In mathematics, factorial of $n$ is defined as $n! = n × (n-1)!$ and $0! = 1$ by fiat. In Standard ML, this function can be implemented as an almost-verbatim of its mathematical definition, using a *primitive recursion*:

```ocaml
fun fac 0 = 1
  | fac n = n * fac (n - 1);
```

When this function is invoked as `fac 3`, it computes the following sequence of function invocations that yields the result $6$:

```
fac 3
  3 * fac (3 - 1 ⇒ 2)
    (3 * 2 ⇒ 6) * fac (2 - 1 ⇒ 1)
      (6 * 1 ⇒ 6) * fac (1 - 1 ⇒ 0)
        6 * fac 0
          6 * 1 ⇒ 6
```

Each step in the evaluation of `fac` contains a call to itself. This is the simplest form of recursion. The symbol $⇒$ above means "reduces to".

This primitive recursion can be transformed into *tail recursion*. In a tail recursion, the final step in the function is a recursive invocation of itself without additional computation. In the primitive recursion version above, the final step in the `else` branch is `n * fac (n - 1)`. That means the result of the recursive invocation `fac (n - 1)` is an intermediate step, not the final step. The tail-recursive version of `fac` is this:

```ocaml
fun fac n =
  let fun fac' a 0 = a
        | fac' a n = fac' (a * n) (n - 1)
  in fac' 1 n end;
```

This version of factorial defines a local, auxiliary function `fac'`. In mathematics, the prime symbol $⊡'$ is used sometimes to represent quantities that are similar, but subtly different. ML family of languages—Haskell, OCaml, F#, Reason, etc.—use this mathematical convention. When this version of `fac` is evaluated as `fac 3`, the tail recursion proceeds as follows, yielding the same result $6$:

```
fac 3
  fac' a=1 n=3
  fac' a=(1 * 3 ⇒ 3) n=(3 - 1 ⇒ 2)
  fac' a=(3 * 2 ⇒ 6) n=(2 - 1 ⇒ 1)
  fac' a=(6 * 1 ⇒ 6) n=(1 - 1 ⇒ 0)
  a=6
```

Unlike the simply recursive version, the compiler transforms tail-recursive calls into the CPU's jumps instructions, thereby eliminating space and time overheads associated with function calls. In other words, the sequence of calls to `fac'` above are evaluated within the same stack frame as the call to `fac`. In essence, the compiler transformed this tail-recursive call into a `for` loop.

I have written the consecutive calls to `fac'` without indentation to highlight the absence of function invocations. And for clarity, I have also labelled the arguments of `fac'` with an `a` and an `n`. The `a` here means "accumulator". The use of a local function and an accumulator to transform a primitive recursion into a tail recursion is a common practice in FP.

There are algorithms in which each step contains multiple recursions. For instance, the famous quicksort algorithm uses *double recursion*.

```ocaml
fun qsort [] = []
  | qsort (x::xs) =
    let val less = List.filter (fn e => e < x) xs
        val more = List.filter (fn e => e >= x) xs
    in (qsort less) @ [x] @ (qsort more) end;
```

Now, if we apply `qsort` to an unsorted list, we get a sorted list as a result.

```ocaml
qsort [5, 2, 6, 9, 0, 1, 8]; (* result = [0, 1, 2, 5, 6, 8, 9] *)
```

The recursive step of `qsort` recur once for the elements of `xs` that are less than the pivot `x` and once more for the elements of `xs` that are greater than or equal to `x`. Hence, `qsort` is doubly recursive. This algorithm states that a sorted list is a concatenation of the sorted sublist of values less than the pivot, the sublist containing only the pivot, and the sorted sublist of values more than the pivot. Like most recursive algorithms, quicksort is mathematically intuitive, and its meaning is evident in the code.

***functional operators***—Recursion is essential. Recursion is elegant. In FP , recursion is everywhere: types are recursive, data structures are recursive, and the functions that operate upon them are recursive. The recursive structure of the list length algorithm we examined above reappears in computation of the sum of a list of numbers, the product of a list of numbers, the concatenation of a list of strings, and plenty of other situations.

Recursion is an abstraction over repetition. But now, we see that recursion itself is getting repetitive: the same primitive-recursive form appears in many different algorithms. The mathematical analogue of this recursive structure is called the *monoid* (not the same thing as monad). In abstract algebra, a monoid is a set equipped with an associative binary operator and its identity element. The monoidal operation combines the elements of the set using the binary operator, thus collapsing the set into a single value.

The higher-order function `foldr` (fold right) captures this monoidal operation. `foldr` collapses a list of values into a single value. The process begins by recursively descending (called `cdr`ing down in LISP) from the head down to the last element of the list, then combining the last element of the list with the supplied identity value, and collapsing the recursive structure until only the combined value remains. Because the combining operation begins from the right side (the last element) of the list, this higher-order function is called "fold right". It uses an externally supplied λ function and initial value. The λ function combines the list elements, and the initial value serves as the λ function's identity value. In the case of list sum, the combining operator is the $+$ operator and its identity value is $0$. In the case of list product, the operator is $×$ and its identity is $1$. In the case of string-list folding, the operator is the string concatenation operator `^` and its identity is the empty string `""`.

The list length algorithm mentioned above can be implemented in Standard ML like this:

```ocaml
fun len [] = 0
  | len (x::xs) = 1 + len xs;
```

The primitive-recursive solution structure of `len` can be captured using `foldr` monoidal operator like this:

```ocaml
List.foldr (fn (_, a) => 1 + a) 0 xs;
```

The expression `fn (_, a) => 1 + a` is the collapsing λ function, which ignores its first argument and uses its second argument `a` as the accumulator. The $0$ is the initial value for the accumulator, and $0$ is also the identity of the associative binary operator $+$. And the  `xs` is the list whose length we are computing. The left-starting counterpart of `foldr` is `foldl` (fold left). These `fold` operators have many other superpowers, but their main use is to collapse a list of values into a combined value.

Another oft-used functional operator is `map`, which applies the supplied λ function to the list. Whereas `fold` collapses the list into a single value, `map` preserves the original structure of the list. This is how to apply a squaring λ function `fn x ⇒ x * x` to the each element of the list `xs`:

```ocaml
List.map (fn x => x * x) xs;
```

The `filter` functional operator, too, is commonly used in daily programming. It applies the supplied λ function predicate to the list to select the desired elements. For example, we can filter out elements of `xs` that are greater than $5$ like this:

```ocaml
List.filter (fn x => x > 5) xs;
```

***strictness and eagerness***—The language's evaluation strategy determines the strictness of the functions defined in that language. Consider a Standard ML constant function, a function that returns a constant, no matter the value of the argument:

```ocaml
fun constant x = 9;
```

In an eager language like ML, if this function is invoked as `constant (1/0)`, the computation yields the $⊥$, because the eager evaluation strategy reduces the input expression `1/0` first, before invoking the `constant` function. That reduction immediately produces the divide-by-zero error. But in a lazy language like Haskell, this computation results in `9`, because the lazy evaluation strategy passes to the `constant` function the unevaluated input expression `1/0`. Being a constant function, `constant` simply ignores the input expression, and returns `9`. Hence, functions are strict in an eager language, and they are non-strict in a lazy language.

Programmers often confuse "strictness" with "eagerness". The term "strict" describes the nature of functions, whereas the term "eager" describes the nature of the strategy used to evaluate function arguments. This confusion springs from the fact that in a language that employs eager evaluation strategy, the behaviour of functions is strict. I shall highlight the difference between these concepts by an analogy: a schoolmarm who runs her institution unwaveringly by the book is strict, whereas her pupil who, at lunch time, scoffs down everything on his plate regardless of whether he is hungry or not is eager. Fine distinctions between strictness and eagerness may seem trivial to programmers who implement business applications, but the differences are significant to programmers who implement compilers.

***types***—A type is a set of values. FP programmers aspire to craft types that admit only those values that are valid in the context of the programme. In a statically typed FP language like ML, validity checks are performed during compilation.

ML was the first FP language to use the Hindley-Milner type system. This type system is static, strong, inferencing, and polymorphic. A *static* type system performs type checking at compile time. A *strong* type system guarantees that a programme that type checks at compile time is safe at runtime. An *inferencing* type system discovers types of variables automatically during compilation, which relieves the programmer from having to supply types manually, as is the case in C and Pascal. And a *polymorphic* type system allows containers, like `'a list`, to hold values of different types: `int list` is a list of integers; `real list` is a list of reals. Take `int list`, for example. Here, when the parameterised type constructor `'a list` is applied `int`, the type value `int` is substituted into the type parameter `'a` and yields `int list`, which is a list that holds integers. By way of analogy, a type constructor is applied to a type value to obtain the result type value, just as a function is applied to a value to obtain the result value. This form of polymorphism is called *parametric polymorphism*.

There is another form, called *ad hoc polymorphism*, which is achieved through function overloading. For example, the addition function, represented by the $+$ operator, is overloaded to work with both `int` and `real`.

Think of polymorphism this way. Polymorphism allows the creation of a family of related functions. Parametric polymorphism allows the same implementation to be used for the whole family, regardless of the argument type. That is, all functions in this family behave the same way, even though each function operates on a different type of argument. By way of example, the `sort` function works the same way for `int list` and `real list`. On the other hand, ad hoc polymorphism allows different implementations to be given the same function name. That is, all functions in this family are named the same, but they behave differently based on the different types of argument given. So, `2 + 3` compiles to the code that uses the integer addition hardware, whereas `2.0 + 3.0` compiles to the code that uses the floating-point addition hardware.

ML was the first popular FP language to provide support for algebraic data types (not the same thing as abstract data types). *Algebraic data types* is a fancy name for sum and product types from category theory. The term "algebraic" derives from the fact that these types allow the programmer to construct complex types from simpler types using sum and product operators, not unlike using $+$ and $×$ operators to form complex arithmetic expressions.

The simplest *sum type* is the Boolean type `bool`, which consists of two distinct cases:

```ocaml
datatype bool = False | True
```

The `datatype` declaration defines a new sum type as a disjoint (non-overlapping) union of the specified cases. The "or" `|` operator separating the cases indicates that a value of the `option` type can be only one case, and that the set of all values representable by the type is the union of all the values representable by the individual disjoint cases. Therefore, a variable of type `bool` can hold either a `False` or a `True`, but not both at once. The `bool` above is referred to as *type constructor*. The `False` and the `True` are known as *value constructors*.

The well-known `option` type is a sum type, too:

```ocaml
datatype 'a option = None | Some of 'a;
```

In the `option` type above, the `None` case carries no data, but the `Some` wraps around a type represented by the type parameter `'a`. A function that sometimes fails to return a valid result returns an `option` result. For example, a function that loads data from a file would return `Some data` if data are successfully read, but would return `None` if not.

Just as functions can be recursive in ML, types can be cursively defined, too. The `list` type is perhaps the simplest *recursive type*:

```ocaml
datatype 'a list = [] | :: of 'a * 'a list;
```

Here, the `list` type is defined as either an empty list `[]` or a list constructed by using the cons operator `::` to prepend an element of type `'a` to a list of `'a` typed elements. In prefix-function form, this construction is written `op :: ('a, 'a list)`. In equivalent infix-operator form, it is written `'a :: 'a list`. The appearance of the `list` type constructor on the right side of the definition of the `list` type makes this a recursive type.

An oft-used *product type* is the tuple type. For example, a complex number can be defined as an alias of a tuple (pair, to be precise) of real numbers as follows:

```ocaml
type complex = real * real;
```

The use of the `*` operator in the definition emphatically states that a tuple type is a product type. The elements of the tuple type are unlabelled, and their order matters: `int * string` is a different type from `string * int`, even though that they both have the same information content. A tuple literal is written like this:

```ocaml
val c = (0.25, 0.0) : complex;
```

Above, we assigned the `: complex` type to the tuple `(0.25, 0.0)`—which represents the complex number $0.25 + i\ 0.0$, the cusp of the [Mandelbrot set](https://en.wikipedia.org/wiki/Mandelbrot_set). Another commonly used product types is the record type, which can be aliased like this:

```ocaml
type professor =
  { first : string
  , last : string
  , contrib : string list };
```

Above, `string list` is the list of strings, which is the `list` type parameterised with the element type `string`. Record types have labelled elements and their order does not matter: `{ id: int, name: string }` is identical to `{ name: string, id: int }`. A record literal is written as follows:

```ocaml
val milner : professor =
{ first = "Robin"
, last = "Milner"
, contrib =
    [ "Logic for Computable Functions"
    , "Hindley–Milner Type System"
    , "Meta Language"
    , "π-calculus" ] };
```

Algebraic data types may be understood in terms of their cardinalities. A sum type's cardinality is the sum of the cardinalities of its constituent data types, and a product types's cardinality is the product of the cardinalities of its constituent data types. Ordinarily, types should always be designed to admit only those values that are necessary to allow the programme to work properly, and not more. If a type admits extraneous values, the programmer is then obliged to implement runtime checks to ensure that the invalid values do not occur, which increases the possibility of programming errors. It is better to rely on the type system and let the compiler eliminate invalid values at compile time.

Most modern programming language, be they OO or FP, support an incarnation of the Hindley-Milner type system. So, today's programmers are generally familiar with the concepts of this type system. But only those who know the proof assistant hereditary of the original version of ML, the LCF/ML, recognise that type theory of programming languages corresponds to proof theory of mathematical logic. This equivalence between computation and logic is referred to as [Curry-Howard correspondence](https://en.wikipedia.org/wiki/Curry%E2%80%93Howard_correspondence):

- A type (a set, by analogy) is a proposition. A typed expression's value (an element) is a proof of the proposition represented by that type. An evaluation of a typed expression is a simplification of the corresponding proof. The type system guarantees the valid typing of the expressions and, as such, guarantees the logical validity of the corresponding proofs.
- Constructing a value of a type (an element of a set) is proving the proposition that corresponds to that type. So, creating a typed object, be it a value or a function, is proving the proposition represented by the object's type. An inhabited type (a non-empty set) is a proven proposition, which is either a lemma or a theorem. An uninhabited type (the empty set $\emptyset$), is a logical [contradiction](https://en.wikipedia.org/wiki/Contradiction) $\bot$.
- A product type (a pair) is a logical conjunction $\land$. A sum type (a disjoint union) is a logical disjunction $\lor$. The nullary product type (the `Unit` type) is the logical $True$ value. The nullary sum type (the `Void` type) is the logical $False$ value. A function from some type to the `Void` type is a logical negation $\neg$ and an absurdity $\bot$.
- A function from one type to another (a map between sets) is an implication $\implies$. Applying a function is employing [modus ponens](https://en.wikipedia.org/wiki/Modus_ponens), as in $p \implies q;\ p;\ ∴ q$. An identity function is reflexivity, a tautology $\top$. A bijective function is symmetry, an equivalence $\equiv$. A function composition is transitivity, as in $x \rightarrow y\ \land\ y \rightarrow z \implies x \rightarrow z$. A recursive function is an [inductive proof](https://en.wikipedia.org/wiki/Mathematical_induction). (Recall, from above, that a function is a product type, namely a set of pairs.)
- A [dependent product type](https://en.wikipedia.org/wiki/Dependent_type#%CE%A0_type) (dependent function type) $\Pi$ is universal quantification $\forall$. A [dependent sum type](https://en.wikipedia.org/wiki/Dependent_type#%CE%A3_type) (dependent pair type) $\Sigma$ is existential quantification $\exists$. (In dependent type theory, $\Pi$ type is a function whose *result type* depends on the *argument value*, and $\Sigma$ type is a pair whose *right element type* depends on the *left element value*.)

This correspondence clearly shows that programming is a mathematical activity, not a mere commercial trade. But why should programmers care about mathematical proofs?

Proofs are integral to CS. Traditionally, algorithm designers and programmers (those CS practitioners with a strong mathematical background) provide proofs of correctness and performance guarantees, along with the implementation. But starting in the 1970s, the scope and reach of IT expanded rapidly and coders (those without a theoretical CS background) came to dominate the workforce. As such, the tradition of providing the accompanying proofs with the code was abandoned.

Today, though, IT systems control every aspect of modern society. Correctness guarantees are thus becoming essential in application domains where life, liberty, and property could be harmed: medical, legal, law enforcement, financial, real estate, infrastructure, transportation, and defence. Current system design and development practices, even the strictest ones, are incapable of offering substantive guarantees of safety. A quick glance at technology news should convince everyone. This is where modern proof assistants with dependant type systems come to the fore.

Modern proof assistants, like [Coq](https://en.wikipedia.org/wiki/Coq), [Epigram](https://en.wikipedia.org/wiki/Epigram_(programming_language)), [Agda](https://en.wikipedia.org/wiki/Agda_(programming_language)), [Idris](https://en.wikipedia.org/wiki/Idris_(programming_language)), [Lean](https://en.wikipedia.org/wiki/Lean_(proof_assistant)), etc., are also strongly, statically typed pure functional languages with a [dependent type system](https://en.wikipedia.org/wiki/Dependent_type) based on Martin-Löf's [Intuitionistic Type Theory](https://en.wikipedia.org/wiki/Intuitionistic_type_theory), Coquand's [Calculus of Constructions](https://en.wikipedia.org/wiki/Calculus_of_constructions), or an equivalent one. Through proofs written in the same language, a dependently typed language can guarantee that the implementation satisfies the specifications. Hence, proof assistants offer a way to develop [formally verified software](https://en.wikipedia.org/wiki/Formal_verification) that meets all the performance and safety criteria.

In fact, ML was originally the scripting language (meta language) within the [LCF](https://en.wikipedia.org/wiki/Logic_for_Computable_Functions) (logic for computable functions) automated theorem prover. ML was used to write tactics that automate proofs. A tactic is a backward proof procedure that starts with the proposition being proved (the conclusion) and works backward to reach already-proven lemmas and theorems (the premises).

What is the key difference between classic automatic theorem provers and modern proof assistants? As the name suggests, *automatic theorem provers*, automate theorem proving. Given the immense difficulty of formalising mathematical proofs, however, the capability and utility of automatic theorem provers are rather limited. On the other hand, *proof assistants*, also known as interactive theorem provers, offer formalised tools and techniques of theorem proving, but rely on an interactive guidance by the user to do the proofs. Because their capabilities are augmented by the ingenuity of the programmer, proof assistants are not limited to proving simple theorems; they enable programmers to offer guarantees of correctness and performance at an industrial scale—a feat heretofore unattainable. For this reason, programmers interested in verified software should learn to use proof assistants.

What about the difference between formal proofs and informal proofs? Over the past couple of centuries, logicians have built up the field of logic by writing down detailed, step-by-step logical proofs, with an unbroken chain of reasoning from explicitly stated hypotheses to the conclusion. Those are *formal proofs*. But mathematicians, in contrast, expanded mathematics by employing *informal proofs*, which freely mixes mathematical statements with trite English phrases like "it is obvious that", "without loss of generality", and my favourite "left for the reader as an exercise". Some proofs are highly detailed and precise. Those are called *rigorous proofs*, but they are still informal. Today, the trend in mathematics is a march towards formalisation, using proof assistants and other computational tools. And these tools and techniques rely on type theory. So, think of type theory as the foundation that underlies both maths and CS.

***exceptions***—Because proof tactics can fail (a dead-end, for instance), higher-order tactics (tacticals) that manipulate tactics employ a failure detection and trapping mechanism, which is equivalent to modern exception handling facilities.

To summarise, functions represent basic computations; functionals manipulate functions to express complex computations, such as proof tactics; and, tacticals manipulate tactics to express complex control flows involving exceptions, retries, and backtracks.

There are a few general guidelines for modelling unusual situations:

- *absence*: If a value is missing and such a situation is a matter of course, represent the missing value using the `option` type. For example, the middle name field in a `person` record would be assigned the `middle : string option` type, since many people do not use their middle names.
- *salvageable*: When an undesirable, but not unexpected, situation arises where it is reasonable for the programme to attempt to resolve the issue, raise an exception, trap it, and try a different tack. For example, if a graph algorithm encounters a dead end along a search path, it would raise an exception, and the control logic, upon trapping the exception, would backtrack to the previous successful step, and try a different search path.
- *unsalvageable*: When an undesirable, but not unexpected, situation arises where it is impossible for the programme to proceed, raise an exception and let the user cope with the matter. For example, it is quite common for a user to enter a malformed value for a necessary input. In such a situation, the only sensible thing the programme could do is to scold the user for his imbecility.
- *bug*: Upon encountering unexpected and irrecoverable situations (a bug)—like divide-by-zero or out-of-memory fatal error—it is appropriate to let the programme $⊥$ and force the programmer to fix the bug during testing.

Do keep in mind that these are mere guidelines. The programmer must use his technical judgement and his domain knowledge to represent exceptional situations precisely and logically to suit the application.

***modules***—Like other languages, ML supports modules. But ML's module system is unique and powerful. ML modules can be parameterised with other modules. This facility is called [*functors*](https://en.wikipedia.org/wiki/Functor). In category theory, a functor is a structure-preserving map from one category to another category: $F: C → C'$. In ML, a functor $F$ parameterises a container module $C$ with a content type $𝛼$, which can itself be a module, and returns a newly parameterised container module $C_{𝛼}$.

It is common practice in programming to use modules to implement [abstract data types](https://en.wikipedia.org/wiki/Abstract_data_type), such as complex numbers, lists, vectors, matrices, stacks, queues, trees, graphs, and so on. For example, using ML's functor facility, we may parameterise the module `matrix` with the `real` primitive type or we may use the `complex` abstract data type as the type parameter. The parameterised types thus obtained—`real matrix` and `complex matrix`—are equipped with the usual matrix operations, which are implemented in the `matrix` module.

ML supports a domain-specific language (DSL) for modules and functors. This module DSL allows the programmer to specify relations and constraints among the modules. This constraint description language is roughly similar to SQL's foreign key specification facilities. ML has no *ad hoc polymorphism*, like C++'s virtual functions and Haskell's type classes, but functors provide a powerful alternative.

An ML module comprises a signature file and a structure file. The signature file is analogous to the C `.h` header file and the structure file to the C `.c` implementation file. Think of it this way: signatures in ML's module language are analogous to types in ML's core language; structures are analogous to values; and functors are analogous to functions, except that the module language exists at an abstraction level higher than that of the core language.

***advice***—At present, FP is enjoying its yet-another round of interest surge in the industry. As such, many experienced programmers are embarking on their quest to conquer FP. Almost universally, experienced programmers today have a strong, and exclusive, background in Java, C#, or another similarly entrenched OO language. To learn FP, Java programmers choose Scala, C# programmers F#, Android programmers Kotlin, and iOS programmer Swift. These are all fine, modern, hybrid OO-FP languages. However, since these hybrid languages tend to lean more toward OO than FP and since experienced programmers are already fluent in OO, they end up using the FP syntax to write OO semantic programmes. And the design of these languages encourage this abomination.

I have seen many OO experts who tried to take up FP suffered the indignity of being unable to think functionally, because they focused on using the FP language's syntax instead of studying the FP paradigm's semantics. Indeed, most did not even bother learning recursion; they resort to the built-in imperative looping constructs provided by these hybrid languages. Furthermore, because these popular languages lean heavily toward the industry, most books written about these languages focus on industrial-strength applications. And being so new, few good introductory books exist for these languages, and even those precious few introductory books focus on implementation, not FP theory. Learning FP concepts in these industrial-strength hybrid-OO languages and from these practice books about enterprise-scale line-of-business software development is a fool's errand: the built-in OO facilities reinforce the old OO habits, and the new FP syntax gives the illusion of learning FP concepts.

It would not do to point out that the student using a modern, industrial, hybrid-OO language to learn FP merely needs to avoid using OO facilities and advanced features of the language. The very purpose of a learning language is that it does not burden the novice with extraneous bits and bobs.

A better way to learn FP is to immerse oneself in theory textbooks, and to use a simple, unadorned FP language, like Scheme or ML. There are numerous introductory FP textbooks written for these languages because, due to their inherent simplicity, they have been used extensively in university CS programmes for decades. Even Haskell, which is famous for its pro-researcher, anti-novice stance, is better for learning FP, when compared to the industrial, hybrid languages. And there are many good, introductory textbooks and articles on Haskell, all written by long-time FP researchers and professors.

Know this. There is no one correct way to learn FP, and there are a great many incorrect ways to learn FP. Given the theory-centric nature of FP, though, a sensible approach is to study the theoretical foundations (𝜆-calculus, type theory, category theory, and so on) and the semantics of FP, instead of merely skimming for the novel FP syntax. The syntax of a programming language is important to an experienced practitioner, because a clean, quiet syntax enables him to be productive, both in creating new programmes and in maintaining old ones. But for a novice, the semantics of the programming paradigm holds a greater import for, without comprehending the fundamental concepts, he cannot create good programmes, no matter the language.

A few words of caution is appropriate, here. Some FP enthusiasts admire purity so much that they become puritanical, others wrap themselves in cloaks of theoretical abstractions, and many fence themselves inside walls of complicated types. These activities are intellectually appealing, for sure. But such exuberance makes things unnecessarily complex. Complexity is poison to commercial projects.

Lastly, there are two groups of people who work with a programme over the course of its lifecycle: writers and readers. Writers prefer convenience; readers favour clarity. Because only a few people will write the code but many people will read the code, it is equitable to insist that the needs of many readers should outweigh the wants of few writers. So, when working on an enterprise-scale application with other programmers, write clear, succinct, documented code that implements plain solutions first, then pursue eloquent abstractions and efficient implementations, only when such extravagances are justifiable—intellectually, socially, commercially.

# RELATIONAL

Technically speaking, any language could be augmented with RP facilities. Indeed, there are countless "data query" languages: GraphQL, LINQ, OQL, Tutorial D, XQuery, etc. Some of these are hierarchical, others are relational. But SQL is the only RP language in use in the industry, today.

SQL was standardised rather early in the language's lifecycle. But because the language was enmeshed into the database product, each vendor has put its unique gloss on the language to distinguish its product. Moreover, the SQL standard itself has mutated through the years. Hence, there are many versions of standards and even more custom extensions. The name "Standard SQL" is thus a cruel joke. SQL is in good company, though; it share with JavaScript the same philosophies on what it means to be standardised.

To master SQL and the RP paradigm, study these:

- Study this introductory textbook on logic, sets, relations, and functions. This book is written for first-year CS students, so it is accessible to all experienced programmers.
  - *[Discrete Mathematics with Applications](https://www.amazon.com/Discrete-Mathematics-Applications-Susanna-Epp/dp/1337694193/ref=sr_1_4?dchild=1&keywords=discrete+mathematics&qid=1634436704&sr=8-4)*, Epp
- Study this famous introductory textbook on relational database (RDB) theory to learn the fundamental database concepts such as normal forms; to understand how database concepts like tables, rows, columns, etc., map to mathematical concepts like relations, tuples, attributes, etc.; and to see how SQL code maps to mathematics. This is the most readable RDB theory textbook.
  - *[An Introduction to Database Systems](https://www.amazon.com/Introduction-Database-Systems-8th/dp/0321197844/ref=sr_1_2?dchild=1&keywords=c+j+date&qid=1634436995&sr=8-2)*, Date
- Download an open-source database product. The most established one is PostgreSQL.
  - [PostgreSQL](https://duckduckgo.com/?q=PostgreSQL&ia=web)
- Read a practice-oriented book for the chosen product to learn about installation, administration, maintenance, optimisation, and so on.
  - *[SQL QuickStart Guide](https://www.amazon.com/SQL-QuickStart-Guide-Simplified-Manipulating/dp/1945051752/ref=sr_1_14?dchild=1&keywords=introduction+to+sql&qid=1634437144&sr=8-14)*, Shields
- Download and experiment with an open-source data set of adequate complexity and intricacy to gain experience in manipulating data using SQL.
  - [Open Data](https://www.freecodecamp.org/news/https-medium-freecodecamp-org-best-free-open-data-sources-anyone-can-use-a65b514b0f2d/)

## *RP concepts*

The relational model, the mathematical foundation of relational databases, is built upon first-order logic and relational computation model. Relational computation can be accomplished through imperative relational algebra or, equivalently, through declarative relational calculus. Relational calculus is taught in academia, and relational algebra is used in industry.

*First-order logic* is one of the foundations upon which RP rests. This logic system allows construction of logical sentences using quantifiers $∀$ (universal quantifier), $∃$ (existential quantifier); negation $¬$; connectives $∧$ (conjunction), $∨$ (disjunction), $→$ (implication); and comparisons $<$, $≤$, $=$, $≥$, $>$.

In *relational algebra*, operands are relations and operators manipulate relations. Relational operators include $∪$ (union), $∩$ (intersection), $×$ (cross product), $-$ (difference), $σ$ (tuple selection), $π$ (attribute projection), several variants of $⋈$ (join), and $ ρ$ (renaming). A relation, an operand, can be viewed as a 2D data grid. The $σ$ operator extracts the specified tuples (rows) form the grid, and the $π$ operator extracts the specified attributes (columns) from the grid.

In mathematics, a relation $R$ over sets $X$ and $Y$ is a subset of their Cartesian product. In relational theory, a relation $R$ is a set of $(a_1, a_2, ...)$ tuples where each attribute $a_i$ is a member of some domain $D_i$.

In database practice, a table (relation) `t` that contains a collection of records `r[i]`. Each record (tuple), in turn, contains a collection of field values (elements) `f[j]` drawn from their respective columns (sets) `C[j]`:

```
t = [ r1
    , r2
    , ... ] where
      r[i] = [ (f1, f2, ...) | f1 ← C1, f2 ← C2, ... ]
```

In practical terms, if a record represents a person, the constituent fields collectively represent a person's characteristics, and the table represents the collection of all the people.

## *SQL concepts*

Just as FP language ML is a realisation of λ-calculus, RP language SQL is a realisation of relational calculus. But ML is not a faithful to the ideals of λ-calculus; ML includes imperative facilities. Likewise, SQL deviates from relational calculus, and includes imperative elements.

The theoretical aspiration of RP was to provide a pure, declarative computation model. Users specify the data they seek declaratively, and the database system handles the imperative details to retrieve and return the specified data. But in practice, databases and their SQL implementations deviate from the declarative computation model. Indeed, real-life applications use the database as a global data structure. Much like a PP programme mutates its global programme state to propel computation, a typical database-backed application mutates its global data structure stored in the database to make progress.

SQL's support for relational algebra includes the following operations:

- `union` is $∪$
- `intersect` is $∩$
- `select t1.c1, t2.c2 ...` is $×$
- `select * ... where ...` is $σ$
- `select c ...` is $π$
- `select ... join ...` is $⋈$

But SQL's claim to fame is its English-like statements. While this natural-looking syntax is loved by novices, experienced programmers detest the clunky syntax, because its irregular forms make it difficult to generate SQL code automatically.

SQL divides its statements into definition, control, manipulation, and query sub-languages:

- The *definition* sub-language comprises `create`, `alter`, `drop`, and other commands that modify the schema (structure).
- The *control* sub-language comprises `grant` and `revoke` commands that modify access privileges.
- The *manipulation* sub-language comprises `insert`, `update`, `delete`, and other commands that mutate the data.
- The *query* sub-language comprises `select` command that retrieves the data and formats the results. During normal operations, only `insert`, `select`, `update`, and `delete` (CRUD) statements are used.

# CONCLUSION

In this article, I described the four most prominent programming paradigms in the industry: procedural, objective, functional, and relational. I present roadmaps of key concepts in each paradigm. And I suggested learning the four iconic programming languages in each paradigm: C, Smalltalk, Standard ML, and SQL. I gave the reasons why these languages should be studied, despite their age, or perhaps because of their age. The longevity of these languages is a dispositive proof of their significance in CS.

As I said earlier, this article is written programmers experienced in one, or a few, languages, all of one paradigm. Today, many senior-level developers work exclusively with JavaScript and OO. Some of those developers maybe interested in FP, due to the resurgence of FP popularity in the industry. This article is aimed at guiding them explore beyond their comfort zones and to expand their domains of knowledge.

But be forewarned: do not blindly follow industry trends. Trends are important, surely, for if we do not keep pace, we are bound to become obsolete, quickly. But chasing trends without understanding the fundamentals is a recipe for headache and hart failure. Having the theoretical knowledge of the four paradigms and possessing the practical skills in the four influential languages will equip one with adequate background to pick up any new language that may become popular in the future.

Many developers today only following industrial trends, but completely ignoring academic progress. This is potentially career-killing. Acquisition of practical skills must be balanced with accumulation of related theoretical knowledge, for one cannot exist without the other. Most importantly, stay humble, and keep learning.
