---
title: "Wrap-Up"
teaching: 20
exercises: 0
questions:
- "What have we learned?"
- "What else is out there and where do I find it?"
objectives:
- "Name and locate scientific Python community sites for software, workshops, and help."
keypoints:
- "Python supports a large and diverse community across academia and industry."
---

Leslie Lamport once said, "Writing is nature's way of showing you how sloppy your thinking is."
The same is true of programming:
many things that seem obvious when we're thinking about them
turn out to be anything but when we have to explain them precisely.

## Different ways to interact with Python

We have been interacting in notebooks, using Jupyter Lab. There are various other ways to interact with Python.

### Notebooks

Notebooks can be accessed via the Jupyter Lab interface, or the 'classic' notebook interface can be launched with:

~~~
jupyter notebook
~~~

From the Jupyter Lab notebook interface, a notebook can be saved to a `.py` text file by selecting *File* > *Save and Export Notebook As* > *Executable Script*.

From the classic notebook interface, select *File* > *Download as* > *Python (.py)*.

### Command Line

From a terminal / Anaconda prompt window, the Python interpeter can be accessed by running `python`. Commands can be entered at the prompt and results can be printed to the terminal output.

From a terminal / Anaconda prompt window, `.py` files can run with:

~~~
python name_of_file.py
~~~

### Spyder

[Spyder](https://www.spyder-ide.org/) is a popular graphical development environment for working with Python, and has similar features to R Studio and Matlab.

When installing the full version of Anaconda, Spyder is included in the installation, and a shortcut to launch the software in the Windows Start Menu. The program can also be launched from a terminal / Anaconda prompt, by running:

~~~
spyder
~~~

To install spyder using the `conda` command:

~~~
conda install -c conda-forge spyder
~~~

## Python supports a large and diverse community across academia and industry.

*   The [Python 3 documentation](https://docs.python.org/3/) covers the core language
    and the standard library.

*   [PyCon](https://pycon.org/) is the largest annual conference for the Python community.

*   [SciPy](https://scipy.org) is a rich collection of scientific utilities.
    It is also the name of [a series of annual conferences](https://conference.scipy.org/).

*   [Jupyter](https://jupyter.org) is the home of Project Jupyter.

*   [Pandas](https://pandas.pydata.org) is the home of the Pandas data library.

*   Stack Overflow's [general Python section](https://stackoverflow.com/questions/tagged/python?tab=Votes)
    can be helpful,
    as well as the sections on [NumPy](https://stackoverflow.com/questions/tagged/numpy?tab=Votes),
    [SciPy](https://stackoverflow.com/questions/tagged/scipy?tab=Votes), and
    [Pandas](https://stackoverflow.com/questions/tagged/pandas?tab=Votes).
