---
title: "Slight"
tags:
  - mathjax
use_math: true
---

## *a Smalltalk-Light that targets JavaScript*

[TOC]

*Slight* is a proposal for a new programming language with a Smalltalk-like purely-objective semantics. Being still in the proposal stage, there is no implementation of Slight, at present.

Slight supports Unicode symbols. It seamlessly interoperates with the JavaScript ecosystem via either Node or Deno. Its syntax is modelled after Haskell. With additional effort, Slight can also generate byte-code for Wasm, CLR, JVM, Beam, and other VMs, as well as native binary for various CPUs.

# STANCE

Slight is designed primarily for rapid development of back-office operations management applications intended to be used by a small number of in-house business experts. Secondary uses of this language are infrastructure automation and scientific simulation. And given its compact size, it could also be used to implement embedded software that run on low-power MCUs.

Slight introduces no new programming concepts, and it provides no new syntactic constructs. Its distinguishing characteristic, though, is its strong stance on being a simple, svelte language with a narrow purpose, which amounts to a novelty in today's practice of designing complex, colossal languages that try to be everything to everyone. Slight's pure, OO semantics is well matched to the business applications domain.

Slight's compact nature reflects its design philosophy: there is no such thing as a "large application"—at least it ought not—only numerous well-isolated "small components" that interact with one another through a simple, shared protocol, quietly and without fanfare. This is the philosophy that underpins [Unix](https://en.wikipedia.org/wiki/Unix) commands. The applications implemented in Slight, too, adhere to this philosophy of being humble in size, being conservative in design, and being deliberate in interaction.

# SEMANTICS

