---
title: "Writing Functions"
teaching: 15
exercises: 15
questions:
- "How can I create my own functions?"
objectives:
- "Explain and identify the difference between function definition and function call."
- "Write a function that takes a small, fixed number of arguments and produces a single result."
keypoints:
- "Break programs down into functions to make them easier to understand."
- "Define a function using `def` with a name, parameters, and a block of code."
- "Defining a function does not run it."
- "Arguments in a function call are matched to its defined parameters."
- "Functions may return a result to their caller using `return`."
---
## Break programs down into functions to make them easier to understand.

*   Human beings can only keep a few items in working memory at a time.
*   Understand larger/more complicated ideas by understanding and combining pieces.
    *   Components in a machine.
    *   Lemmas when proving theorems.
*   Functions serve the same purpose in programs.
    *   *Encapsulate* complexity so that we can treat it as a single "thing".
*   Also enables *re-use*.
    *   Write one time, use many times.

## Define a function using `def` with a name, parameters, and a block of code.

*   Begin the definition of a new function with `def`.
*   Followed by the name of the function.
    *   Must obey the same rules as variable names.
*   Then *parameters* in parentheses.
    *   Empty parentheses if the function doesn't take any inputs.
    *   We will discuss this in detail in a moment.
*   Then a colon.
*   Then an indented block of code.

~~~
def print_greeting():
    print('Hello!')
~~~
{: .language-python}

## Defining a function does not run it.

*   Defining a function does not run it.
    *   Like assigning a value to a variable.
*   Must call the function to execute the code it contains.

~~~
print_greeting()
~~~
{: .language-python}
~~~
Hello!
~~~
{: .output}

## Arguments in a function call are matched to its defined parameters.

*   Functions are most useful when they can operate on different data.
*   Specify *parameters* when defining a function.
    *   These become variables when the function is executed.
    *   Are assigned the arguments in the call (i.e., the values passed to the function).
    *   If you don't name the arguments when using them in the call, the arguments will be matched to
parameters in the order the parameters are defined in the function.

~~~
def print_date(year, month, day):
    joined = str(year) + '/' + str(month) + '/' + str(day)
    print(joined)

print_date(1871, 3, 19)
~~~
{: .language-python}
~~~
1871/3/19
~~~
{: .output}

Or, we can name the arguments when we call the function, which allows us to
specify them in any order and adds clarity to the call site; otherwise as
one is reading the code they might forget if the second argument is the month
or the day for example.
~~~
print_date(month=3, day=19, year=1871)
~~~
{: .language-python}
~~~
1871/3/19
~~~
{: .output}

