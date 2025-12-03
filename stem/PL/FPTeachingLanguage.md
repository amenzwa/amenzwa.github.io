---
title: "𝜆aconic"
tags:
  - mathjax
use_math: true
---

## *a proposal for an FP teaching language*

[TOC]

There once was a beautiful little language called [Meta Language](https://en.wikipedia.org/wiki/ML_(programming_language)) (ML) for [Logic of Computable Functions](https://en.wikipedia.org/wiki/Logic_for_Computable_Functions) (LCF). LCF was an early [automated theorem prover](https://en.wikipedia.org/wiki/Automated_theorem_proving). ML was the scripting language for implementing [tactics](https://lean-lang.org/theorem_proving_in_lean4/Tactics/) used in automating theorem proving. Incidentally, LISP, the first FP language, began its life as the implementation language for automated reasoning. Not surprisingly, LCF and ML were initially implemented in LISP. There were a few feeble attempts to industrialise this research language, but all those efforts fizzled in the face of C's dominance as the premiere IT language of the 1980s. But ML did become an important academic research platform in the field of programming language design. ML eventually gave rise to Caml, OCaml, Miranda, Haskell, and just about every modern OO-FP hybrid language, including F#, Reason, Rust, Swift, Kotlin, TypeScript, et al.

In due course, ML was standardised, and it came to be known as Standard ML (SML) 1997. Unlike other language standards, like those for FORTRAN and C, that kept up with the times, SML became frozen in 1997. This militated against SML gaining the critical mass needed for widespread adoption. Still, SML was used as an instructional language for teaching FP to CS undergraduates, because it is arguably the simplest of FP languages.

OCaml, though, kept innovating and, today, it is used extensively in language implementation, financial technology, and other mathematically inclined systems programming areas. OCaml came about at a time when OO was the rage of IT, on the backs of C++ and Java. OCaml injected OO facilities into the FP core. Indeed, OCaml could be deemed the progenitor of modern OO-FP languages.

Around the same time, SML was standardised, and the standard shuns all things OO, opting to remain steadfastly in the FP world. One of the philosophical objections against OO was that it abstracts and hides the very thing that makes computation intractable: objects freely mutating each other's states. But by the late 1990s, the IT industry was fully entrenched in OO, and there was no appetite for purely functional approaches. Haskell, though, remained purely functional, which may, in part, account for its lack of popularity compared to Swift, Kotlin, and other OO-FP hybrids.

But I strongly believe that a simple FP language unburdened by OO facilities, compiler pragmas, asynchrony, parallelism, mutations, laziness, and those other industrial-strength paraphernalia is an ideal platform upon which to learn the fundamentals of the FP paradigm. Here, I propose a new FP teaching language, $\lambda$aconic, which has a Haskell-like syntax and an SML-like semantics. Suffice it to say, our new language is not intended to be used in industrial, enterprise applications.

$\lambda$aconic employs a strong, static, inferencing type system ([Hindley-Milner](https://en.wikipedia.org/wiki/Hindley%E2%80%93Milner_type_system)), just like SML. And its evaluation semantics, like SML, is eager, which means our functions are strict. And since we have no OO-style inheritance, we adopt Haskell-style typeclasses (hereafter, referred to as "classes"). Specifically, we forego SML's powerful [functors](https://people.mpi-sws.org/~dreyer/courses/modules/dreyer-thesis-chapter2.pdf) and the attendant complexity of the module DSL. Semantically speaking at least, our new language is nothing new at all; it is about as fashionable as the 1970s-chic paisley bell-bottoms. Syntactically, $\lambda$aconic supports Haskell-style offside rule syntax originated in the 1960s by [ISWIM](https://en.wikipedia.org/wiki/ISWIM), with some minor tweaks designed to make the svelte syntax even more streamlined. But our new language does supports the Agda-style mixfix operators. So, $\lambda$aconic is but a more succinct, more ergonomic syntax for a stripped-down SML.

I present this new syntax below, intermixed with semantic discussions where appropriate. Do note that Unicode symbols can be used in the code for identifier names: $\pi$, $\sigma$, $\le$, $\ge$, $\sqrt{}$, $\infty$, $\bot$, $\lnot$, $\land$, $\lor$, $\emptyset$, $\otimes$, $\oplus$, etc. These symbols are entered using standard [$\LaTeX$](https://en.wikipedia.org/wiki/LaTeX) commands, as is done in Agda. IDEs can provide keyboard shortcuts, of course. Since programming, especially in an FP language, is a mathematical activity, the ability to use Unicode identifiers makes implementing mathematical constructs pleasant, rather like typesetting a mathematical text.

The target audience of this article is the designers of FP teaching languages that employ simply-typed $𝜆$-calculus, extended with polymorphic types and typeclasses, along with a few creature comforts such as Agda-like mixfix operators. The guiding principles of language design used here are comfort, clarity, and concision in the mathematical tradition. And we strive for minimalism, syntactically and semantically, guided by the user interface [design principle of least surprise](https://en.wikipedia.org/wiki/Principle_of_least_astonishment). A succinct way to summarise $\lambda$aconic might well be "boring"—as in predictable, unsurprising, familiar. This document was written with a design to promote discussion, but it is not a design document for a new FP language. In other words, the recommendations given here are fragmentary ideas, not firm dicta.

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

We use a slightly altered version of SML's function definition syntax.

```
qsort : Ord 𝛼 ⇒ [𝛼] → [𝛼]
  | [] → []
  | x,xx → qsort [l | l ← xx, l < x] + [x] + qsort [g | g ← xx, g ≥ x]
```

Here, `Ord 𝛼 ⇒` constrains the type parameter `𝛼` to be an instance of the `Ord` class, so that the `qsort` function may use `<` and `≥` comparison operators on the list elements `x`, `l`, and `g` of type `𝛼`. We get this type constraint syntax from Haskell. SML does not have classes, neither in OO sense nor in FP sense; it has functors.

# MODULES

asdf

# IMPLEMENTATION

asdf

# CONCLUSION

asdf
