---
title: "How Computers Work"
tags:
  - mathjax
use_math: true
---

# INTRODUCTION

In recent years, computing technologies have advanced at a ferocious pace and IT systems have become immensely sophisticated. Software systems have always been built in layers. But of late, the industry has been obliged to build new layers of complex technologies atop outmoded, ill-fitting technologies. This is due in part to the economics and practices of modern software development and in part to the deeply enmeshed nature of the older, hastily developed, poorly understood technologies. Progressive layering removes programmers farther and farther from the hardware, so much so that many experienced programmers today no longer understand something as fundamental as the boot-up sequence or the instruction execution cycle. Surely, a software developer can have a profitable career working on social media and line of business applications without ever having peered inside a computer case. But software development is more than captivating user interfaces and undocumented REST requests. To be effective, a programmer must, at the very least, possess an accurate mental model of how a computer executes programmes.

This article is about 8-bit CPUs, like [Intel 8080](https://en.wikipedia.org/wiki/Intel_8080), [Motorola 6800](https://en.wikipedia.org/wiki/Motorola_6800), [MOS 6502](https://en.wikipedia.org/wiki/MOS_Technology_6502), and [Zilog Z80](https://en.wikipedia.org/wiki/Zilog_Z80). These processors were used in the popular home computers of the 1980s, because they were capable, simple, and cheap. My goal here is modest; I aim to explain the most basic aspects of computing: how an 8-bit computer is built from disparate subsystems, how these subsystems collectively perform simple calculations, and how complex system behaviour emerges from combinations of just two symbols, a `0` and a `1`. But who really cares about such lowly matters? Every IT practitioner should, I say. Recognising that things happen when they do is a sign of intelligence, a commonplace phenomenon within [Animalia](https://en.wikipedia.org/wiki/Animal). But desiring to understand why things are as they are— that is a mark of intellect, a quality unique to [Homo sapiens](https://en.wikipedia.org/wiki/Human).

# COMPUTING

We humans possess a unique ability to plan for the future. But to exercise this ability, we are obliged to assume the burden continually to observe, calculate, and predict. To ease that burden, we have amassed a collection of ingenious tools and techniques. Thousands of years ago, we used stones to build computers that can measure the passage of seasons. Today, we use silicon, stones in a different guise, to make supercomputers that can predict the paths of storms.

The term "computer" can be applied broadly to any mechanical means that can be used in calculating. So, [beans](https://en.wikipedia.org/wiki/Bean_machine) and [bones](https://en.wikipedia.org/wiki/Ishango_bone) are as much "computing devices" as are [slide rules](https://en.wikipedia.org/wiki/Slide_rule) and [supercomputers](https://en.wikipedia.org/wiki/Supercomputer). And until the 1940s, a "computer" was the [person who performs numerical computations](https://en.wikipedia.org/wiki/Computer_(job_description)) using the slide rule. But in this article, "computer" means the modern digital computer. With all its sophistication, the modern digital computer is still a mechanical aid for calculating. Yet, simple calculations like additions and subtractions, when mixed with human ingenuity, achieves marvellous, maybe even miraculous, feats like air traffic control and artificial intelligence (AI).

## *from symbols to intelligence*

***bits, bytes, and booleans***—The name "digital computer" derives from the fact that this device can manipulate only binary digits ([bits](https://en.wikipedia.org/wiki/Bit)). A bit can be either `0` or `1`. The simplest modern computer is the 1980s home computer. Such a computer is called the 8-bit machine, because it manipulates an 8-bit quantity (a byte) at a time. The CPU can examine the individual bits within a byte. Boolean (true or false) values are represented using bits within a byte. But a particular bit can be access only through its containing byte. This is the consequence of byte-at-a-time processing scheme of the 8-bit computer.

The byte is also known as the word on an 8-bit machine. But on a 16-bit, 32-bit, or 64-bit computer, a word is respectively those quantities. That is, a word matches the CPU's native data size. For simplicity, we focus exclusively on 8-bit CPUs in this article.

***numbers and letters***—A decimal digit can represent 0, 1, 2, ..., 9, but a binary digit can represent only 0 up to 1. The decimal number system requires multiple digits to represent a number greater than 9. Likewise, the binary number system requires multiple digits to represent a number greater than 1. Hence, decimal 0 is represented as binary `0`, 1 as `1`, 2 as `10`, 3 as `11`, 4 as `100`, and so on. The minimum value a byte can represent is `00000000` (decimal 0), and the maximum value is `11111111` (decimal 255). Thus, a byte can represent $2^8 = 256$ different values. Numbers greater than 255 must be represented by placing two bytes, side by side. An 8-bit CPU manipulates 16-bit quantities one byte at a time. Since the 1940s, the dawn of the electronic computer, numbers have been represented and manipulated using various formats. But all modern computers use [2's complement](https://en.wikipedia.org/wiki/Two%27s_complement) to represent signed integers and [IEEE 754](https://en.wikipedia.org/wiki/IEEE_754) floating-point format to approximate real numbers.

Computers use ASCII and Unicode standard formats to represent characters. [ASCII](https://en.wikipedia.org/wiki/ASCII) was adopted as the standard binary format in the 1960s, with the advent of the modern digital computer. The numbers, letters, and myriad symbols that appear on the American standard keyboard are mapped to the ASCII symbol table. ASCII uses one byte to represent one character, so it can represent up to 256 different symbols. For instance, the word `"hi"` in ASCII binary representation requires two bytes: `01101000` for `h` and `01101001` for `i`. But tens of thousands of symbols are needed to represent all the languages in the world. The 1980s personal computer revolution prompted various efforts to represent complex characters in multiple bytes, which culminated in the [Unicode](https://en.wikipedia.org/wiki/Unicode) standard of the 1990s. The old ASCII standard 8-bit character format has been subsumed into Unicode as [UTF-8](https://en.wikipedia.org/wiki/UTF-8).

Note that the CPU recognises only the following types: byte value, unsigned integer value, signed integer value, floating-point value, and memory address. As stated above, a character value is represented as an unsigned integer, and a string value is represented as a sequence of character values. All other data types are treated as byte sequences.

***addition, subtraction, multiplication, and division***—With standard formats like 2's complement, IEEE 754, and Unicode, the computer can represent numbers and letters. But representation is one thing, computation is quite another. The most basic computation that a digital computer performs is the addition. The CPU adds numbers using a circuit called the adder. Two binary integers are added much like two decimal integers. In the decimal number system, 9 + 1 = 10, because adding 1 to the maximal value that a decimal digit can represent, namely 9, overflows the digit, and hence must be represented by two digits. Similarly, in the binary number system, 1 + 1 = 10​ (decimal 2), because adding 1 to the maximal value that a binary digit can represent, namely 1, overflows the digit, and hence must be represented by two digits. Hence, an 8-bit unsigned quantity can represent a total of 256 values.

But what about negative numbers? In 2's complement format, the left-most bit of a binary quantity represents the negative sign. Hence, `00000001` is +1, and `10000001` is -1. Because this format uses the left-most bit for sign representation, the largest positive integer an 8-bit quantity can represent is `01111111` (decimal 127) and the smallest negative number is `11111111` (decimal -128). Hence, an 8-bit singed integer can represent 128 negative values, the `00000000` which is considered a positive value, and 127 other positive values, giving a total of 256 different values. In other words, an 8-bit quantity, singed or unsigned, can represent 256 different integer values. An unsigned byte can represent decimals in the closed interval $[0, 255]$, and signed byte can represent decimals in the closed interval $[-128, +127]$. Using the 2's complement representation of negative integers, the integer adder unit can compute subtraction: 8 + (-5) = 3​.

Traditionally, integer arithmetic (`add`, `sub`, `mul`, `div`) is performed by the [arithmetic logic unit](https://en.wikipedia.org/wiki/Arithmetic_logic_unit#INTOP) (ALU) inside the CPU. The ALU also performs boolean logic (`not`, `and`, `or`)—hence, the "logic" in its name. Old 8-bit CPUs performed floating-point arithmetic in software, because additional, specialised, floating-point hardware would have made the machines uneconomical for the home market. A more powerful 16-bit CPU of that era, Intel 8086 for example, also lacks floating-point hardware, but the CPU can be augmented with an optional add-on [floating-point unit](https://en.wikipedia.org/wiki/Floating-point_unit) (FPU) that performs floating-point arithmetic (`fadd`, `fsub`, `fmul`, `fdiv`). The FPU was then known as the [floating-point coprocessor](https://en.wikipedia.org/wiki/Intel_8087). Modern CPUs, starting with the [Intel 80486](https://en.wikipedia.org/wiki/Intel_80486) processor, have integrated FPU hardware on chip.

***decision and repetition***—A sequence of bits (`0`s and `1`s) can represent letters and numbers. And the adder unit can add and subtract numbers. Programmes must make decisions based on conditions:

```assembly
     ...
     cond a < b ⇒ jump CON ⇏ jump ALT
     ...
CON: ; consequent code block
     ...
ALT: ; alternative code block
     ...
```

For clarity and concision, the above code is written in pseudo assembly language. The conditional branch is computed by comparing two integers `a` and `b`. The CPU compares these two integers by first computing the subtraction `a - b`, then checking if the result is negative, zero, or positive. A negative means `a < b`; a zero means `a = b`; positive means `a > b`. By taking one execution path or another on the basis of this result, the CPU accomplishes conditional branching.

Repetitive execution of a block of code, also known as looping, is accomplished by jumping back to the top of the block, based on a branching condition located at the bottom of the block:

```assembly
      ...
LOOP: i ← 0
      ...
      cond i < n ⇒ jump LOOP ⇏ jump DONE
DONE: ; loop completed
      ...
```

Above, integer `i` is the loop index which is initialised to 0 at the top of the loop, and `n` is the maximum number of iterations. When `i = n`, the loop termination condition is met, so the CPU jumps out of the loop, instead of jumping back to the top of the loop.

***algorithm and intelligence***—A CPU equipped with boolean logic operations, character and string operations, integer and floating-point operations, and branching and looping constructs is capable of simple, but general, computations. For example, the integer averaging algorithm sums up a sequence $s_i$ of integers, and divides the sum with the sequence length $n$:

<div>
$$
avg = \frac{\sum_{i=1}^{n} s_i}{n}
$$
</div>
The integer averaging algorithm above uses looping, addition, and division. More complex computations, like $sin(a)$ where $a$ is an angle in radians, can be computed using Taylor series with sufficiently large number of iterations $n$:
<div>
$$
sin(a) = \sum_{i=0}^{n} \frac{(-1)^i}{(2i+1)!} a^{2i+1}
$$
</div>
The above sine algorithm uses looping, addition, subtraction, multiplication, and division. Exponentiation $a^i = a \cdot a \cdot ... \cdot a$ and factorial $i! = i \cdot (i - 1) \cdot (i - 2) \cdot ... \cdot 2 \cdot 1$ also use these same, simple computations.

Algorithms like these are implemented as functions that take inputs and return results. When performing a conditional branch, the CPU can jump immediately to the designated code blocks, depending on the condition. But when calling a function, the CPU must assemble the input values for the function to use and arrange for the function to return its results to the caller, before jumping into the function's code block. This function call mechanism is described in detail, later.

More sophisticated functions, like [sorting](https://en.wikipedia.org/wiki/Sorting_algorithm), [searching](https://en.wikipedia.org/wiki/Search_algorithm), and [graph](https://en.wikipedia.org/wiki/Graph_theory) algorithms, are implemented by composing simpler functions. Complicated AI algorithms like [chess](https://en.wikipedia.org/wiki/Computer_chess) and [Go](https://en.wikipedia.org/wiki/Computer_Go) soon follow. Thus arose semblance of intelligence from streams of two symbols, a `0` and a `1`.

By its very name, "artificial intelligence" is not intelligence, but an imitation thereof. Thinking, feeling machines have not been invented, because humans do not yet understand the nature of human intellect at a fundamental level. There are two broad categories of AI algorithms: rule-based AI and connectionist AI. Rule-based AI is used when the problem is well understood and the solution can be expressed as a small set of clearly defined rules. Board game algorithms are prime examples of rule-based AI. Connectionist AI, more popularly known as neural networks (NNs), is used when the problem is poorly understood, has a large set of potential solutions which makes it impracticable to be described in terms of rules, and a vast amount of input data can be collected beforehand. Autonomous vehicle navigation, crowd behaviour modelling, and similar open-ended problems are solved using NNs.

# HARDWARE

- microarchitecture
- system bus, memory, and I/O
- standard hardware model

# SOFTWARE

- instruction set architecture, compilers, and languages
- representations, types, and transformations
- standard software model

# CONCLUSION

I explained in this article how an 8-bit computer is built, how it boots up, how its CPU performs calculations, how these calculations when combined exhibit behaviours as complex as playing chess, and how software algorithms are designed and implemented. My main goal here was to give software developers a better understanding of how the computer hardware executes programmes, with the hope that this low-level knowledge may make them more mechanically sympathetic programmers. This hardware execution model also sheds light on the inner workings of [virtualisation technologies](https://en.wikipedia.org/wiki/Hardware_virtualization), [hardware emulators](https://en.wikipedia.org/wiki/Hardware_emulation), and [virtual machines](https://en.wikipedia.org/wiki/Virtual_machine).

As much as possible, I avoided delving into the low-level details like clock signals, clock skew, pipelining, vector processing, multi-cores, on-chip instruction and data caches, on-chip high-speed and low-speed buses, serial and parallel I/O protocols, signal degradation during transmission, heat dissipation, power regulation, circuit layout, and the like. Those interested in modern processors and microcontrollers should read textbooks like *[Computer Architecture: A Quantitative Approach](https://www.amazon.com/Computer-Architecture-Quantitative-Approach-Kaufmann/dp/0128119055/ref=sr_1_2?dchild=1&keywords=computer+architecture&qid=1614712937&sr=8-2)* and *[The Designer's Guide to the Cortex-M Processor Family: A Tutorial Approach](https://www.amazon.com/Designers-Guide-Cortex-M-Processor-Family/dp/0081006292/ref=sr_1_8?dchild=1&keywords=cortex-m&qid=1614714051&sr=8-8)*.