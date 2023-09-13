(software)=
# Software installation


## Installing Conda

You will need the Conda package manager to setup your environment required for the course.
You can install [Anaconda](https://www.anaconda.com/) or [Miniconda](https://docs.conda.io/en/latest/miniconda.html).
The user guide and short reference on Conda can be found [here](https://docs.conda.io/projects/conda/en/latest/user-guide/cheatsheet.html).

Miniconda is already installed in the VMA computer rooms.



## Installing the course environment

To setup the course environment first create a YAML file (e.g. geo4436.yaml in your course directory) with the following content:

```{literalinclude} ../../environment/environment.yaml
:language: yaml
```

Then launch [Anaconda prompt](https://anaconda.org/conda-forge/prompt) and change the prompt directory into course directory (where you stored the yaml file) using ```cd ```, e.g.:

```python
cd C:\Users\YourName\course_GEO-4436
```

Then create the environment with:

```python
conda env create -f geo4436.yaml
```

This will install all required software for the course, and may take a while.


## Activating the course environment

When starting the computer practicals you first need to activate your environment:

```python
conda activate geo4436
```

You then can start e.g. Spyder or Python from the command prompt.
