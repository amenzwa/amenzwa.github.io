---
title: "Programming Paradigms"
tags:
  - mathjax
use_math: true
---

# INTRODUCTION

To be an efficient programmer, one must master the art of software design and the science of computing (CS). To be an effective thinker, he must learn multiple programming languages from different programming paradigms. In the article *[Programming Languages](ProgrammingLanguages.md)*, I described the different programming paradigms and enumerated a representative list of languages to learn within each paradigm. That article gave a broad overview of programming languages that are currently popular in the IT industry. In this article, I show a way to go beyond merely knowing a few programming languages to mastering various programming paradigms.

Note that this article is about exploring, learning, and mastering various programming paradigms. It is a study guide, a roadmap as it were, to learning various programming paradigms, not a tutorial on particular programming languages. Being that this is a high-level, conceptual presentation of programming paradigms, code examples are used sparingly, only where a specific syntax promotes presentation clarity. The reader is expected to study the sources materials mentioned to learn the details of the languages and the paradigms. To put it another way, this guide is written for advanced programmers who wish to expand their theoretical knowledge and programming skills in order to bolster their software development careers, not for novices who are merely seeking to learn a language to secure a programming job.

The secondary audience is CS students who are interested in programming language design. All CS undergraduates are introduced to multiple programming paradigms. This article provides tips to these students on how to master various programming paradigms.

There are many programming languages in popular use, and there are equally many ways to learn these languages. But knowing a language does not make one an expert in the paradigm. Indeed, there is but one way to master a programming paradigm: by repeatedly using the design idioms of the paradigm and by writing many programmes in a canonical language of that paradigm.

A novice programmer, say a first-year CS student, typically learns his first programming language this way:

- Study the language manual written by the language designer, focusing on the syntax.
- Implement small programmes suggested by the end-of-chapter exercises.

The goal of a novice, at this early stage, is to learn how to use the language, especially the syntactic elements of the language. This practical knowhow, alone, will not make him a good programmer, however. To become a well-rounded programmer, the novice must additionally study CS theory: discrete mathematics, algorithms, complexity theory, and so on. Those interested in CS education may read my article, *[Computer Science Curriculum](CSCurriculum.md)*.

An experienced programmer, especially one who has already learned a handful of different languages, picks up a new programming language in a very different way:

- Study the language manual written by the language designer, focusing on the semantics.
- Implement small projects, either from the exercises or from his repertoire of favourite problems.
- Apply the language in a commercial setting, thereby deepening his knowledge of the language.

When a conscientious programmer studies a new programming language, he not only learns the static, syntactic structures of programming languages, but also absorbs the dynamic, semantic behaviours of various programming paradigms to which these languages belong. And he takes in a bit of historical background of both the paradigm and the language. He reads the texts (yes, plural) that have been written about that language, preferably by the one who designed the language or by those who are active in that community. He does the end-of-chapter exercises in the texts. His reading list includes definitive textbooks, academic papers, and official online documentation. For a more effective learning, he additionally employs the paradigm's prescribed design techniques and the language's preferred implementation techniques to solve a few pet problems that are substantive but not too complicated—for instance, graph algorithms, neural network algorithms, computer graphics algorithms, or comparable ones. This is the most effective, proven way, regardless of whether one is learning the language in a formal, classroom setting or in an informal, bedroom setting.

An expert programmer masters a programming paradigm as follows:

- Study the underlying theories of the paradigm, and identify the concepts that distinguish the paradigm.
- Study a canonical language of the paradigm, focusing on the language's support for the key concepts.
- Implement small projects to master the implementation practices of the language.
- Implement a large project to master the design theories of the paradigm.

One learns a programming language for these reasons: because it is commercially *successful* in the industry; because it is intellectually *influential* in academia among programming language designers; or because it is *both* influential and successful. Below, I suggest a way to master four languages in four different paradigms. Absorbing these languages and their respective paradigms will equip one with the fundamentals necessary to pick up new languages that are, or may become, popular.

# PARADIGMS

There are two predominant programming paradigms: the *imperative* paradigm, which reflects the way the computing hardware performs its work, and the *declarative* paradigm, which reflects the way the computer scientist thinks about his work.

***imperative paradigm***—Within the imperative paradigm, there are three divisions: machine programming (MP) languages, procedural programming (PP) languages, and object-oriented (OO) languages.

*MP* languages are the assembly languages for various instruction set architectures, be they actual hardware or virtual machines. Today, very few programmers read, let alone write, in assembly. Only compiler writers regularly deal with assembly. The most prominent MP languages at present are ARM, Intel, JVM, and CLR.

As for *PP*, the classic languages of this paradigm include FORTRAN, COBOL, ALGOL, C, and Pascal. Of these, only C remains in extensive use. But the linguistic innovations that originated in ALGOL live on in most languages that are popular today, including C. Hence, ALGOL is considered an influential language, although it never attained the commercial success of its contemporaries, FORTRAN and COBOL.

Classic *OO* languages are Simula and Smalltalk. Both are all but dead, but their intellectual descendants include C++, Java, C#, and just about every new language that emerged in the past decade or two. OO is, by far, the most successful programming paradigm in the industry. The persnickety nature of MP is quelled by the high-level constructs of PP languages, and PP's laissez-faire attitude toward code organisation is tamed by the OO concepts of class, inheritance, objects, and methods. It could be said that OO is the most evolved expression of the imperative paradigm.

***declarative paradigm***—The declarative paradigm, too, has three divisions: functional programming (FP) languages, relational programming (RP) languages, and logical programming (LP) languages.

*FP* languages are realisations of λ-calculus, a theoretical framework for describing computation. FP languages emphasise creation, application, and manipulation of functions as values. Classic FP languages include LISP, ISWIM, and ML. LISP lives on in popular, modern languages like Racket and Clojure. ML is still used extensively in academia as the introductory language for first-year CS students.  Through the decades, there have been many great ML textbooks written by prominent FP researchers and professors. ML is the only language in popular use that has a comprehensive theoretical description. And ML's type system, syntactic facilities, and semantic elements appear in most new languages that came about over the past several years, including Haskell, OCaml, Rust, Kotlin, and Swift. Hence, ML is highly influential intellectually, though not successful commercially. ISWIM is a conceptual language. Although it was never implemented, the concepts it pioneered were adopted by ML and the descendants of ML. As such, ISWIM is indeed the most influential FP language.

