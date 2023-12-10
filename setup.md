---
title: "Setup"
---

## Installing Anaconda / Miniconda

The default Anaconda installation includes most of the packages required for the session.

The additional components can be added from a terminal / Anaconda prompt window:

~~~
conda install -y -c conda-forge iris cartopy
~~~

Miniconda is a minimal version of the Anaconda software which includes enough components to create and manage different environments.

It is possible to create a dedicated environment containing all of the required components for the session, and this can be done using either the full version of Anaconda, or using Miniconda.

Miniconda installers can be found [here](https://docs.conda.io/en/latest/miniconda.html)

Notes for installing the full version of Anaconda can be found below.

## Creating an environment

From a terminal / Anaconda prompt window, an environment containing all of the components which are required for these sessions can be created with the command:

~~~
conda create -c conda-forge -n python_training jupyterlab numpy matplotlib pandas iris cartopy
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
