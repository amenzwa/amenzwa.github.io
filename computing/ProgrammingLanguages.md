---
title: "Programming Languages"
---

# INTRODUCTION

Young people often ask me which programming language is the best one to learn. To that, I give a lawyerly answer: it depends. The truth is, there is no such thing as the best programming language. But there are many good languages from which to choose for each endeavour. And choose we must, for there are many languages, and every one was created to solve a specific set of problems. Even those so-called general-purpose languages were designed with a bias toward one set of problems or another. So, no one language can suit every imaginable problem.

Banish the thought that you can learn one best language, and can become the best programmer that you can be. At a minimum, you should learn the seminal language in each branch of the programming language family tree, provided that the language in question remains relevant to modern computing, either because it is still in prominent use or because it is an effective pedagogical tool.

Like human languages, computer languages may be thought of as belonging to different branches of family tree. Knowing languages from different branches enables you to reason about a problem in multiple ways, which often leads to efficient, elegant solutions. In other words, mastery of multiple computer languages can make you a better programmer, just as fluency in multiple human languages can make you a better communicator. Moreover, new languages are being created constantly, and each adds its own set of innovations that may turn out to be significance. Hence, over the course of your STEM career, you should continually learn new programming languages. Studying languages that the conventional wisdom says are irrelevant to your field can give you the insights not possessed by those with mere conventional wisdom.

In this guide, I shall list a handful of starter languages that I consider are essential in various STEM fields that require programming. This guide is not a tutorial on learning how to program, but an overview of what languages—yes, plural—to start learning. Note that a starter language is not necessarily easy to learn. And it may not even be one of the more popular languages used in the industry. But mastering it will give you the fundamental knowledge necessary to acquire additional programming skills and to learn new languages.

Non-practitioners tend to think that programming is all there is to software development and that software development is all there is to computer science. Not so. In truth, software development is intertwined with other human endeavours—science, technology, engineering, mathematics, law, politics, economics, competition, management, philosophy, psychology, camaraderie, and more. These topics are far afield from the scope of this guide. You will learn some of them in college, others at work, and the rest over a lifetime. Programming is but a small part of software development, and software development, likewise, is a small part of computer science.

I begin this guide with a bit of background by drawing analogies between human languages and computer languages. Next, I provide a short list of programming languages, the knowledge of which I consider are essential for refining one's programming skills. Then, I conclude with a few tips on how best to cope with the ever-changing field of software development. Along the way, I weave fragments of computing history and bits of career advice into the discussions. My intended audience is *STEMers* who wish to expand their programming knowledge and problem solving skills.

# FAMILIES

Human languages cross the chasms of time and space by evolving—they morph, they mix, they grow, they degenerate, they refine. But every language springs from a linguistic family. Each language descended from a more ancient mother language. For instance, Hindi, Gujarati, Bengali, and Urdu descended through Sanskrit, which is in the *Indic* family line. French, Spanish, Portuguese, and Italian descended through Latin, and they belong to the *Italic* family line. Similarly, English, Dutch, and German are in the *Germanic* family line. In turn, Indic, Italic, and Germanic lines trace up the family tree to an even more ancient protolanguage that formed the *Indo-European* line. Burmese, my mother tongue, rolls up to another protolanguage that founded the *Sino-Tibetan* line. There are many more linguistic family lines. But virtually all modern languages share a trait—each has an ancestor language that belongs to a family line that extends far into the past. The farther back in time we trace, the smaller the human population, and the fewer the number of different languages.

We cannot be sure, but it may well be that modern languages trace their origins back to one mother language. What we do know for certain is that all computer languages trace their origins to mathematics, the Eve of all programming languages. So, give her due regard. And like human languages, computer languages fall into family lines. Informally speaking, all computer languages sprang from three matriarchs—What, How, and Why—the daughters of Eve.

The *What* family line goes by an imposing title of “declarative paradigm”. When programming in a declarative language, you assemble the programme out of declarations, which are expressions that describe what it is that you wish to achieve, without providing any details about how to compute the result. The computer figures out the details, and computes the result you wanted. This is akin to ordering an item off the menu at a restaurant: you order your meal without having to dictate the recipe. Of course, the designer of the language had to provide in advance the operations that transform the high-level declarative expressions into low-level instructions that the computer understands. In the restaurant analogy, you are the customer, the keyboard-monitor combination is the waiter, the language designer is the executive chef, and the computer is the line cook. Haskell, SQL, and Prolog are the prominent members of the declarative family.

The *How* family line goes by an imperious title of “imperative paradigm”. In grammar, an imperative is a command or an instruction. Likewise, a programme written in an imperative language comprises a sequence of detailed instructions on how to compute the result. The computer simply follows the instructions, step-by-step. C, the most famous procedural language, belongs to the imperative family, and so do all object-oriented languages like Smalltalk, Objective-C, C++, Java, JavaScript, and practically every modern programming language.

The *Why* family line, the oldest of the three, goes by a humbler title of “assembly language”. Every processor line, such as ARM, AVR, Intel, etc., has its own assembly language. Programmes written in high-level languages are translated down to assembly language, then further down to machine code consisting of 0s and 1s, which are the only two symbols understood by the computer’s CPU. I call this family of assembly languages “why”, because once you encounter assembly language, you suddenly understand why computers do exactly as you command, but not necessarily what you wish them to do. Alternatively, you can think of it as “why bother”, because very few situations today call for the use of hand-crafted assembly language and there are very few reasons why you should bother with it at all. And here are those few, but important, reasons. If you are a hardware engineer, a digital signal processing engineer, an operating system designer, a compiler designer, or a 3D game programmer, you will, at some point, need to learn the assembly language of the hardware platform on which you work. But even if you do not work in these fields, being familiar with the hardware platform at this level of detail will give you the edge in solving intricate, difficult problems.

Now, let us look at a pair of examples to better understand the declarative-imperative dichotomy. I shall not give an example in assembly language; why bother.

