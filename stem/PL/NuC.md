---
title: "𝜈C"
tags:
  - mathjax
use_math: true
---

## *a proposal for a new C programming language*

[TOC]

- for the exclusive use to implement small system programmes (like UNIX commands)
- C semantics with exceptions
  - No pointers
  - No manual memory management, with automatic GC
  - No statements, only expressions
  - No loops, only recursion with tail-call optimisation
- Haskell-style ADT syntax for product and sum types
- TypeScript-style `×` syntax for composing product types
- Haskell-style syntax for modules
- Unicode identifiers

# SYNTAX

## *types*

### PRIMITIVE TYPES

```
Bol
𝔹 : Bol

U08, U16, U32, U64
I08, I16, I32, I64

Nat : U64
ℕ : Nat

Int : I64
ℤ : Int

Flt ## 64-bit
ℝ : Flt

Chracter ## Unicode character
𝕌 : Character

String ## Unicode string
𝕊 : String
```

### PRODUCT TYPES

```
## UDP packet
UdpHead : udpHead { src dst : Port, ## source and destination ports
                    len chk : ℕ } ## length and checksum
Udp : { head : UdpHead, body : U08 }
```

### SUM TYPES

```
Complex :
  | rectangular {x y : ℝ}
  | polar {r 𝜑 : ℝ}
ℂ : Complex
```

## *expressions*

```
## arithmetic expressions
a × (b + c)
(b + c) ÷ a

## conditional expression
cond ⇒ csq | alt ## cond : 𝔹, csq alt : 𝛼

## case expression
c : ℂ
case c
  | rectangular {x, y} → ...
  | polar {r, 𝜑} → ...
```

## *functions*

```
## naïve version
len : [𝛼] → Int
  | [] → 0
  | x,xx → 1 + len xx

## tail-recursive version
len : [𝛼] → Int
  | xx → let len' : Int → [𝛼] → Int
           | a [] → a
           | a x,xx → len' (a + 1) xx
         len' 0 xx

xx = [1, 2, 3, 4, 5]
len xx ## 5
```

## *operators*

```
## logical operators
p q : 𝔹
¬p ## boolean not
p ∧ q ## boolean and
p ∨ q ## boolean or
p ⊕ q ## boolean xor
p = q ## boolean equal
p ≠ q ## boolean not equal

## bit manipulation operators
a b : U08
n : ℕ
¬a ## unsigned 1's complement
a ∧ b ## unsigned and
a ∨ b ## unsigned or
a ⊕ b ## unsigned xor
b ↤ n ## unsignedleft shift
b ⟲ n ## unsignedleft rotate
b ↦ n ## unsignedright shift
b ⟳ n ## unsignedright rotate
a = b ## unsigned equal
a ≠ b ## unsigned not equal

## complex modulus operator
|_| : ℂ → ℝ
  | rectangular {x, y} → √ (x^2 + y^2)
  | polar {r, _} → |r|
c = rectangular {x=4.0, y=3.0} ## 4.0 + i3.0
|c| ## 5.0
```