In set theory, a relation is a generalisation of a function. Compared to a function, a relation has less stringent mathematical constraints. This laxity endows the relation with more expressive power, as well as with more theoretical pitfalls, than the function. *RP*, based on relational theory, is a generalisation of FP. RP emphasises creation and manipulation of relations, which are commonly referred to by practitioners as tables. The only RP language in popular use today is SQL. It has been in a sustained, intense use in the industry for five decades. In a way, SQL is about as successful as C. But unlike C, SQL has evolved and mutated, extensively and frequently. And just as C's domain is system programming, SQL's domain is database programming. Almost all non-trivial, modern web and mobile applications use SQL to store and manipulate data. An application typically uses embedded SQL, directly. Alternatively, an application may use an ORM API or a REST API, and the API in turn uses embedded SQL.

*LP* is even more theoretical than RP and FP. LP is based on formal logic, a foundation of computation, philosophy, law, and several other fields. LP emphasises definition, derivation, and evaluation of logic rules. A well-written LP programme is capable of performing automated logical proofs. Proofs have always been the Holy Grail of AI research. It could be said that LP is the highest expression of the declarative paradigm. As with RP and SQL, the only LP language that remains in use today is Prolog and, not surprisingly, only in academia.

***different but equivalent***—Programming paradigms provide different, but equivalent, ways to solve problems. All paradigms are equivalent in that they are all designed to aid in the production of software. But they are different in that each paradigm espouses a unique philosophy. The right choice of paradigm and language depends on the problem at hand.

Compare the data manipulation philosophies, for example. An imperative programme mutates its state. It initialises a central data structure by loading the input data into it, and evolves this programme state by mutating it using various procedures. On the other hand, a declarative programme incrementally evolves its state, without maintaining a central data structure. It passes the input data through a pipeline of functions where each function incrementally computes its output based on its input but without mutating that input. At the end of execution, however, both programmes produce the same results from the same set of inputs. Typically, applications that are close to the computing hardware are written in imperative languages, and applications that are close to the human mind are written in declarative languages.

Today, PP is used almost exclusively in system programming. OO is predominant in business computing, but its use is widespread in system programming, too. Until recently, FP was used primarily in academic research and scientific computing but, of late, FP has become the IT industry's darling of the day. It took the industry four decades to appreciate all that FP has to offer. As mentioned above, RP is used only in database programming, but all modern applications use databases, so RP is significant. MP is used exclusively for hardware-proximate uses, such as operating systems, games, and microcontroller, and even in those domains, only rarely. In the heyday of AI in the 1980s, LP (Prolog) was nearly as prominent as LISP. But now, LP is confined to academia. Since this article is aimed mainly at enterprise programmers working in the IT industry, I shall discuss only PP, OO, FP, and RP paradigms.

## *procedural*

C is the quintessential PP language, which is now more than half-a-century old. Indeed, C is the most successful PP language still in heavy use. Despite its age, C has remained essentially unaltered over time, because its design, from the very beginning, matched its purpose: for creating software that hugs the hardware, such as infrastructure application, operating system (OS), device driver, digital signal processing (DSP), etc.

The newer Nim language has a clean syntax, a static type system, and a customisable garbage collector. It compiles to C first, then uses the C compiler to generate the executable. As such, Nim programmes run anywhere C programmes run, and they perform about as fast as C programmes. Like C, Nim is purely PP, but supports OO and FP, naturally. Hence, for business, scientific, and system programming on an enterprise scale, Nim is the better choice over C. Due to its simplicity, Nim is also well suited to novices. However, C remains the gold standard for PP languages. As such, all programmers should learn C, at some point in their careers.

To master C and the PP paradigm, study these:

- The de factor industry standard C compiler has long been the GNU `gcc`, which comes with macOS, a modern UNIX, and Linux. To prevent developing mental disorders in the future, one should not learn C programming on Windows.
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

### PP CONCEPTS

In PP, the key organising principle is the procedure. A *procedure* is a named sequence of statements. Ordinarily, a procedure, by its constituent statements, accesses and mutates some global data. This behaviour is referred to as *side effect*. The behaviour of a procedure can be controlled by providing it a set of input parameters. Although a return value is not mandatory, a procedure can return a result.

Outwardly, a procedure resembles a function. But a mathematical *function* does not have side effects; its behaviour is entirely defined by its set of input parameters. And a mathematical function always returns a meaningful value.

A PP programme is designed by grouping reusable behaviours into procedures. At runtime, the distinguished main procedure first initialises the global data structure, then invokes other procedures. These procedures, in turn, invoke yet lower-tier procedures. Programme execution proceeds, procedure-by-procedure, statement-by-statement. When the global data structure has been manipulated into its final desired form, the programme execution is deemed complete.

Large PP programmes often use modules as the next higher level of programme organisation. A *module* contains its own data and procedures, which other modules may use.

### C CONCEPTS

C is a small, simple language; it can be learned in a day. But it takes an ordinary programmer a couple of years to master the language. The reason for this difficulty is that although the language is simple, it is very close to the hardware. As such, the programmer is exposed to the intricacies of the hardware. The programmer must develop a mechanical sympathy for the computer. He must first acquaint himself with the computer's architecture, before he could wield C's power.

C is armed with a low-level facility call pointers, which are numerical values that represent memory addresses in the underlying hardware. Pointers are unheard of in modern programming languages, but C without pointers is unthinkable. Through pointers, a programme can directly access and control hardware resources—RAM, ROM, graphics card, hard disc, network port, etc.—as through they are memory addresses. The concept of pointers has haunted many generations of young C programmers, because these novices usually try to learn C without first studying computer architecture. The above-mentioned introductory books on architecture and UNIX help a novice to develop a high-level mental picture of how the memory is organised, how the CPU addresses a memory location, how the CPU accesses contents of a memory location, how the C compiler allocates the memory, and how UNIX manages the memory. Once these concepts have been absorbed, pointers become second nature to the hardware-minded programmer.

C's high-level abstraction facilities are `union`, `struct`, function, and module. In category theory terms, a `union` is a sum type and a `struct` is a product type. They are used to group primitive data types, like `char`, `int`, `float`, etc., into compound data types. A common technique for structuring complex data hierarchy is to create a top-level compound data structure, which contains several lower-level compound data structures. For time and space efficiency, higher-level data structures typically contain pointers to, not copies of, lower-level data structures.

A *function*, which is C's term for PP's procedure, can accept primitive data types, compound types, and pointer types, and a function can also return those types. C has no support for higher-order function, but a C function can accept and return a function pointer, which is just the name of the function. This ability can be used to simulate some of the behaviours of higher-order functions.

