---
title: "Setup"
---

## Installing Anaconda / Miniconda

Miniconda is a minimal version of the Anaconda software which includes enough components to create and manage different environments.

For these sessions, we will create an environment containing all of the required components, and this can be done using either the full version of anaconda, or using Miniconda.

Miniconda installers can be found [here](https://docs.conda.io/en/latest/miniconda.html)

Notes for installing the full version of Anaconda can be found below.

## Creating an environment

From a terminal / Anaconda prompt window, an environment containing all of the components which are required for these sessions can be created with the command:

~~~
conda create -c conda-forge -n python_training python=3.9 jupyterlab numpy matplotlib pandas gdal cartopy iris
~~~

Once the environment has been created, it can be activated with:

~~~
conda activate python_training
~~~

## Getting the Data

We will be working with various data files throughout the session.

To obtain the data, download and unzip the file
[python-data.zip]({{page.root}}/files/python-data.zip).
In order to follow the presented material, you should launch the JupyterLab
server in the root directory (see [Starting JupyterLab]({{ page.root }}/01-run-quit/#starting-jupyterlab)).

## Installing Python Using Anaconda

{% include python_install.html %}

<br>

[anaconda]: https://www.anaconda.com/
[anaconda-mac]: https://www.anaconda.com/download/#macos
[anaconda-linux]: https://www.anaconda.com/download/#linux
[anaconda-windows]: https://www.anaconda.com/download/#windows
[gapminder]: https://en.wikipedia.org/wiki/Gapminder_Foundation
[jupyter]: http://jupyter.org/
[python]: https://python.org
[video-mac]: https://www.youtube.com/watch?v=TcSAln46u9U
[video-windows]: https://www.youtube.com/watch?v=xxQ0mzZ8UvA
