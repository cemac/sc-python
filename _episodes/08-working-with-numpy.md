---
title: "Working with NumPy"
teaching: 10
exercises: 10
questions:
- "What is NumPy and how do I use it?"
objectives:
- "Import the NumPy library."
- "Create a NumPy array."
- "Apply functions to NumPy arrays."
keypoints:
- "NumPy provides many funtions for working with numerical data."
- "The NumPy `ndarray` can be used to store numerical data with multiple dimensions."
- "The NumPy functions enable efficient processing of values in a `ndarray`."
---
## Working with the NumPy library

*   [NumPy](https://numpy.org/) is a widely-used Python library for numerical operations.
*   NumPy uses the `ndarray` type for storing data.
*   Load it with `import numpy as np`. The alias `np` is commonly used for NumPy.

~~~
import numpy as np

primes = np.array([2, 3, 5, 7, 9])
print(primes)
~~~
{: .language-python}
~~~
[2 3 5 7 9]
~~~
{: .output}

The NumPy array looks similar to a list, but let's take a closer look:

~~~
print(type(primes))
print(len(primes))
print(primes.shape)
print(primes.dtype)
~~~
{: .language-python}
~~~
<class 'numpy.ndarray'>
5
(5,)
int64
~~~
{: .output}

* The `shape` attribute contains information about the dimensions of the array.
* All values in the array must have the same `dtype` (data type).

## Array functions

NumPy provides many functions, including its own versions of `min` and `max`:

~~~
print(np.min(primes))
print(np.max(primes))
print(np.mean(primes))
~~~
{: .language-python}
~~~
2
9
5.2
~~~
{: .output}

A NumPy array will have many methods available, including `min`, `max` and `mean`:

~~~
print(primes.min())
print(primes.max())
print(primes.mean())
~~~
{: .language-python}
~~~
2
9
5.2
~~~
{: .output}

NumPy functions can operate on all elements in an array. For example, what happens if we try to run the `math.sin` function on multiple items?

~~~
import math

sequence = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
math.sin(sequence)
~~~
{: .language-python}
~~~
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
/tmp/ipykernel_76280/1284448365.py in <module>
      2 
      3 sequence = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
----> 4 math.sin(sequence)

TypeError: must be real number, not list
~~~
{: .error}

The `math.sin` function can only process a single value.

The NumPy `sin` function can process multiple values:

~~~
sequence = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
np.sin(sequence)
~~~
{: .language-python}
~~~
array([ 0.        ,  0.84147098,  0.90929743,  0.14112001, -0.7568025 ,
       -0.95892427, -0.2794155 ,  0.6569866 ,  0.98935825,  0.41211849])
~~~
{: .output}

The `sequence` list is converted to a NumPy `ndarray` during this process.

## Multi dimensional arrays

NumPy arrays can have multiple dimensions:

~~~
values = np.array([[0, 7, 2], [4, 4, 5]])
print(values)
print(values.shape)
~~~
{: .language-python}
~~~
[[0 7 2]
 [4 4 5]]
(2, 3)
~~~
{: .output}

The `values` array is two dimensional, with 2 rows and 3 columns.

Values in NumPy arrays with multiple dimension have multiple indexes. The index of the value `5` in the array is `[1, 2]`. The row or y index comes first, followed by the column or x index:

~~~
print(values[1, 2]) 
~~~
{: .language-python}
~~~
5
~~~
{: .output}

> ## Finding the median value
>
> If we can find the mean value of the values array with:
> ~~~
> print(values.mean())
> ~~~
> {: .language-python}
> Can we find the median value in a similar way? If not, is there another
> way to find the median value?
> > ## Solution
> > ~~~
> > print(np.median(values)) 
> > ~~~
> > {: .language-python}
> > ~~~
> > 4.0
> > ~~~
> > {: .output}
> > The ndarray type does not have a median method, so values.median() does
> > not work.
> > However, the numpy library does include the median function, which can be
> > applied to an array.
> {: .solution}
{: .challenge}

> ## Applying functions along an axis
>
> What is the difference between these commands and the results they return?
> ~~~
> print(values.max())
> print(values.max(axis=0))
> print(values.max(axis=1))
> ~~~
> {: .language-python}
> > ## Solution
> > ~~~
> > 7
> > [4 7 5]
> > [7 5]
> > ~~~
> > {: .output}
> > The first command returns the maximum value from the whole array.
> > The second command returns the maximum value from each column (`axis=0`).
> > The third command returns the maximum value from each row (`axis=1`).
> {: .solution}
{: .challenge}

> ## Data types
>
> What is the data type of the `values` array, and how could the array be created with a different data type, e.g. `np.float32`?
> > ## Solution
> > ~~~
> > values = np.array([[0, 7, 2], [4, 4, 5]])
> > print(values.dtype)
> > print(values)
> > 
> > values = np.array([[0, 7, 2], [4, 4, 5]], dtype=np.float32)
> > print(values.dtype)
> > print(values)
> > ~~~
> > {: .language-python}
> > ~~~
> > int64
> > [[0 7 2]
> >  [4 4 5]]
> > float32
> > [[0. 7. 2.]
> >  [4. 4. 5.]]
> > ~~~
> > {: .output}
> > The `dtype` argument can be used to specify the data type when creating a NumPy array.
> {: .solution}
{: .challenge}

> ## NaN values
>
> If we create an array containing a NaN (not a number) value, how do we find the maximum value?
> ~~~
> results = np.array([0.3, 7.2, np.nan, 4.5, 9.7])
> ~~~
> {: .language-python}
> > ## Solution
> > ~~~
> > print(results.max())
> > print(np.nanmax(results))
> > ~~~
> > {: .language-python}
> > ~~~
> > nan
> > 9.7
> > ~~~
> > {: .output}
> > NumPy includes functions, such as `nanmax`, which will ignore any NaN values in the input.
> {: .solution}
{: .challenge}