Primitive and compound data types are sometimes referred to as *concrete data types*, in a sense that the data they contain are tangible and can be manipulated directly by functions. In contrast, *abstract data types* hide the internal representations of their constituent data; only operations (functions) that create and manipulate them are visible to other code. Users of an abstract data type does not know, and does not care, how the constituent data are represented and manipulated internally; the users access an abstract data type using only the published operations.

A typical C programme is divided into *modules*. Physically, a module is a file. Conceptually, a module represents an abstract data type. Variables and functions adorned with the `static` modifier cannot be access from outside the module. C modules are a rudimentary, but an effective, abstraction mechanism. This technique is adopted and enhanced by later OO and FP languages.

C employs a static type system, but a rather weak one at that: it provides no substantive type safety. Programmers, thus, rely on an elaborate set of conventions and idioms as a form of manual type safety protocol. The combination of a weak type system and a permissive, pointer-based memory access techniques make C programmes prone of many kinds of runtime errors, which invariably result in the all-too-familiar console message, "Segmentation fault (core dumped)". This message means that the programme had somehow trampled upon a region of memory not allotted to it, and as a consequence UNIX has forcibly terminated it and has preserved its memory state in a file named `core` for later examination by the programmer using low-level debugging tools. Modern C programmers do not use such low-level tools; instead they use a sophisticated, GUI-driven IDE with an integrated debugger.

***purpose of C***—It is important to recognise that C was created to implement operating systems at a time when even the most expensive computers had a 24-bit CPU and 1 MB of RAM, and many had only a 16-bit CPUs and 16 KB of RAM. The ability directly to manipulate the hardware was of paramount importance to C. The designers did not equip C with sophisticated high-level abstraction facilities, because such features were unnecessary for the intended purpose and they would only have bloated the language. Although C was used on many enterprise-scale projects in the 1980s, it was clear to everyone that this was not the application domain that suited C. OO thus came to the rescue. Today, C has returned to its roots: small-scale, hardware-level programming. Hence, an experienced programmer who uses C should be familiar with at least one microcontroller platform, such as the popular ARM Cortex-M family.

Do note that C, the language, is eminently capable of handling any level of complexity. It is the average C programmer who cannot. Very few large projects now use C. The Linux kernel is one of those few. This famous open-source project admits into their midst only the most proficient C programmers.

## *objective*

In the 1990s, the IT industry was consumed by an almost-irrational enthusiasm for OO. There were many reasons why the industry adopted OO wholesale, but the primary motivator was the desire to manage the rampant increase in software complexity.

OO concepts were pioneered by Simula in the early 1960s, as an OO extension of ALGOL, a PP language. Simula's forte was discrete event simulation, which was an ideal playground for OO. Theoretical developments trickled in during the 1970s and 1980s. By the early 1990s, OO had matured, theoretically and practically. OO's coming of age coincided with the advent of RISC, which represented a massive jump in hardware sophistication. This hardware revolution empowered software to do much more than was possible, previously.

The 1990s saw the rise of distributed computing platforms, like Sun's RPC, OSF's DCE, OMG's CORBA, and most importantly, CERN's WWW. These advances inevitably resulted in rapid rise in software complexity. The most dominant language of the time, the hardware-centric C with its lax attitude toward software abstractions, was unequal to the task of cope with this increased complexity. The industry looked to OO as the solution to managing software complexity, and OO delivered in spades.

Although Simula is to be credited as the progenitor of OO, it was Smalltalk, with the backing of a corporate giant Xerox, that popularised OO in the industry, in the 1970s. And by the mid 1980s, C was being used extensively in the industry on a large scale. Soon, C was found to be lacking in its ability to handle enterprise-scale software complexity. Objective-C was created by melding Smalltalk and C.

The NeXTSTEP OS adopted this little-known language in the late 1980s, and propelled Objective-C into the pantheon of modern languages. NeXT was to be Apple 2.0, and the original MacOS was the embodiment of Smalltalk's legendary MVC GUI. Naturally, NeXTSTEP was powered by Objective-C and MVC.

Around the same time, Bell Labs hatched C++ by melding Simula and C, in order to create a more modern system simulation language. C++'s OO support was appealing to C programmers struggling with enterprise applications that were becoming larger and more complex. By the early 1990s, C++ was already being used for desktop GUI, business software, scientific computing, system programming, operating system, device driver, game development, and everything else.

Together, Objective-C and C++ dominated the software development industry throughout the 1990s. Today, Objective-C is still used on the modern macOS, the descendant of NeXTSTEP, but it is rapidly bing displaced by Apple's new language, Swift. And C++ is still used extensively throughout the industry, especially in performance-critical applications like VR games.

Smalltalk is now all but confined to a few remaining legacy business applications. Nevertheless, Smalltalk is considered by OO aficionados as the definitive OO language. After all, Smalltalk inspired Objective-C, Java, C#, Scala, Ruby, and loads of other OO languages in popular use, at present. Although most modern programmer knows Smalltalk is OO, not many know that Smalltalk has a decent FP support, owing to its LISP influence. For instance, Smalltalk has λ function (`[...]` block), higher-order function (method that manipulates other methods), `map` (`collect:` method), `filter` (`select:` method),  `foldl` (`inject:into:` method), continuation (`currentDo:` method), and other FP facilities. Despite its pedigree and power, Smalltalk, as the name suggests, is a small, simple language endowed with a clean, cogent syntax. This makes Smalltalk a very good first language, even for young children. The compact syntax is easy to learn, and the pure OO nature is quick to grasp. Experienced programmers in the industry cannot escape OO, and they cannot shrug their responsibility to teach the less experienced. Smalltalk simplifies the teacher's job, when teaching OO concepts to novices.

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

### OO CONCEPTS

The state of an entire PP programme is held inside a large, global data structure. Any procedure can access this data structure, at will. In large, complex programmes, this unrestrained mutation of global data leads to chaos.

OO strives to tame this chaos by holding portions of the programme state inside various objects with distinct responsibilities. The central idea of OO is quite simple: ensconce a piece of data inside an *object*, and let the object guards its data against undisciplined access by outsiders. The object allows other objects to access to its internal data only via some well-defined methods. This concept is called *encapsulation*.

Without the concept of classes, there will be no objects. A *class* is a static template from which many identical copies of dynamic objects are created and are subsequently customised to suit their individual runtime behaviours.

Classes represent the static side of OO, and objects its dynamic side. At runtime, the programme state is smeared across the myriad active objects. These objects interact and collaborate with one another by sending messages. When an object receives a message, it invokes its method that the message specifies. This method accesses or mutates the associated object's internal state, as necessary. In this way, the dispersed programme state advances in lockstep amongst the objects.

