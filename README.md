# Basic programming

Below you will find programming exercises of increasing complexity. Each exercise has a corresponding Python file in the `src/` directory that you modify. All ten files already exist as templates — you never have to create a new file, just fill in the one that belongs to the exercise. (You can also write your own from scratch if you run into problems with the templates, but then the automatic checks below will not find your solution.)

Do not worry if you do not get through all of the exercises. We have tried to cover a wide range of difficulties, so there is a challenge for those who have never programmed before and those who already have some experience. Make it as far as you can, and don't sweat it if it isn't everything.

Give each exercise a go, though, because sometimes you can get stuck on a medium-hard problem and still handle a harder one, simply because the difficulty is highly subjective.


## Getting started

You need three things: Python 3.10 or newer, `git`, and an editor. The instructions below use [Visual Studio Code](https://code.visualstudio.com), but nothing in the exercises depends on it — if you already have an editor you like, skip to step 5 and work in a terminal.

Python must be 3.10 or newer because some of the templates use `match`-statements, which do not exist in older versions. Check with

```sh
> python3 --version
```

### 1. Install VS Code and the Python extension

Install VS Code, open it, go to the Extensions view in the sidebar (the four-squares icon, or `Cmd+Shift+X` / `Ctrl+Shift+X`) and install **Python** by Microsoft. That one extension brings along Pylance for autocompletion and the test integration used in step 7.

### 2. Clone the repository

Cloning means downloading the repository along with its history, so that `git` can keep track of your changes. Either do it from a terminal:

```sh
> git clone https://github.com/CTiB-exercizes/basic-python.git
> cd basic-python
```

or from inside VS Code, without touching a terminal: press `Cmd+Shift+P` / `Ctrl+Shift+P` to open the Command Palette, type `Git: Clone`, paste the repository URL, and pick a folder to put it in. VS Code will offer to open the clone when it is done — say yes.

### 3. Open the folder in VS Code

**File → Open Folder…** and pick the `basic-python` folder — the one that contains `src/`, not `src/` itself and not the folder above it. This matters more than it sounds: the tests look for `src/` relative to the folder you have open, so they only find your work if the repository root is the open folder.

You should now see `src`, `test.py`, `requirements.txt` and a few dot-folders in the Explorer sidebar.

### 4. Choose a Python interpreter

Open the Command Palette again and run `Python: Select Interpreter`. Pick a Python 3.10+ installation. If you prefer to keep the course packages separate from the rest of your system — a good habit, and on some systems the only thing that works — create a virtual environment first:

```sh
> python3 -m venv .venv
```

then re-run `Python: Select Interpreter` and choose the one inside `.venv`. VS Code remembers the choice per folder and will use it for the terminal and the tests from then on.

### 5. Install what the tests need

In the VS Code terminal (**Terminal → New Terminal**, which opens in the repository root and with your chosen interpreter active):

```sh
> python3 -m pip install -r requirements.txt
```

That installs `pytest`. If a later exercise needs another package, add it to `requirements.txt`, one per line, and run the command again.

### 6. Run one exercise

Open `src/hello.py` and press the ▷ *Run Python File* button in the top-right corner, or run it from the terminal:

```sh
> python3 src/hello.py
```

One warning about the ▷ button: several of these programs read input with `input()`, and a couple of them take command-line arguments. For those, use the terminal — type the command yourself so you can supply the input and the arguments. The table below gives the exact command for each exercise.

### 7. Run the tests

`test.py` checks your solutions for you. From the repository root:

```sh
> python3 -m pytest test.py -v
```

Or use VS Code's Testing view (the flask icon in the sidebar): run `Python: Configure Tests` once from the Command Palette, choose `pytest` and then the repository root as the test directory, and you get a list of the individual checks that you can run one at a time with a click.

Before you have solved anything, most of these tests fail. That is not a problem — it is a to-do list. A test that passes tells you that you are done with that exercise, for now at least.

### 8. Commit as you go

You don't have to use `git` to do the exercises, but this is a good, low-stakes place to get used to it. In VS Code's Source Control view (`Ctrl+Shift+G`) you see every file you have changed, you can click one to see exactly what you changed, then stage it with `+`, write a short message and commit. From a terminal the same thing is

```sh
> git add src/hello.py
> git commit -m "Solve the Hello, World! exercise"
```

Commit whenever a test goes green. Then you always have a working version to go back to, and `git diff` will tell you what you have changed since.


## What is in this repository

| Path | What it is |
| --- | --- |
| `src/` | The ten files you edit. One per exercise. |
| `test.py` | The test suite you run while working. |
| `.test/expected/` | Files with the exact expected output for some exercises. |
| `requirements.txt` | Packages the tests need. Add your own here if you need more. |
| `.github/` | Leftover automation from when this exercise was handed out through GitHub Classroom. See the note below. |

The `.github/` folder still contains the old GitHub Classroom autograder, which ran on every push back when the course used Classroom. **It is not how your work is checked any more — `test.py` is.** It is worth knowing about for one reason only: `.github/classroom/autograding.json` lists the exact expected output of every exercise, so it is a useful thing to peek at when a test failure leaves you guessing. Be aware that it and `test.py` disagree about how `src/lists.py` receives its numbers; where they differ, `test.py` is the one that counts.


## Output has to match exactly

The tests compare your output to the expected output **character by character**. That is stricter than it sounds, so three things are worth knowing before you start debugging something that looks correct:

* An extra `print()` — a "Goodbye!", a blank line at the end — makes an otherwise correct program fail.
* Trailing spaces at the end of a line count. Several exercises below say "no space at the end of the line" for exactly this reason.
* The text you pass to `input()` is part of your output, because it is printed to the terminal. Use the prompt strings given in the exercises verbatim.


## The exercises at a glance

| Exercise | File | Run it like this |
| --- | --- | --- |
| [Hello, World!](#hello-world) | `src/hello.py` | `python3 src/hello.py` |
| [Hello n times](#hello-n-times) | `src/hello-n.py` | `python3 src/hello-n.py` then type a number |
| [Do you want to stop?](#do-you-want-to-stop) | `src/do-you-want-to-stop.py` | `python3 src/do-you-want-to-stop.py` |
| [Print 1 to 10](#print-1-to-10) | `src/print-1-10.py` | `python3 src/print-1-10.py` |
| [A growing list of numbers](#a-growing-list-of-numbers) | `src/print-1-10-growing.py` | `python3 src/print-1-10-growing.py` |
| [A pattern of stars](#a-pattern-of-stars) | `src/pattern.py` | `python3 src/pattern.py` |
| [Lists: mean, times three, even](#lists) | `src/lists.py` | `python3 src/lists.py mean 1 2 3 4 5` |
| [Counting characters](#counting) | `src/counts.py` | `echo foobar \| python3 src/counts.py` |
| [Password validation](#password-validation) | `src/password.py` | `python3 src/password.py Foob@r1` |
| [Hex encoding and decoding](#hex-encoding) | `src/hex.py` | `python3 src/hex.py encode foobar` |

Anyway, let's get started with the exercises...


## Hello, World!

**File:** `src/hello.py`

It is tradition, when you start programming or when you start learning a new programming language, that the first program you write is one that prints the string `"Hello, World!"` to the terminal.

We will not break this tradition, and anger the programming gods, so change the code in `src/hello.py` so it prints that exact string.

```sh
> python3 src/hello.py
Hello, World!
```


## Hello n times

**File:** `src/hello-n.py`

Assume you have a number `n`. In `src/hello-n.py` you get it from the user running the program, with the line that is already there:

```python
n = int(input("How many times should I loop? "))
```

Now write a loop that prints `"Hello, World!"` `n` times. You choose if you prefer a `for`- or a `while`-loop.

```sh
> python3 src/hello-n.py
How many times should I loop? 3
Hello, World!
Hello, World!
Hello, World!
```

Make sure `n = 0` prints nothing at all — that case is checked, and some ways of writing the loop get it wrong. Leave the prompt string exactly as it is; it is part of the output that is compared.


## Do you want to stop?

**File:** `src/do-you-want-to-stop.py`

Let us do a `while`-loop that continues to ask us `"Do you want to stop?"` until you tell it that you want to stop. You can use the function `input()` to get user input. It lets the user write an answer on the terminal prompt, and once he or she hits enter, Python gets the string. So you can ask the user if you should stop using

```python
input('Do you want to stop? ')
```

Write a `while`-loop that asks the user if you should stop in each iteration, and make it stop if the user answers `'yes'` (lower case). Remember that you can tell Python to stop iterating with the keyword `break`.

```sh
> python3 src/do-you-want-to-stop.py
Do you want to stop? no
Do you want to stop? maybe
Do you want to stop? yes
```

The question is the only thing your program should print. Don't add a farewell message when the loop ends.


## Print 1 to 10

**File:** `src/print-1-10.py`

Write a loop that runs through the numbers 1 to 10 (not 0 to 9!), and prints the number, one per line.

```sh
> python3 src/print-1-10.py
1
2
3
4
5
6
7
8
9
10
```


## A growing list of numbers

**File:** `src/print-1-10-growing.py`

Now write a new version where we add a little more to each line; we will add the numbers from 1 up to and including the number we printed before. In iteration one the program should print `1`, in iteration two it should print `1 2`, in iteration three it should print `1 2 3`, and so forth. The final output should look like this:

```
1
1 2
1 2 3
1 2 3 4
1 2 3 4 5
1 2 3 4 5 6
1 2 3 4 5 6 7
1 2 3 4 5 6 7 8
1 2 3 4 5 6 7 8 9
1 2 3 4 5 6 7 8 9 10
```

The numbers are separated by a single space, and there is no space after the last number on a line.


## A pattern of stars

**File:** `src/pattern.py`

Write a program to construct the following pattern:

```
*
* *
* * *
* * * *
* * * * *
* * * *
* * *
* *
*
```

There is a single space between the `'*'`s and no space at the end of a line.


## Lists

**File:** `src/lists.py`

Consider a list such as this:

```python
x = [1, 2, 3, 4, 5, 6]
```

The three exercises below all manipulate such a list. While working on them it is easiest to define a list directly in Python, as above. In `src/lists.py` I have written template code that builds the list for you instead, from the numbers you give the program on the command line, and that picks which of the three exercises to run from the first argument:

```sh
> python3 src/lists.py mean 1 2 3 4 5      # the first exercise
> python3 src/lists.py times 1 2 3         # the second exercise
> python3 src/lists.py even 1 2 3 4 5 6    # the third exercise
```

The template also contains a helper, `print_list()`, for printing a list the way the exercises want it — `print(x)` would give you the square brackets and commas, which is not what we are after. We haven't covered functions yet, it is a few weeks away, but all you have to do to print a list `y` is to write `print_list(y)`.

Leave the last two cases of the `match`-statement alone. They make the program exit with an error when you give it a command it doesn't know, or no command at all, and that behaviour is checked too.

> **Two things in the template are misleading.** The comment above the first line says it reads standard input, but the code reads command-line arguments (`sys.argv[2:]`), which is what the commands above and the tests in `test.py` use — the comment is left over from an earlier version. The retired Classroom autograder still expects the standard-input version (`echo "1 2 3 4 5" | python3 src/lists.py mean`). Follow the code and the commands above; if you want the program to cope with both, read `sys.argv[2:]` when it has something in it and fall back to standard input when it doesn't.

### Exercise: the mean

Write a loop over `x` that computes the sum of the numbers in `x`. Then write code to compute the mean of the numbers in `x`. Put it above the line that reads

```python
    print(mean)
```

```sh
> python3 src/lists.py mean 1 2 3 4 5
3.0
```

### Exercise: times three

Write a loop over the list `x` that creates another list, `times_three`, that contains the elements in `x` but multiplied by 3. Put it above the line that reads

```python
    print_list(times_three)
```

```sh
> python3 src/lists.py times 1 2 3
3 6 9
```

### Exercise: the even numbers

Write a loop that creates a list, `even`, that contains all even numbers in `x` (and only the even numbers). You can check if a number is even by taking the integer division remainder with two and checking if it is zero: `n % 2 == 0`. Put it above the line that reads

```python
    print_list(even)
```

```sh
> python3 src/lists.py even 1 2 3 4 5 6
2 4 6
```


## Counting

**File:** `src/counts.py`

We use dictionaries for tables, and you can make an empty dictionary like this:

```python
table = {}
```

Write code that counts how often a character occurs in a string. You can iterate through a string, character by character, using

```python
for c in string:
	# process the character c
```

You can then use a table to count the characters. You can increment a count using

```python
table[c] += 1
```

but you will get an error if the character isn't in the table yet. You can check whether that is the case with

```python
if c not in table:
	# handle this case
```

If you insert `c` here, you avoid the problem. Go count the characters in a string.

`src/counts.py` already reads one line from standard input into the string `x`, and already prints the counts in sorted order at the end — it just needs your counting code in the middle, filling in the dictionary called `count`.

```sh
> echo foobar | python3 src/counts.py
a: 1
b: 1
f: 1
o: 2
r: 1
```

You can also run it without piping anything in, and then type the string yourself and hit enter.


## Password validation

**File:** `src/password.py`

Write a program to check the validity of a password input by users. A valid password has:

* At least 1 letter between `[a-z]` and 1 letter between `[A-Z]`. You can use the methods `a.islower()` and `a.isupper()` to check if the letter `a` is one of these.
* At least 1 number between `[0-9]`. You can use the method `a.isnumeric()` for this.
* At least 1 character from `[$#@]` (`a in "$#@"` will test if `a` is one of these).
* Minimum length 6 characters.
* Maximum length 16 characters.

The program in `src/password.py` is set up and ready to go: it takes the password as a command-line argument and prints the variable `is_valid` at the end. You need to implement the checks that set `is_valid`.

```sh
> python3 src/password.py Foob@r1
True
> python3 src/password.py foobar
False
```

Printing the boolean gives you exactly the `True`/`False` that is expected, so you don't need to print a message of your own.


## Hex encoding

**File:** `src/hex.py`

This exercise is a little more involved. We want to create a textual representation for strings of bytes—it is something that was once necessary to send binary files over email (and might still be, but I have lost track of the various internet protocols). A byte is an 8-bit number, but we will use characters in Python strings (they are a little more complex, but for the exercise it doesn't matter). If you have a character in Python, you can get the corresponding number using the function `ord()`. For example

```python
print(ord('a'))
```

will print 97. Python uses so-called *unicode* to represent strings, and the number you get is the integer that the unicode standard assigns to that character. Anyway, it doesn't matter. What matters is that we have a mapping from characters to numbers, and we can get the number for a character using `ord()`.

You can go the other way using the function `chr()`, so

```python
print(chr(ord('a')))
```

gives you `a` back. So to translate a string of bytes into something human readable, we can go through it, get the underlying numbers out (using `ord()`) and that gives us a string that we can send with an old email program. If you want to get the original string back, you run through it and translate back with `chr()`.

Well, not that fast! If you see the string `123` do you have three, two, or one number? `1`, `2`, and `3`? or `12` and `3`? or `1` and `23`? or `123`? For the trick to work, we need some way to delimit the characters. What people did (and might still do) is to translate the numbers into hexadecimal, which is base-16 numbers. You can encode more numbers in less space that way, and you can recognise when a number starts because it will always start with `0x`. You can get the hexadecimal string from a number using the function `hex()`.

### Exercise

Take a string such as

```python
x = "abcdabc"
```

and run through each character, get its number, and put the hex encoding into a list. Once you have the list, `y`, you can create the corresponding string using

```python
z = ''.join(y)
```

In `src/hex.py`, implement the encoding above the line that says

```python
    print(encoding)
```

The program takes two arguments, the command `encode` and the string to encode:

```sh
> python3 src/hex.py encode foobar
0x660x6f0x6f0x620x610x72
```


## Hex decoding

**File:** `src/hex.py`

There is no particular reason to prefer hexadecimal (except that two hex-numbers is enough to encode all bytes). You could use any textual encoding, you could use any delimiter, or you could require that all the numbers had the same number of digits. They avoided the latter because numbers that start with zero are interpreted as octal in the programming language C, which was used for most programs at the time. Anyway, this is how you would encode a string of bytes into a textual representation that wouldn't confuse old email programs.

However, encoding is not the full story. If I send you an encoded file, you probably want to decode it again. You need the real string of bytes, and that is not what I am sending you. So, you need to go through the string and translate the numbers back—first you need to get an `int` for each hexadecimal number, and then you need to translate that number into the original character (the last step, we already know that we can do with the `chr()` function).

You can split the string of hexadecimal numbers, `x`, using

```python
x.split('0x')
```

It gets rid of the `0x` strings and gives you a list of the strings between them. Throw away the first element, it is an empty string and doesn't represent a number. You can run through this list and translate the strings into integers. You need to interpret the strings as hexadecimal (and not for example decimal), so call the function `int` with an extra argument, `base = 16`. If `n` is a string in hexadecimal, then

```python
int(n, base = 16)
```

gives you the underlying number, that you can then give to `chr()`.

### Exercise

Write code that takes a string of hexadecimal strings and decodes it into the original string. Add it to `src/hex.py` above the line that says

```python
    print(decoding)
```

```sh
> python3 src/hex.py decode 0x660x6f0x6f0x620x610x72
foobar
```

Now you have both an encoding and a decoding, and you can check if it works by going full circle. In the `bash` shell, this

```sh
> python3 src/hex.py decode $(python3 src/hex.py encode foobar)
foobar
```

should print `foobar`. The command `$(python3 src/hex.py encode foobar)` encodes `foobar` and gives it as a string argument to the second command, that decodes it again.

There are other (and smarter) encodings. Now that we have mostly moved to unicode for text representations, there are many options for simple text, and for binary files there have always been many. They are optimised for different things and for different applications, so you run into them every day, without knowing them. One day, perhaps, you will need to write your own encoders and decoders—it is quite likely if you ever need to develop your own file format—and now you have seen a very simple solution.
