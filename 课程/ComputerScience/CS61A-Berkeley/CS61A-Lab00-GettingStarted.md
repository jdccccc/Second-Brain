#CS61A #Lab

# Set Up

1. [[如何在VirtualBox上安装Ubuntu20-04？]]

2. [[如何在ubuntu20-04上使用anaconda？]]

3. [[如何使用vscode？]]


# Using the Terminal
4. Try the following command:`python3`
	If the installation worked, you should see some text printed out about the interpreter followed by `>>>` on its own line. This is where you can type in Python code.You can type `exit()` or `Ctrl-D` to return to your command line.


# Organizing your files
5. `ls`
	The `ls` command **l**i**s**ts all the files and folders in the current directory.

6. `cd`——change into the specified directory
	- `cd ..` (two dots). The `..` means "the parent directory". In this case, the parent directory of `cs61a` is your home directory, so you can use `cd ..` to go up one directory.
	- `cd ~` (the tilde). Remember that `~` means home directory, so this command will always change to your home directory.
	- `cd` (`cd` on its own). Typing just `cd` is a shortcut for typing `cd ~`

7. `mkdir`——which **m**a**k**es new **dir**ectories

8. download lab00.zip
	` wget https://inst.eecs.berkeley.edu/~cs61a/fa21/lab/lab00/lab00.zip`

9. Extract starter files —— `unzip lab00.zip`

10. The `mv` command will **m**o**v**e the `~/Downloads/lab00` folder into the `~/cs61a/lab` folder.
	`mv ~/Downloads/lab00 ~/cs61a/lab`

11. Summary:
	- `ls`: **l**i**s**ts all files in the current directory
	- `cd <path to directory>`: **c**hange into the specified **d**irectory
	- `mkdir <directory name>`: **m**a**k**e a new **dir**ectory with the given name
	- `mv <source path> <destination path>`: **m**o**v**e the file at the given source to the given destination


# Python Basics
## Expressions and Statements
![[CS61A-Chapter1-BuildingAbstractionsWithFunctions#First Example]]

## Primitive Expressions
Primitive expressions only take one step to evaluate. These include numbers and booleans, which just evaluate to themselves.

``` python
>>> 3
3
>>> 12.5
12.5
>>> True
True
```

## Arithmetic Expressions
Numbers may be combined with mathematical operators to form compound expressions. In addition to the `+` operator (addition), the `-` operator (subtraction), the `*` operator (multiplication) and the `**` operator (exponentiation), there are three division-like operators to remember:

- Floating point division (`/`): divides the first number number by the second, evaluating to a number with a decimal point _even if the numbers divide evenly_.
- Floor division (`//`): divides the first number by the second and then rounds down, evaluating to an integer.
- Modulo (`%`): evaluates to the positive remainder left over from division.

Parentheses may be used to group subexpressions together; the entire expression is evaluated in PEMDAS (Parentheses, Exponentiation, Multiplication / Division, Addition / Subtraction) order.

``` python
>>> 7 / 4
1.75
>>> (2 + 6) / 4
2.0
>>> 7 // 4        # Floor division (rounding down)
1
>>> 7 % 4         # Modulus (remainder of 7 // 4)
3
```

## Assignment statements

An assignment statement consists of a name and an expression. It **changes the state of the program** by evaluating the expression to the right of the `=` sign and _binding_ its value to the name on the left.

``` python
>>> a = (100 + 50) // 2
```

Now, if we evaluate `a`, the interpreter will display the value 75.

``` python
>>> a
75
```

# Doing the Assignment
## Testing with OK
### Test specific questions

To test a specific question, use the `-q` option with the name of the question:

```
python3 ok -q ### Q1
```

### Test all questions

You can run all the tests with the following command:

```
python3 ok
```

### Display all tests

By default, only tests that **fail** will appear. If you want to see how you did on all tests, you can use the `-v` option:

```
python3 ok -v
```

### Test locally

If you do not want to send your progress to our server or you have any problems logging in, add the `--local` flag to block all communication:

```
python3 ok --local
```
## Unlocking tests
One component of lab assignments is to predict how the Python interpreter will behave.
`python3 ok -q python-basics -u`
## Understanding problems

Labs will also consist of function writing problems. Open up `lab00.py` in your text editor.You should see something like this:

``` python
def twenty_twenty_one():
    """Come up with the most creative expression that evaluates to 2021,
    using only numbers and the +, *, and - operators.

    >>> twenty_twenty_one()
    2021
    """
    return ______
```

The lines in the triple-quotes `"""` are called a **docstring**, which is a description of what the function is supposed to do. When writing code in 61A, you should always read the docstring!

## Writing code

Once you understand what the question is asking, you're ready to start writing code! You should replace the underscores in `return ______` with an expression that evaluates to 2021.

## Running tests

In CS 61A, we will use a program called `ok` to test our code. `ok` will be included in every assignment in this class.

In that directory, you can type `ls` to verify that there are the following three files:

- `lab00.py`: the starter file you just edited
- `ok`: our testing program
- `lab00.ok`: a configuration file for Ok

You can run `ok` with this command:
```bash
python ok --local
```

# Appendix: Useful Python command line options

When running a Python file, you can use options on the command line to inspect your code further. Here are a few that will come in handy.

- Using no command-line options will run the code in the file you provide and return you to the command line. For example, if we want to run `lab00.py` this way, we would write in the terminal:
    
    ```bash
    python3 lab00.py
    ```
    
- **`-i`**: The `-i` option runs your Python script, then opens an interactive session. In an interactive session, you run Python code line by line and get immediate feedback instead of running an entire file all at once. To exit, type `exit()` into the interpreter prompt. You can also use the keyboard shortcut `Ctrl-D` on Linux/Mac machines or `Ctrl-Z Enter` on Windows.
    
    **If you edit the Python file while running it interactively, you will need to exit and restart the interpreter in order for those changes to take effect.**
    
    Here's how we can run `lab00.py` interactively:
    
    ```bash
    python3 -i lab00.py
    ```
    
- **`-m doctest`**: Runs doctests in a particular file. Doctests are surrounded by triple quotes (`"""`) within functions.
    
    Each test in the file consists of `>>>` followed by some Python code and the expected output (though the `>>>` are not seen in the output of the doctest command).
    
    To run doctests for `lab00.py`, we can run:
    
    ```bash
     python3 -m doctest lab00.py
    ```

