---
title: "Plotting"
teaching: 20
exercises: 10
questions:
- "How can I plot my data?"
objectives:
- "Use `matplotlib` to create various plots"
keypoints:
- "[`matplotlib`](https://matplotlib.org/) is the most widely used scientific plotting library in Python."
- "Many styles of plot are available: see the [Python Graph Gallery](https://python-graph-gallery.com/matplotlib/) for more options."
- "Can plot many sets of data together."
---
## [`matplotlib`](https://matplotlib.org/) is the most widely used scientific plotting library in Python.

*   Commonly use a sub-library called [`matplotlib.pyplot`](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.html#module-matplotlib.pyplot).
*   The Jupyter Notebook will render plots inline by default.

~~~
import matplotlib.pyplot as plt
~~~
{: .language-python}

*   Simple plots are then (fairly) simple to create.

~~~
time = [0, 1, 2, 3]
position = [0, 100, 200, 300]

plt.plot(time, position)
plt.xlabel('Time (hr)')
plt.ylabel('Position (km)')
~~~
{: .language-python}

![Simple Position-Time Plot](../fig/9_simple_position_time_plot.svg)

> ## Display All Open Figures
> 
> In our Jupyter Notebook example, running the cell should generate the figure directly below the code. 
> The figure is also included in the Notebook document for future viewing.
> However, other Python environments like an interactive Python session started from a terminal 
> or a Python script executed via the command line require an additional command to display the figure.
>
> Instruct `matplotlib` to show a figure:
> ~~~
> plt.show()
> ~~~
> {: .language-python}
>
> This command can also be used within a Notebook - for instance, to display multiple figures
> if several are created by a single cell.
>
{: .callout}

## Plotting data from NumPy arrays

Lets generate some data using NumPy:

~~~
x = np.arange(0, 10, 0.1)
sin_x = np.sin(x)
cos_x = np.cos(x)
~~~
{: .language-python}

The `np.arange` function will generate an array of number starting at `0` and stopping _before_ `10`, with an interval of `0.1`.

We can plot the value of `sin(x)` and `cos(x)` on the same axes:

~~~
plt.plot(x, sin_x)
plt.plot(x, cos_x)
~~~
{: .language-python}

![Sin and Cos Plot 1](../fig/9_sin_cos_1.svg)

We can set the [colour](https://matplotlib.org/stable/_images/sphx_glr_named_colors_003.png) of the lines using the `c` option to `plot()`, and we can add a legend to indicate which values belong to which series:

~~~
plt.plot(x, sin_x, c='teal', label='sin(x)')
plt.plot(x, cos_x, c='peru', label='cos(x)')
plt.legend(loc='lower left')
~~~
{: .language-python}

![Sin and Cos Plot 2](../fig/9_sin_cos_2.svg)

> ## Adding a Legend
> 
> Often when plotting multiple datasets on the same figure it is desirable to have 
> a legend describing the data.
>
> This can be done in `matplotlib` in two stages:
> 
> * Provide a label for each dataset in the figure:
>
> ~~~
> plt.plot(x, sin_x, label='sin(x)')
> plt.plot(x, cos_x, label='cos(x)')
> ~~~
> {: .language-python}
>
> * Instruct `matplotlib` to create the legend.
>
> ~~~
> plt.legend()
> ~~~
> {: .language-python}
>
> By default matplotlib will attempt to place the legend in a suitable position. If you
> would rather specify a position this can be done with the `loc=` argument, e.g to place
> the legend in the upper left corner of the plot, specify `loc='upper left'`
>
{: .callout}

Matplotlib is capable of making many type of plots. We can create a scatter plot of the `sin(x)` values:

~~~
plt.scatter(x, sin_x, c=x, s=x*3)
plt.xlabel('x', fontsize=16)
plt.ylabel('sin(x)', fontsize=16)
plt.title('sine plot', fontsize=18)
plt.tick_params(labelsize=14)
plt.colorbar()
plt.savefig('plot2.svg')
~~~
{: .language-python}

![Sin and Cos Plot 2](../fig/9_sin_scatter.svg)

Each plotting function in Matplotlib has its own set of argmuents. The documentation for the `scatter()` function can be found [here](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.scatter.html).

The `c=x` option sets the colour value of the scatter points based on the value of `x`. The `s=x*3` options sets the size of the scatter points based on the values of `x` multiplied by 3.

A title is added to the plot using `plt.title()`. The font size is set using the `fontsize` argument for the title, x axis label and y axis label. To set the font size for the tick labels, the `plt._tick_params()` function is used, where the size is set using the `labelsize` option. 

A colour scale is added using the function `plt.colorbar()`.

> ## Saving your plot to a file
> 
> If you are satisfied with the plot you see you may want to save it to a file,
> perhaps to include it in a publication. There is a function in the
> matplotlib.pyplot module that accomplishes this:
> [savefig](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.savefig.html).
> Calling this function, e.g. with
> ~~~
> plt.savefig('my_figure.png')
> ~~~
> {: .language-python}
> 
> will save the current figure to the file `my_figure.png`. The file format
> will automatically be deduced from the file name extension (other formats
> are pdf, ps, eps and svg).
>
> Note that functions in `plt` refer to a global figure variable
> and after a figure has been displayed to the screen (e.g. with `plt.show`) 
> matplotlib will make this  variable refer to a new empty figure.
> Therefore, make sure you call `plt.savefig` before the plot is displayed to
> the screen, otherwise you may find a file with an empty plot.
{: .callout}

> ## Making your plots accessible
>
> Whenever you are generating plots to go into a paper or a presentation, there are a few things you can do to make sure that everyone can understand your plots.
> * Always make sure your text is large enough to read. Use the `fontsize` parameter in `xlabel`, `ylabel`, `title`, and `legend`, and [`tick_params` with `labelsize`](https://matplotlib.org/2.1.1/api/_as_gen/matplotlib.pyplot.tick_params.html) to increase the text size of the numbers on your axes.
> * Similarly, you should make your graph elements easy to see. Use `s` to increase the size of your scatterplot markers and `linewidth` to increase the sizes of your plot lines.
> * Using color (and nothing else) to distinguish between different plot elements will make your plots unreadable to anyone who is colorblind, or who happens to have a black-and-white office printer. For lines, the `linestyle` parameter lets you use different types of lines. For scatterplots, `marker` lets you change the shape of your points. If you're unsure about your colors, you can use [Coblis](https://www.color-blindness.com/coblis-color-blindness-simulator/) or [Color Oracle](https://colororacle.org/) to simulate what your plots would look like to those with colorblindness.
{: .callout}