The other big idea of OO is *inheritance*. A class can inherit structure and behaviour from another class, and augment what was inherited with its own specialised functionality. C++ is a multiple-inheritance OO language; it allows a child class to inherit from multiple parent classes. But Smalltalk is a single-inheritance OO language. That means a child class may inherit only from one parent class. Smalltalk's static inheritance hierarchy of classes is a tree, the root of which is the distinguished class called `Object`. At runtime, though, the dynamic hierarchy of objects can take on an arbitrary graph structure to suit the needs of a running application.

A category theory point of view simplifies the matter: a class is a product type, and inheritance is a means by which to create a sum type from existing classes.

Designing an OO programme is a matter of finding discrete concepts, naming them, and creating classes for them. A banking simulator, for example, would have classes like `Bank`, `Teller`, `Queue`, `Customer`, `Account`, and so on.

Despite these simple, humble beginnings, however, OO has, over the years, amassed an exasperatingly unwieldy amount of glossy theories and swanky idioms, among which the SOLID principle and the GoF Patterns are the most famous. But all theories and idioms can be viewed as conventions for deciding what responsibility to assign to which class, in order to simply future software maintenance tasks.

### SMALLTALK CONCEPTS

The core concepts of Smalltalk are inheritance, class, object, method, and message, which are the fundamental concepts of OO; nothing is special, there. What makes Smalltalk special is the understated way it achieves its express power through simple design and harmonious philosophy.

The unifying principle in Smalltalk is that everything is an object. Primitive values like characters and numbers are objects. Even classes are objects. For instance, to create a new object of the `Employee` class, one sends the `new` message to the global object that represents this class which, incidentally, is named `Employee`.

Computation is performed by sending messages to objects. For example, `5 factorial` computes $5! = 120$. Here, the receiver is the `Integer` object `5` and the message is `factorial`.

The conditional expression, too, is a message: `b ifTrue: [csq] ifFalse: [alt]`. Here, the receiver `b` is an object of the `Boolean` class, the message is `ifTrue:ifFalse:`, and the message parameters `[csq]` and `[alt]` are the consequent and the alternative blocks. If `b` evaluates to a `true` value, the `[csq]` block is evaluated, and otherwise, the `[alt]` is evaluated.

A count-up loop over integers is written thus: `1 to: 10 do: [:i | i printNl]`. Here, the receiver is the `Integer` object `1`, the message is `to:do:`, and the message parameters are the `10` and the `[...]` block. Each time through the loop, the receiver's current value is passed to the block as the argument `i`, and the receiver is then automatically incremented. An equivalent loop in C is this:

```c
for (int i = 1; i <= 10; i++) printf("%d\n", i + 1);
```

The condition method and the loop method above are analogous to higher-order functions in FP, and the blocks are analogous to λ functions. Other FP influences in Smalltalk include  `collect:`, `select:`, `inject:into:`, whose FP equivalents are `map`, `filter`, `foldl`. It is not only possible, but also quite natural, to program in Smalltalk using FP techniques, such as λ functions and these higher-order functional operators.

