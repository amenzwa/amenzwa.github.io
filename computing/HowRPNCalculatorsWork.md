---
title: "How RPN Calculators Work"
tags:
  - mathjax
use_math: true
---

# INTRODUCTION

In the annals of computing, calculators reigned supreme in a brief 30-year period, between early 1970s and early 2000s. Here, by "calculator", I mean a commonly available electronic pocket calculator with a microprocessor. I am excluding from this definition mechanical calculators, valve (vacuum tube) calculators, transistor calculators, and desk calculators. In fact, it is evident from the title of this article that I am focusing narrowly on [Hewlett-Packard](https://en.wikipedia.org/wiki/Hewlett-Packard) (HP) programmable calculators with reverse Polish notation (RPN) input method and LCD display. To an engineer like me, anything less is insupportable.

The [microprocessor](https://en.wikipedia.org/wiki/Microprocessor) is the little engine that powers the modern world. Children in 2021 play games on powerful CPUs, like the 64-bit [AMD Ryzen](https://www.amd.com/en/processors/ryzen). Only 50 years earlier in 1971, the first microprocessor, the 4-bit [Intel 4004](https://en.wikipedia.org/wiki/Intel_4004), came out. At the time, the 4004, which integrated 2,300 transistors on a single chip, was a massive leap forward in technology.

The 4004 came about because [Busicom](https://en.wikipedia.org/wiki/Busicom), a Japanese electronic calculator company, asked Intel in 1969 to develop a microprocessor for use in calculators. Naturally, Busicom calculators, like the [141-PF](http://www.vintagecalculators.com/html/busicom_141-pf.html), were the first production electronic devices to be powered by a microprocessor. Although the 141-PF holds the distinction of being the first microprocessor-based calculator, its design was unremarkable; it was an ordinary, large, four-function desk calculator with a few business-friendly features, like memory and percentage.

Then only a year later in 1972, HP introduced their game-changing model, the [HP-35](https://www.hpmuseum.org/hp35.htm), the world's first pocket scientific calculator. And bucking the trend, it uses the RPN input method. At 395 USD introductory price (almost 2,700 USD in 2021), the HP-35 was a rich man's toy; most engineers just kept using their [slide rules](HowSlideRulesWork.md), at least for a few more years, until electronic calculators became more affordable. By 1982, the engineers' favourite advanced scientific calculator, the [HP-15C](https://www.hpmuseum.org/hp15.htm), costs only 135 USD (about 400 USD in 2021). And the ultimate HP scientific calculator, the [HP Prime](https://en.wikipedia.org/wiki/HP_Prime), which was introduced in 2015, can be had for a mere 100 USD in 2021. That is [Moore's law](https://en.wikipedia.org/wiki/Moore's_law)—in the flesh.

# RPN

The [reverse Polish notation](https://en.wikipedia.org/wiki/Reverse_Polish_notation) is the opposite of the LISP [s-expression](https://en.wikipedia.org/wiki/S-expression) syntax. Both are reviled by most, but revered by the cognoscenti. In mathematics, a binary function $f$ is notated as $f(a, b)$, and a binary operator $\bigotimes$ is notated as $a \bigotimes b$. In RPN, the notations are `a b f` and `a b ⨂`. And in LISP, they are `f a b` and `⨂ a b`. The mathematical notations evolved organically. The LISP prefix notation was invented by the Polish logician [Jan Łukasiewicz](https://en.wikipedia.org/wiki/Jan_%C5%81ukasiewicz) in 1924. The RPN is the postfix version thereof, and hence the "reverse" in the name.

Because mathematical notation is meant to be read by humans, the fussy, and sometimes whimsical, syntax makes it a chore for a computer to parse. In the 1950s when the early computers had very little processing power and memory storage, parsing mathematical expressions was a very difficult task. As such, [John McCarthy](https://en.wikipedia.org/wiki/John_McCarthy_(computer_scientist)) opted for the much simpler s-expression syntax for LISP. Almost 20 years later, the HP-35 sported a 1-bit CPU—yes a serial processor—and a 4-register stack. So, RPN was the ideal input method for the HP-35.

The HP-35 is a [stack architecture](https://en.wikipedia.org/wiki/Stack_machine) computer, albeit a wee one. A stack machine uses a stack register file as opposed to general purpose register file. A register is a fast, on-chip, temporary storage used by the CPU while performing operations. A collection of registers is called a register file. You can read a detailed explanation of how the CPU uses registers in my article *[How Computers Work](HowComputersWork.md)*. A general purpose register is a register that can be used by the CPU to store anything temporarily, whereas a special purpose register is a register that can only be used for a particular purpose. All CPUs need special purpose registers. For example, the programme counter (PC) is a special purpose register; its only use is to hold the address of the next instruction to be fetched from RAM. Older CPUs have only two general purpose registers, and many instructions access the RAM, directly. But modern CPUs, like the ARM RISC processor, have a sizeable number of general purpose registers. Instructions always load the registers with values from RAM first, then compute with those registers. For this register-centric behaviour, modern CPUs are commonly refereed to as register machines.

The HP-35 has 4 stack registers: `x`, `y`, `z`, and `t`. To compute $2 + 3$, for instance, you press the following key sequence:

```Python
2↵
3↵
+
```

Here, the symbol `↵` represents the `ENTER` key. Pressing the `2` key shows the value $2$ in the display. Pressing the `ENTER` pushes the value into register `x`. Pressing `3↵` moves $2$ into register `y`, and pushes $3$ into register `x`. Then, pressing the `+` key causes the CPU to use the values in registers `x` and `y` to compute `[x] + [y] = 3 + 2 = 5`, and in the process clearing the register `y` then storing the result $5$ in the register `x`.