Say, your local library has a large collection of novels, and you wish to know the titles of the novels written by [Jane Austen](http://en.wikipedia.org/wiki/Jane_Austen). You can walk up to the librarian and ask, thusly:

> "Can you find me the *titles* of the *novels* by the *author* Jane Austen?"

It would be becoming if you append the word “please” to your request, but since this supplicatory word has no equivalent keyword in programming languages, I left it out.

Alternatively, you can send to the library’s catalogue database the following query written in the declarative language SQL:

```sql
select Title from Novels where Author = "Jane Austen"
```

Whichever method you choose, you will receive the following result:

```text
Northanger Abbey
Sense and Sensibility
Pride and Prejudice
Mansfield Park
Emma
Persuasion
```

Note the structural similarity between the SQL query and the English request. In both cases, you focus on the *what*. The system, either the librarian or the database, takes care of the *how*. Are you [all astonishment](http://www.pemberley.com/janeinfo/ppv1n06.html)?

Now, compare the SQL query to the following sequence of retrieval instructions that would be required, if the catalogue system understands only imperatives:

```pseudocode
let Novels = {library's novel collection}
let N = |Novels|
for n = 1 to N
  let n = Novels{i}
  if n.Author == "Jane Austen"
    print n.Title
```

For clarity, I used a pseudo programming language above, instead of an actual one. And for simplicity, I used a naïve, linear search algorithm, instead of an optimal one. In this pseudo code, the first statement defines the library’s novel collection, and the second statement defines the total number of novels. Let us assume that the collection *Novels* is a set, so it contains only unique elements. Hence, even if the library has multiple copies of a novel, that novel will appear only once in this set. Next, the programme repeats the following steps for every novel in the set: retrieve one novel from the set; check if its author is Jane Austen; and if so, print its title.

Puerile, you say? Well, this is how all computers work; be thankful that humans do not. Imagine that the library staff responds only to imperatives. Then, you would be obliged to issue step-by-step instructions like this: “Walk to the aisle where shelves of novels are kept. Pick out the first novel. If its author is Jane Austen, write down its title on a piece of paper, provided that title has not already been recorded on the paper. Repeat the previous two steps, until all the novels on all the shelves have been examined. Return to this information desk. Hand me the list.” That would enrage even the meekest of bookworms.

To sum up, a *declarative* language allows the programmer to focus on the application concepts, while the language takes care of the niggly details. This yields a more expressive, succinct code. There is less work for the programmer, and fewer ways for him to make mistakes. And the programme is easier to understand, because it reflects the way humans think. To enjoy these benefits, however, the programmer must necessarily relinquish some of the control to the computer. By the way, mathematics is a declarative language.

An *imperative* language espouses a different philosophy. It gives the programmer control over the details of how the computer performs the work, thereby allowing him to make the programme work as efficiently as the computer is capable. But in exchange for this enhanced control over the programme’s behaviour, the programmer must assume the responsibility of maintaining the niggly details, like how to loop over the data collection, how to keep track of the current step inside the loop, how to use storage space efficiently, and so on. These low-level details that govern programme behaviour are referred to collectively as programme state. State management has associated costs: it distracts the programmer from his primary responsibility of solving the problem, because he must allocate a great deal of his attention to state management; it increases his workload; and it inflates his opportunities to make mistakes. Incidentally, most pernicious programming errors arise from improper state management, and not from incorrect solution logic.

## *programming paradigms*

The term “programming paradigm” means “a method of reasoning about programme behaviour”. That is, a programming paradigm emphasises a particular model of thought. The study of [programming paradigms](http://en.wikipedia.org/wiki/Programming_paradigm) spans vast tracts of the computer science landscape. But in this guide, we discuss only the three most prevalent paradigms in the industry: functional, object-oriented, and procedural. The functional approach belongs to the declarative family, and the object-oriented and the procedural approaches belong to the imperative family.

***functional***—In a *functional* programming language like Haskell, you define data types to represent application concepts and write functions that transform the data, thereby implementing programme behaviour. You start with simple functions that perform trivial calculations, then create complex functions by composing many simple ones. The functions that you write behave the same way mathematical functions like sine and cosine do: they accept input arguments, perform well-defined sets of calculations on the input data, and return a result upon completion. As an example, an input audio signal can be represented as a list of numbers. This signal is transformed by a function that implements a low-pass filter algorithm to produce another list of numbers that represent the output signal whose high-frequency components have been removed.

***objective***—In an *object-oriented* programming language like Java, you model application concepts as classes that possess both state and behaviour and create objects that conform to those class definitions. Each object guards its internal state, and permits other objects to modify its internal state only in a prescribed manner. The interactions amongst these objects gradually evolve the programme state, thus implementing programme behaviour. In a bank transaction simulator, for example, you may create objects like queue, customer, teller, account, transaction, and so forth, and these objects collaborate with one another to accomplish the common goal. The customer queues up, and waits for his turn. When his turn arrives, he informs the teller what he wants done, the teller initiates a new transaction, and changes the account state in accordance with the customer’s wishes. The customer verifies the changes made to his account are correct. The teller then concludes the transaction, and the customer exits the queue. The final amounts in the accounts of all the customers represent the final state of the simulation.

***procedural***—In a *procedural* programming language like C, you define data structures to represent a shared programme state and implement programme behaviour by writing procedures to manipulate that shared programme state. A procedure is a reusable collection of step-by-step computing instructions. You assemble the programme from many such procedures. Each procedure propels the computation forward by incrementally modifying the shared programme state, until the programme execution terminates when the exit condition is met. The result, then, is the final programme state. For example, your programme loads data from a file using the read procedure, modifies that data using the update procedure, saves the updated data back into the file using the write procedure, then exits.

***comparisons***—There is a superficial similarity between procedures and functions: both represent small chunks of computation, which are combined to create large programmes. But there is a subtle, yet significant, difference: functions reflect small chunks of the programmer’s thought; procedures are small chunks of the computer’s work.

I shall elaborate upon that pithy remark. We humans cannot cope with a large, complex problem, unless we first decompose it into smaller, more readily understood elements. Both functional and procedural paradigms offer means of decomposition. This much is similar. The difference lies in the way we decompose the problem. The functional approach emphasises decomposing the programme into small *conceptual units* that maybe composed into a coherent whole, thus reflecting the programmer’s understanding of the problem and his description of the solution. The procedural approach emphasises decomposing the programme into small *computational units* that may conveniently be assembled into an executable. Outwardly, both the conceptual unit and the computational unit represent small pieces of reusable code. But their internal natures are starkly different: one exists at the level of a human thought, but the other at the level of a machine operation.

So, what of the object-oriented approach? The objective style came about, in order to rein in the procedural approach’s laissez-faire attitude toward modifying the programme state. When different parts of a large programme use and change the shared programme state in an uncontrolled and uncoordinated manner, the state quickly becomes corrupted, and chaos ensues. One way to temper the chaos is to break down the programme state into smaller chunks, and ensconce each chunk inside its own protective shell that jealously guards access thereto. So, an object comprises a small chunk of state, its protective shell, and the restrictive mechanisms through which other objects may access and mutate its state.

## *interpreted v. compiled*

In this guide I draw no distinctions between which language is interpreted and which compiled. The source code written in a *compiled* language, say C, must first be transformed into the machine code understood by the computer, before the computer can execute the programme. This transformation is called compilation. But the source code written in an *interpreted* language, like Python, is executed immediately by the interpreter, without the need to first compile the programme. The interpreter is the programme in this case, and the code the programmer wrote merely guides the behaviour of the interpreter.

The difference between compilation and interpretation was once significant. In the bad old days, the source code was stored on punch cards, and the card stack had to be submitted to the computer operator. During the night, the operator compiles and runs all the submitted programmes in one batch. The programmer comes back to the computer centre in the morning, and examines the result. If his programme contained errors, he must repeat the whole process. By contrast, the interpreted language offered a command-line interface into which the programmer typed in his source code and obtained the result, instantly.

Today though, this dichotomy is a distinction without a difference. Irrespective of the language, we now write programmes in integrated development environment (IDE), test run the programmes from within the IDE, and debug the programmes also from inside the IDE. The intricacies of compilation are transparent to the programmer. And the user cares not whether the programme was compiled or whether it will be interpreted when he runs it, so long as it does what he wanted it to do. And modern compiled languages provide command-line interpreters that allow the programmer to experiment interactively and obtain results instantaneously.

Moreover, the so-called compiled languages, like Java, F#, Erlang, etc., are not as they appear. Java source code, for instance, is first compiled down to the Java bytecode, a set of low-level instructions. But the bytecode instructions are not the machine code understood by the computer. They are meant for the Java Virtual Machine (JVM). The JVM is the programme that interprets the Java bytecode, in much the same way the Python interpreter interprets the Python source code. And the Python interpreter actually compiles the source code into its internal bytecode, before running it. So much for the compiled-interpreted dichotomy.

Suffice it to say the line between compiled and interpreted languages is now so thin that it is hardly noticeable to programmers. Of course, this distinction is still significant to language designers.

## *popular programming languages*

Now that you understand families and paradigms, we can talk about where on the family tree some of the better-known languages hang. You do not have to learn all the popular languages, but it helps to be familiar with their names, their lineages, and their strengths.

**Declarative**

- Logical—Programmer defines a set of logical rules, and the language evaluates them, drawing inferences automatically, to reach a conclusion.
  - Prolog

- Relational—Programmer creates a query by defining relations between sets of data, and the language selects and returns the desired subset of the data.
  - SQL

- Functional—Programmer defines data types and functions that operate on those types, and the language evaluates the functions to transform the input data to produce the result.
  - Lisp, Scheme, Common Lisp, Clojure, Mathematica, Julia
  - Standard ML, Haskell, OCaml, F#, Reason, Rust, Elm
  - Erlang, Elixir

**Imperative**

- Objective—Programmer creates objects that hold data of various types, and the language animates the objects so that they interact with one another in a controlled way, without corrupting each other's internal data.
  - Smalltalk, Ruby, Java, C#, Scala, Kotlin
  - Simula, Objective-C, C++, Swift
  - Go, Python, JavaScript, TypeScript

- Procedural—Programmer defines global programme state and procedures that modify that state incrementally, and the language executes the procedures in sequence to reach the final state of the programme.
  - C, Nim, Perl
  - Cobol, Pascal, Algol, Basic
  - Fortran, Matlab

- Mechanical—Programmer defines step-by-step, low-level instructions that the computer understands, and the machine executes the instructions in sequence to produce the result.
  - Assembly, Hexadecimal, Binary

Languages make much of programming paradigms, but in truth very few languages are paradigmatically pure. For example, Lisp is the seminal functional programming language, and is the matriarch of the declarative line. But it permits the mutation of the programme state, a distinctive trait of the imperative family. C is the perennial procedural programming language, and an honoured member of the imperative family. Simula is the first, true object-oriented language. Smalltalk is the first, pure object-oriented language. Crossing Smalltalk with C yields Objective-C and mixing Simula with C yields C++. C# is a derivative of Java, which in turn is a descendant of Smalltalk and C++. Adding a few functional programming constructs to Java yields Scala. Python is an object-oriented language but it supports many functional features. JavaScript, another famous object-oriented language, has even stronger ties to functional family.

Languages that support a number of different paradigms are referred to as multi-paradigm languages. Indeed, all popular languages in use today are multi-paradigm languages. For instance, Swift, the new official language for iOS apps, and Kotlin, the new official language for Android apps, are both object-oriented languages with strong support for the functional style. On the other hand, F# is a functional-first language, but it interoperates seamlessly with .NET object system, which was designed to support C#.

Haskell, however, is purely functional, Prolog is purely logical, and Smalltalk is purely object-oriented. In spite of their purity and utility, these languages do not enjoy a large user base today, perhaps because it is unnatural for people to think in a paradigmatically pure way.

All the languages that became popular over the past few decades have primarily been object-oriented. All new languages today continue to support the object-oriented style, because objective way of thinking is natural—almost instinctual—to programmers. Nevertheless, the appreciation for the functional style is growing rapidly. So, the current trend in programming languages is objective-functional mixed paradigm, with some languages (Swift and Kotlin) leaning more object-oriented and others leaning more functional (F# and Reason).

# RECOMMENDATIONS

Here are the programming languages that I consider good, first language to learn for various disciplines of STEM. Obviously, something is “first,” only if it is followed by other things. So, accept the fact that you will have to learn more than one programming language over the course of your career.

When learning a new language, be sure to check your preconceived notions, and immerse yourself fully in the new concepts. It is unsettling, whenever we are exposed to strange, new ideas. But persevere, and they will turn into old, familiar concepts.

If you already know a programming language, and are now learning a new one, do not let your thought processes become anchored to the old, familiar language. If you fail to exercise the requisite mental discipline, you will end up writing programmes in the new language using the idioms of the old. The result would be an uncomely union of incoherent incantations.

## *for children*

I have seen many young children, some as young as five, learning [Scratch](https://scratch.mit.edu/). Scratch is great for children who are barely out of the toddler stage. But anyone eight years of age or older should learn to use [Squeak Smalltalk](https://squeak.org/), preferably on something fun like the [Raspberry Pi](https://www.raspberrypi.org/), and with parental guidance.

Smalltalk is a general-purpose, object-oriented programming language. It is the ancestor of most modern languages currently being used in the IT industry. The Squeak learning environment makes learning Smalltalk not only easy but also fun. There is also the BBC [micro:bit](https://microbit.org/). This little microcontroller is smaller than a credit card, but it comes with a pre-installed MicroPython runtime. Because the micro:bit is aimed at school age children, its ecosystem has many programmable robots and other educational toys. With micro:bit, children learn Python programming and hardware interfacing.

Scratch is a graphical programming language with limited capabilities. A driven, precocious child will soon out grow the language and will quickly become frustrated with its limitations, thus turning him away from programming. On the flip side, Smalltalk is an industry-grade programming language. The tiny Pi is a full-fledged computer that runs Linux, an industry-grade operating system. And the cute micro:bit requires a host computer to program it. So, Squeak, Pi, and micro:bit can be intimidating to a young child; adult supervision is therefore mandatory. Fortunately, Squeak, Pi, and micro:bit sites all have tonnes of visual tutorials and guided lessons that parents and teachers can use to teach very young children.

By the way, the low-cost [Raspberry Pi 400](https://www.raspberrypi.org/products/raspberry-pi-400/) is eminently capable of serving a college student as his dorm room desktop computer. It is ideal for STEM college students.

## *for all STEMers*

Mathematics, and of course English too, are important to all things STEM. All STEMers must think, read, write, and speak in these two languages, throughout the career. So, learn these languages, live them, love them, and never leave them.

And all STEMers should master [TeX](http://www.tug.org). TeX is not a programming language; it is the original, text markup language created by famous American mathematician [Knuth](https://en.wikipedia.org/wiki/Donald_Knuth). Naturally, TeX renders mathematical expressions with impeccable quality. Many mathematics textbooks are written in TeX. No self-respecting STEM practitioner should embark on his career without TeX in his bag, for sooner or later he will have to publish peer-reviewed papers.

STEM folk, in general, are visual creatures. So, it is sensible to learn a diagramming language like [UML](https://en.wikipedia.org/wiki/Unified_Modeling_Language). It is used for diagraming system designs. You can use it to document and to share your ideas. More mathematically minded STEMers should consider using [category theory as a visual language](https://ocw.mit.edu/courses/mathematics/18-s996-category-theory-for-scientists-spring-2013/textbook/MIT18_S996S13_textbook.pdf).

## *for non-IT STEMers*

***mathematicians***—If you plan to make a living as an applied mathematician, learn to program in Mathematica, Python, and R.

[Mathematica](http://www.wolfram.com/mathematica/), which is officially called the Wolfram language. It is a Lisp-like functional programming language endowed with mathematical sensibilities. And it has a superb IDE. Incidentally, all [Raspberry Pi](https://www.raspberrypi.org/) computers come with fully functional Mathematica, pre-installed. All applied mathematicians should learn at least a couple of functional languages. So, pick up Scheme, too, which is arguably the simplest functional programming language. And it is good to learn Prolog as well, because it will come in handy when you study formal logic.

Most colleges provide their mathematics students with access to Maple, Mathematica, or a similar [computer algebra system](http://en.wikipedia.org/wiki/List_of_computer_algebra_systems) (CAS). These commercial systems are very expensive, and when you graduate, you may not have access to them. So, you should explore open-source CAS. [Jupyter](https://jupyter.org/) is a safe bet. It is modelled upon Mathematica and is implemented in Python. Indeed, [JupyterLab](https://hub.gke2.mybinder.org/user/jupyterlab-jupyterlab-demo-efuc48zp/lab) is a clone of Wolfram Notebook. That means you can do CAS, graphing, and the like, without having to pay exorbitant licensing fees. And you can construct full-fledged applications in Python by leveraging other Python-friendly scientific software like [SciPy](http://www.scipy.org), [OpenCV](http://opencv.org/), etc. Moreover, Python has a good support for the functional style, which for a mathematician is an advantage. One more thing: you can hand your algorithm prototyped in Jupyter to your software developer colleagues, and they can readily translate it into product code using the C++, Java, C#, whatever. Because Python is popular and simple, experienced developers can at least understand what the code is doing, even if they do not comprehend the underlying mathematics. For these reasons, I recommend that you get comfortable with Python and Jupyter, even if you have access to Mathematica.

Another functional programming language with a mathematical bent is [R](http://www.r-project.org), which is an open-source language for statistical computation, complete with an IDE called [RStudio](http://www.rstudio.com). R has an extensive collection of add-on packages applicable in every scientific pursuits. Jupyter support R, as well.

***scientists***—If you plan to become a physicist, astronomer, chemist, etc., you should learn to program in Python, R, and Julia.

Julia is a more recent language specifically designed for high-performance computing. It is a functional language with built-in support for object-orientation and parallel processing. Its syntax is as plain as that of Python’s. Unlike Python, which is an interpreted language, Julia’s compiler converts the code into native machine code the first time the programme is run, yielding speeds comparable to C. That means you can take your prototype algorithms straight to production, without needing to rely on your developer colleagues. So, you should take a serious look at [Julia](https://julialang.org/). And yes, Jupyter works with Julia, too.

***engineers***—Hardware engineers should learn to program in C, Matlab, and Rust.

Use [C](http://en.wikipedia.org/wiki/C_(programming_language)) and assembly to program [peripheral interface controllers](http://en.wikipedia.org/wiki/PIC_microcontroller) (PICs) and [microcontrollers units](https://en.wikipedia.org/wiki/Microcontroller) (MCUs). If you are interested in [Internet of Things](https://en.wikipedia.org/wiki/Internet_of_things) (IoT), you should start with [Arduino](https://www.arduino.cc/), a low-cost, easy-to-use MCU and its supporting circuitry on one, convenient circuit board, or a more advanced [Raspberry Pi](http://www.raspberrypi.org/) [single-board computer](https://en.wikipedia.org/wiki/Single-board_computer) (SBC), a low-cost, desktop-grade computer that fits on a circuit board not much bigger than a wallet.

If your interests lean more toward chip design, study in college computer engineering, which combines electrical engineering and computer science. Chip design is one of the most advanced specialities of computing, and it is the flag bearer of technological advances in all things STEM.

And if you are a youngster with an incurable robotics fixation, but the engineering college is a decade into the future, ask mummy to buy you a [LEGO Mindstorms](https://www.lego.com/en-us/themes/mindstorms/about) kit. Now! The current version is Mindstorms EV3, and Oracle has an [embedded Java](http://www.oracle.com/technetwork/java/embedded/downloads/javase/javaseemeddedev3-1982511.html) for the platform. JavaScript, Python, and C support are also available.

When I was a young college student studying electrical engineering, I always had my [slide rule](https://en.wikipedia.org/wiki/Slide_rule) within reach. Alas, slide rules are no more. [Matlab](http://www.mathworks.com/products/matlab/?nocookie=true) is the new slide rule for engineers; it will be your constant companion in school and at work. Learn well this language. In particular, master its [vector processing](https://en.wikipedia.org/wiki/Vector_processor) facilities that perform array computations in parallel.

But I recommended C as the starter language, not Matlab. Here is why. Matlab is designed for those who possess theoretical foundations of engineering. Moreover, you will have no choice but to use Matlab when you study engineering in college, and your knowledge of C will allow you to pick up the linguistic elements of Matlab in a matter of hours. Lastly, Matlab license is expensive, but a top-notch C compiler comes with Linux and macOS. So, start learning C, now.

I must warn you that while Matlab is ideal for analysing algorithm designs and prototyping implementations, it is not suited to large-scale product development. Sure, you can invoke Matlab procedures from your programme written in C or Java; loads of engineers take this shortcut, when they are cornered into building product-quality software. But if you do this, your production system will have external dependencies on Matlab runtime, and Matlab license would be required for each installation of your programme. The C-Java-Matlab unholy polygamy maybe tolerable for a small, off-line system, but you should consider a cleaner, faster, more maintainable alternative, if you are working on a large application. The approach I favour is to explore, design, analyse, prototype, and test the algorithm in Matlab, and once it has been proven—mathematically and experimentally—to work, translate it into the language in which the production system is implemented. The downside, of course, is that you have to maintain two versions of the algorithm, one in Matlab and the other in the production language. But it is manageable if proper software practices are followed, and it sure is preferable to the alternative.

Hardware engineers often end up working with operating systems, device drivers, and IoT. For software work like that, C is the language of choice. But newer [Rust](https://www.rust-lang.org/) programming language has the potential to depose C off its decades-long perch at the top. Rust supports safe, static type system and functional programming style. Rust also gives the programmer nearly as much control over the hardware as does C, but without any of C’s famously dangerous traps.

And it is never harmful to familiarise yourself with the instruction set and the processor architecture of the microcontroller you are using. This knowledge will make you a more sympathetic engineer, one who is attuned to the inner workings of his hardware.

## *for IT STEMers*

***computer scientist***—If your goal is to become a computer scientist, expect to learn many different programming languages throughout your career. By "different", I mean languages from different family lines. At a minimum, you must be familiar with all seminal languages that are still relevant: C, Standard ML, Smalltalk, Scheme, Prolog, SQL, and JavaScript ( but only [the good parts](https://www.oreilly.com/library/view/javascript-the-good/9780596517748/)). And mastering C, OCaml, and SQL will enable you to pick up any new, popular language used in the IT industry.

[Scheme](http://groups.csail.mit.edu/mac/projects/scheme/), an old, sincere, and unadorned functional programming language, is a direct descendent of Lisp. Lisp is an extremely simple language with only seven primitive forms to learn, yet it has the ability to reprogram the learner's brain for the better. Modern Scheme is a great starter language for you, if you aspire to be a computer scientist. You should already know this language before finishing high school. [Racket](https://racket-lang.org/) is a superb environment in which to learn Scheme.

The computer science curriculum includes a survey course that gives the student an overview of several languages from various paradigms. In such a course, Lisp and Prolog are taught because they are historically significant. C++ and Java, are taught because they are economically significant. And Standard ML and Haskell are taught because they are theoretically significant. An exposure to many different languages that this type of survey course provides is valuable, but it is well neigh impossible for the student to grasp any language thoroughly, given that decades worth of knowledge is crammed into a few short weeks of a semester. Indeed, this type of course tends to turn away the under-motivated from pursuing these important languages. But classic languages like Lisp, Prolog, Standard ML, etc., are still taught today, because they broaden the students' perspective. So, it behoves you to delve deeper, go farther.

The fortunate few who attend collages with strong, theoretical tradition will encounter a functional language—Scheme, Standard ML, Haskell, OCaml, or something else more exotic. Computer scientists design and analyse algorithms using mathematics. The functional style offers a natural, convenient, and sound way to transform mathematically expressed algorithms directly into executable code. So, the closer the programming language approximates the facilities of mathematics, the better. Scheme is easy to learn and convenient to use. Standard ML is somewhat tougher to learn, but you should learn it, because its [Hindley-Milner type system](https://en.wikipedia.org/wiki/Hindley–Milner_type_system) is at the core of all modern, functional languages. Standard ML is the direct or indirect ancestor of just about every popular, modern language: Haskell, OCaml, F#, Reason, TypeScript, Rust, Swift, Kotlin, and many others. Standard ML, therefore, is a worthy language to learn, early in one's CS career.

These days, it is virtually certain that your college will foist upon you Java, C#, or C++, because these languages are currently in high demand in the industry. But I strongly recommend that you pursue [OCaml](https://ocaml.org/), [F#](https://dotnet.microsoft.com/languages/fsharp), or [Reason](https://reasonml.github.io/) on your own, in addition to the compulsory language. I strenuously suggest that you master OCaml. If you know OCaml, you automatically know its descendants, F# and Reason. And OCaml is an elegant, theoretically-sound functional programming language with support for object-orientation and system-level programming. In other words, OCaml has beauty, brawn, and brains. In fact, many CS programmes that taught Standard ML for decades have switched to OCaml, recently.

So, which should you learn: Standard ML or OCaml? The short answer is both. But if you must pick one, let this be your guide: there are tonnes of theory-based programming books on Standard ML, but there are comparatively few academic books on OCaml; on the other hand, there are quite a lot of practice-based programming books on OCaml, some of them were written by well-known industry practitioners, but there are no such books for Standard ML. This state of affairs reflects Standard ML's long-time association with academia and OCaml's long-time use in mathematically intense commercial applications.

***software developers***—By "software developers", I mean those who develop line of business applications or social media applications, web or mobile. If you wish to become a software developer, you should learn Smalltalk and JavaScript, at the very least.

Virtually all software development projects today use object-oriented languages. If you are bent on becoming a software developer, a good object-oriented language to learn as your first programming language is [Smalltalk](http://www.smalltalk.org/main/)—the mother of Objective-C, Ruby, Java, JavaScript, C#, Swift, and Kotlin. The easiest way to start learning Smalltalk is to use [Squeak](http://www.squeak.org). Squeak can be loads of fun, whether one is a precocious eight-year-old or a jaded eighteen-year-old.

Consider this. Applications that run on iOS and macOS are programmed in Objective-C or Swift. Android mobile applications are programmed in Java or Kotlin. Windows applications are programmed in C#. This lot covers the majority of the world’s applications. Almost all web applications and a large number of enterprise systems are programmed in Java, C#, or JavaScript. These languages are all descendants of Smalltalk. A software developer may well be able to make a decent living knowing nothing but the Smalltalk family of languages. Chuffed? Wait! To avoid learning other family of languages would be a grave error, an error as grievous as a jazz saxophonist renouncing the study of harmony, because his instrument cannot produce chords.

For business application development, JavaScript is perhaps the most important of the lot, today. Its mixed ancestry comprises [Self](https://en.wikipedia.org/wiki/Self_(programming_language)), [Smalltalk](https://en.wikipedia.org/wiki/Smalltalk), and [Scheme](https://en.wikipedia.org/wiki/Scheme_(programming_language)). This language has an undeserved ill reputation in the software industry for yielding unmaintainable code. Sure, there is a lot of poorly written JavaScript code. But there are tonnes of bad Java and C code in the world, too. Bad code is primarily the fault of the programmer, and the language is responsible only to the extent that it did not prevent him from writing bad code. In truth, JavaScirpt is a great language that supports functional, object, and procedural paradigms, but you have to learn to avoid the bad parts and use only [the good parts](https://www.amazon.com/JavaScript-Good-Parts-Douglas-Crockford/dp/0596517742). For the past decade, JavaScript has been used both to build sophisticated web clients and complex web servers. So, master it.

For the past few decades, the IT industry had lived the object-oriented lifestyle, hard and fast. But there is a growing realisation within the industry of the importance of the functional style. The trend now is functional languages hosted inside Java Virtual Machine (JVM) or Common Language Runtime (CLR). F# is a functional language derived from OCaml. It is Microsoft’s functional offering for its .NET platform. Because .NET languages compile to the CLR bytecode, C# and F# coexist in harmony. Scala and Kotlin are Java with functional extensions, so they all get on well within the JVM. Clojure is Lisp that can be compiled down to CLR or JVM bytecode, thereby allowing Lisp fanciers to leverage the substantial capabilities of those platforms. And there are JavaScript translators for just about every language, which allows programmers to develop sophisticated, single-page web clients in their favourite language, instead of in JavaScript.

Another virtual machine language that has not enjoyed as much hype as Java and C# is [Erlang](https://www.erlang.org/), a unique, functional language designed by Ericsson to implement their fault-tolerant telecommunication infrastructure. Erlang has been around since the mid-1980s, but very few took note, perhaps because it was mistakenly viewed as a telephony-specific language, because it is a functional language, or because it did not originate in academia. Regardless, Erlang is enjoying a resurgence today, because of its superb support for concurrency, fault-tolerance, and high-availability, making it the ideal server programming language for the social media age. The best known, modern descendent of Erlang is Elixir. [Elixir](https://elixir-lang.org/) is essentially Erlang with Ruby syntax. If your interests lie in massive social media applications, you should study Erlang, especially its [Open Telecom Platform](https://en.wikipedia.org/wiki/Open_Telecom_Platform) (OTP) facilities.

A few words of caution, if you please. Software industry is founded upon computer science knowledge, and programming is a mathematical activity. But these days, although the industry makes much of the “computer,” it cares not enough about the “science” bit. The industry seeks code cutters, not analytical thinkers. It admires complexity and apparent sophistication, not correctness and actual simplicity. It desires quick delivery, not stable, speedy operation. Distance yourself the best you can from that lot. And you would do well to pay attention to the computer science theory courses in college, not just on the programming courses.

***system programmers***—Originally, the term "system programming" meant programming operating systems. But today, its meaning is much more expansive, connoting "system-dependent programming"—essentially anything outside of line of business or social media application development. If you wish to become a system programmer, you should learn C, Nim, C++, OCaml, Rust, and at least one assembly language, preferably Intel or ARM.

Traditional system programming languages are C and the host hardware's assembly language. But today, C++ is used quite extensively, as well. So, if you are interested in 3D game programming, weather modelling, industrial process control, and the like, learn both C and C++. And you should also have a solid background in electronics and mathematics, because many system programming applications rely heavily on these subjects. In some sectors where mathematics, algorithms, performance, and complexity rule the day, such as financial modelling, compiler development, etc., OCaml is the language of choice.

[Nim](https://nim-lang.org/) is a relatively young procedural language with multi-paradigm support. It has an inferencing, static type system and a clean, Python-like syntax. Although it is a procedural language, it supports FP and OO. It also has a powerful meta-programming facilities—generics, templates, and macros—that reduce repetition and clutter in the code. And Nim supports various garbage collection strategies, thereby allowing the programmer to select the one that best fits his solution. Nim runs on just about every type of machine, from servers to microcontrollers. In other words, Nim could well be the best friend of a modern system programmer who does not need to dive into the kernel.

Proponents of [Rust](https://www.rust-lang.org/), a relative newcomer, claim it will soon be the next de facto system programming language. But whether Rust can displace C remains an open question, for the time being. My bet is on C.

***system administrators***—If you are interested in becoming a system administrator, you should learn to program in Python, Bourne shell, and PowerShell. And because many business software are implemented as JavaScript web applications, some familiarity with the basics of JavaScript would be a plus. Of course, you must learn how properly to use `vi`, `sed`, `grep`, and other Unix command-line tools.

Good system administrators are also good system programmers. The difference between a system administrator’s code and a system programmer's code is scale: the former writes small programmes to automate infrastructure tasks, but the latter writes large programmes to automate industrial processes.

My reason for recommending Python as the first programming language is as follows. As a system administrator, you will have no choice but to learn and use Bourne shell and PowerShell, on the job. Most automation scripts are written in these languages. But they are not general-purpose programming languages. Python is. Not only is Python a full-fledged programming language, it is also a shell scripting language that you can use directly from a system command prompt. And Python is a hybrid, object-procedural-functional language, so it allows the user to follow whichever paradigm he fancies. It is no wonder that many configuration management systems with dependency checking and build automation features are written in Python.

I strongly recommend you try out [Jupyter](https://jupyter.org/), a visual, interactive, data analytic shell for Python. System administrators routinely collect and analyse massive amounts of log data, from which they extract trends using statistical methods and produce charts to be inserted into reports. [JupyterLab](https://hub.gke2.mybinder.org/user/jupyterlab-jupyterlab-demo-eqjkb7jo/lab) user interface allows the programmer to embed live data into beautifully formatted reports, all in one go, using nothing more than a web browser.

Also, there are a lot of system administration scripts written in Perl, the erstwhile king of automation. Like Python, Perl is a full-fledged programming language. Perl is another language with a bad reputation, because there are mounds of poorly written code in the wild. But if done right, however, Perl is a marvellous timesaver, especially for compact, complex one-liners. So, you will need to know Perl, at some point.

Lastly, if you are interested in large-scale system automation, pick up the [Go](https://golang.org/) programming language. It is a descendant of C with object-oriented facilities. But unlike other modern languages, it is a relatively compact, yet powerful, language suited to high-performance system applications.

The IT industry views network administration as a distinct and separate track from system administration. I see things differently. A well-rounded system administrator should know networking, security, cloud infrastructure, storage architecture, and the like. Likewise, a good network administrator should know system administration and all the rest. In terms of requisite knowledge, there is very little daylight between system administration and network administration.

Of course, a database administrator should breathe, eat, and sleep SQL, and it would not hurt to be familiar with [XSLT](https://en.wikipedia.org/wiki/XSLT), [GraphQL](https://graphql.org/), and other query languages. He should also be comfortable with system and network administration tasks, too.

In short, system, network, and database administration fields are so closely related that they cannot—at least should not—be practised in isolation. It is fine to specialise in one track or another, but it would be a mistake to think that because you are a master of one speciality, you need no knowledge of the others.

# LEARNING

Most people encounter programming in their teens, when they are in high school or in college. But it is eminently possible for a precocious child to start learning programming on his own, without being tutored (pronounced tortured) by anyone. Software development on a large-scale is difficult; even those who make their living in the field cannot get it right, every time. But programming on a small-scale—class assignments or personal projects—is not difficult; a determined learner can pick it up on his own. And even if one is enrolled in a programming course, he should still augment that with self-paced study, using the information provided here as a guide.

Just as there is no one best programming language, there is no one best way to learn programming. Each person learns in a unique way. So, I shall describe the different ways in which you can learn, and it is up to you to choose. Use them all, if you can. But regardless of how you learn a language, the only way you gain proficiency is to write programmes in it. Daily.

But first, a caution. Many young people who are interested in computing ask which programming language is the most popular in the industry, the one that has the most jobs, the jobs that pay the most, and the like, so that they may pick up that one language and be done with it all. This is akin to you rushing into the most jam-packed restaurant on the block and demanding to be served immediately the most popular menu item, without knowing what the dish is or what type of cuisine the restaurant serves, and while you are not even in the mood for food. If you wish to make money quickly, driving Uber is likely more fun and profitable than working as an unmotivated, unskilled programmer. But if you want a long career in computing, study computer science or computer engineering, and be prepared to continue learning for the rest of your life.

All popular programming languages have numerous learning resources available. There are countless on-line articles and tutorials. And you will surely find free PDF reference manuals that are written by the designers of the respective languages. And there are countless tutorial books, each over a thousand pages in length, that provide step-by-step training of any language currently in vogue.

If you are new to programming or are presently learning your very first language, you should do what most people do—buy a tutorial book, and follow the lessons. When you have gained experience in a handful of programming languages from different paradigms, you may wish to learn the way I do.

When I learn a new language, my preference is to start with the peer-reviewed papers, the reference manual, or the language specification written by the designer of that language. More likely than not, all of them will be available as free PDF documents. If the designer of the language published a book about his language, I make it a point to read it, so as to get a better grasp of his motivations, his biases, and his insights. As I encounter the unique features and facilities of the new language, I compare them to the similar ones provided by the mother language in that linguistic family line. Because I am already proficient in that mother language, it is easy and fast for me to absorb the new concepts introduced in the new language. Simultaneously, I start writing programmes in that new language. Small, simple algorithms without external dependencies are great for this. I usually implement in the new language the well-known algorithms from my practice areas: image processing and artificial intelligence. Because the algorithm was designed, proved, and published long ago and because I am a practitioner in that speciality, I am able to focus on the features of the new language without being distracted with the complexities and the intricacies of the application domain.

Most people today, however, learn a new language by implementing a toy social-media web application. This is perhaps the worst way for a beginner to learn, because web development is excessively complicated and highly tumultuous. Of course, there are plenty of shortcuts to get a web application up and running, and many books encourage beginners to take those shortcuts. But in so doing, the beginners are robbed of the opportunity to learn how and why their application works. These shortcuts are useful to experienced programmers as time savers, but they are useless as teaching aids for beginners. If you are interested in web development, you should start with the basics of computing, instead of climbing straight up to it, and certainly not while attempting to learn a new programming language.

Sometimes, you may come across a language that is so new that no books or articles have yet been published. In that case, your options are limited. If you are fortunate, there may already exist a discussion group dedicated to the new language. In the worse case, you may have to wade through the source code of the language implementation. But since a new language offers no guarantees of being able to establish itself in the industry, most people will not devote this much time and effort to learn it.

There is, however, a good reason why such an expenditure of effort maybe warranted. Every popular language in use today began in that state—rough around the edges, no fancy features, no documentation, hardly any users. By becoming proficient in a new language in its nascent stage, you are poised to contribute to its advancement: by creating promotional blog posts, by writing explanatory books, or by expanding some of its features. Typically, those early adopters are friends and colleagues of the language designer. That the language may never blossom, of course, is the risk that the early adopter assumes.

## *resources*

The following are the learning resources I recommend, either because they cater to the beginners, because they deal adequately with advanced topics, or because they present important new concepts. Remember, you do not need to learn all these languages, all at once. But if you stay in the software industry long enough, your will encounter most of these languages or their descendants, eventually.

Note that there are four types programming books: purely theoretical, more theoretical than practical, less theoretical than practical, and purely practical. The former two types are read by CS students, and the latter two types are read by industry programmers. In general, books on the ML family of functional languages (Standard ML, Haskell, OCaml, etc.) lean toward CS theory, whereas books on the C++ family of object-oriented languages (C++, Java, JavaScript, etc.) are devoid of any CS theory. You will need to learn to read all these types of books. But do understand that you cannot benefit fully from a purely practical book without some theoretical background.

**Logical**

- Prolog
  - [*Programming in Prolog: Using the ISO Standard*](http://www.amazon.com/Programming-Prolog-Using-ISO-Standard/dp/3540006788/ref=sr_1_1?ie=UTF8&qid=1401776122&sr=8-1&keywords=prolog), Clocksin
  - [*An Introduction to Prolog Programming*](http://staff.science.uva.nl/~ulle/teaching/prolog/prolog.pdf), Endriss

**Relational**

- SQL
  - [*Learning SQL*](http://www.amazon.com/Learning-SQL-Alan-Beaulieu/dp/0596520832/ref=sr_1_3?s=books&ie=UTF8&qid=1401774621&sr=1-3&keywords=sql), Beaulieu

**Functional**

- Lisp family
  - Scheme
    - [*The Scheme Programming Language*](http://www.amazon.com/Scheme-Programming-Language-Kent-Dybvig/dp/026251298X/ref=sr_1_1?s=books&ie=UTF8&qid=1401772978&sr=1-1&keywords=scheme+language+programming), Dybvig
    - [*Structure and Interpretation of Computer Programs*](http://www.amazon.com/Structure-Interpretation-Computer-Programs-Engineering/dp/0262510871/ref=sr_1_8?s=books&ie=UTF8&qid=1401819781&sr=1-8&keywords=scheme+steele), Abelson
    - [*How to Design Programmes*](http://https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=4&ved=0CFIQFjAD&url=http%3A%2F%2Flib.org.by%2Fget%2FCs_Computer science%2FCsAl_Algorithms%2FFelleisen M.%2C Findler R.B.%2C Flatt M.%2C Krishnamurthi S. How to design programs.. an introduction to computing and programming (using Scheme)(MIT press%2C free web version%2C 2002)(565s).pdf.gz&ei=2cyVU5KED7GysASk1IDQBg&usg=AFQjCNGS0tGWk95huAQM9kWBJDZOwSD8sQ&sig2=gcMcjGA12OdFut9xcuuSIQ&bvm=bv.68445247,d.c), Felleisen (DrRacket designer)
    - [*Programming Languages*](http://cs.brown.edu/courses/cs173/2012/book/book.pdf), Krishnamurthi
  - Clojure
    - [*The Joy of Clojure*](http://www.amazon.com/Joy-Clojure-Michael-Fogus/dp/1617291412/ref=sr_1_2?s=books&ie=UTF8&qid=1401774361&sr=1-2&keywords=clojure), Fogus
- ML family
  - Standard ML
    - [*Elements of ML Programming*](https://www.amazon.com/Elements-ML-Programming-ML97-2nd/dp/0137903871/ref=sr_1_2?dchild=1&keywords=standard+ml&qid=1608746865&s=books&sr=1-2), Ullman
    - [*Programming in Standard ML*](http://www.cs.cmu.edu/~rwh/isml/book.pdf), Harper
  - OCaml (hybrid functional, objective)
    - [*The OCaml System*](https://ocaml.org/releases/4.11/ocaml-4.11-refman.pdf), Leroy (OCaml designer)
    - [*Real World OCaml*](https://www.amazon.com/Real-World-OCaml-Functional-programming/dp/144932391X/ref=sr_1_1?dchild=1&keywords=Real+World+OCaml&qid=1608746985&sr=8-1), Minsky
  - F# (hybrid functional, objective)
    - [*Beginning F#*](https://www.amazon.com/Beginning-F-4-0-Robert-Pickering-ebook/dp/B01JC6N1QM/ref=sr_1_8?dchild=1&keywords=F#&qid=1608745572&s=books&sr=1-8), Pickering
    - [*Expert F#*](https://www.amazon.com/Expert-F-4-0-Don-Syme/dp/1484207416/ref=sr_1_9?dchild=1&keywords=F#&qid=1608745572&s=books&sr=1-9), Syme (F# designer)
    - [*Domain Modeling Made Functional*](https://www.amazon.com/Domain-Modeling-Made-Functional-Domain-Driven-ebook/dp/B07B44BPFB/ref=sr_1_2?dchild=1&keywords=F#&qid=1608745572&s=books&sr=1-2), Wlaschin
  - Reason (hybrid functional, objective)
    - [*Learn Type-Driven Development*](https://www.amazon.com/Learn-Type-Driven-Development-applications-ebook/dp/B079DW69VL/ref=sr_1_2?dchild=1&keywords=reasonml&qid=1608747037&sr=8-2), Amin
    - [*Reason*](https://reasonml.github.io/docs/en/what-and-why), Facebook (Reason designer)
    - [*ReScript*](https://rescript-lang.org/docs/manual/latest/introduction), Facebook
    - [*Native Reason*](https://reasonml.github.io/docs/en/native), Facebook
  - Haskell (pure functional)
    - [*Introduction to Functional Programming*](https://usi-pl.github.io/lc/sp-2015/doc/Bird_Wadler. Introduction to Functional Programming.1ed.pdf), Bird
    - [*Haskell from the Very Beginning*](https://www.amazon.com/Haskell-Very-Beginning-John-Whitington/dp/095767113X/ref=sr_1_8?dchild=1&keywords=haskell&qid=1608745855&s=books&sr=1-8), Whitington
    - [*Programming in Haskell*](https://www.amazon.com/Programming-Haskell-Graham-Hutton/dp/1316626229/ref=sr_1_4?dchild=1&keywords=haskell&qid=1608745826&s=books&sr=1-4), Hutton
    - [*The Haskell School of Music*](https://www.amazon.com/Haskell-School-Music-Signals-Symphonies/dp/1108416756/ref=sr_1_10?dchild=1&keywords=haskell&qid=1608745906&s=books&sr=1-10), Hudak
    - [*Why Functional Programming Matters*](https://www.cs.kent.ac.uk/people/staff/dat/miranda/whyfp90.pdf), Hughes

- Erlang family
  - Erlang
    - [*Introducing Erlang*](http://www.amazon.com/Introducing-Erlang-Getting-Functional-Programming-ebook/dp/B00B634R04/ref=sr_1_5?ie=UTF8&qid=1401805713&sr=8-5&keywords=erlang), St. Laurent
    - [*Programming Erlang*](https://www.amazon.com/Programming-Erlang-Concurrent-Pragmatic-Programmers/dp/193778553X/ref=sr_1_3?dchild=1&keywords=erlang&qid=1608745780&s=books&sr=1-3), Armstrong (Erlang designer)
  - Elixir
    - [*Programming Elixir*](https://www.amazon.com/Programming-Elixir-1-6-Functional-Concurrent/dp/1680502999/ref=sr_1_3?dchild=1&keywords=elixir&qid=1608746507&s=books&sr=1-3), Thomas
    - [*Programming Phoenix*](https://www.amazon.com/Programming-Phoenix-1-4-Productive-Reliable/dp/1680502263/ref=sr_1_6?dchild=1&keywords=elixir&qid=1608746547&s=books&sr=1-6), McCord

- Scala (hybrid functional, objective)
  - [*Programming in Scala*](http://www.amazon.com/Programming-Scala-Comprehensive-Step---Step-ebook/dp/B004Z1FTXS/ref=sr_1_1?s=books&ie=UTF8&qid=1401774514&sr=1-1&keywords=scala), Odersky (Scala designer)

- Julia
  - [*Mastering Julia*](http://www.amazon.com/Mastering-Julia-Malcolm-Sherrington/dp/1783553316/ref=sr_1_2?ie=UTF8&qid=1473245684&sr=8-2&keywords=julia+language), Sherrington

- Mathematica
  - [*Wolfram Language and System*](http://reference.wolfram.com/language/), Wolfram (Mathematica designer)
  - [*The Mathematica GuideBook for Programming*](http://www.amazon.com/Mathematica-GuideBook-Programming-Michael-Trott/dp/0387942823/ref=sr_1_6?s=books&ie=UTF8&qid=1401772792&sr=1-6&keywords=mathematica), Trott

- R
  - [*The R Book*](http://www.amazon.com/R-Book-Michael-J-Crawley/dp/0470973927/ref=sr_1_16?s=books&ie=UTF8&qid=1401772904&sr=1-16&keywords=r+language+programming), Crawley

**Objective**

- Smalltalk family
  - Smalltalk (pure objective)
    - [*Smalltalk-80: The Language*](http://www.amazon.com/Smalltalk-80-Language-Adele-Goldberg/dp/0201136880/ref=sr_1_1?s=books&ie=UTF8&qid=1401774209&sr=1-1&keywords=smalltalk), Goldberg (Smalltalk designer)
    - [*Smalltalk-80: The Language and its Implementation*](http://www.amazon.com/Smalltalk-80-The-Language-its-Implementation/dp/0201113716/ref=sr_1_5?ie=UTF8&qid=1401820559&sr=8-5&keywords=smalltalk), Goldberg
    - [*Smalltalk-80: The Interactive Programming Environment*](http://www.amazon.com/Smalltalk-80-Interactive-Programming-Environment-Addison-Wesley/dp/0201113724/ref=sr_1_18?ie=UTF8&qid=1401820630&sr=8-18&keywords=smalltalk), Goldberg
    - [*The Design Patterns Smalltalk Companion*](http://www.amazon.com/Design-Patterns-Smalltalk-Companion/dp/0201184621/ref=sr_1_4?s=books&ie=UTF8&qid=1401774209&sr=1-4&keywords=smalltalk), Alpert
  - Objective-C
    - *[Object-Oriented Programming : An Evolutionary Approach](https://www.amazon.com/Object-Oriented-Programming-Evolutionary-Brad-Cox/dp/0201548348)*, Cox (Objective-C designer)
    - [*Programming with Objective-C*](http://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/ProgrammingWithObjectiveC/Introduction/Introduction.html), Apple, Inc.
  - Ruby
    - [*Programming Ruby*](http://www.amazon.com/Programming-Ruby-1-9-2-0-Programmers/dp/1937785491/ref=sr_1_5?s=books&ie=UTF8&qid=1401774107&sr=1-5&keywords=ruby), Thomas
  - Java
    - [*Java: A Beginner's Guide*](http://www.amazon.com/Java-Beginners-Guide-Sixth-ebook/dp/B00J4XLILY/ref=sr_1_1?s=books&ie=UTF8&qid=1401774042&sr=1-1&keywords=java), Schildt
    - [*The Java Language Specification*](http://www.amazon.com/Java-Language-Specification-SE-ebook/dp/B00BHEY5EU/ref=sr_1_23?s=books&ie=UTF8&qid=1401773907&sr=1-23&keywords=java), Gosling (Java designer)
  - C#
    - [*C# in a Nutshell*](http://www.amazon.com/C-8-0-Nutshell-Definitive-Reference/dp/1492051136/ref=sr_1_4?dchild=1&keywords=C%23&qid=1608747966&sr=8-4), Albahari
    - [*C# and .NET*](https://www.amazon.com/NET-Cross-Platform-Development-intelligent-Framework/dp/180056810X/ref=sr_1_2?dchild=1&keywords=C#&qid=1608747926&sr=8-2), Price
  - Swift (hybrid objective, functional)
    - [*Swift Programming Language*](http://https://developer.apple.com/library/prerelease/ios/documentation/Swift/Conceptual/Swift_Programming_Language/index.html#//apple_ref/doc/uid/TP40014097), Apple (Swift designer)
  - Kotlin (hybrid objective, functional)
    - [*Kotlin in Action*](https://www.amazon.com/Kotlin-Action-Dmitry-Jemerov/dp/1617293296/ref=sr_1_11?dchild=1&keywords=kotlin&qid=1608747783&sr=8-11), Jemerov
    - [*Learn Kotlin*](https://kotlinlang.org/docs/reference/), JetBrains (Kotlin designer)
- JavaScript family
  - JavaScript (hybrid objective, functional)
    - [*JavaScript: The Definitive Guide*](http://www.amazon.com/JavaScript-Definitive-Most-Used-Programming-Language/dp/1491952024/ref=sr_1_2?dchild=1&keywords=javascript&qid=1608746146&sr=8-2), Flanagan
    - [*Eloquent JavaScript*](https://www.amazon.com/Eloquent-JavaScript-3rd-Introduction-Programming/dp/1593279507/ref=sr_1_3?dchild=1&keywords=javascript&qid=1608746146&sr=8-3), Haverbeke
    - [*JavaScript: The Good Parts*](https://www.amazon.com/JavaScript-Good-Parts-Douglas-Crockford/dp/0596517742/ref=sr_1_11?dchild=1&keywords=javascript&qid=1608746103&sr=8-11), Crockford
  - TypeScript (hybrid objective, functional)
    - [*Programming TypeScript*](https://www.amazon.com/Programming-TypeScript-Making-JavaScript-Applications/dp/1492037656/ref=sr_1_2?dchild=1&keywords=typescript&qid=1608746733&s=books&sr=1-2), Cherny
    - [*The TypeScript Handbook*](https://www.typescriptlang.org/docs/handbook/intro.html), Microsoft (TypeScript designer)
- Python (hybrid objective, functional)
  - [*The Python Tutorial*](http://www.amazon.com/Python-Tutorial-2-7-5-Guido-Rossum-ebook/dp/B00FJRV9QI/ref=sr_1_13?s=books&ie=UTF8&qid=1401775234&sr=1-13&keywords=python), van Rossum (Python designer)
  - [*Guide To Functional Python and Comprehension Constructs*](http://www.amazon.com/Guide-Functional-Python-Comprehension-Constructs-ebook/dp/B00CUZDOSI/ref=sr_1_1?s=books&ie=UTF8&qid=1401775298&sr=1-1&keywords=functional+python), Harrison
  - [*Functional Programming How-To*](http://docs.python.org/3/howto/functional.html), Kuchling
  - [*Programming the Raspberry Pi: Getting Started with Python*](http://www.amazon.com/Programming-Raspberry-Pi-Getting-Started/dp/0071807837/ref=sr_1_16?ie=UTF8&qid=1403700541&sr=8-16&keywords=Raspberry+Pi), Monk
- C++
  - [*The C++ Programming Language*](http://www.amazon.com/C-Programming-Language-4th/dp/0321563840/ref=sr_1_1?s=books&ie=UTF8&qid=1401773170&sr=1-1&keywords=C%2B%2B+language+programming), Stroustrup (C++ designer)
- Go
  - *[The Go Programming Language](https://www.amazon.com/Programming-Language-Addison-Wesley-Professional-Computing/dp/0134190440/ref=sr_1_3?dchild=1&keywords=golang&qid=1611867815&sr=8-3)*, Donovan
  - [*Effective Go*](http://golang.org/doc/effective_go.html), Google (Go designer)
- Windows PowerShell
  - [*PowerShell for Sysadmins*](https://www.amazon.com/Automate-Boring-Stuff-PowerShell-Sysadmins/dp/1593279183/ref=sr_1_5?dchild=1&keywords=powershell&qid=1608748061&sr=8-5), Bertram
  - [*PowerShell Documentation*](https://docs.microsoft.com/en-us/powershell/), Microsoft (PowerShell designer)

**Procedural**

- C (pure procedural)
  - [*The C Programming Language*](http://www.amazon.com/Programming-Language-2nd-Brian-Kernighan/dp/0131103628/ref=sr_1_8?s=books&ie=UTF8&qid=1401772856&sr=1-8&keywords=r+language+programming), Kernighan & Ritchie (C designer)
- Nim (hybrid procedural, functional, objective)
  - *[Nim Basics](https://narimiran.github.io/nim-basics/)*, Miran
- Matlab (hybrid procedural, objective)
  - [*Matlab Language Fundamentals*](http://www.mathworks.com/help/matlab/index.html), MathWorks, Inc. (Matlab designer)
- Unix Bourne shell
  - [*The Unix Programming Environment*](http://www.amazon.com/Unix-Programming-Environment-Prentice-Hall-Software/dp/013937681X/ref=sr_1_1?s=books&ie=UTF8&qid=1401775485&sr=1-1&keywords=The+Unix+Programming+Environment), Kernighan (Unix designer)
  - [*UNIX: A History and a Memoir*](https://www.amazon.com/UNIX-History-Memoir-Brian-Kernighan/dp/1695978552/ref=sr_1_1?dchild=1&keywords=kernighan&qid=1608746441&s=books&sr=1-1), Kernighan
- AWK
  - [*The AWK Programming Language*](http://www.amazon.com/The-AWK-Programming-Language-Alfred/dp/020107981X/ref=sr_1_1?ie=UTF8&qid=1401820819&sr=8-1&keywords=awk+programming), Aho (AWK designer)
- Perl
  - [*Programming Perl: Unmatched Power for Text Processing and Scripting*](http://www.amazon.com/Programming-Perl-Unmatched-processing-scripting/dp/0596004923/ref=sr_1_1?s=books&ie=UTF8&qid=1401820920&sr=1-1&keywords=Programming+Perl), Wall (Perl designer)

**Mechanical**

- ARM
  - *[ARM 64-Bit Assembly Language](https://www.amazon.com/64-Bit-Assembly-Language-Larry-Pyeatt/dp/0128192216/ref=sr_1_4?dchild=1&keywords=arm+cpu&qid=1630599595&s=books&sr=1-4)*, Pyeatt
- AVR
  - *[Arduino Cookbook: Recipes to Begin, Expand, and Enhance Your Projects](https://www.amazon.com/Arduino-Cookbook-Recipes-Enhance-Projects/dp/149190352X/ref=sr_1_4?dchild=1&keywords=arduino&qid=1630600127&s=books&sr=1-4)*, Margolis

## *programming tools*

I would be remiss not to mention software development tools. Which tools you use depend on what you are doing. There are many programming languages. Each language has many types of support tools, and each tool type has many exemplary products. It would be impracticable for me to enumerate all the good tools that are available. So, I will describe just a few popular tools, and explain what they are and how you can use them.

A bit of computing history is necessary, I feel. Decades after its birth, Unix is still thriving, along with many of its descendants. Sun Solaris, IBM AIX, and HP-UX are all based on Unix. The ever-popular FreeBSD is an open-source Unix. Sony PlayStation runs on a modified version of FreeBSD. Darwin, the open-source kernel that underlies macOS, is a derivative of Mach, which in turn descended from Unix. Cisco IOS is based on a Unix-like, real-time operating system called QNX. Today’s most popular open-source operating system, Linux, is not Unix, but it looks, feels, and acts like Unix. And at the core of the Android operating system is Linux. Then, there is Microsoft Windows, the operating system that runs large governments and large businesses. It is most assuredly not Unix. Windows traces its roots to Unix’s contemporary and competitor, VMS. Other operating systems have gone defunct, but the descendants of Unix and VMS are thriving.

From the very start, Unix was conceived as not merely an operating system, but a comprehensive programming environment. It comes complete with programming tools, documentation tools, and administration tools. Unix did not put up artificial boundaries that separate programmers, technical writers, and system administrators. Unix is the power user’s asylum. Indeed, Unix was the original IDE. VMS, although just as capable, had a different philosophy. It was targeted at business users, who neither desired nor countenanced fiddlers. These opposing philosophies live on in macOS and Windows, and are clearly observable, when the pretty, user-interface veneers are peeled off.

Software development work today is done on Linux, macOS, and Windows. I grew up on UNIX®, as it was spelled back in the day. I like Unix’s boffin-friendly disposition and use-mindfully philosophy, so I work on descendants of Unix, macOS and Linux, most of the time. But if you have not yet developed an affinity for one, use all three systems. Most programming tools are available on all three. Whatever your preference, understand that the operating system is an integral part of your “integrated” software development environment.

Now, let us talk about the IDE, which is likely the only software development tool you will use in most circumstances. In the not-so-distant past, programming involved many distinct steps, each requiring a disparate set of tools. I shall explain this old process, so that you can better appreciate what a modern IDE does for you.

Under the traditional software development process of days-gone-by, the programmer starts by analysing the requirements. He then selects an appropriate design elements for the solution, and sketches out his composite design on paper. The programmer uses English and mathematics to conduct his analysis and design. Although he is not yet using a programming language at this stage, this step is the most important one in the entire programming process, because a solid understanding of the problem and a careful choice of a solution are the keys to a successful creation of a programme. Next, the programmer translates his paper-and-pencil design into a programme by typing in the code into an editor and by saving the code in a text file.

Once typing is completed, he compiles the code by presenting the source file to the compiler. The compiler translates the programme text into an executable machine code, if all goes well. If there are syntax errors (grammatical errors) in the code, the compiler emits cryptic error messages. The programmer must now decipher these error messages, find the syntax errors in the programme, fix them, and recompile. He repeats this until all syntax errors have been eliminated, and the compiler produces an executable file.

Now, the programmer runs the executable with a set of test data, and sure enough he discovers semantic errors (logical errors) in his programme. These errors, called bugs, may either cause the programme to crash, or they may cause it to produce incorrect results. I know of no programmer who can create, in one go, a non-trivial programme that is free of bugs. That is because such a programmer does not exist. The programmer must now identify and fix the errors. This step is called testing, and the tool for this job is the debugger. The debugger allows the programmer to evaluate his code one line at a time, as though the programming language were an interpreted language, and not a compiled one. Eventually, the programmer eliminates all the bugs discovered during testing, and the programme is considered finished. Note though that all substantial programmes contain undiscovered bugs. So, bug fixes and new releases are integral to the software development life cycle. Indeed, discovering and eliminating bugs in the existing software is more important than adding new features. Otherwise, you will simply add more bugs to a bug-laden software.

A modern programming process is quite different, thanks to the IDE. The IDE integrates the distinct steps and disparate tools into a unified, coherent collection. The programmer types in his code in the editor window of the IDE. The editor even formats and renders the programme text in a way that is easy on the eyes. The keywords are shown in a unique colour, code blocks are indented to accentuate their hierarchical structure, and so forth. And even as the programmer types, the IDE analyses the code, identifies the syntax errors therein, and suggests to him the fixes. Thereafter, the programmer presses a button, which causes the IDE to compile the code on the fly and to start the built-in debugger. Compilation is almost instantaneous, because the IDE has already done the bulk of the code analysis work, while the programmer was typing. The programmer now steps though his code, line by line, in the integrated debugger. The debugger mimics the look and feel of the familiar editor, complete with syntax highlights and block indentations. And if the target platform is an external device, say an iPhone, the IDE can debug the programme on an integrated device emulator. Suffice it to say the IDE is a timesaver.

Microsoft’s multi-platform, open-source [Visual Studio Code](https://code.visualstudio.com/) (VScode) is a great tool, despite being a relatively new product. It has support for just about every programming language. It can be used for web, desktop, mobile, embedded, or IoT development work. In any event, I present below a list of popular software development tools. When you start using a new language on a new project, try VScode first. Only if you are dissatisfied with it, try the tools listed here.

**Logical**

- Prolog—Emacs

**Relational**

- SQL—[DataGrip](https://www.jetbrains.com/datagrip/), Emacs

**Functional**

- Scheme—[Racket](http://racket-lang.org/)
- Clojure—[Eclipse](http://www.eclipse.org/), [Emacs](http://www.gnu.org/software/emacs/)
- Scala—Eclipse
- F#—[Visual Studio](http://visualstudio.microsoft.com/), [Rider](https://www.jetbrains.com/rider/)
- Rust—[CLion](https://www.jetbrains.com/clion/)
- Erlang—Eclipse
- Haskell—Eclipse, Emacs 
- Mathematica—[Mathematica](http://www.wolfram.com/mathematica/)
- R—[RStudio](http://www.rstudio.com)

**Objective**

- Smalltalk—[Squeak](http://www.squeak.org/)
- Ruby—Eclipse, [Xcode](http://developer.apple.com/xcode/), [RubyMine](https://www.jetbrains.com/ruby/)
- Java—Eclipse, Xcode
- C#—Visual Studio, Rider
- C++—Eclipse, Xcode, Visual Studio, CLion
- Objective-C—Xcode, [AppCode](https://www.jetbrains.com/objc/)
- Swift—Xcode, AppCode
- Go—Eclipse, [GoLand](https://www.jetbrains.com/go/)
- JavaScript—Eclipse, Xcode, [Atom](https://atom.io/), [WebStorm](https://www.jetbrains.com/webstorm/)
- TypeScript—Atom, WebStorm
- Python—[Jupyter](https://jupyter.org/), Eclipse, Xcode, [PyCharm](https://www.jetbrains.com/pycharm/)

**Procedural**

- C—Emacs, Eclipse, Xcode, CLion
- Matlab—[Matlab](http://www.mathworks.com/products/matlab/), Octave (mostly compatible with Matlab)

- Bourne shell—Emacs, [vi](http://www.atmos.albany.edu/deas/atmclasses/atm350/vi_cheat_sheet.pdf)
- AWK—Emacs, vi
- Perl—Emacs, vi

**Mechanical**

- ARM—[ARM Development Studio](https://www.arm.com/products/development-tools/embedded-and-software/arm-development-studio)
- AVR—[Arduino IDE](https://www.arduino.cc/en/software)

Software development is much more than just programming. You will need to use several other tools: communication, collaboration, documentation, and project management. These tools used to be separate, but are now merging with one another.

People still communicate by phone, email, and text messaging, but they are now making increasing use of information repositories like [MediaWiki](http://www.mediawiki.org/wiki/MediaWiki), [Confluence](http://https://www.atlassian.com/software/confluence), [Basecamp](http://https://basecamp.com/), and [SharePoint](http://office.microsoft.com/en-us/sharepoint/). MediaWiki is open-source and you have to run it on an in-house server, but the others are available as paid on-line services. For small project teams on a tiny budget, consider using free tools: [Meet](https://apps.google.com/meet/), [Gmail](http://mail.google.com), [Calendar](http://www.google.com/calendar), [Drive](http://drive.google.com), [GitHub pages](https://pages.github.com/) and [GitHub repository](https://github.com/). And you can create a public presence for your project on [Twitter](https://twitter.com/).

The best project management advice I can offer is this. Track every major event that occurs on the project by immediately creating a brief entry in the wiki, memorialising at a minimum the event, the decision, the factors considered, and the identities of the deciders. And if you do not use a dedicated time-tracking system, record the hours you worked on each task, when you make a log entry in the wiki. Record the time with a tenth-of-an-hour, or six-minute, precision, as in 3.9 or 4.1, not 4. The wiki, thus, preserves a record of who made what key decisions, who partook in the decision making, who received what information and when, what tasks were planned, who spent how much time on a task, what delayed the progress, and so on.

This record will become necessary when problems erupt. You may need to justify the team’s expenditures to the sponsor, for instance. Or you may have to defend against a legal action. You will then be happy that you had recorded all the important bits in the wiki. If your company intends to patent your work, a record of who invented what and when, who implemented which and how, who spent how much effort on what, etc., will become pertinent. And if your company’s exit strategy is a mergers and acquisitions (M&A) transaction, count on the fact that your product will be examined under the accountant’s magnifier. Having this record will smooth the valuation process.

But the most important reason to have a project wiki is to share information effectively and efficiently with those who need it. A big word like “collaboration” has no bite, unless the project participants share the essential information. And the information you maintain in the wiki gives you a historical insight into the project, which you may use to steer the execution of the upcoming phases of the project, as well as future projects. This information is the institutional knowledge that will not evaporate, when key team members depart.

And regardless of whether your project team is large, small, or solo, you should use a source code repository like [Git](http://git-scm.com/). GitHub provides an excellent support for this, and it is free to boot. A source code repository not only stores the latest version of the code, it retains the complete history of who made what changes and when. And if things go awry with your current version, you can backtrack to the previous, working version. This is why I strongly advise never to check in a source file to the repository, until you have eliminated all known bugs therein, and your programme has passed all the existing tests. In other words, keep the source code repository as clean as humanly possible. And while the requirements, design, and business justification documents are fine and good, do make it a habit to document your algorithmic decisions in comments, as well.

Information is power. Some use information to seize power for themselves. We programmers use it to empower everyone.

# CONVECTIONS

At present, the IT industry is in a state of disquiet. New devices arrive on the market every few months. Operating systems get patched with astonishing frequency, and new security holes are discovered with even greater frequency. New languages are continually added to an already-formidable mound of [existing languages](http://en.wikipedia.org/wiki/List_of_programming_languages), but without making substantive advancement to the state of the art. An equally chaotic growth occurs as well in application frameworks.

*Frameworks* are all the rage in software development, at present. They handle the detailed, system-level work like rendering user interface widgets, enforcing security policies, ensuring data integrity, and so on, thereby allowing the programmer to focus on his application. The Android application framework is one such example. *Libraries* are a more traditional approach. They, too, conceal system-level implementation details, but they work differently from frameworks. The C standard I/O library is an example of a well-designed library.

The key difference between a framework and a library is this. A framework is an application with an imperious disposition. It obliges the programmer to do its bidding by writing plug-in components for it, and it uses them where and when *it* pleases. A library, on the other hand, is servile component. And it is not an application. It is a collection of pre-programmed facilities that perform small amounts of work. From within his application, the programmer uses these procedures where and when *he* pleases.

As such, a framework forces the programmer to think and work in a particular way. It will condescend to perform the low-level tasks for the programmer, so long as he adheres to its dicta. But if the programmer transgresses even slightly, his programme will not compile, or worse, his application will fail at runtime in unexpected ways, thereby vexing the users. A framework establishes software development standard by requiring programmers to think and work in a prescribed way. It reduces workload and increases productivity by relieving the programmers of the responsibility to handle the niggly bits. And because it takes care of the low-level tasks, programmers are free to focus on their applications. So, a framework is a fabulous idea. But in practice, things are not that rosy.

No two programmers think and work alike, and not one programmer appreciates being told by another how he should think and work. As such, just about every experienced programmer believes he has a better idea for a new framework, and countless masses go on to create new frameworks of their own. Moreover, there are many different categories of frameworks: user interface, web application, web service, data exchange, security, communication, cloud computing, parallel computing, persistent storage, and so on. Read the Wikipedia article [*Comparison of web application frameworks*](http://en.wikipedia.org/wiki/Comparison_of_web_application_frameworks) to see how many of them there are in just one category—web application frameworks. By the way, that lengthy article covers only a partial list of web application frameworks in existence. Moreover, each category of framework will have many competing implementations, each intended for a different language or an operating system, and each aimed at a particular application domain. This violent proliferation of frameworks depresses their potential utility, because good ideas are locked into incompatible framework, instead of coming together in a coherent whole.

New frameworks are being created daily, and the old ones continually moult in order to compete with the new challengers. Indeed, the pace of development is so furious that most framework designers do not bother creating documentations at all. They expect the users to look at the code to learn to use their frameworks. Barmy!

Frameworks aspire to standardise software development. But that goal remains as unattainable as any good aspiration. It is not difficult to imagine the chaos that roils at the junction of several convective currents: new languages, new frameworks, new operating systems, new hardware, new programmers, new economic realities, new [global pandemics](https://en.wikipedia.org/wiki/Coronavirus_disease_2019).

## *failure to standardise*

The desire to standardise is not peculiar to the IT industry. Nor is the idea revolutionary. Virtually every field of human endeavour relies on industry-wide standards. For instance, a civil engineer designs a bridge in accordance with the architect's vision and in compliance with the standard engineering practices, using materials of standardised dimensions and strengths that have been shown to meet relevant government safety standards. Departing from these standards is an anathema to an engineer, because it is a breach of professional code of conduct and a violation of the law. A failure to adhere to the standards could lead to loss of property and lives, and it may result in a loss of license to practice, and perhaps even a jail term, for the engineer. By contrast, there is not even an industry-wide standard for a software developer to follow. Here, I am talking about a software developer who implements commonplace software like a social media site or an enterprise application, not one who creates life-critical software like avionics software, power plant monitoring software, or air traffic control software. Hardware engineers and software developers in those specialities do follow very stringent standards and regulations.

Indeed, engineers, architects, lawyers, doctors, dentists, pharmacists, and accountants are allowed to practice their profession, only if they pass the standardised licensing examinations administered by their state governments. Such is not the case in software development. Because programming is not a licensed profession subject to strict government regulations, the term “software engineering” is an oxymoron.

There is another fundamental difference between software development and traditional engineering. A civil engineer would choose with equanimity a supplier who promises to deliver I-beams that have been certified to meet the government safety standards. And he would incorporate the material into his bridge design using proven engineering methods that have existed for hundreds, if not thousands, of years. But a software developer typically goes through the following rigmarole: explore the existing frameworks, select a promising framework, struggle with the framework’s design choices, abandon the framework, choose another framework, and repeat the process. Eventually, his frustrations with the products of others grow too great to bear, and he proceeds to create his own framework. A civil engineer, however, cannot storm out of his office in disgust, and fashion a new I-beam in his backyard. Even if he could, his homemade I-beam is unlikely to meet the government safety standards. In traditional engineering, everyone is required to follow the industry standards for safety and compatibility reasons. But in software development, individual, ad hoc solutions are the “industry standards”.

But the most significant of differences between the I-beam hardware and the framework software is this. A standardised I-beam imposes external constraints—like budget, length, weight, strength, and longevity—on the civil engineer’s design, but it does not restrain him internally. When designing his structure, he is able to exercise his intellectual freedom. A software framework, on the other hand, imposes on the software developer a particular way of thinking—someone else’s preferred way of thinking—thereby robing him of the intellectual freedom he so cherishes. Imagine if all civil engineers are allowed to build their bridges only if they adhere strictly to the design of [the first iron bridge](https://en.wikipedia.org/wiki/The_Iron_Bridge)—there will be riots. The desire to break arbitrary restraints upon creativity is the main reason why software developers reinvent frameworks, endlessly.

At present, there is no one best way to wade through the language-framework-platform-architecture quagmire. My advice is to start your career by mastering a small collection of seminal languages and one or two established frameworks in the relevant application domain. Even if your work requires you to know just one language, take up other languages from different programming paradigms, and use them in your personal projects. The same goes for frameworks. In this way, gradually incorporate more languages and frameworks into your repertoire. With experience, it becomes easier to learn new languages and frameworks, because you can quickly build a new layer of knowledge atop a solid foundation of prior experiences.

But do not foist upon the coworkers your favourite new toy. Propose, by all means, but do not dictate. Adopt a new language or a framework, only if the majority of the team agrees, and the management approves, based on thorough analysis of risks and needs. In addition to technical merits, there are economic, political, social, and other factors that must be considered, when adopting a new, radically different technology. Above all, do not use your client's time and money to pick up that new language or framework you have always wanted to learn. That is unethical.

As I mentioned above, software development is much more than merely learning one programming language and using it to solve every problem encountered. On the other hand, what makes you a good programmer is not how many languages you know, but how many different ways you can reason about, and solve, a problem. A variety of reasoning methods can only be acquired through experience in myriad mathematical concepts and different programming paradigms. So, when selecting new languages to study, choose based on not only their popularity, but also their conceptual uniqueness.

It is also essential that you know intimately the operating systems and the computer architectures you work with. And as you climb up the career ladder, you will invariably need to develop leadership skills, which comprise technical knowhow, communication skills, business acumen, financial savvy, social conscience, legal sophistication, political astuteness, management talent, psychological sensibilities, immaculate timing, and angelic patience. You will acquire these skills in due course. But for now, focus on honing your English, mathematics, science, and technology skills. Most of all, be cool, stay in school.

# CONCLUSION

If one language is insufficient, what languages should you learn at a minimum? Regardless of your career specialisation, if you plan to write more than a few lines of code in the foreseeable future, you should at least know the following foundational languages:

**Declarative**

- Logical—[Prolog](https://www.swi-prolog.org/)
- Relational—[SQL](https://www.postgresql.org/)
- Functional—[Standard ML](https://www.smlnj.org/)

**Imperative**

- Objective—[Smalltalk](http://www.squeak.org/)
- Procedural—[C](http://gcc.gnu.org/)
- Mechanical—[Arduino](https://www.arduino.cc/reference/en/)

It is fair to say that all popular, modern languages have a mixed ancestry comprising of Lisp, ML, Smalltalk, and C. With these languages as your foundation, you are better prepared to learn new programming concepts. A solid understanding of C, especially its pointer and memory facilities, will prepare you for operating system kernels, device drivers, 3D simulation engines, IoT, and other low-level, system programming tasks. Also, since many scripting languages like AWK, Perl, and JavaScript have C-like syntax, your knowledge of C will enable you to gain proficiency in those languages, quickly. Knowing Smalltalk in addition to C will ease learning Ruby, Objective-C, Swift, Kotlin, Go, C++, Java, C#, and indeed every object-oriented language currently in use. And proficiency in Scheme and ML will prepare you well for studying other functional languages like Clojure, Scala, F#, OCaml, Haskell, Erlang, and Elixir. Most people use popular scripting languages like JavaScript, TypeScript, and Python exclusively as object-oriented languages. But these languages also support the functional programming paradigm. Your background in functional programming will enable you to write clean, succinct, maintainable code in any language. Functional background will also help a great deal, when you study algorithm analysis and design, as part of your computer science curriculum. And you should consider taking foundational courses in computing, like [logical reasoning](http://en.wikipedia.org/wiki/Logical_reasoning), [discrete mathematics](http://en.wikipedia.org/wiki/Discrete_mathematics), and [algorithm analysis](https://en.wikipedia.org/wiki/Analysis_of_algorithms), even if you have no plans to major in computer science.

It is fine to have a favourite programming language. Mine is Standard ML, for its correctness, safety, pragmatism, and longevity. But we can ill afford to stick with just one language over the course of our careers. Every language is designed for a particular task, and it is, at best, a compromise when applied to tasks for which it was not intended. Knowing and using multiple languages from different paradigms and different application domains will help you think and work efficiently, whatever your speciality. In computing, one needs both the breadth of knowledge and the depth thereof.

I shall conclude with the following observation. New programming languages and application frameworks come out, incessantly. The IT industry takes delight in inventing new wheels that are almost as round as the old ones. One lifetime is insufficient to master every new thing that pops out of a hole. Nevertheless, use Google, Twitter, and other services to monitor the evolving trends, and at least try to figure out where on the family tree the new languages hang, even if you do not have the opportunity to immerse yourself in them. Every new language belongs to a lineage, no matter how tenuous its link to the seminal language of that family line. By knowing the mother language of that lineage, you will be well prepared to absorb and adopt any new language, when the need arises. And as I mentioned above, mastering only four mother languages—Scheme, ML, Smalltalk, and C—will prepare you to pick up any new language without undue effort.

> “What has been will be again, what has been done will be done again; there is nothing new under the sun.”
>
> — Ecclesiastes 1:9

For the moment, the darlings of the IT industry are JavaScript on the client side and Java on the server side. The next top language will likely be a Java-compatible, functional language. Kotlin and Scala are two such languages on the rise, and a few short years ago, it was Clojure. It is impossible to know what will become of any them in the near future. Language evolution through mutation is not new. C took ideas from Algol. C++ snuck onto the market on the backs of C and Simula. Java beat C++ at its own game. Kotlin and Scala may take Java’s place someday, maybe not. But sooner or later, Java’s reign will end and JavaScript will fall. Nothing is permanent. Come what may, your prepared mind is ready.

> “To every thing there is a season, and a time to every purpose under the heaven.”
>
> — Ecclesiastes 3

## *resources*

**Theory**

- *[The Next 700 Programming Languages](https://www.cs.cmu.edu/~crary/819-f09/Landin66.pdf)*, Landin
- [*The Little Prover*](http://www.amazon.com/Little-Prover-Daniel-P-Friedman/dp/0262527952/ref=sr_1_4?ie=UTF8&qid=1433974273&sr=8-4&keywords=theorem+proving), Friedman
- *[The Little Typer](https://www.amazon.com/Little-Typer-MIT-Press/dp/0262536439/ref=sr_1_1?dchild=1&keywords=The+Little+Typer&qid=1612639929&sr=8-1)*, Friedman
- [*Understanding Arguments: An Introduction to Informal Logic*](http://www.amazon.com/Understanding-Arguments-Introduction-Informal-Logic/dp/0495603953/ref=sr_1_fkmr0_1?ie=UTF8&qid=1433974594&sr=8-1-fkmr0&keywords=walter+sinnot+Armstrong), Armstrong
- *[Category Theory for Programmers](https://github.com/hmemcpy/milewski-ctfp-pdf)*, Milewski
- [*Statistics*](http://www.amazon.com/gp/product/0393929728/ref=pd_lpo_sbs_dp_ss_1?pf_rd_p=1944687742&pf_rd_s=lpo-top-stripe-1&pf_rd_t=201&pf_rd_i=0393970833&pf_rd_m=ATVPDKIKX0DER&pf_rd_r=1S1TBWX07JCT43D899C3), Freedman
- [*Discrete Mathematics with Applications*](http://www.amazon.com/Discrete-Mathematics-Applications-Susanna-Epp/dp/0495391328/ref=sr_1_2?s=books&ie=UTF8&qid=1433950209&sr=1-2&keywords=discrete+structures), Epp
- *[Introduction to Functional Programming](https://usi-pl.github.io/lc/sp-2015/doc/Bird_Wadler.%20Introduction%20to%20Functional%20Programming.1ed.pdf)* (IFP), Bird
- [*Structure and Interpretation of Computer Programs*](http://www.amazon.com/Structure-Interpretation-Computer-Programs-Engineering/dp/0262510871/ref=sr_1_8?s=books&ie=UTF8&qid=1401819781&sr=1-8&keywords=scheme+steele) (SICP), Abelson
- *[How to Design Programs](https://htdp.org/2021-5-4/Book/index.html)* (HDP), Felleisen
- *[Concepts, Techniques, and Models of Computer Programming](https://www.amazon.com/Concepts-Techniques-Models-Computer-Programming/dp/0262220695/ref=sr_1_3?dchild=1&keywords=Concepts%2C+Techniques%2C+and+Models+of+Computer+Programming&qid=1629563174&sr=8-3)* (CTM), van Roy
- [*Introduction to Algorithms*](http://www.amazon.com/Introduction-Algorithms-3rd-Thomas-Cormen/dp/0262033844/ref=sr_1_3?s=books&ie=UTF8&qid=1433949776&sr=1-3&keywords=algorithms), Cormen
- [*The Art of Computer Programming*](http://www.amazon.com/Computer-Programming-Volumes-1-4A-Boxed/dp/0321751043/ref=sr_1_1?s=books&ie=UTF8&qid=1433949817&sr=1-1&keywords=knuth), Knuth
- [*Introduction to Graph Theory*](http://www.amazon.com/Introduction-Graph-Theory-Dover-Mathematics/dp/0486678709/ref=sr_1_1?s=books&ie=UTF8&qid=1433975084&sr=1-1&keywords=graph+theory), Trudeau
- [*Theory of Computation: Formal Languages, Automata, and Complexity*](http://www.amazon.com/Theory-Computation-Languages-Automata-Complexity/dp/0805301437/ref=sr_1_2?s=books&ie=UTF8&qid=1433949889&sr=1-2&keywords=automata+theory), Brookshear
- *[Introduction to Functional Programming](https://usi-pl.github.io/lc/sp-2015/doc/Bird_Wadler.%20Introduction%20to%20Functional%20Programming.1ed.pdf)*, Bird
- [*An Introduction to Functional Programming Through Lambda Calculus*](http://www.amazon.com/Introduction-Functional-Programming-Calculus-Mathematics-ebook/dp/B00CWR4USM/ref=sr_1_3?s=books&ie=UTF8&qid=1433950302&sr=1-3&keywords=functional+programming), Michaelson
- [*An Introduction to Mathematical Cryptography*](http://www.amazon.com/Introduction-Mathematical-Cryptography-Undergraduate-Mathematics/dp/1441926747/ref=sr_1_16?s=books&ie=UTF8&qid=1433950146&sr=1-16&keywords=cryptology), Hoffstein
- [*Paradigms of Artificial Intelligence Programming: Case Studies in Common Lisp*](http://www.amazon.com/Paradigms-Artificial-Intelligence-Programming-Studies/dp/1558601910/ref=sr_1_1?s=books&ie=UTF8&qid=1433950620&sr=1-1&keywords=lisp+artificial+intelligence), Norvig
- [*Database in Depth: Relational Theory for Practitioners*](http://www.amazon.com/Database-Depth-Relational-Theory-Practitioners/dp/0596100124/ref=la_B000AQ6OJA_1_4?s=books&ie=UTF8&qid=1433950017&sr=1-4), Date
- [*Computer Architecture*](http://www.amazon.com/Computer-Architecture-Fifth-Quantitative-Approach/dp/012383872X/ref=la_B000APA2GC_1_2?s=books&ie=UTF8&qid=1433950857&sr=1-2), Hennessy
- [*The Design of the Unix Operating System*](http://www.amazon.com/Design-UNIX-Operating-System/dp/0132017997/ref=sr_1_1?ie=UTF8&qid=1433949574&sr=8-1&keywords=bach+unix), Bach
- [*Discrete-Event System Simulation*](http://www.amazon.com/Discrete-Event-System-Simulation-Jerry-Banks/dp/0136062121/ref=sr_1_1?s=books&ie=UTF8&qid=1433950986&sr=1-1&keywords=discrete+simulation), Banks
- [*Computer Graphics: Principles and Practice in C*](http://www.amazon.com/Computer-Graphics-Principles-Practice-2nd/dp/0201848406/ref=sr_1_2?s=books&ie=UTF8&qid=1433949713&sr=1-2&keywords=foley+computer+graphics), Foley
- [*The Elements of Style*](http://www.amazon.com/Elements-Style-Fourth-William-Strunk/dp/020530902X/ref=sr_1_1?ie=UTF8&qid=1433955145&sr=8-1&keywords=elements+of+style), Strunk
- [*Elements of Grammar*](http://www.amazon.com/Elements-Grammar-Margaret-Shertzer/dp/0028614496/ref=sr_1_1?ie=UTF8&qid=1433955155&sr=8-1&keywords=elements+of+grammar), Shertzer

**Practice**

- *[ML for the Working Programmer](https://www.amazon.com/ML-Working-Programmer-2nd-Paulson/dp/052156543X)*, Paulson
- *[OCaml from the Very Beginning](https://www.amazon.com/OCaml-Very-Beginning-John-Whitington/dp/0957671105/ref=sr_1_1?dchild=1&keywords=OCaml+from+the+Very+Beginning&qid=1611698270&sr=8-1)*, Whitington
- *[Programming in Haskell](https://www.amazon.com/Programming-Haskell-Graham-Hutton/dp/1316626229/ref=sr_1_1?dchild=1&keywords=hutton+haskell&qid=1611698302&sr=8-1)*, Hutton
- [*The Joy of Clojure*](http://www.amazon.com/Joy-Clojure-Michael-Fogus/dp/1617291412/ref=sr_1_2?s=books&ie=UTF8&qid=1401774361&sr=1-2&keywords=clojure), Fogus
- [*Programming in Scala: A Comprehensive Step-by-Step Guide*](http://www.amazon.com/Programming-Scala-Comprehensive-Step---Step-ebook/dp/B004Z1FTXS/ref=sr_1_1?s=books&ie=UTF8&qid=1401774514&sr=1-1&keywords=scala), Odersky (Scala designer)
- [*Expert F#*](https://www.amazon.com/Expert-F-4-0-Don-Syme/dp/1484207416/ref=sr_1_2?dchild=1&keywords=syme+f#&qid=1608771880&s=books&sr=1-2), Syme
- [*Programming Erlang: Software for a Concurrent World*](https://www.amazon.com/Programming-Erlang-Concurrent-Pragmatic-Programmers/dp/193778553X/ref=sr_1_1?dchild=1&keywords=armstrong+erlang&qid=1608771930&s=books&sr=1-1), Armstrong
- [*Real World Haskell: Code You Can Believe In*](http://www.amazon.com/Real-World-Haskell-Code-Believe-ebook/dp/B0026OR2FY/ref=sr_1_3?s=books&ie=UTF8&qid=1401804657&sr=1-3&keywords=haskell), O’Sullivan
- [*Wolfram Language and System*](http://reference.wolfram.com/language/), Wolfram, Inc. (Mathematica designer)
- [*The R Book*](http://www.amazon.com/R-Book-Michael-J-Crawley/dp/0470973927/ref=sr_1_16?s=books&ie=UTF8&qid=1401772904&sr=1-16&keywords=r+language+programming), Crawley
- [*Programming in Prolog: Using the ISO Standard*](http://www.amazon.com/Programming-Prolog-Using-ISO-Standard/dp/3540006788/ref=sr_1_1?ie=UTF8&qid=1401776122&sr=8-1&keywords=prolog), Clocksin
- [*Learning SQL*](http://www.amazon.com/Learning-SQL-Alan-Beaulieu/dp/0596520832/ref=sr_1_3?s=books&ie=UTF8&qid=1401774621&sr=1-3&keywords=sql), Beaulieu
- [*Smalltalk-80: The Language*](http://www.amazon.com/Smalltalk-80-Language-Adele-Goldberg/dp/0201136880/ref=sr_1_1?s=books&ie=UTF8&qid=1401774209&sr=1-1&keywords=smalltalk), Goldberg (Smalltalk designer)
- [*Programming Ruby: The Pragmatic Programmers' Guide*](http://www.amazon.com/Programming-Ruby-1-9-2-0-Programmers/dp/1937785491/ref=sr_1_5?s=books&ie=UTF8&qid=1401774107&sr=1-5&keywords=ruby), Thomas
- [*The Java Language Specification*](http://www.amazon.com/Java-Language-Specification-SE-ebook/dp/B00BHEY5EU/ref=sr_1_23?s=books&ie=UTF8&qid=1401773907&sr=1-23&keywords=java), Gosling (Java designer)
- [*C# in a Nutshell: The Definitive Reference*](http://www.amazon.com/C-8-0-Nutshell-Definitive-Reference/dp/1492051136/ref=sr_1_4?dchild=1&keywords=C%23&qid=1608772000&s=books&sr=1-4), Albahari
- [*The C++ Programming Language*](http://www.amazon.com/C-Programming-Language-4th/dp/0321563840/ref=sr_1_1?s=books&ie=UTF8&qid=1401773170&sr=1-1&keywords=C%2B%2B+language+programming), Stroustrup (C++ designer)
- [*Effective Go*](http://golang.org/doc/effective_go.html), Google, Inc. (Go designer)
- [*Swift Programming Language*](http://developer.apple.com/library/prerelease/ios/documentation/Swift/Conceptual/Swift_Programming_Language/index.html#//apple_ref/doc/uid/TP40014097), Apple, Inc. (Swift designer)
- [*JavaScript: The Definitive Guide*](http://www.amazon.com/JavaScript-Definitive-Guide-Activate-Guides-ebook/dp/B004XQX4K0/ref=sr_1_2?s=books&ie=UTF8&qid=1401775003&sr=1-2&keywords=javascript), Flanagan
- [*Programming TypeScript: Making Your JavaScript Applications Scale*](https://www.amazon.com/Programming-TypeScript-Making-JavaScript-Applications/dp/1492037656/ref=sr_1_3?dchild=1&keywords=typescript&qid=1608772098&sr=8-3), Cherny
- [*The Python Tutorial*](http://www.amazon.com/Python-Tutorial-2-7-5-Guido-Rossum-ebook/dp/B00FJRV9QI/ref=sr_1_13?s=books&ie=UTF8&qid=1401775234&sr=1-13&keywords=python), van Rossum (Python designer)
- [*The C Programming Language*](http://www.amazon.com/Programming-Language-2nd-Brian-Kernighan/dp/0131103628/ref=sr_1_8?s=books&ie=UTF8&qid=1401772856&sr=1-8&keywords=r+language+programming), Ritchie (C designer)
- [*Matlab Language Fundamentals*](http://www.mathworks.com/help/matlab/index.html), MathWorks, Inc. (Matlab designer)
- [*The AWK Programming Language*](http://www.amazon.com/The-AWK-Programming-Language-Alfred/dp/020107981X/ref=sr_1_1?ie=UTF8&qid=1401820819&sr=8-1&keywords=awk+programming), Aho (AWK designer)
- [*Programming Perl: Unmatched Power for Text Processing and Scripting*](http://www.amazon.com/Programming-Perl-Unmatched-processing-scripting/dp/0596004923/ref=sr_1_1?s=books&ie=UTF8&qid=1401820920&sr=1-1&keywords=Programming+Perl), Wall (Perl designer)
- [*The Unix Programming Environment*](http://www.amazon.com/Unix-Programming-Environment-Prentice-Hall-Software/dp/013937681X/ref=sr_1_1?s=books&ie=UTF8&qid=1401775485&sr=1-1&keywords=The+Unix+Programming+Environment), Kernighan (Unix designer)
- [*Unix Network Programming*](http://www.amazon.com/Unix-Network-Programming-Sockets-Networking/dp/0131411551/ref=sr_1_1?s=books&ie=UTF8&qid=1433949655&sr=1-1&keywords=stevens+network+programming), Stevens
- [*LaTeX: A Document Preparation System*](http://www.amazon.com/LaTeX-Document-Preparation-System-2nd/dp/0201529831/ref=sr_1_2?ie=UTF8&qid=1433957749&sr=8-2&keywords=lamport), Lamport
