(software)=
# Software installation


## Installing Conda

You will need the Conda package manager to setup the work environment for the course.
You can install [Anaconda](https://www.anaconda.com/) or [Miniconda](https://docs.conda.io/en/latest/miniconda.html).
The user guide and short reference on Conda can be found [here](https://docs.conda.io/projects/conda/en/latest/user-guide/cheatsheet.html).

Miniconda is already installed in the VMA computer rooms.



## Installing the course environment

To setup the course environment, first create a YAML file (e.g. geo4436.yaml in your course directory) with the following content:

```{literalinclude} ../../environment/environment.yaml
:language: yaml
```

Then launch [Anaconda Prompt](https://anaconda.org/conda-forge/prompt) and change the prompt directory into course directory (where you stored the yaml file) using ```cd ```, e.g.:

```
(base) C:\Users\YourName> cd C:\Users\YourName\course_GEO-4436
```

```{note}
Anaconda Prompt should be installed together with Anaconda. You can look for it in your search bar.
```

Then create the environment with:

```
(base) C:\Users\YourName> conda env create -f geo4436.yaml
```

This will install all required software for the course, and may take a while.

```{important}
If you are working on a Mac or Linux computer, the Anaconda prompt is not installed. However, the above commands should work as well if you run them in the [Terminal](https://en.wikipedia.org/wiki/Terminal_(macOS)), which you can find through the search bar. Note that the syntax for directories/paths is different on Mac and Linux than on Windows.
```

## Activating the course environment

When starting the computer practicals, you first need to activate your environment in [Anaconda Prompt](https://anaconda.org/conda-forge/prompt) or the [Terminal](https://en.wikipedia.org/wiki/Terminal_(macOS)):

```
(base) C:\Users\YourName> conda activate geo4436
```

You then can start e.g. Spyder or Python from the command prompt.

```
(geo4436) C:\Users\YourName> spyder
```
