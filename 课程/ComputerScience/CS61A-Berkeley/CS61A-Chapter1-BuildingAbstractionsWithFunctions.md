#python #SICP #CS61A
# Getting started
All computing begin with representing information, specifying the logic to process it, and designing abstractions that manage the complexity of that logic.

## Programming in Python

The python itself is the product of a large volunteer community that prides itself with the diversity of its contributors.

Python is combination of flexibility and accessibility.

## Installing python 3
[[如何在ubuntu20-04上使用anaconda？]]
[[如何在anaconda中建立虚拟环境？]]

## Interactive Sessions
**Interactive controls.** Each session keeps a history of what you have typed. To access that history, press `<Control>-P` (previous) and `<Control>-N `(next).`<Control>-D` exits a session, which discards this history. Up and down arrows also cycle through history on some systems.

## First Example
```Python
from urllib.request import urlopen
shakespeare = urlopen('http://composingprograms.com/shakespeare.txt')
words = set(shakespeare.read().decode().split())
{w for w in words if len(w) == 6 and w[::-1] in words}

```
**Statements & Expressions**. Python code consists of expressions and statements. Broadly, computer programs consist of instructions to either

1.  Compute some value
2.  Carry out some action

Statements typically describe actions. When the Python interpreter executes a statement, it carries out the corresponding action. On the other hand, expressions typically describe computations. When Python evaluates an expression, it computes the value of that expression.

**Functions**. Functions encapsulate logic that manipulates data.
The chain of commands to read, decode, and split, each operate on an intermediate computational entity: we read the data from the opened URL, then decode the data into text, and finally split the text into words. All of those words are placed in a set.

**Objects**. A set is a type of object, one that supports set operations like computing intersections and membership. An object seamlessly bundles together data and the logic that manipulates that data, in a way that manages the complexity of both.

**Interpreters**. Evaluating compound expressions requires a precise procedure that interprets code in a predictable way. A program that implements such a procedure, evaluating compound expressions, is called an interpreter.

## Errors
Learning to interpret errors and diagnose the cause of unexpected errors is called _debugging_. Some guiding principles of debugging are:

1. **Test incrementally**: Every well-written program is composed of small, modular components that can be tested individually. Try out everything you write as soon as possible to identify problems early and gain confidence in your components.
2. **Isolate errors**: An error in the output of a statement can typically be attributed to a particular modular component. When trying to diagnose a problem, trace the error to the smallest fragment of code you can before trying to correct it.
3. **Check your assumptions**: Interpreters do carry out your instructions to the letter — no more and no less. Their output is unexpected when the behavior of some code does not match what the programmer believes (or assumes) that behavior to be. Know your assumptions, then focus your debugging effort on verifying that your assumptions actually hold.
4. **Consult others**

Incremental testing, modular design, precise assumptions, and teamwork are themes that persist throughout this text.

# Elements of Programming
When we describe a language, we should pay particular attention to the means that the language provides for combining simple ideas to form more complex ideas. Every powerful language has three such mechanisms:

- **primitive expressions and statements**, which represent the simplest building blocks that the language provides,
- **means of combination**, by which compound elements are built from simpler ones, and
- **means of abstraction**, by which compound elements can be named and manipulated as units.

In programming, we deal with two kinds of elements: functions and data.  Informally, data is stuff that we want to manipulate, and functions describe the rules for manipulating the data. Thus, any powerful programming language should be able to describe primitive data and primitive functions, as well as have some methods for combining and abstracting both functions and data.

## Expressions
[[CS61A-Lab00-GettingStarted#Python Basics]]
Expressions representing numbers may **be combined with mathematical operators** to form a compound expression, which the interpreter will evaluate:

```python
>>> -1 - -1
0
>>> 1/2 + 1/4 + 1/8 + 1/16 + 1/32 + 1/64 + 1/128
0.9921875

```

These mathematical expressions use _infix_ notation, where the _operator_ (e.g., +, -, \*, or /) appears in between the _operands_ (numbers).

## Call Expressions

The most important kind of compound expression is a _call expression_, which applies a function to some arguments.
The way in which Python expresses function application is the same as in conventional mathematics.
[[数学分析-LEC01-集合和函数#数学分析的研究对象_函数]]

This call expression has subexpressions: the _operator_ is an expression that precedes parentheses, which enclose a comma-delimited list of _operand_ expressions.

![](attachments/call_expression.png)

The operator specifies a _function_. When this call expression is evaluated, we say that the function max is _called_ with _arguments_ 7.5 and 9.5, and _returns_ a _value_ of 9.5.

