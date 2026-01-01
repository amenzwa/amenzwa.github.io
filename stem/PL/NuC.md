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

### PRODUCT TYPES

```
Udp : { head : UdpHead, body : Byt }
UdpHead : udpHead { src dst : Port, ## source and destination ports
                    len chk : ℕ } ## length and checksum
```



### SUM TYPES

```
Complex :
  | rectangular {x, y : ℝ}
  | polar {r, 𝜑 : ℝ}
ℂ : Complex
```

## *expressions*

- infix arithmetic and logic operators
- condition → consequent | alternative (condition : Bol)

## *functions*

```
len : [𝛼] → Int
  | [] → 0
  | x,xx → 1 + len xx
```