Slight is semantically close to [Smalltalk](https://en.wikipedia.org/wiki/Smalltalk) and [Self](https://en.wikipedia.org/wiki/Self_(programming_language)), both purely objective, single inheritance languages in which multiple inheritance is simulated with [traits](https://en.wikipedia.org/wiki/Trait_(computer_programming)). Smalltalk's object system is class-based, whereas Self's is prototype-based. JavaScript, a descendant of Self, also employs prototypal inheritance.

Slight adopts a handful of time-tested concepts from these languages, including the prototype concept, but with a twist. Slight discards the class-object syntactic distinction, because every linguistic element—type, object, method, function, operator, constant—is an object. Hence, declaring a new type is just creating a new object and so too is defining a new method.

That data and code are both objects makes Slight [homoiconic](https://en.wikipedia.org/wiki/Homoiconicity). Furthermore, because types are also objects, this is no distinction between type-level code and value-level code. As such, like other dynamically type checked languages, Slight does not distinguish between type expressions and value expressions. This uniformity considerably increases the expressivity and the comprehensibility of type expressions.

## *objects*

As a pure OO language with imperative semantics, computations in Slight generally are the side effects of object interactions. An object interacts with another object via a *message*. The name of the message is called the *selector*. A message is sent to an object using the conventional `.` syntax. The target object of a message is called its *receiver*. A message's behaviour is implemented by the receiver object's *method*, whose name matches the message selector. In other words, the method responds to the message. A type's data contents are held in *data slots* and the code of its methods are held in *code slots*. There is no `null` in Slight.

Like Smalltalk, Slight employs *live objects*. A Slight application automatically and incrementally persists its runtime state to disc, and the application automatically restores the saved state from disc when it resumes. As such, a Slight application is inherently crash-resistant, though not crash-proof. Live objects are ideal persistence mechanism for implementing small applications—Slight's intended use. ORM can, of course, be implemented as a library, if database storage mechanism is necessary.

## *types*

Unlike Smalltalk, but like Self, there are no classes in Slight; we use the term *type*, instead. But a type is just a prototype object. So, types in Slight are just objects. The `Type` is the primordial prototype object, the ancestor of all objects and, by extension, the ancestor of all types, too.

Slight is strongly typed and dynamically checked. And every type inherits from one existing type, and this single inheritance chain terminates at the root `Type`. Multiple inheritance is simulated using [traits](https://en.wikipedia.org/wiki/Trait_(computer_programming)), which are also objects, naturally.

Slight's type system can infer the types of most expressions. So, there are only a few places in the code where explicit typing is necessary. This freedom from mandatory typing increases programmer productivity and code readability, without diminishing type safety. The type system also enables the IDE to provide the usual coding assistive technologies.

## *safety*

Slight has no constructs that threaten type safety. There are no `nil`, `null`, `undefined`, and sundry [billion-dollar *naughts*](https://en.wikipedia.org/wiki/Tony_Hoare). A possible absence of a value must be indicated with the `Opt` option type. There is no `Any` type that pierces the type shield. There is no implicit type conversion. Type conversions must either be inherited or it must be implemented with methods like `asStr`, `asInt`, etc.

## *built-ins*

Because everything in Slight is an object, there are no "primitive types", per se. But Slight supports the following built-in types:

- `Type` is the mutable, primordial type from which every type descends
- `(x : T, ...)` is a mutable tuple
- `{x : T, ...}` is a mutable object (a record)
- `[T]` is a mutable list of `T`-typed elements
- `<Str#T>` is a mutable hash with `Str`-typed keys and `T`-typed values
- `Str` is a mutable Unicode string
- `Chr` is an immutable Unicode character
- `Bol` is an immutable boolean flag
- `Int` is an immutable 64-bit integer
- `Flt` is an immutable 64-bit IEEE 754 floating-point number
- `Opt 𝛼` is the option type whose value is either `none` or `value : 𝛼`
- `Rsl 𝛼` is the result type whose value is either `error` or `value : 𝛼`

Although objects are mutable in general, it is nonsensical to mutate objects that represent constant values, such as `true`, `'ॐ'`, `9`, `1.618`, and the like. However, a variable holding such a constant value can be mutated using the `←` assignment operator.

```Slight
vowel ← 'अ'
...
vowel ← 'इ'
```

Above, the mutable, `Chr`-typed variable `vowel` is initialised to the value `'अ'` and is subsequently updated to the value `'इ'`. The objects that represent the Unicode character literals अ and इ are, of course, immutable.

# SYNTAX

The Slight syntax strives to be concise, consistent, and cogent. Syntactically, Slight is slimmer than both Smalltalk and JavaScript. It relies on the type system, the Unicode symbols, and the IDE assistive technologies to keep the syntactic constructs to a minimum, without compromising code legibility.

Note, though, that as there exists no Slight implementation at the moment, the code examples below appear unadorned with syntax colouring, alignment bars, and other visual aids that enhance legibility.

## *documentation*

Slight's IDE subtly, but persistently, chides the developers to document non-trivial definitions. The IDE also enforces the standard documentation format and it automatically inserts appropriate documentation templates for various code sections which can be filled out by programmers and technical writers. The Slight IDE is a [literate programming](https://en.wikipedia.org/wiki/Literate_programming) environment, like the iPython [Jupyter](https://jupyter.org/), and it is also a live object explorer, like the Smalltalk [Browser](https://pharo.org/).

In-code documentation is written as either inline comments or as block comments. Inline comments start with `##` and spans until the end of the line. Block comments start with `#{` and end with `#}`. Both inline and block comments consistently begin with the `#` character. Block comments can wrap other comments. So, a block comment can temporarily blank out a section of commented code.

As a matter of style, in-code comments should be used sparingly; they should only be used for short citations, brief reminders, and spot warnings. A more comprehensive documentation should be written in the literate programming text cells provided by the IDE.

## *user interface*

Slight software could be implemented as a command-line application or as an interactive [TUI](https://en.wikipedia.org/wiki/Text-based_user_interface) application. Ideally, though, it should be implemented as an IDE-based literate programme with each `.sl` source file serving as a section of *executable manual*.

During development, the programmers implement the code in the IDE's expanded code cells and technical writers inject the user's manual in the text cells. Once deployed, much of the embedded code is hidden from the end users, who see only the manual text and a few essential UI components. These UI components, too, are live objects, just like in Smalltalk. So, they always reflect the current application state.

## *names*

Slight follows the Smalltalk [camel case](https://en.wikipedia.org/wiki/Camel_case) naming convention: types use capitalised camel case names; values use uncapitalised camel case names. Slight's naming scheme is not a convention, though; it is a dictum of the compiler. This strong stance on naming improves code consistency and readability.

All-caps names are frowned upon by the Slight IDE, which would suggest naming the [UUID](https://en.wikipedia.org/wiki/Universally_unique_identifier) type  `Uuid`, not `UUID` . This is a convention whose purpose is to eliminate a potential source of inconsistency that often leads to disputes and confusion.

Moreover, long names are vehemently objected to by the IDE. This is an antithesis of the modern software development practice of using lengthy and descriptive, but illegible, names as an easy means to evade the responsibility to document the code.

Slight encourages using short names consistently and documenting the code thoroughly, in the prose style of a mathematical text. This approach produces legible code and comprehensible documentation.

## *values*

Slight is an imperative language in the OO tradition. As such, Slight variables are mutable by nature. The `←` operator assigns a value to a variable.

```Slight
x ← 0
...
x ← x + 1
```

Slight permits defining module-level variables, like `x` above. A module-level value is implicitly slotted into the object that represents the containing module. But using module-level variables is considered uncouth.

When necessary, constants can be defined using the following syntax.

```Slight
∆ 𝜋 = 3.141592654

∆ c = 299792458.0 ## speed of light (m/s)
∆ G = 6.67408e-11 ## gravitational constant (m^3/kg/s^2)
```

Note that constant names can be either capitalised or uncapitalised. Names longer than one character should use camel case, as in `MaxLen`. The compiler is able to recognise the constants and enforce their immutability, because their definitions are prefixed with `∆` annotations.

Universal constants, like `π`, `c`, and `G`, should be defined at the module level, as shown above. But local constants should be defined at the type level or the method level, so as to minimise namespace pollution.

## *types*

Recall that types in Slight are objects with capitalised names. To define a new type `T`, we use the object literal syntax, like this.

```Slight
T = { field : U, ... }
```

What appears to be a root type `T` is implicitly a direct descendant of `Type`. So, the type declaration `T = { ... }` is a shortcut for `T = Type + { ... }`, which states that `T` inherits `Type`'s properties and additionally declares its own properties. Note that types are generally defined at the module level.

In the type `T` above, one of its data slots is `field`, whose type is `U`. `T` implicitly inherits `Type`'s `asStr` code slot, the method that serialises the object's data representation to a Unicode string.

We use the `+` operator to add new properties to an existing type. We can also use the `-` operator to delete properties from an existing type. Since types have a set theoretic interpretation, we may think of `+` and `-` as set addition and subtraction operators.

```Slight
X = { x1 : T, x2 : T }
Y = X - { x2 } + { y1 : U } ## Y = { X.x1, Y.y1 }
```

Although Slight employs a Smalltalk-like single inheritance, it simulates multiple inheritance using its prototypal inheritance mechanism. Inheriting from multiple types often causes property name collisions. Slight automatically resolves name collisions by overwriting the earlier inherited property with the later inherited property of the same name. Note that the property types are elided from the example below for clarity.

```Slight
X = { a, b }
Y = { a, c }
Z = X + Y + { d } ## type Z = { Y.a, X.b, Y.c, Z.d }
```

Alternatively, the programmer can manually use the `-` operator to remove the unwanted properties of the parent types.

```Slight
X = { a, b }
Y = { a, c }
Z = X + (Y - { a }) + { d } ## type Z = { X.a, X.b, Y.c, Z.d }
```

This set addition and subtraction syntax works with ordinary objects, as well. In the example below, the type of the object `z` is inferred to be `Z = { X.a, X.b, Y.c, Z.d }`.

```Slight
x = X { a←0, b←1 }
y = Y { a←2, c←3 }
z = x + (y - { a }) + { d←4 } ## object z = { a=0, b=1, c=3, d=4 }
```

Indeed, it is possible to mix types and objects in the same expression.

```Slight
x = X { a←0, b←1 }
y = Y { a←2, c←3 }
Z = x + (y - { a }) + { d } ## type Z = { X.a, X.b, Y.c, Z.d }
```

Note the syntax uniformity amongst the type expressions and the value expressions, above. Code legibility is not compromised, due to the consistencies of the naming convention and the IDE syntax colouring.

Slight's prototype system permits the programme to alter the structures of types and objects, using the `+` and the `-` operators. This is a powerful programming technique, but wielding it indiscriminately will surely lead to chaos. We must exercise special care when modifying `Type`; altering the global namespace without aforethought is unwise.

Moreover, the Slight programmer need not mentally segregate classes from objects. Indeed, there are no classes in Slight semantics; only objects. All that the programmer needs to know is that capitalised names stand for types and uncapitalised names stand for values. This approach minimises the programmer's cognitive load.

Behind the scene, Slight implements the prototypal multiple inheritance using traits, the way Self does.

## *methods*

We may also define methods to implement the behaviour of objects. Every method returns a result, which is the value of the last expression in the method. Multiple expressions may be sequenced using the `;` operator. And following the functional style, there is no `return` and, hence, there is no way to invoke an early escape from a method.

A method definition may optionally start with its type signature. The type signature of a simple method may be omitted, because the type system can usually infer the type. But a more complicated method that accepts multiple arguments and performs non-trivial operations on the receiver object should, as a matter of form, be preceded by its type signature.

```Slight
T = { field : U, ... }
  message : U → U → U ## type signature of method
  message first second = ...; ...; ... ## method definition
```

The signature `message : U → U → U` above means that the method named `message` accepts two arguments, both typed `U`, and returns a result, also typed `U`.

The Slight runtime evaluates a method when the receiver object is sent a message whose selector matches the name of the method.

```Slight
o ← T { field←v, ... } ## create the object o of type T
...
o.message a b ## send a message to o with arguments a and b
```

Slight supports named-argument method invocation, like Python does, but using the `←` assignment operator, as in `t.message first←a second←b`. Using the named-argument construct, we may give semantically meaningful names to methods. In the example below, the object `o` is sent a message named `signal` with the value `"hello"`, and the object is instructed to retry this operation up to the specified number of times, in case of failures.

```Slight
o.send signal←"hello" retries←3
```

Note the consistent use of the `←` operator for binding values to variables in assignment, object creation, and method invocation.

A Slight programme performs its task by composing many short methods. Large monolithic methods, though syntactically valid, are eschewed stylistically. In that respect, the Slight programming style resembles that of purely functional languages, like Haskell and Agda. The Slight IDE will, from time to time, suggest that large, unwieldy methods should be refactored.

In Slight, an object's internal data slots are accessed exclusively through accessor methods, which the runtime automatically implements for each data slot. So, in the declaration of the type `T` above, there exists an implicit getter method `t.field` which returns the value of the `field` property and an implicit setter method `t.field value←v` which sets the value `v` to the `field` property and returns the value of `field`.

The getter and setter methods allow us to intercept access requests. For instance, we may restrict the values that are permitted to be assigned to `field` by explicitly implementing the setter method, as shown below. The type system can easily infer that the type of `v` must match the type of `field`, so we need not provide the type signature of this trivial method.

```Slight
T = { field : U, ... }
  field v = ## explicit definition of setter method
    assert (valid v) ## assert v's validity
    field ← v
```

To minimise namespace pollution, a method may define inner methods, which are utility functions accessible only within that enclosing method. But inner methods may access the values defined in the enclosing method, as well as the properties of the receiver object. In other words, inner methods are [closures](https://en.wikipedia.org/wiki/Closure_(computer_programming)).

```Slight
T = { field : U, ... }
  outer p q = ...
    inner x = ... ## may access p, q, and field
    ...
    inner 3 ## call inner utility function
```

Slight methods can be recursive.

```Slight
T = { field : U, ... }
  method (x::xx) =
    ...
    method xx ## call recursively with smaller argument
```

## *functions*

Slight permits the definition of module-level *functions*, like `foldr` below. Such a function is slotted into the containing module object. This is similar to the way JavaScript [simulated modules](https://nodejs.org/api/modules.html#modules-commonjs-modules) using function objects, in the early days. But the Slight syntax is succinct and clear, without any extraneous bits.

```Slight
foldr : (𝛼 → 𝛽 → 𝛽) → 𝛽 → [𝛼] → 𝛽
foldr f id (x::xx) = f x (foldr f id xx)
```

The type signature `foldr : (𝛼 → 𝛽 → 𝛽) → 𝛽 → [𝛼] → 𝛽` states the following:

- `foldr` takes these arguments:
  - A function `f` of type `𝛼 → 𝛽 → 𝛽`
  - An identity value `id` of type `𝛽`
  - A list `x::xx` of type `[𝛼]`
- `foldr` returns a value of type `𝛽`

Here, `𝛼` and `𝛽` are type variables into which actual types are substituted at the call site of `foldr`. And the syntax `x::xx` represents a list with the head element `x` and the tail elements `xx`.

In addition to module-level functions, Slight also supports LISP-like [*lambda functions*](https://en.wikipedia.org/wiki/Anonymous_function). These are analogous to *blocks* in Smalltalk and Self.

```Slight
xx ← [5, 9, 1]
foldr (𝜆 acc x = acc + x) 0 xx ## (5 + (9 + (1 + 0))) = 15
```

Slight also supports [Agda-like overloading](https://agda.readthedocs.io/en/v2.5.2/language/mixfix-operators.html) of module-scoped operators: `⊙_` for prefix operators, `_⊙` for postfix operators, and `_⊙_` for infix operators, where `⊙` is some operator and `_` is an operand. Operator associativity and precedence are defined using `fixl p ⊙` for left-associativity and `fixr p ⊙` for right-associativity. The `p` value specifies the precedence. An operator with a higher precedence binds more tightly than those with lower precedences. In an expression containing two same-precedence operators, their associativity determines the evaluation order. Operator precedence and associativity rules eliminate pesky parentheses in most situations.

We may define the string concatenation operator, like this.

```Slight
_+_ : Str → Str → Str
s + t = s.concat t
```

We may concatenate the strings `s` and `t` as `s.concat t`, as `_+_ s t`, or more idiomatically as `s + t`.

## *inheritance*

Recall that types in Slight are declared by attaching object literals to capitalised names and, because every linguistic construct is an object, the same syntax applies to both types and to objects. Consequently, Slight's prototypal type declaration syntax is more succinct and comprehensible than the class declaration syntax of classical languages like Smalltalk, C++, Python, Java, etc. The compactness of this syntax does not detract from its legibility, especially in the presence of IDE syntax colouring.

```Slight
## organization

Company =
  { name : Str
  , ceo : Manager
  , dd : <Str#Department> } ## departments hash keyed by name

Department =
  { name : Str
  , manager : Manager
  , tt : <Str#Team> } ## teams hash keyed by name

Team =
  { name : Str
  , leader : Leader
  , ee : <Email#Member> ## team's employees hash keyed by email
  , dept : Department }

## employee

⩜ Employee = ## employee abstract type
  { eid : Str
  , name : Str
  , email : Email ## Email is built-in type with syntax validation
  , title : Str
  , dept : Department }
  init = eid ← nextEid ## initializer method
  contact = "{name} ({email})" ## access method

Manager = Employee ## manager is employee

⩜ Staff = Employee + { team : Team } ## staff abstract type
  managedBy = dept.manager ## access method

Leader = Staff ## team leader

Member = Staff ## team member
  ledBy = team.leader ## access method
```

Above `Company`, `Department`, `Team`, and `Employee` implicitly inherit from `Type`. But `Leader` and `Member` explicitly inherit from `Staff`, which in turn explicitly inherits from `Employee`. The declaration `Staff = Employee ...` states that `Staff` inherits all the data and code slots of `Employee`. The declaration `Staff = Employee + { team : Team }` states that `Staff` adds its own data slot named `team`.

Given Slight's simplicity of purpose, all object properties are publicly accessible; there are no complicated access modifiers like C++'s `private`, `protected`, and `public`. So, how could we use Slight to write a large, enterprise application that requires sophisticated data hiding techniques to prevent data sharing chaos?

Well, we do not! We use Slight to build small, focused, isolated applications that interact with one another via a simple, shared communications protocol. This architecture relies not on hiding, but on sharing, of data in an orderly and responsible manner.

Having declared our type hierarchy above, we may now create an object of type `Manager`, this way.

```Slight
m ← Manager { name←"Ima Manager", ... }
```

Here, we invoke the `Manager` *constructor* with initialisation data specified by the object literal `{ ... }`. The type system ensures that this object literal matches the structure of the `Manager` type. This is sometimes referred to as *[structural typing](https://en.wikipedia.org/wiki/Structural_type_system)*. In this case, the object literal must define `name`, `email`, `title`, and `dept`. It need not supply `eid`, because the `Employee` super type initialises this property, during object creation.

In this creation sequence, the runtime creates an empty object of the specified type, and calls the type's initialiser method `init`. If the type des not define the `init` method, the runtime looks for another initialiser method along the type's inheritance chain. It is an error, if the runtime cannot initialise the newly created object, since all Slight values must be initialised to sensible, non-`null` values.

The `⩜` annotations on `Employee` and `Staff` indicate that these are *abstract types* and, as such, objects of these types cannot be created directly by invoking their constructors.

A type declaration may also include access method definitions, like the `managedBy` method of `Staff` and the `ledBy` method of `Member`.

Note the lack of extraneous keywords, like `type`, `data`, `alias`, `extends`, `override`, and so on, in the type declarations.

## *modules*

A module is an object, as expected. A module's scope is the `.sl` file that contains it, and the module gets its name from the file name, which must be in capitalised camel case. A module serves as a namespace.

By default, everything defined in a module is exported. Prepending the `-` annotation to a definition marks it as private, making it invisible to the users of the module.

```Slight
## Util.sl

∆ c = 3.0e8 ## speed of light (exported)

- ∆ 𝜀 = 0.000001 ## error minimum (private)

log x = ... ## logging utility function (exported)
```

Module-level definitions like `c`, `𝜀`, and `log` above are slotted into the enclosing module object, which in this case is `Util`. A large, complex type may conceivably need to declare a local, utility type. But to keep the syntax simple, Slight only supports the declaration module-level types. Local types should thus be made private to the module using the `-` annotation.

```Slight
G = { ... } ## general use type (exported)

- L = { ... } ## local use type (private)
```

A module's contents can be imported by another module using the `import` construct. The imported module's definitions are accessed via that module's name. The `@` construct can be used to give the module a different name, either to prevent a name collision or to give it a shorter name.

```Slight
import Util @ U

...
U.log U.c ## access via U
```

All the exported definitions in a module can be subsumed into the current module using the `open` construct.

```Slight
open Util

...
log c ## access directly
```

A module's ability selectively to hide its contents makes it the ideal container for implementing an *[abstract data type](https://en.wikipedia.org/wiki/Abstract_data_type)*. Capitalising module names is a nod to this typeful nature. Modules, like types, define their own structure and behaviour, which are aggregates of the constituent types and values contained in the module. In a way, Slight modules emulate The modules-are-types approach is analogous to [Standard ML](https://en.wikipedia.org/wiki/Standard_ML) functors, but with a vastly simpler syntax afforded by Slight's purely objective semantics.

```
## Stack.sl

Stack 𝛼 = [𝛼]
```

