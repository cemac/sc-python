---
title: "Setup"
---

## Installing Anaconda / Miniforge

The default Anaconda installation includes all of the packages required for the main part of the session.

The additional components required for the optionsl [Working with Geospatial Data]({{ page.root }}/18-geospatial-data/) section can be added from a terminal / Anaconda prompt window:

~~~
conda install -y -c conda-forge iris cartopy
~~~

Miniforge is a minimal version of the `conda` software which includes enough components to create and manage different environments, and only uses the `conda-forge` channel by default, which is more permissively licensed than the Anaconda `default` channel.

It is possible to create a dedicated environment containing all of the required components for the session, and this can be done using either the full version of Anaconda, or using Miniforge.

Miniforge installers can be found [here](https://conda-forge.org/miniforge/)

Notes for installing the full version of Anaconda can be found below.

## Creating an environment

From a terminal / Anaconda prompt window, an environment containing all of the components which are required for all of the excercises can be created with the command:

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
