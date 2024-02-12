---
layout: post
title: "Language syntax reference: type declaration and annotation"
categories: ["python", "hci", "programming languages"]
---
For CS 7650 Human-Computer Interaction this semester, I'm doing a design analysis of type annotation syntax in programming languages. My motivation relates to the recent (well, not actually recent, but only now old enough that it's starting to see much use) introduction of optional type annotation and hinting in Python. Having started programming in Python 3.5, I didn't see the point of explicit type assignment in language syntax - it seemed like confusing extraneous syntax that created additional hurdles to writing correct code. I didn't see the light until taking a [Java course](https://courses.cs.washington.edu/courses/cse373/18au/); in fact, I didn't notice how much I'd come to appreciate the power of static type checking until I started to rewrite some basic data structures in [Python](https://github.com/jsstevenson/data_structures) as a practice exercise, and found myself internally stressing at all the havok duck typing could be wreaking. What had seemed like an encumbrance in Java quickly became a necessity.

Returning to HCI, my interest in Python's addition of type annotation lies in its syntactical choices. As far as I can tell, there's nothing in the Python parser that would necessarily prevent it from using C-style declarations, and presumably it could've used a colon after its argument list to denote a return type, as in TypeScript, rather than the ASCII arrow. I don't think any of these strategies are necessarily wrong or right, but it's infinitely curious to me how different languages demonstrate consistency in some areas and diverge in others. To visualize these differences, I did a quick poll of how different languages declare variable types and function signatures. (The wise among us will note the absence of Haskell. It confuses me. I am working on it.)

Language    | Variable            | Function                             | Mandatory?
---         | ---                 | ---                                  | ---
Rust        | `let foo: Bar = 0`  | `fn baz(foo: Bar) -> Bar`            | Inferred
Python      | `foo: Bar = 0`      | `def baz(foo: Bar) -> Bar`           | Optional
Scala       | `val foo: Bar = 0`  | `def baz(foo: Bar) => Bar`           | Inferred
TypeScript  | `let foo: Bar = 0`  | `baz(foo: Bar): Bar`                 | Inferred
C/C++       | `Bar foo = 0`       | `Bar baz(Bar foo)`                   | Mandatory
C-Sharp     | `Bar foo = 0`       | `Bar baz(Bar foo)`                   | Mandatory
Swift       | `var foo: Bar = 0`  | `func baz(_ foo: Bar) -> Bar`        | Inferred
Java        | `Bar foo = 0`       | `Bar baz(Bar foo)`                   | Mandatory
Kotlin      | `val foo = 0`       | `fun baz(foo: Bar): Bar`             | Inferred for variables
Objective C | `Bar foo = 0`       | `Bar baz(Bar foo)`                   | Mandatory
Go          | `var foo Bar = 0`   | `func baz(foo Bar) (return_foo Bar)` | Inferred?
Standard ML | `val foo = 0 : Bar` | `fun baz(foo : Bar)`                 | Inferred
ALGOL 68    | `Bar foo = 0`       | `proc baz = (Bar foo) Bar`           | Mandatory
Pascal      | `var foo: Bar`      | `procedure baz(var foo : Bar)`       | Mandatory
Elm         | `foo: Bar`          | (no type annotation)                 | Mandatory

`*`*I've never used a good 2/3 of these languages and may well be messing up some of the details*

What sticks out is a pretty clear division between "C-style" syntax (where the type name is positioned like a prefix, immediately prior to the function or variable name) and punctuation-based syntax, where colons or arrows are used to denote a type relationship with the identifier. Anyone with a cursory knowledge of programming language history will recognize a pattern for what languages adopt which style (and may also notice a pattern regarding the use of the ASCII arrow for function return types).

Language    | Release`*`                                            | Style
---         | ---                                                   | ---
ALGOL 68    | 1968                                                  | Prefix
Pascal      | 1970                                                  | Punctuation
C           | 1973                                                  | Prefix
Standard ML | 1983                                                  | Punctuation
Objective C | 1984                                                  | Prefix
C++         | 1985                                                  | Prefix
Java        | 1995                                                  | Prefix
C#          | 2000                                                  | Prefix
Scala       | 2004                                                  | Punctuation, Arrow
Python      | [2006](https://www.python.org/dev/peps/pep-3107/)`**` | Punctuation, Arrow
Go          | 2009                                                  | Postfix
Rust        | 2010                                                  | Punctuation, Arrow
Kotlin      | 2011                                                  | Punctuation
TypeScript  | 2012                                                  | Punctuation
Elm         | 2012                                                  | Prefix
Swift       | 2014                                                  | Punctuation, Arrow

`*`*The dates are fuzzy - who knows when in language development a decision is made about syntax - but the point is pretty clear*

*`**`Python, of course, didn't ship with annotation ability - PEP 3107 added annotion capabilities, and PEP 484 integrated their use for type hinting*

First, it's hard to miss the influence that ALGOL68 had on programming language history - Dennis Ritchie wrote at length on its significance in his development of C, and it's well-known that both Java and C# were designed in part to capture the interests of disaffected C programmers. I was, however, surprised to see that punctuation-style syntax has early roots as well, though. I think this speaks to the intuition on display with the colon operator: it's very easy for the brain to replace it with something like "is a" (e.g. "foo is a String"). I think this is a big appeal of the "arrow" operator, although it's curious to me that Scala's arrow uses different punctuation than subsequent languages (<= vs <-).

It's nitpicky, but I think these design decisions can have a significant affect on code readability and the programmer's experiment. I hope to have more insight into this at the conclusion of my project.