***anecdote***—In the late 1980s, I had the opportunity to observe, up-close, the many struggles that experienced PP programmers faced when adopting OO. They were my colleagues. They were C experts. They read the excellent [*The C++ Programming Language, 1ed*](https://stroustrup.com/1st.html) (Brown Book) by Stroustrup, as we all did, in those days. C++ was but a small extension of C then, having only classes, visibility modifiers, and multiple inheritance. For a Smalltalking, C programmer like me, adopting C++ was a simple matter of learning a few syntactic quirks. But my C-is-my-life colleagues went through a year-long ordeal. They learned easily the syntactic elements, but they struggled with OO design concepts; they kept falling back into familiar C idioms, and ended up using C++ to write C programmes.

I came to Smalltalk by way of C, and assembly before that. So, a few years prior, I was in a similar situation, attempting to make PP-to-OO transition. But I did not experience that shocking ordeal, because Smalltalk was a small, simple, strictly OO language without pointers, `goto`, and other PP paraphernalia. I had no choice but to abandon my PP habits. And because, by then, I had already learnt some LISP, I was able to cognise and exploit Smalltalk's FP idioms. It was not a smooth transition, but it certainly was not an ordeal.

This experience taught me that early exposure to different perspectives is vital in one's continuing intellectual development. Learning is mostly working hard with the right attitude. Humility is the trait from which both hard work and right attitude sprang. Do not be seduced by the temptation of "my way is the only way". The best way sways in the winds of trend and time; humility does not. So, be humble. Learn.

## *functional*

Fortunes of FP seem to wax and wane in decennial cycles. LISP, the world's second high-level language (after FORTRAN) and the first FP language, came out in the 1950s. Naturally, there was much enthusiasm for both FORTRAN and LISP, because most programmers at the time were programming in various assembly languages.

But by the 1960s, COBOL held the business computing market and FORTRAN the scientific computing market, the two largest applications of computers in those early days. Programming language researchers in academia were preoccupied with ALGOL, in those days. This was not FP's time to shine.

The 1970s saw the rebirth of LISP as the definitive language for the AI expert system, which was the IT industry's obsession of the day. ML emerged during this period, too. Its strong, static type system with inferencing (Hindley-Milner type system), its clean syntax, and its theoretical foundations seduced many CS university programmes into adopting ML as their teaching language. It appears FP was on the rise again, both in academia and in industry.

In the 1980s, though, C took the computing world by storm. C was especially popular in business computing, which up till then was occupied by COBOL. C is generally regarded as a much more powerful language than COBOL, and for good reasons, too. The enthusiasm for C in the industry was keen, then, and university CS programmes that leaned toward the industry dropped ML altogether, and the lot of them went C-razy. Moreover, the hype surrounding AI expert systems in the decade prior did not yield dividend. LISP was forever tied to the downfall of expert systems. Consequently, many derided LISP in those days; some referred to it as "Lost In Stupid Parentheses".

Again, FP returned in the 1990s, in the guises of OCaml and Haskell, both descendants of ML. OCaml successfully combined its academic FP core with the industry OO hype, which was in full swing, by then. The existence of Scala, F#, Reason, and other popular languages is a vindication of OCaml's hybrid OO-FP approach. Haskell, however, took a completely different approach. It was designed by a committee of CS professors to serve as "the standard" language for pure FP research. Many theoretically-inclined university CS programmes, thus, adopted Haskell as their teaching language.

However, the 2000s were undoubtedly the age of Java. Almost overnight, Java displaced C++ in enterprise computing. Indeed, the original Web was fuelled by Java: web programmes ran on instances of Java VM, and web programmers ran on cups of Java. Java gave birth to C# and Scala directly, and it indirectly influenced many modern languages, including Kotlin and Swift.

In the 2010s, JavaScript did to Java what Java did to C++, a decade prior. But JavaScript is Java only syntactically; semantically JavaScript is a derivative of Self and Scheme. Self is a dialect of Smalltalk, and Scheme a dialect of LISP. Although JavaScript is known in the industry as an OO language, owing to its adoption of Self's class system and prototype-based inheritance, JavaScript possesses a LISP-influenced FP core. For example, JavaScript has LISP's dynamic type system, `quote` (`Symbol` class), λ function (`=>` function), higher-order function, `map` (`map` method), `filter` (`filter` method), `foldl` (`reduce` method), continuation (`await` operator), and homoiconicity (via the much-maligned `eval` function). This period also saw the resurgence of interest in FP due, in part, to many JavaScripters having adopted FRP as a means to control the complexities associated with HTTP-based distributed computing. This renewed interest in FP, in turn, heightened the industry's awareness and respect for existing FP languages like OCaml, Haskell, Scala, and Clojure, and additionally created a demand for new FP-inspired languages, like Rust, Kotlin, and Swift. If the 1990s were the era of the OO hype, the 2010s were certainly the time of the FP hype.

Now, in the 2020s, new languages are cropping up seemingly every few hours. The designers of these new languages keep injecting FP facilities into their languages, but it is plain to see that most programmers continue to use the OO facilities with which they are familiar. It is too early to say whether FP will be snubbed by the industry, again, in this decade.

For the time being, though, much enthusiasm for FP permeates the industry, especially in domains such as mathematical computing, parallel computing, and FRP. Hence, it is advisable for an experienced programmer to take up the FP paradigm.

In truth, any new language in popular use today can be used to study FP, because they all support FP, to varying degrees. But there are scant few academic textbooks for these languages. Many new languages do not have books; they only have blogs. Some have books, but they are written by, and for, those who view programming as a trade, not an intellectual pursuit. This makes it rather difficult to acquire deep insight into FP. On the other hand, OCaml, Haskell, and especially Standard ML, have extensive collection of books written by CS professors and IT practitioners alike. These books span gentle introduction to the language, heavy-duty industrial application, compiler construction, exploration of category theory, the whole gamut.

Haskell has a reputation for being difficult to learn and even more difficult to teach. Indeed, one cannot write a "Hello, World!" in Haskell, unless one understands the concept of *monad*, which is a rather high bar for novice FP programmers. OCaml is easier to learn, but its OO facilities may distract novices who are endeavouring to learn FP. And both Haskell and OCaml are large, complex languages that are continually evolving. But Standard ML, the version of ML that was standardised in 1997, is stable, has been around for a long time, and is used extensively in academia as the teaching language. As such, there are many more textbooks on Standard ML that are accessible to FP novices. And since OCaml, Haskell, and other modern FP languages either descended from or were inspired by ML, it is straightforward for an experienced ML programmer to pick up those newer languages. For these reasons, Standard ML is considered by many to be the best language in which to teach FP.

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

### FP CONCEPTS

From the perspective of state management, OO is but a gloss on PP. PP holds all programme state in a global data structure. Computation progresses when procedures mutate the global data. Of course, the procedures can mutate that global data, without restraint. On the other hand, OO apportions the programme state amongst autonomous objects who guard their own pieces of data. Computation progresses when objects exchange messages amongst themselves, which result in controlled, coordinated mutation of the disparate pieces of programme state. Despite these outward differences, both PP and OO propel computation by mutating programme state.

FP eschews the store-and-mutate way of working. Instead, FP propels computation by applying functions to input data and by producing transformed output data to be passed to the next function in the pipeline. The programme state is whatever the result happens to be at a particular moment, be it intermediate or final. If necessary, copies of the sequence of intermediate states could be saved, say for "undo" operations.

Form the programme design point of view, the whole FP programme is just a function. This top-level function accepts input data, and passes the data to other functions which it invokes, and these functions in turn invoke other lower-tier functions. The bottom tier consists of functions that implement simple expressions.

The key concepts behind FP are simple, minimalist. But FP derives immense expressive powers by composing these simple, individual concepts in a uniform way. This readily composable nature of concepts distinguishes FP from other programming paradigms, when things get complicated.

Objects in OO are, by design, can be assembled. But object assembly is different in kind form function composition. Functions compose like the individual stations are coupled in an assembly line. So long as the next station is equipped to accept the output of the previous station, the assembly line works smoothly. The arrival of the input animates a station into action. There is a unified sense of timing and flow. The traversal time through the assembly line is *linearly* proportional to the number of stations in the assembly line. By contrast, objects assemble and organise themselves rather like a group of people at an office party. People are autonomous; their individual actions are govern their internal motivations. But in a crowd, individuals regulate their actions and coordinate with the others, in accordance with applicable social norms. There is no unified sense of timing and flow. Social order emerges organically. However, the need for coordination is a form of overhead—a social overhead. And this overhead grows *exponentially* with the number of people.

Another way to look at this is that FP abstracts flow, whereas OO abstracts coordination. Abstracting something hides the finicky details thereof, in order to simplify the task. So, FP hides the low-level details associated with composition, thereby simplifying the task of composing large systems from subsystems. But because OO hides the low-level details associated with coordination, it simplifies the task of inter-object interactions. Interactions contribute to the exponential growth of system complexity. Since OO abstracts interactions, their explosive growth is hidden from view.

Now, let us switch gears and discuss a few FP terms. FP takes delight in giving ornate names to simple concepts. Below, I shall peel the arcane FP terms to reveal the simple concepts they denote.

***purity***—Mathematical functions mutate neither their input arguments nor external values. This property of functions is referred to as *purity*. Purity guarantees that FP functions will not mutate data sneakily—no side effects. By contrast, PP procedures often have side effects, usually in the form of global data mutation.

***immutability***—Because functions are pure and they do not mutate data structures, when a a function makes a modification to a data structure, it always produces a new copy of the data structure containing that modification. This property of FP data structures is known as *immutability*.

***transparency***—Functions do not maintain internal data that they secretly maintain and mutate to make hidden computation decisions. That is, a function's behaviour is defined entirely by the input parameters. The same input always yields the same output. This property of functions is called *referential transparency*.

***first-class functions***—Functions are values, just like characters, integers, reals, lists, and such. This property of functions is known as *first-class*.

***higher-order functions***—Since in FP functions are values, a function can accept another function as its argument value and a function can return another function as its result value. This property of functions is called *higher-order* functions. Higher-order functions can abstract away the low-level recursions, thereby making the task of the programmer more convenient and, more importantly, less error-prone.

Higher-order functions are also called *functionals*. The term "functional programming" is a respectful nod to this key concept of FP.

***partial functions***—In mathematics, a *total* function is one that is defined for the entirety of its domain. A *partial* function is a function that is not define for the entirety of its domain. In other words, if a partial function is given a value from its domain on which it is not defined, the computation is goes to the $⊥$.

***recursion***—Because in FP state maintenance is forbidden, counting loops are forbidden, too. The `for` loop construct in PP, for instance, maintains the loop count, which is a state. Instead, FP performs repetition with *recursion*. A recursive function is one that invokes itself, as part of its operation. Many problems in CS are hierarchically structured. At the top level, there is the original problem. This problem can be expressed in terms of smaller, self-similar sub-problems.

Take, for instance, the algorithm for computing the length of a list $l$:
$$
|l| =
\begin{cases}
  0 & \text{if l = Ø} \\
  1 + |tail(l)| & \text{otherwise} \\
\end{cases}
$$
A *list* is the tail sublist $tail(l)$ with the singleton head element $head(l)$ tacked on at the front: $l = head(l) + tail(l)$. The tail, being a sublist, can be split further in the same manner. Using this hierarchical, self-similar representation, the above algorithm computes the length of the list as follows: the length of an empty list $|Ø|$ is clearly $0$; the length of a non-empty list is the length of the head $|head(l)|$, which is obviously $1$, plus the length of the tail $|tail(l)|$, which is computed recursively on the smaller sublist. As the algorithm proceeds down the tail, the tail shortens down to the empty list. The resultant length is $1 + 1 + ... + 0$, where the $1$s stand for each element of the list, and the $0$ for the terminating empty list.

The above equation is not merely logical; it is downright intuitive. This comprehensibility and simplicity are the consequences of the hierarchical, self-similar representation, which epitomises the divide-and-conquer problem solving technique employed throughout CS. And the structure of a typical list processing solution like this matches that of the mathematical induction proof method, which means such an algorithm can be proved correct by a direct appeal to induction.

The technique we used in list processing algorithms can be extended to handle trees. A *tree* is constructed of two types of nodes: a branch and a leaf. A tree also has a distinguished node called the root, which is the ancestor of all other nodes. Branches provide a means for structuring the tree, and leaves serve as containers for values held in the tree. A tree, too, has a hierarchical, self-similar structure: any node within the tree can be viewed as the root of a smaller subtree.

Just as trees are generalisations of lists, graphs are generalisation of trees. A graph is a collection of vertices connected with edges. Vertices contain values held in the graph, and the edges represent the relationships between these values. A graph has a hierarchical, self-similar structure: any collection of vertices and edges within the graph, called a subgraph, resembles the parent graph.

In programming, lists are used to represent sequential data. Trees are used to represent hierarchical data. Graphs are used to represent networked data. A database table is a list of records. A JSON data structure is a tree. A road network is a graph. Any complex data can be represented using a combination of these three recursive data structures.

***bottom***—A computation that does not yield a result (for example, infinite recursion) or one that terminates due to a fatal error (for example, divide by zero) is called *bottom*, written $⊥$.

***strictness***—A function that returns a $⊥$ when given a $⊥$ as an argument is referred to as a *strict* function. Otherwise, that function is deemed *non-strict*.

***laziness***—FP languages use either the eager evaluation strategy or the lazy evaluation strategy. The *eager* strategy reduces every expression to its value, before proceeding with the computation. When using paper and pencil to evaluate a complex arithmetic expression, one instinctively begins the reduction from the innermost subexpression, and works outward until the entire expression is reduced to a number. This is an example of eager evaluation. ML is an eager language.

The *lazy* strategy reduces an expression to its value, only if that value is needed in the subsequent computation. Evaluating a complex expression by beginning with the outermost subexpression and proceeding inward only when necessary is an example of lazy evaluation. Lazy evaluation permits the use of infinite data structures, whose values are computed only when the need arises. Haskell is lazy language.

***currying***—Currying is a technique for transforming a multi-argument function into a single-argument version. Currying transforms $f : x, y → z$ into $g : x → h$, where $h : y → z$. That is, the multi-argument function $f(x, y)$ is automatically transformed into a single-argument function $g(x)$ that returns another single-argument function $h(y)$ which has value $x$ baked into its body. When the function $h$ is applied to value $y$, it uses both $x$ and $y$ to compute the result $z$. In FP, a multi-argument function may always be thought of as a pipeline of single-argument functions.

***partial application***—A partial application of a multi-argument function is a consequence of currying. In the currying example above, the function $h$ is a partially applied version of the original function $f$. Applying the dyadic $f(x, y)$ to only $x$ is referred to as a *partial application* of $f$ to $x$. When $f$ receives only $x$, it knows that it cannot complete the computation, and instead returns $h(y)$, which accepts $y$ and already has $x$ in its body. When $h$ is given $y$, it becomes the fully applied, so it uses both $x$ and $y$ in its computation, and returns the final result $z$.

Note that many programmers confuse the term "partially applied function" with "partial function"; these two concepts are unrelated. A partial application is analogous to the situation in which a painter is handed a 1 L can of paint and is told to paint a wall that requires 5 L to cover. He would paint as much of the wall as he can cover, but it is impossible for him to complete the job, until he is supplied with an adequate amount of paint. On the other hand, a partial function is like a painter who is famous for his intense hatred of white paint. If he were to be handed a can of white paint, he would surely blow his top in rage and, instead of painting the wall, would burn down the house.

***sections***—A *section* is a partially applied dyadic operator. For instance, when the $+$ operator is partially applied to only one value, as in $(+1)$, it automatically returns a function $g : x → x + 1$. When $g$ is applied to value $3$, it returns  $3 + 1 = 4$. The function $g$ could be used as the increment operator.

### ML CONCEPTS

***recursion***—ML uses recursion for repetition. Let us examine the factorial function. In mathematics, factorial of $n$ is defined as $n! = n × (n-1)!$ and $0! = 1$ by fiat. In Standard ML, this function can be implemented as an almost-verbatim of its mathematical definition.

```Haskell
fun fac n = if n = 0 then 1 else n * fac (n - 1);
```

When this function is invoked as `fac 3`, it computes the following sequence of function invocations that yields the result $6$:

```Haskell
fac 3
  3 * fac (3 - 1 ⇒ 2)
    (3 * 2 ⇒ 6) * fac (2 - 1 ⇒ 1)
      (6 * 1 ⇒ 6) * fac (1 - 1 ⇒ 0)
        6 * fac 0
          6 * 1 ⇒ 6
```

Each step in the evaluation of `fac` contains a call to itself. This is the simplest form of recursion. The symbol $⇒$ above means "reduces to".

This simple recursion can be transformed into *tail recursion*. In a tail recursion, the final step in the function is a recursive invocation of itself without additional computation. In the simple recursion version above, the final step in the `else` branch is `n * fac (n - 1)`. That means the result of the recursive invocation `fac (n - 1)` is an intermediate step, not the final step. The tail-recursive version of `fac` is this.

```Haskell
fun fac n =
  let fun fac' a n = if n = 0 then a else fac' (a * n) (n - 1)
  in fac' 1 n end;
```

This version of factorial defines a local, auxiliary function `fac'`. In mathematics, the prime symbol $\_'$ is used sometimes to represent a quantity that is similar but subtly different. ML family of languages—Haskell, OCaml, F#, Reason, etc.—use this mathematical convention to label subtly different quantities, as we did here with `fac` and `fac'`. When this version of `fac` is evaluated as `fac 3`, the tail recursion proceeds as follows, yielding the same result $6$.

```Haskell
fac 3
  fac' a=1 n=3
  fac' a=(1 * 3 ⇒ 3) n=(3 - 1 ⇒ 2)
  fac' a=(3 * 2 ⇒ 6) n=(2 - 1 ⇒ 1)
  fac' a=(6 * 1 ⇒ 6) n=(1 - 1 ⇒ 0)
  a=6
```

Unlike the simply recursive version, the compiler transforms tail-recursive calls into the CPU's jumps instructions, thereby eliminating space and time overheads associated with function calls. In other words, the sequence of calls to `fac'` above are evaluated within the same stack frame as the call to `fac`. In essence, the compiler transformed this tail-recursive call into a `for` loop.

I have written the consecutive calls to `fac'` without indentation to highlight the absence of function invocations. And for clarity, I have also labelled the arguments of `fac'` with an `a` and an `n`. The `a` here means "accumulator". The use of a local function and an accumulator to transform a simple recursion into a tail recursion is a common practice in FP.

***functional operators***—Recursion is essential. Recursion is elegant. In FP , recursion is everywhere: data structures are recursive, and the functions that operate upon them are recursive. The recursive structure of the list length algorithm we examined above appears in computation of the sum of a list of numbers, the product of a list of numbers, to concatenate a list of string, and so on.

Recursion is an abstraction over repetition. But now, we see that recursion itself is getting repetitive, the same recursive form appearing in many different algorithms. It tuns out that this recursive solution structure can be abstracted into a higher-order operator `foldr` (fold right). This operator collapses a sequence of values into a single value, starting from the right. This functional operator uses an externally supplied collapsing function. In the case of list sum, that collapsing function is the $+$ operator. In the case of list product, it is the $×$ operator. In the case of list of strings, it is the string concatenation operator.

The list length algorithm above can be implemented in Standard ML like this.

```Haskell
fun len [] = 0
  | len (x::xs) = 1 + len xs;
```

The recursive structure of the `len` function can be captured using `foldr` like this.

```Haskell
List.foldr (fn (_, a) => 1 + a) 0 xs;
```

The expression `fn (_, a) => 1 + a` is the collapsing λ function, which uses an accumulator `a`. The $0$ is the initial value for the accumulator. And the  `xs` is the list whose length we are computing. The left-start counterpart of `foldr` is `foldl`. The `fold` operator has many other superpowers, but its main use is to collapse a sequence of values into some form of a summary value.

Another oft-used functional operator is `map`, which applies the supplied λ function to the list. Whereas `fold` collapses the list into a single value, `map` preserves the original structure of the list. This is how to apply a squaring λ function `fn x ⇒ x * x` to the each element of the list `xs`.

```Haskell
List.map (fn x => x * x) xs;
```

The `filter` functional operator, too, is commonly used in daily programming. It applies the supplied λ function predicate to the list to select the desired elements. For example, we can filter out elements of `xs` that are greater than $5$ like this.

```Haskell
List.filter (fn x => x > 5) xs;
```

***strictness and eagerness***—The language's evaluation strategy determines the strictness of the functions defined in that language. Consider a Standard ML constant function, a function that returns a constant, no matter the value of the argument:

```Haskell
fun constant x = 9;
```

In an eager language like ML, if this function is invoked as `constant (1/0)`, the computation yields the $⊥$, because the eager evaluation strategy reduces the input expression `1/0` first, before invoking the `constant` function. That reduction immediately produces the divide-by-zero error. But in a lazy language like Haskell, this computation results in `9`, because the lazy evaluation strategy passes to the `constant` function the unevaluated input expression `1/0`. Being a constant function, `constant` simply ignores the input expression, and returns `9`. Hence, functions are strict in an eager language, and they are non-strict in a lazy language.

***types***—ML was the first FP language to use the Hindley-Milner type system. This type system is static, strong, inferencing, and polymorphic. A *static* type system performs type checking at compile time. A *strong* type system prohibits runtime changing of variables' types. An *inferencing* type system discovers types of variables automatically during compilation, which relieves the programmer from having to supply types manually, as is the case in C and Pascal. And a *polymorphic* type system allows containers, like lists and trees, to hold values of different types: `int list` is a list of integers; `float list` is a list of reals.

***modules***—Like other languages, ML supports modules. But ML's module system is unique and powerful. ML modules can be parameterised with other modules. This facility is called *functors*. In category theory, a functor is a map from one category to another category: $F: C → D$. In that sense, a functor in ML transforms the argument module into a new result module.

It is common practice in programming to use modules to implement commonly used abstract data types, such as lists, trees, graphs, and so on. It is also a usual practice to implement business domain models, such as task, project, workflow, etc. Using ML functors, we may create a list of tasks, a project tree, a workflow graph, and the like. ML supports a domain-specific sublanguage for modules and functors. This module language allows the programmer to specify relations and constraints among the modules. This constraint language is roughly similar to SQL's foreign key specifications.

***anecdote***—At present, FP is enjoying its yet-another round of interest surge in the industry. As such, many experienced programmers are embarking on their quest to conquer FP. Almost universally, these programmers have a strong, and exclusive, background in an OO language, JavaScript, Java, or C#. To learn FP, Java programmers choose Scale, C# programmers F#, Android programmers Kotlin, and iOS programmer Swift. These are all fine, modern, hybrid OO-FP languages. However, since these languages tend to lean more toward OO than FP and the programmers are already fluent in OO, they end up using the FP syntax to write OO semantics programmes. And the design of these languages encourage this.

I have seen many OO experts who tried to take up FP suffer the indignity of not being able to think functionally, because they focus on using the FP language's syntax, instead of studying the FP paradigm's semantics. Indeed, most did not even bother learning recursion; instead they fall back upon the built-in imperative looping constructs provided by these hybrid languages. Furthermore, because these popular languages lean heavily toward the industry, most books written about these languages focus on industrial-strength applications. Few good introductory books exist for these languages, and even those few books lean toward applications, not FP theory. This is a somewhat reckless way to wade into the deep, choppy waters of FP.

A better way to learn FP is to immerse oneself in theory textbooks, and to use a simple, unadorned FP language, like Scheme or ML. There are a great many introductory FP textbooks for these languages, because they have been used extensively in university CS programmes for decades. Even Haskell, which is famous for its pro-researcher, anti-novice stance, is better for learning FP, when compared to those commercial languages. There are quite a few good, introductory textbooks and articles on Haskell, all written by long-time FP researchers and professors.

Know this. There is no one correct way to learn FP, and there are a great many incorrect ways to learn FP. Given the theory-centric nature of FP, though, a sensible approach is to absorb theory, instead of merely skimming for the syntax. The syntax of a programming language is important to an experienced practitioner, because a clean syntax enables him to be productive, both in creating new programmes and in maintaining old ones. But for a novice, the semantics of the underlying programming paradigm holds a greater import, for without a grasp of the FP paradigm, one cannot create good designs in an FP language.

## *relational*

Technically speaking, any FP language could be augmented with RP facilities. Indeed, there are countless "data query" languages: GraphQL, LINQ, OQL, Tutorial D, XQuery, etc. Some of these are hierarchical, others are relational. But SQL is the only RP language in use in the industry, today.

SQL was standardised rather early in the language's lifecycle, but the language has continually adopted technological advances, and hence there are many versions of standards and many more custom extensions. The name "Standard SQL" is thus a bad joke. SQL is in good company, though; it share with JavaScript similar philosophies on what it means to be standardised.

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

### RP CONCEPTS

The relational model, the mathematical foundation of relational databases, is built upon first-order logic and relational computation model. Relational computation can be accomplished through imperative relational algebra or, equivalently, through declarative relational calculus. Relational algebra is used in practice.

*First-order logic* is one of the foundations upon which RP rests. This logic system allows construction of logical sentences using quantifiers $∀$ (universal quantifier), $∃$ (existential quantifier); negation $¬$; connectives $∧$ (conjunction), $∨$ (disjunction), $→$ (implication); and comparisons $<$, $≤$, $=$, $≥$, $>$.

*Relational algebra*, in which operands are relations and operators manipulate relations. Relational operators include $∪$ (union), $∩$ (intersection), $×$ (cross product), $-$ (difference), $σ$ (tuple selection), $π$ (attribute projection), several variants of $⋈$ (join), and $ ρ$ (renaming).

In mathematics, a relation $R$ over sets $X$ and $Y$ is a subset of their Cartesian product: $\{xRy\ :\ x ∈ X, y ∈ Y\} ⊆ X × Y$.

In relational theory, a relation $R$ is a set of tuples $(a_1, a_2, ...)$ where each attribute $a_i$ is a member of some domain $D_i$: $R = \{(a_1, a_2, ...)\ :\ a_1 ∈ D_1, a_2 ∈ D_2, ...\}$.

In database practice, a relation is a table `t` that contains a row collection of records `r.i` where each record comprises a collection of field values `f.j` drawn from their respective columns `C.j`.

```
t = [ r1
    , r2
    , ... ] where
      r.i = [ (f1, f2, ...) | f1 ← C1, f2 ← C2, ... ]
```

### SQL CONCEPTS

Just as FP language ML is a realisation of λ-calculus, RP language SQL is a realisation of relational calculus. But ML is not a faithful to the ideals of λ-calculus; ML includes imperative facilities. Likewise, SQL deviates from relational calculus, and includes imperative elements.

The aspiration of RP was to provide a pure, declarative computation model. Users specify the data they seek declaratively, and the database system handles the imperative details to retrieve and return the specified data. But in practice, databases and their SQL implementations depart from the declarative computation model. Indeed, real-life applications use the database as the global data structure. Much like a PP programme mutates its global programme state to propel computation, a typical database-backed application mutates the global data structure stored in the database to make progress.

SQL's relational algebra support includes the following operations:

- `union` is $∪$
- `intersect` is $∩$
- `select t1.c1, t2.c2 ...` is $×$
- `select * ... where ...` is $σ$
- `select c ...` is $π$
- `select ... join ...` is $⋈$

But SQL's claim to fame is its English-like statements. While this natural-looking syntax is loved by novices, experienced programmers detest the clunky syntax, because its irregular forms make it difficult to generate SQL code automatically.

SQL divides its statements into definition, control, manipulation, and query sub-languages. The *definition* sub-language comprises `create`, `alter`, `drop`, and other commands that modify the scheme. The *control* sub-language comprises `grant` and `revoke` commands that modify access privileges. The *manipulation* sub-language comprises `insert`, `update`, `delete`, and other commands that mutate the data. The query sub-language comprises `select` command that retrieves the data and formats the results. During normal operations, only `insert`, `select`, `update`, and `delete` (CRUD) statements are used.

# CONCLUSION

In this article, I described the four most prominent programming paradigms in the industry: procedural, objective, functional, and relational. I present roadmaps of key concepts in each paradigm. And I suggested learning the four iconic programming languages in each paradigm: C, Smalltalk, Standard ML, and SQL. I gave the reasons why these languages should be studied, despite their age, or perhaps because of their age. The longevity of these languages is a dispositive proof of their significance in CS.

As I said earlier, this article is written programmers experienced in one, or a few, languages, all of one paradigm. Today, many senior-level developers work exclusively with JavaScript and OO. Some of those developers maybe interested in FP, due to the resurgence of FP popularity in the industry. This article is aimed at guiding them explore beyond their comfort zones and to expand their domains of knowledge.

But be forewarned: do not blindly follow industry trends. Trends are important, surely, for if we do not keep pace, we are bound to become obsolete, quickly. But chasing trends without understanding the fundamentals is a recipe for headache and hart failure. Having the theoretical knowledge of the four paradigms and possessing the practical skills in the four influential languages will equip one with adequate background to pick up any new language that may become popular in the future.

Many developers today only following industrial trends, but completely ignoring academic progress. This is potentially career-killing. Acquisition of practical skills must be balanced with accumulation of related theoretical knowledge, for one cannot exist without the other. Most importantly, stay humble, and keep learning.
