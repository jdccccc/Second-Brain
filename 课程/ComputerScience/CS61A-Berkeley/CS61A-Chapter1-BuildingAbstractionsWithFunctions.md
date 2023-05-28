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