*   Via [Twitter](https://twitter.com/minisciencegirl/status/693486088963272705):
    `()` contains the ingredients for the function
    while the body contains the recipe.

## Functions may return a result to their caller using `return`.

*   Use `return ...` to give a value back to the caller.
*   May occur anywhere in the function.
*   But functions are easier to understand if `return` occurs:
    *   At the start to handle special cases.
    *   At the very end, with a final result.

~~~
def average(values):
    if len(values) == 0:
        return None
    return sum(values) / len(values)
~~~
{: .language-python}

~~~
a = average([1, 3, 4])
print('average of values:', a)
~~~
{: .language-python}
~~~
average of values: 2.6666666666666665
~~~
{: .output}

~~~
print('average of empty list:', average([]))
~~~
{: .language-python}
~~~
average of empty list: None
~~~
{: .output}

*   Remember: [every function returns something]({{ page.root }}/04-built-in/).
*   A function that doesn't explicitly `return` a value automatically returns `None`.

~~~
result = print_date(1871, 3, 19)
print('result of call is:', result)
~~~
{: .language-python}
~~~
1871/3/19
result of call is: None
~~~
{: .output}

## Adding helpful information

Helpful information can be added to a function using a _docstring_.

After the `def` line of a function, textual information explaining what the function does can be added using a multi line comment.

Multi line comments start and end with three quotation marks, `"""`:

~~~
def average(values):
    """
    Return the average of a set of values
    """
    if len(values) == 0:
        return None
    return sum(values) / len(values)

help(average)
~~~
{: .language-python}

~~~
Help on function average in module __main__:

average(values)
    Return the average of a set of values
~~~
{: .output}

> ## Identifying Syntax Errors
>
> 1. Read the code below and try to identify what the errors are
>    *without* running it.
> 2. Run the code and read the error message.
>    Is it a `SyntaxError` or an `IndentationError`?
> 3. Fix the error.
> 4. Repeat steps 2 and 3 until you have fixed all the errors.
>
> ~~~
> def another_function
>   print("Syntax errors are annoying.")
>    print("But at least python tells us about them!")
>   print("So they are usually not too hard to fix.")
> ~~~
> {: .language-python}
>
> > ## Solution
> >
> > ~~~
> > def another_function():
> >   print("Syntax errors are annoying.")
> >   print("But at least Python tells us about them!")
> >   print("So they are usually not too hard to fix.")
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

> ## Definition and Use
>
> What does the following program print?
>
> ~~~
> def report(pressure):
>     print('pressure is', pressure)
>
> print('calling', report, 22.5)
> ~~~
> {: .language-python}
> > ## Solution
> >
> > ~~~
> > calling <function report at 0x7fd128ff1bf8> 22.5
> > ~~~ 
> > {: .output}
> >
> > A function call always needs parenthesis, otherwise you get memory address of the function object. So, if we wanted to call the function named report, and give it the value 22.5 to report on, we could have our function call as follows
> > ~~~
> > print("calling")
> > report(22.5)
> > ~~~
> > {: .language-python}
> > ~~~
> > calling
> > pressure is 22.5
> > ~~~
> > {: .output}
> {: .solution}
{: .challenge}

> ## Order of Operations
>
> 1. What's wrong in this example?
>
>     ~~~
>     result = print_time(11, 37, 59)
>
>     def print_time(hour, minute, second):
>        time_string = str(hour) + ':' + str(minute) + ':' + str(second)
>        print(time_string)
>     ~~~
>     {: .language-python}
> 
> 2. After fixing the problem above, explain why running this example code:
>
>     ~~~
>     result = print_time(11, 37, 59)
>     print('result of call is:', result)
>     ~~~
>     {: .language-python}
>
>     gives this output:
>
>     ~~~
>     11:37:59
>     result of call is: None
>     ~~~
>     {: .output}
>
> 3. Why is the result of the call `None`?
>
> > ## Solution
> > 
> > 1. The problem with the example is that the function `print_time()` is defined *after* the call to the function is made. Python
> > doesn't know how to resolve the name `print_time` since it hasn't been defined yet and will raise a `NameError` e.g.,
> > `NameError: name 'print_time' is not defined`
> >
> > 2. The first line of output `11:37:59` is printed by the first line of code, `result = print_time(11, 37, 59)` that binds the value 
> > returned by invoking `print_time` to the variable `result`. The second line is from the second print call to print the contents 
> > of the `result` variable.
> >
> > 3. `print_time()` does not explicitly `return` a value, so it automatically returns `None`.
> >
> {: .solution}
{: .challenge}

> ## Encapsulation
>
> Fill in the blanks to create a function that takes a single filename as an argument,
> loads the data in the file named by the argument,
> and returns the minimum value in that data.
>
> ~~~
> import pandas as pd
>
> def min_in_data(____):
>     data = ____
>     return ____
> ~~~
> {: .language-python}
> > ## Solution
> >
> > ~~~
> > import pandas as pd
> > 
> > def min_in_data(filename):
> >     data = pd.read_csv(filename)
> >     return data.min()
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

> ## Find the First
>
> Fill in the blanks to create a function that takes a list of numbers as an argument
> and returns the first negative value in the list.
> What does your function do if the list is empty? What if the list has no negative numbers?
>
> ~~~
> def first_negative(values):
>     for v in ____:
>         if ____:
>             return ____
> ~~~
> {: .language-python}
> > ## Solution
> >
> > ~~~
> > def first_negative(values):
> >     for v in values:
> >         if v < 0:
> >             return v
> > ~~~
> > {: .language-python}
> > If an empty list or a list with all positive values is passed to this function, it returns `None`:
> > ~~~
> > my_list = []
> > print(first_negative(my_list))
> > ~~~
> > {: .language-python}
> > ~~~
> > None
> > ~~~
> > {: .output}
> {: .solution}
{: .challenge}

> ## Calling by Name
>
> Earlier we saw this function:
>
> ~~~
> def print_date(year, month, day):
>     joined = str(year) + '/' + str(month) + '/' + str(day)
>     print(joined)
> ~~~
> {: .language-python}
> We saw that we can call the function using *named arguments*, like this:
> ~~~
> print_date(day=1, month=2, year=2003)
> ~~~
> {: .language-python}
>
> 1.  What does `print_date(day=1, month=2, year=2003)` print?
> 2.  When have you seen a function call like this before?
> 3.  When and why is it useful to call functions this way?
>
> > ## Solution
> > 
> > 1. `2003/2/1`
> > 2. We saw examples of using *named arguments* when working with the pandas library. For example, when reading in a dataset 
> > using `data = pd.read_csv('data/temperature_2022-07.csv', index_col='Date')` the last argument `index_col` is a 
> > named argument.  
> > 3. Using named arguments can make code more readable since one can see from the function call what name the different arguments 
> > have inside the function. It can also reduce the chances of passing arguments in the wrong order, since by using named arguments 
> > the order doesn't matter.
> {: .solution}
{: .challenge}
