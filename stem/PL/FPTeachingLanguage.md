---
title: "𝜆aconic"
tags:
  - mathjax
use_math: true
---

## *a proposal for an FP teaching language*

[TOC]

As of this writing in 2025, the most popular languages used in the industry—C++, Python, Java, JavaScript, OCaml, Haskell—were all created in the 1980s and the 1990s. The youngest of the lot, JavaScript, is 30 years old, now. In IT, that is an eternity. So, these popular languages may fairly be labelled "old", and unfairly "infirm". Still, these popular, industrial languages had done their best to keep up with the new trends in language design and implementation that had emerged over the past three decades. But there is no denying that these languages, despite their capability and prominence, feel ectopic at places, mainly due to the retrofitting of modern syntactic constructs and semantic concepts into a decades-old design lattice. So, every now and again, it is appropriate to create new programming languages that incorporate modern thinking on language design. I hereby propose $\lambda$aconic, a new, small, simple, pure-FP, teaching language.

Modern pure FP languages (Haskell, PureScript, etc.) and hybrid OO-FP languages (OCaml, F#, Scala, Kotlin, Swift, etc.) are large, powerful, industrial-strength languages with massive ecosystems. In a not-so-distant past, FP was taught using small, simple languages, namely Scheme (with a strong, dynamic type system) and ML (with a strong, static, polymorphic, inferencing type system). The Lisp family of languages, including Scheme, fell out of favour with both academia and industry, in the 1990s. Racket, a modern Scheme, still has a small, but strong, community of users, especially in academia. But the user community of Standard ML, the modern ML, is very small, smaller even than that of Racket's. To my knowledge, no CS university programme uses Standard ML to teach FP, any longer. Also, the modern versions, [R$^7$RS Scheme](https://codeberg.org/scheme/r7rs) and [Standard ML 1997](https://mitpress.mit.edu/9780262631815/the-definition-of-standard-ml/), have evolved into large, complicated languages. Unfortunately for today's FP novices, these very-complicated, industrial-strength languages are all they have, and they must wade through the inherent complexities of advanced features, as they try to navigate the basic concepts of the FP paradigm.

Proponents of various industrial FP languages argue that novices just have to avoid using the advanced features, when learning the FP paradigm. But that argument is fallacious: novices, especially those who are learning FP on their own, simply do not possess the ware with all to extricate the fundamental concepts of FP from a massive pool of complicated language features. In my view, the older, smaller, simpler version of ML, in which I learned typed FP many years ago, is the superior platform for teaching FP to CS undergraduates.

[ML](https://en.wikipedia.org/wiki/ML_(programming_language)) was arguably the first typed FP language, and in a fairly short time, it became a popular FP teaching language in academia. ML was not conceived as an industrial-strength programming language; it was designed to implement tactics (scripts) that [automate theorem proving](https://en.wikipedia.org/wiki/Automated_theorem_proving). And when it was released in 1973, the dominant languages used in the industry were FORTRAN, LISP, and COBOL. So, ML never escaped academia. But ML gave rise to a series of influential FP languages, including Caml, OCaml, F#, Miranda, Haskell, Scala, to name a few. And just about every popular, modern language, including F#, Reason, Scala, Kotlin, Swift, and even Rust, are proximate descendants of OCaml, and hence distant relatives of ML.

The OO-FP hybrid nature of those OCaml-derived, popular, industrial FP languages is nothing new. [Smalltalk](https://en.wikipedia.org/wiki/Smalltalk), the earliest industrial OO language that became popular in the industry, is a contemporary of ML; it was released in 1972. Smalltalk is a pure-OO language: all things in Smalltalk—numbers, characters, and so—are objects and, indeed, even classes are objects. Smalltalk heavily influenced Object-C and Java. Most every modern OO language is either a direct or an indirect descendant of Smalltalk. Smalltalk also influenced, indirectly, C++, a close relative of the first OO academic language, Simula. And Smalltalk, in turn, was influenced by Simula and LISP.

I now present the design of $\lambda$aconic, a new, small, simple language specifically designed to teach the fundamental concepts of FP to CS undergraduates.

# $𝜆$ACONIC

Today, it is fashionable to learn FP in a sophisticated, industrial-strength, ML descendant language that employs a strong, static, inferencing type system ([Hindley-Milner](https://en.wikipedia.org/wiki/Hindley–Milner_type_system)), referred to in type theory as a [simple type](https://en.wikipedia.org/wiki/Simply_typed_lambda_calculus) system. Do note, though, that this type system is far from simple, especially for novices. But this moniker is used to distinguish it from an even less simple [dependent type](https://en.wikipedia.org/wiki/Dependent_type) system. With some exertion, a novice could learn [FP in Lean](https://lean-lang.org/functional_programming_in_lean/), a very sophisticated, dependently-typed proof assistant.

But I believe that a small, simple FP language, unburdened by industrial-strength paraphernalia, is an ideal platform upon which a novice could, and should, learn the fundamentals of FP. Here, I propose a new FP teaching language, $\lambda$aconic. It has a lightweight, Haskell-like syntax. Surprisingly, though, its semantics is Smalltalk-like. Suffice it to say, our new language is not intended to be used in industrial, enterprise applications. Still, its syntactic proximity to OCaml, F#, Haskell, and Agda makes it easy for the student to transition to myriad industrial-strength FP languages. Indeed, the skills of $\lambda$aconic translate well to the functional subset of Python.

$\lambda$aconic employs a Haskell-like, lightweight syntax. But its semantics is Smalltalk-like in that $\lambda$aconic employs a strong, dynamic type system. But despite being an innately-OO language, $\lambda$aconic pretends to be a pure-FP language. It insists upon immutability. It insists upon the use of recursion as its looping mechanism. It supports functionals. It provides no syntactic facilities, in the traditional OO style. It provides no `derive` or `extend` syntax for inheritance. Instead, it supports [algebraic data types](https://en.wikipedia.org/wiki/Algebraic_data_type) (ADTs), in the FP tradition, for declaring product (record) and sum (union) types, with the Haskell-style typeclasses to implement behavioural inheritance. Also, there are no `private`, `protected`, and `public` visibility modifiers. All components of a record are public since, being a pure-FP language, there is no way to mutate values, which obviates the need for those complicated access-control mechanisms. $\lambda$aconic does provide a coarse-grained visibility control at the module level, rather like how C implements [abstract data types](https://en.wikipedia.org/wiki/Abstract_data_type) (confusingly, also called ADTs) using `static` and `extern`. Thus, $\lambda$aconic is a pure-FP language with a Haskell-like syntax and a Smalltalk-like semantics. These design choices make $\lambda$aconic syntactically compact and semantically comprehensible, making it an ideal for a novice to study the FP paradigm, without entangling himself with OO concepts, like he would be forced to, if he were to use an OCaml-derived OO-FP hybrid, industrial language.

I present this new syntax below, intermixed with semantic discussions where appropriate. Given that CS undergraduate teaching arena being the intended domain of $\lambda$aconic, allowing the use of the Unicode mathematical symbols—$\pi$, $\sigma$, $\le$, $\ge$, $\sqrt{}$, $\infty$, $\bot$, $\lnot$, $\land$, $\lor$, $\emptyset$, $\otimes$, $\oplus$, etc.—as identifier names is the proper design choice, I feel. These symbols are entered using standard [$\LaTeX$](https://en.wikipedia.org/wiki/LaTeX) commands, as is done in Agda. IDEs can provide keyboard shortcuts, of course. Since programming, especially the academic FP variety, is a mathematical activity, the ability to use Unicode identifiers makes implementing mathematical constructs pleasant, rather like typesetting a mathematical text.

The target audience of this article is the designers of teaching languages. The guiding design principles of $\lambda$aconic are comfort, clarity, and concision, in the mathematical tradition. A succinct way to summarise our new language might well be "boring"—as in predictable, unsurprising, familiar. This document was written with a design to promote discussion, but it is not a design document for a new FP language. In other words, the recommendations given here are fragmentary ideas, not firm dicta.

It is also my fervent hope that, having learned FP in a novice-friendly language like $\lambda$aconic, CS graduates would carry their passion for the FP paradigm into graduate school and become researchers that propel the field further. And those who enter the industry would, where appropriate, cattle-drive their OO-crazed colleagues towards the FP paradigm.

# TYPES

We support these primitive types: boolean, character, integer, natural number, and floating-point number. The *boolean* is a one-byte quantity, the *character* is a variable-byte quantity represented using Unicode, the *natural number* is an unsigned 64-bit quantity represented using native binary, the *integer* is a signed 64-bit quantity represented using 2's compliment binary, and the *floating-point number* is a 64-bit quantity represented using the IEEE 754 format. We have no C-style hardware-proximate primitive types, since ours is an academic FP language, not an industry-grade systems programming language. We shall call these primitive types `Bol`, `Chr`, `Nat`, `Int`, and `Flt`, respectively. Larger data types with greater precisions are defined in the standard library: infinite-precision integer as `Integer`, 128-bit integer as `Int128`, and 128-bit floating-point number as `Flt128`. The types `Nat`, `Int`, `Int128`, `Integer`, `Flt`, and `Flt128` constitute the number class `Num`.

The standard library defines the following type aliases for convenience: $\mathbb{B}$ for `Bol`, $\mathbb{U}$ for Unicode `Chr`, $\mathbb{N}$ for `Nat`, $\mathbb{Z}$ for `Int`, $\mathbb{R}$ for `Flt`, and $\mathbb{S}$ for `String` which is aliased to `[𝕌]`. By convention, we use short names like `Int` and `Chr` for primitive types, but longer names like `Integer` and `String` for non-primitive types.

We define type aliases as follows, in a Python-like succinct syntax, without the preceding `type` or `alias` keyword.

```
String : [𝕌] ## type alias
```

Similarly, algebraic data types (ADT) are declared like this, without the preceding `data`, `datatype`, or `record` keyword.

```
Person : {firstName: String, lastName: String, phone: String} ## product type

Bol : ## sum type
  | false
  | true
𝔹 : Bol

List 𝛼 : ## sum of products type
  | []
  | 𝛼,[𝛼]
[𝛼] : List 𝛼
```

Wherever possible, we strive for a uniform syntax, like using `:` for all things type-related, so as to lighten the cognitive load of the programmer. Despite the differences in the way aliases, products, sums, and sums-of-products are implemented by the language, the programmer—especially the novice FP programmer—is free to see the lot of them as just "types". Moreover, we afford the convenience of forward-referring types, so that the programmer need not define a unique order of type definitions, as is the case with most languages, today. The compiler, in the service of the programmer, performs multiple passes to resolve such type references. This behaviour is evident in the declaration of the `List` type above: we used the `[𝛼]` in the second clause of the `List` type, before we aliased it as `[𝛼] : List 𝛼`. But, in general, it is good form to introduce something before using it, like we declared the `Bol` type first, then aliased `𝔹 : Bol`.

Note, also, the expression `𝛼,[𝛼]` in the `List` type declaration. In Haskell, this expression is `𝛼:[𝛼]` and in SML it is `𝛼::[𝛼]`. But because we aim for syntactic consistency and because we use the `,` to separate the list elements in a list literal, as in `[1, 2, 3]`, we reuse the `,` to prepend (cons) `x` to `xx`, as in `x,xx`, where `x` is the element being prepended to the head of the list `xx`. This syntactic consistency eliminates yet another special case that the programmer has to remember.

# FUNCTIONS

We use a slightly-altered version of SML's function definition syntax. That is, we use the `|` symbol to signify each disjoint clause of the function definition. This reuse of the `|` symbol clearly highlights the conceptual proximity between the sum type data constructors and the function clauses: each function clause applies the corresponding sum type data constructor to the argument values, in order to perform pattern matching on those values.

```
qsort : Ord 𝛼 ⇒ [𝛼] → [𝛼]
  | [] → []
  | x,xx → qsort [l | l ← xx, l < x] + [x] + qsort [g | g ← xx, g ≥ x]
```

Above, `Ord 𝛼 ⇒` constrains the type parameter `𝛼` to be an instance of the `Ord` class, so that the `qsort` function may use `<` and `≥` comparison operators on the list elements `x`, `l`, and `g`, each a value of type `𝛼`. We inherit this class-constraint syntax from Haskell. Do note that SML does not have classes, neither in OO sense nor in FP sense; it has functors, instead.

In a functional language like ours, functions are first-class values. As such, they can be held in variables, can be passed to functions, and can be returned from functions. Higher-order functions that accept and return other functions as values are called *functionals*. The name "functional programming" derives from the fact that this style of programming relies on functionals. Since functions are first-class values, we provide a lightweight syntax to define functions, in addition to the clausal syntax described above. Using this lightweight syntax, we may create on-the-fly functions ($𝜆$-functions), as shown below.

```
foldl (𝜆 a x → a + x) 0 [3, 5, 7, 9] ## return 24
```

Above, the function foldl is applied to three arguments: a binary, associative $𝜆$-function `𝜆 a x → a + x`, the initial value `0`, and the list `[3, 5, 7, 9]`. The list, the initial value, and the binary, associative operator, together, form an algebraic structure called a [monoid](https://en.wikipedia.org/wiki/Monoid).

# MODULES

asdf

# IMPLEMENTATION

asdf

# CONCLUSION

asdf
