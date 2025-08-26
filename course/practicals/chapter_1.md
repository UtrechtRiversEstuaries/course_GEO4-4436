# **Chapter 1 - Starting programming with Python**

```{important}
***NOTES ABOUT CHAPTER 1***

-   The exercises in this chapter will be graded on the following criteria:
	(1) Does the program run?
	(2) Can we understand it (= properly commented)?
	(3) Does it do the right thing as specified in assignment? See the end of this chapter for the full rubric.

-   There are 4 exercises that you must hand in, that increase in difficulty and time required for completion. Try to schedule your workload accordingly.

-   Please note, for this exercise you must submit the scripts (with appropriate comments) as a ***.zip*** file, which will be used to determine your grade.

-   The deadline for this Chapter is at 9:00 before the start of next practical.
```

## 1.1 Getting started

While there are some good Python books, the best material for learning most things Python is **online**, thanks to the large Python community.

For this course, we write our Python files using an IDE (Integrated Development Environment), which is a software application that provides for user-friendly programming. There are many free IDEs to write code in Python. Here we use ***Spyder***.

```{note}
Make sure you have completed the {ref}`software` in order to be able to run Spyder in the course environment.
```

### 1.1.1 Overview on Spyder

The Spyder interface is split into multiple parts:

- **Editor** -- this is where you will write your code.

- **Console & log** -- when you run your code, the outputs and errors will be displayed here. In the console you can also give commands, e.g. to get instant output or for testing lines of your code.

- **Multipurpose Window** -- this is where all the files, variables and plots in your workspace are listed and displayed.

```{figure} ./img/media/image1.png
---
name: Fig. 1
---
Setup of Spyder text editor. Source: [Harish Maddukuri](https://medium.com/coderbyte/spyder-python-ide-for-absolute-beginners-89e4ea1832af)
```

### 1.1.2 Creating your own workspace (directory)

Python scripts are generally created and saved into _Projects_. These projects are located in a workspace/directory. The current workspace or directory is shown in the taskbar.

We advise you start every new practical by creating a new Project. To do that:

-   Projects $\rarr$ New Project

-   Give the project a name, e.g. _Practical1_

-   Enter the location where you would like to save the project

```{figure} ./img/media/image2.png

```

```{figure} ./img/media/image3.png
:name: Fig. 2

Creating a new Spyder project
```

Any files that you create will now all be found in your project at the location you specified. In this project we can now have multiple scripts in the form of .py files. You can also click on the following icons:

-	![](img/media/image4.png) to create a new .py file

-   ![](img/media/image5.png) to open an existing .py file

-   ![](img/media/image6.png) to save the currently displayed .py file

-   ![](img/media/image7.png) to save all open .py files

Now create a new project and a new file called `Practical1.py`. This is the file you will be working in today.

```{note}
For the coming exercises, you need to create different .py files. Don't code the exercises in the _Practical1_ file.
```

### 1.1.3 Python basics

#### Variables and operations

In this section we will perform some introductory exercises of Python. We will do the following exercises in the {ref}`Console <Fig. 1>`. So leave your {ref}`Editor <Fig. 1>` empty for now.

-	Type in the console: ```print("Hello, World!")``` and then press enter.

You can see that the output prints the text (=_string_) you just wrote between the quotation marks.

```{tip}
**Definition**
A _string_ ('str') is an object that Python displays as-is and does not interpret, such as text that is intended for the human user. You can create a string by putting the text in single (`' '`) or double (`" "`) quotation marks.

For example, in the code `print("Hello, World!")`, the sequence `Hello, World!` is a string. The word `print` is a function (we will learn about these later), a type of instruction to the computer. If we were to write `"print"` instead, Python would no longer interpret this as an instruction, and would not pring the subsequent string to the console.
```

-	To verify whether this is indeed a string, run: ```type("Hello, World!")```.

You just asked the Spyder console to directly display information. Python will immediately forget this information after displaying it. For Python to remember information for future use, we need to store it in a **variable**.

-	For instance, declare variable _a_ by running: ```a = 2.5```.

With this command, we declare a new variable _a_ and assigned the value 2.5 to it.

```{tip}
**Definition**
A _variable_ is a container for storing information. It has a name, such as `a`, and a value, such as `2.5`. The value of a variable may be a number, a string, or an entire collection of such objects. Pretty much anything can be stored in a variable.

Assigning a value to a new variable is known in programmer-speak as _declaring_ that variable.
```

```{important}
Assigning a new value to an existing variable will delete the old value of that variable.
For example, if we run:
`[1]: x = 5`
`[2]: x = "Hello, World!"`
only the value "Hello, World!" will be stored in the variable `x`.
```

-	Now type in the console: ```b = 3 * a ** 2``` and press enter.

We declared a new variable, *b*, equal to $3a^2$.

-	To see the value of *b*, run ```print(b)``` or just ```b``` in your console.

```{important}
**Printing to the console**
As you can see above, when working in the console it is enough to type a command or variable name, and its result or value will be printed (shown) on screen.

In the next section, we will start working in `.py` files (a.k.a. code files or scripts). With these, only objects or outputs that are explicitly printed using the `print` function will appear on screen. Everything else will remind behind the scenes, as it were.
```

You can also navigate to the {ref}`Variable Explorer <Fig. 1>`. This provides the name, type, size, and value of the variables that are currently stored in the Spyder application.

The basic Python operations and their symbols are presented in {numref}`Table 1`. The most important data types for this course are listed in {numref}`Table 2`.

```{list-table} Basic Python operations and associated symbols
:header-rows: 1
:name: Table 1

* - Operation
  - Symbol
* - Addition
  - \+
* - Subtraction
  - \-
* - Multiplication
  - \*
* - Division
  - /
* - Exponentiation
  - **
```

```{list-table} Most important data types in Python
:header-rows: 1
:name: Table 2

* - Type
  - Description
  - Example
* - ```str```
  - String; text
  - ```"Hello, World!"```
* - ```int```
  - Integer; numeric
  - ```2```
* - ```float```
  - Float; numeric
  - ```2.5```
* - ```bool```
  - Boolean
  - ```True``` or ```False```
```

#### Initial lines of a Python script

Now we start working in the {ref}`Editor <Fig. 1>`. A new `.py` file in Spyder will automatically show some initial information, e.g.:

```
# -*- coding: utf-8 -*-
"""
Created on Tue Apr  4 12:00:00 2023

@author: userName
"""
```

For **EVERY** future Python script you will make, it is important to add information that tells any viewer what this script is about. This is handy both for you and for others who want to see your script at a later moment. For instance, you could add to your _Practical1_ file:

```
"""
This script calculates the "Python Basics" exercises of Practical 1
for the course River and Delta Systems (GEO4-4436) at Utrecht University.

Created on Tue Apr  4 12:00:00 2023

@author: userName
"""
```

````{note}
The ```# -*- coding: utf-8 -*-``` is a remnant of an older Python version. You can ignore and delete this.
````

#### Running a Python script or specific lines

-	Add two new lines to your script where you declare the same variables _a_ and _b_ as you did earlier above.

-	Add ```print(b)``` in a new line.

-	Now run your script by clicking: ![](img/media/image8.png)

What do you observe in your console and variable explorer?

-	Select all lines of code in your Editor.

-	Press F9.

-	Now do the same with just selecting the line which states ```print(b)```.

````{note}
Note: there is a difference between RUNNING the file (using the green play button) and executing it in the console. Execution in the console is much slower than simply running the file, works great for validating whether specific lines in your code actually work.
````

#### Clearing the console and variable explorer

-   Clear the console using the clear button ![](img/media/image9.png)

-   Now type in the console: ```c = a * 30``` and press Enter

We are declaring a new variable $c$, as a function of variable $a$, but you just deleted $a$. The command cannot be executed, because $a$ is not stored in Python's memory anymore. An error message appears in the console.

(functions_intro)=
#### Python functions

You might imagine that doing lots of complicated calculations and working on large datasets may result in extremely long and complicated scripts. To counter this, you can break up programming tasks into separate **functions**, which include the following advantages:

-	_Simplicity_: functions typically focus on a small task rather than an entire problem.

-	_Maintainability_: if functions have a high degree of independence from each other, updating one such function will have limited impact on other functions.

-	_Reusability_: functions can easily be reused in a script, limiting duplication of code.

Run in your console:

```
from numpy import pi
from numpy import cos
```

You just imported two object -- one is the constant _pi_ and the other is a function that calculates the _cosine_ of a value. Run: ```cos(pi)```. Now clear the console and run ```cos(pi)``` again. Clearing the console also deletes all imported objects!

Now, what exactly is ```numpy```?

(packages_intro)=
#### Python packages

The advantage of Python is that it is free and open-source, where any user can write code and functions and share them online for anyone to use. This isn't limited to individual users, but also applies to big _software development teams_. If such a team has developed a large set of functions, they typically store them in a _library_ or _package_. One such important _package_ is [numpy](https://numpy.org/doc/stable/index.html#), which provides numerous mathematical functions and is widely applied in scientific calculations.

-	Instead of importing separate functions (e.g. ```numpy.cos```), you can also import the entire package. Add to your {ref}`Editor <Fig. 1>` and run:

	```
	import numpy as np
	```

	````{note}
	The ```as np``` tells your program that wherever a command starts with ```np.``` it needs to look it up in the _numpy_ library.
	````

	```{note}
	For any package or function that you want to import, it is important to do this at the beginning of your Python script, **before** using them!

	If you import a package but don't use it, an orange triangle ![](img/media/image10.png) will appear to the left of the import command in the Spyder editor.
	```

-	Run your script and you can use all of the functions available in the _numpy_ library. Run in your console: ```np.cos(np.pi)``` and then ```cos(pi)```. Do you understand the difference here?

-   Now test some of the other frequently-used mathematical functions of _numpy_, given in {numref}`Table 3`.

```{list-table} Several important mathematical functions in _numpy_.
:header-rows: 1
:name: Table 3

* - Functions
  - Description
* - ```np.sin()```, ```np.cos()```, ```np.tan()```
  - sine, cosine and tangent (arguments in radians)
* - ```np.arcsin()```, ```np.arccos()```, ```np.arctan()```
  - inverse sine, cosine and tangent
* - ```np.abs()```
  - absolute value
* - ```np.sqrt()```
  - square root
* - ```np.round()```
  - round towards the nearest {ref}`integer <Table 2>`
* - ```np.ceil()```, ```np.floor()```
  - round towards plus (`ceil`) or minus (`floor`) infinity
* - ```np.log()```, ```np.log10()```
  - natural logarithm, logarithm base 10
* - ```np.exp()```
  - exponential
```

```{important}
All of these mathematical functions have their own documentation at the [official numpy web page](https://numpy.org/doc/stable/reference/routines.math.html), or on many of the other Python-related web pages. A very important step of debugging is **always** to ask a search engine! Also see the the debug manual on Brightspace. Note, however, that asking an Artificial Intelligence to write your code will not help your learning (and may count as plagiarism, and has an enormous CO<sub>2</sub> footprint).
```

-	If you want to see all the attributes of a function or package, run for instance ```help(np)``` or ```help(np.cos)```.


Aside from _numpy_, there are countless other free and open source packages that constitute the vibrant community of Python. As you will find out later, other important packages in this course are:

-	[pandas](https://pandas.pydata.org/), which is handy for data analysis and manipulation.

-	[matplotlib](https://matplotlib.org/stable/index.html), which is used for data visualisation.

```{note}
A Python function is specific to a single task. Packages can also include modules, which define multiple functions, classes, attributes etc.
```

## 1.2  Working with .py files

A `.py` file is a program file or script written in Python. It is a succession of Python commands which can be written and edited using a text editor and then is run using the Python interpreter - this is the behind-the-scenes part of Python, which translates our code into something the computer can understand directly. A Python IDE such as Spyder contains a text editor (and other useful elements, as we've seen), and is capable of communicating directly with the interpreter. Using `.py` files allows you to organise and save different series of commands. Scripts can be edited, extended or corrected whenever you want and can be executed several times. Writing the commands into a script is necessary when you perform advanced data analysis, since it allows you to check/improve your methodology, but also to be sure you perform the exact same data processing for several datasets, for instance.

````{important}
Good code includes comments to explain to anyone reading what different parts of it do - most importantly to Future You, who will be staring at the script a month from now, wondering "wth was I trying to do here?"
Comments in Python start with a `#`, which tells the interpreter to skip the rest of the line and move on to the next one.
In Spyder, comments will appear in a different colour (grey by default).
````

When a script is executed, Python executes the commands in the order they are written. It is therefore important to consider in which order you want to execute your commands. Generally, scripts are structured as follows:

-	**Docstring (documentation string)**	Describe the script in a few words (e.g. objective, date of creation, author of the script)

-	**Package import**						Import all the necessary packages to perform operations (e.g. numpy)

-	**Initialization**						Declare the main variables and load your data

-	**Calculations**						Execute the calculations

-	**Output and visualisation**			Commands to display the results, plot graphics and save output

Copy-paste and execute the simple example below:

```
"""
This script provides an example of a "basic" structure of a .py file
for the course River and Delta Systems (GEO4-4436) at Utrecht University.

Created on Mon Apr  17 12:00:00 2023

@author: userName
"""

# Package import
import numpy as np
import matplotlib.pyplot as plt

# Initialization
a = np.array([0, 1, 2, 3, 4, 5])

# Calculations
b = a ** 2

# Output and visualisation
plt.plot(a, b)
```

```{tip}
Best practices for using Python are described in a series of "Python Enhancement Proposals" or [PEPs](https://peps.python.org/pep-0000/). Most relevant to the beginning and even advanced Python user are [PEP 8 - the style guide](https://pep8.org/) and [PEP 20 - the Zen of Python](http://www.thezenofpython.com/) (or run `import this` in your Spyder console).
```

---

(EXERCISE-1.1)=
## **EXERCISE 1 - Calculate river flow velocity and water depth**

```{important}
**You are expected to hand in this code.**
```

The aim is to calculate flow velocity and water depth in a river from known variables and parameters (use a web search to find out what the difference is between "variable" and "parameter"). The flow resistance parameter for this river is $C = 44$ m<sup>1/2</sup>/s, the discharge $Q = 2500$ m<sup>3</sup>/s, the channel width $W = 500$ m and the channel gradient $S = 1.6 × 10^{−4}$ m/m. $Q$ is defined as:

$$
Q = h u W \\
$$ (Eq_1_1)

where $h$ is water depth in m and $u$ is flow velocity in m/s averaged over the depth and width of the channel. $u$ is related to $h$ following the Chezy equation:

$$
u = C\sqrt{h S}\\
$$ (Eq_1_2)

See [Kleinhans, 2005](https://agupubs.onlinelibrary.wiley.com/doi/full/10.1029/2005JE002521#) for a brief overview how the Chezy relation is equivalent to the Darcy-Weisbach relation and the Manning relation, which you might be more familiar with.

The commands should be written in a _.py_ file called _Exercise1_, saved in your current directory. The script should display the results.

Do not forget to comment the file and give meaningful names to the variables.

````{hint}
$S = 1.6 × 10^{−4}$ can be written in Python as: ```1.6e-4```.
````

```{Important}
End of Exercise 1.

_Please add this script to the folder that you will zip and send to us._
```

---

## 1.3  Data structures

A data structure is the fundamental form that Python uses to store and manipulate data. It allows for efficient calculations and analysis over entire datasets. There are multiple types of data structures. In this course we will discuss _lists_, _arrays_ and _DataFrames_.

-	A **list** is simply a one-dimensional series of elements (e.g. numbers, strings, or other lists) and can be create using using square brackets `[]`.

-	An **array** is similar to a list, but it can have any number of dimensions. An array contains data of all the same type (e.g. all integers or all strings).

-	A **DataFrame** is a matrix of different elements organized in rows and columns which CAN be of different datatypes.

Different data types that can be stored in lists, arrays and DataFrames are provided in {numref}`Table 2`.

In this section we will learn how to create lists, arrays and dataframes, extract the relevant information from one of them, and perform calculations with them.

### 1.3.1 Creating lists, arrays and DataFrames

-   Clear your variables and run in your console: ```L = [1, 2, 5, 10]```. Check the Variable Explorer to see the type of data structure that is produced.

-   Now run in your console: ```L2 = [[1, 2, 5, 10], [3, 4, -2, 7]]```. Now compare $L$ and $L2$ in the Variable Explorer. Do you understand the difference in size?

	```{hint}
	By double clicking on a variable in the variable explorer, you can see more information.
	```

$L$ and $L2$ are data structures of the type _list_. A list is a basic [Python structure](https://docs.python.org/3/tutorial/datastructures.html#) included in the core Python modules. It therefore does not require a {ref}`package<packages_intro>` to be imported.

-   Now import numpy again as np.

-	Run: ```A = np.array(L2)```. What kind of variable do you obtain and how is different from $L2$?

$A$ is of type [array](https://numpy.org/doc/stable/reference/generated/numpy.array.html), which is a data structure type of the _numpy_ package.

-   Now run: ```import pandas as pd``` and ```D = pd.DataFrame(L2)```. What is the difference between $L2$, $A$ and $D$?

	```{note}
	Similar to importing _numpy_ as _np_, it is very common to import _pandas_ as _pd_.
	```

$D$ is of type [DataFrame](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.html), which is a data structure type of the _pandas_ package.

-	Now run: ```A2 = np.array(D)``` and ```D2 = pd.DataFrame(A)```. Are there differences between $A$ and $A2$ or $D$ and $D2$?

Because of the worlwide usage of both packages, _numpy arrays_ can be easily transformed into _pandas DataFrames_ and vice versa.

(note_on_data_structures)=
```{important}
Some {ref}`functions<functions_intro>`, classes or attributes require a specific type of data structure (e.g. array or DataFrame). Therefore, you should always consider whether your variable is stored in the proper data structure!
```

The advantage of package-built data structures is that they have their own built-in attributes. Attributes are called using a ```.```.

-   Run the following code:

	```D.size```

	```D.shape```

	```A.size```

	```A.shape```

As you can see, there are overlapping attributes between _numpy arrays_ and _pandas DataFrames_. For any type of data structure, you can usually find the attributes online in the official documentation of the specific data structure (e.g. [pandas DataFrame](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.html)).

-   Have a closer look at the attributes listed in [DataFrame documentation](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.html). Run the following codes:

	```len(D.index)```

	```len(D.columns)```

	Do you understand what the above lines display and what the funcion ```len()``` does?

Instead of defining all the specific elements, as you did for $L$ and $L2$, you can also define an array of an amount of elements following an interval. You can do this using the numpy function [np.arange](https://numpy.org/doc/stable/reference/generated/numpy.arange.html):

-	Run the following codes:

	```A3 = np.arange(1, 6, 1)```

	```A4 = np.arange(1, 6, 2)```

	```A5 = np.arange(12, 0, -3)```

	```A6 = np.arange(12, 0, 3)```

	Compare the outcomes. Do yo understand how the np.arange function works?

The np.arange function requires as input "(begin, end, interval)". If no interval is specified, the default interval is 1. So ```np.arange(1, 6)``` will return the same as ```np.arange(1, 6, 1)```.

````{note}
The _end_ number is not included in the output array.

Thus ```np.arange(1, 6, 1)``` returns ```[1 2 3 4 5]``` and NOT ```[1 2 3 4 5 6]```.
````

### 1.3.2 Concatenation, vstack and hstack

Sometimes it can be useful to combine several related arrays or lists into one unique array and join them together. This can be done using the numpy operation of [concatenate](https://numpy.org/doc/stable/reference/generated/numpy.concatenate.html).

-	Clear your variables and import numpy. Run the following codes:

	```a = np.arange(1, 3)```

	```b = np.arange(4, 6)```

	```c = np.concatenate((a, b))```

	Inspect how arrays $a$ and $b$ are joined together into array $c$.

	```{note}
	Several functions require double parens (parentheses, `(())`) or double brackets (`[[]]`), e.g. _np.concatenate(( ))_.
	```

The default is to concatenate arrays in the same dimension (also referred to as horizontally).

```{note}
The above arrays are 1-dimensional (i.e. their size has only one direction, for example (2,) and not (2,1)). Double-clicking a 1-dimensional vector in the variable explorer provides a default vertical display. Don't confuse this as a 2-dimenstional display of several rows and one column (e.g. (2,1) )!
```

-	Now run:

	```d = np.vstack((a, b))```

	```e = np.hstack((a, b))```

	Compare the outcomes.

Numpy [vstack](https://numpy.org/doc/stable/reference/generated/numpy.vstack.html) is used to vertically concatenate arrays, whereas [hstack](https://numpy.org/doc/stable/reference/generated/numpy.hstack.html) is used for horizontal or 1-dimensional concatenation (for the situation above, $c$ and $e$ yield the same concatenation output).

```{note}
_concatenate_, _hstack_ and _vstack_ can be used to combine strings, and lists or arrays of floats and integers ({numref}`Table 2`). To vertically stack two lists they must have the same dimensions!
```

### 1.3.3 Manipulating data structures using their subscripts

Elements of data structures are usually identified by their position (row and column numbers), also called subscript or index. {numref}`Table 4` shows how the different elements of a 3 *×* 6 matrix can be identified using their subscripts.

```{list-table} Subscripts of 3 *×* 6 matrix
:header-rows: 0
:name: Table 4

* - [0,0]
  - [0,1]
  - [0,2]
  - [0,3]
  - [0,4]
  - [0,5]
* - [1,0]
  - [1,1]
  - [1,2]
  - [1,3]
  - [1,4]
  - [1,5]
* - [2,0]
  - [2,1]
  - [2,2]
  - [2,3]
  - [2,4]
  - [2,5]
```

For a _numpy array_ you can identify an element by position as follows:

-	Clear your variables and import numpy and pandas as np and pd, respectively. Run the following codes:

	```L = [[1, 2, 5, 10], [3, 4, -2, 7]]```

	```A = np.array(L)```

	```NA = A[1, 3]```

	Here $NA$ provides the element of array $A$ at position (1,3).

-	Now try if this also works for a _pandas DataFrame_ by running:

	```D = pd.DataFrame(L)```

	```ND = D[1, 3]```

	Here we refer to an {ref}`earlier note<note_on_data_structures>` on data structures.

To identify the element of a _pandas DataFrame_ through a subscript, we use [iloc](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.iloc.html) (= index location):

-	Run:

	```ND = D.iloc[1,3]```

	As _iloc_ is an attribute to _pandas DataFrame_, it won't work for a _numpy array_. Try: ```NA = A.iloc[1,3]```

-	Write your own code that returns ```-2``` for both $A$ and $D$.

To replace an element with something else we use [numpy where](https://numpy.org/doc/stable/reference/generated/numpy.where.html) or [pandas replace](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.replace.html).

-   Run the following codes:

	```A = np.where(A == -2, 2, A)```

	```D = D.replace(-2, 2)```

	Compare $A$ and $D$ with their previous outputs. Do you understand how the _np.where_ function works?

Instead of single elements, you can also call entire rows and columns.

-   Run the following codes:

	```RA = A[0, 0:4]```

	```CA = A[0:2, 2]```

	```RD = D.iloc[0, 0:4]```

	```CD = D.iloc[0:2, 2]```

	Examine the outputs.

	````{note}
	Instead of defining a row or column through its first and last index, you can also just use ```:```, e.g. for the variables definede here, ```RA = A[0, :]``` yields the same output as ```RA = A[0, 0:4]```. The same goes for ```CD = D.iloc[:, 2]``` and ```CD = D.iloc[0:2, 2]```.
	````

-	Create two new vectors containing the second rows of $A$ and $D$.

-	Replace all elements of the second columns of $A$ and $D$ with zeros.

## 1.4 Operations on numpy arrays and pandas DataFrames

### 1.4.1 Operations between a scalar and a matrix

If you conduct simple operations on a numpy array with a scalar, all the elements in the array are multiplied by that scalar.

-	For instance, inspect the outputs of the following commands:

	```2 * A```

	```2 / A```

	```2 + A```

	```2 - A```

-	Now try the same operations with pandas DataFrame $D$. Do these operations also work for Dataframes?

### 1.4.2 Operations between matrices

#### Simple operations between arrays and DataFrames

Addition or subtraction operations can only be applied to matrices of identical size. The resulting matrix is obtained by adding (subtracting) their corresponding elements. Example:

-   Define the following new matrix $M$ of same size as $A$ and $D$ and store it **both** as a _numpy array_ and as _pandas DataFrame_:

	$$
	M = \begin{pmatrix}
		3 & 8 & 0 & 160\\
		13 & 42 & 21 & 17
	\end{pmatrix}
	$$

-	Now try operations of ```+```, ```-```, ```*```, ```/``` and ```**``` between $A$, $D$ and $M$. Also try operations between arrays and DataFrames. Inspect the outputs.

#### Multiplication of two matrices

Matrix multiplication according to linear algebra follows different rules.

-	Define two new _arrays_ $B$ and $C$:

	$$
	B = \begin{pmatrix}
		1 & 0 & 2\\
		5 & 10 & 7
	\end{pmatrix}
	\quad \textrm{and} \quad C = \begin{pmatrix}
		1 & 3\\
		4 & 1\\
		2 & 2
	\end{pmatrix}
	$$

-	To execute a matrix multiplication, you use [np.matmul](https://numpy.org/doc/stable/reference/generated/numpy.matmul.html), run:

	```E = np.matmul(B,C)```

	This will calculate the matrix product of matrices $B$ and $C$ as follows:

	$$
	E(i,j) = \sum_{k=1}^{n} B(i,k) \ast C(k,j) = \begin{pmatrix}
		1 \ast 1 + 0 \ast 4 + 2 \ast 2 & 1 \ast 3 + 0 \ast 1 + 2 \ast 2\\
		5 \ast 1 + 10 \ast 4 + 7 \ast 2 & 5 \ast 3 + 10 \ast 1 + 7 \ast 2
	\end{pmatrix} = \begin{pmatrix}
		5 & 7\\
		59 & 39
	\end{pmatrix}
	$$

## 1.5 Python built-in functions for arrays and DataFrames

### 1.5.1 Examples of elemantary functions

We are now going to look at several additional examples of built-in functions for both arrays and DataFrames. For a complete list, go to the official documentation of [numpy arrays](https://numpy.org/doc/stable/reference/arrays.html) and [pandas DataFrames](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.html). If you're looking for something specific, it's always a good idea to conduct a Google search for the data structure you are using.

-	It is possible to **round** the value of floats and matrices using [np.round](https://numpy.org/devdocs/reference/generated/numpy.round.html). Run the following and inspect the outcomes to see if you understand what happens:

	```np.round(1.555)```

	```np.round(1.555,2)```

	```np.round(A/3)```

	```np.round(D/3)```

-	To **transpose** a matrix, you change the rows of the matrix into columns, and vice versa using [np.transpose](https://numpy.org/doc/stable/reference/generated/numpy.transpose.html). As a consequence, a matrix of size n × m will turn into a matrix of size m × n containing the same elements organised in a different way.

	```np.transpose(A)```

	```np.transpose(D)```

-	To **create new matrices**, you are not required to write down every element, such as you did earlier by defining $L$. Run the following and inspect the outcomes:

	```np.zeros((3,5))```

	```np.ones((5,3))```

	```np.full((3,5),2)```

	```np.full((3,5),np.nan)```

-	With the help of functions previously introduced, create a matrix of size 20x30 containing only floats that represent $5/3$ in six digits after the decimal point. Try to do this in only one line of code!

### 1.5.2 Data analysis

The main numpy functions available to perform (statistical) data analysis on arrays are summarized in {numref}`Table 5`. Some examples of the use of these functions are given below.

-	Define the following vector as an array:

	```vectA = np.array([6,2,5,7])```

-	Run the following commands and inspect the outputs:

	```np.mean(vectA)```

	```np.median(vectA)```

	```np.sum(vectA)```

	```np.max(vectA)```

	```np.min(vectA)```

-	In some practical cases, it is important to know when a maximum (or minimum) value has been reached, that is to say, what is the position of the largest value in the original vector. To return the index/location of the max or minimum value use [np.argmax](https://numpy.org/doc/stable/reference/generated/numpy.argmax.html) or [np.argmin](https://numpy.org/doc/stable/reference/generated/numpy.argmin.html#numpy.argmin), respectively. Inspect the following runs:

	```np.argmax(vectA)```

	```np.argmin(vectA)```

-   Now run:

	```s = np.sort(vectA)```

	Compare $s$ and $vectA$.

-	For DataFrames, these statistical numpy operations work differently in that they handle each column separately. The output is therefore a vector of length the amount of columns. Run for instance:

	```np.mean(D)```

-	It is generally possible to specify the direction (rows or columns) along which the computations have to be performed as an additional input argument. Run for instance:

	```np.mean(D,0)```

	```np.mean(D,1)```

	What is the difference?

```{list-table} Some important numpy functions for statistical data analysis on matrices
:header-rows: 1
:name: Table 5

* - Function
  - Description
* - [np.max](https://numpy.org/devdocs/reference/generated/numpy.max.html)
  - Maximum value
* - [np.min](https://numpy.org/devdocs/reference/generated/numpy.min.html)
  - Minimum value
* - [np.median](https://numpy.org/doc/stable/reference/generated/numpy.median.html)
  - Median value
* - [np.mean](https://numpy.org/doc/stable/reference/generated/numpy.mean.html)
  - Average/mean value
* - [np.std](https://numpy.org/doc/stable/reference/generated/numpy.std.html)
  - Standard deviation
* - [np.var](https://numpy.org/doc/stable/reference/generated/numpy.var.html)
  - Variance
* - [np.percentile](https://numpy.org/doc/stable/reference/generated/numpy.percentile.html)
  - Percentile values
* - [np.sum](https://numpy.org/doc/stable/reference/generated/numpy.sum.html)
  - Sum of the elements
* - [np.sort](https://numpy.org/doc/stable/reference/generated/numpy.sort.html)
  - Arrange the elements in ascending order
```

---

(EXERCISE-1.2)=
## **EXERCISE 2 - Array calculations**

```{important}
**You are expected to hand in this code.**
```

Make a new _.py_ file called _Exercise2_ in your work-directory, where the commands need to solve the following assignments. The script should display the results of all assignments.

1.  Create the following numpy array $A$:

$$
A = \begin{pmatrix}
  16 & 3 & 2 & 13\\
  5 & 10 & 11 & 8\\
  9 & 6 & 7 & 12\\
  4 & 15 & 14 & 1
\end{pmatrix}
$$

2.  Define an array $A1$ containing the first row of $A$.

3.  Define a scalar, $sumA1$, equal to the sum of the elements of $A1$.

4.  Create a vector $sumRows$, where each element contains the sum of the elements of one of the rows of $A$. The first element of this vector should be equal to:

	$$
	sumRows[0] = \sum_{k=0}^{4} A[0,k]
	$$

	Try to use only one command line!

5.  Create a vector $sumColumns$, containing the sum of the columns of $A$.

6.	What do you notice when comparing $sumRows$ and $sumColumns$?

	_Answer open questions as remarks in separate lines starting with: '#'_.

```{Important}
End of Exercise 2.

_Please add this script to the folder that you will zip and send to us._
```
---

## 1.6 Visualising data

**How to make a simple 2D-plot: example**

Add all the following codes in the .py file in your {ref}`Editor <Fig. 1>`, not your console!

-	Clear your variables, import numpy and define the following arrays in your file:

	```x = np.arange(-np.pi, np.pi,0.5)```

	```y = np.sin(x)```

	```y2 = np.cos(x)```

-	Now we will use the package [matplotlib](https://matplotlib.org/stable/index.html) to create a figure. Add to the beginning of your file:

	```import matplotlib.pyplot as plt```

-	Add to your file the following lines of code:

	```plt.figure(1)```

	```plt.plot(x,y)```

	```plt.show()```

	````{note}
	You have to include the ```plt.figure(1)``` because you have to give unique numbers your separate plots in your script.
	````
	Select all the lines you have in your file and press **F9**. Inspect what happens.

-	Now run in your console:

	```plt.plot(x,y2)```

	A new plot has replaced the previous one in the figure window. To display the second graph on top of the first one you have to edit your file as follows:

	```
	plt.figure(1)
	plt.plot(x,y)
	plt.plot(x,y2)
	plt.show()
	```

	Run the following lines with **F9**.

	```{note}
	As is alwas the case in programming, the order of your lines of code is very important here!
	```

-	Edit the second plotting line so it now reads

    ```plt.plot(x,y2, color = 'r')```

	Run the lines. Do you understand what happened?

-	Title, labels on the x- and y-axis and legends can now be defined. Type the following commands (before ```plt.show()```!) one by one and analyse their effects on the figure:

	```plt.title('Sine and cosine functions')```

	```plt.xlabel('Radians')```

	```plt.ylabel('Function value')```

	```plt.legend(['sine', 'cosine'])```

-	Matplotlib is the basic package for plotting your data, but there are also other packages that can be used complementary to matplotlib, for instance [seaborn](https://seaborn.pydata.org/). Include at the top of your script where you import your packages:

	```import seaborn as sns```

	```sns.set()```

	Run the plotting lines again, do you see the difference?

-	To specify the limits of the x- and y-axis include for instance (before ```plt.show()```!):

	```plt.xlim(-np.pi, np.pi)```

	```plt.ylim(-2,2)```

	Run the plotting lines again. What has happened?

-	It is also possible to plot without specifying the *x* argument. Run:

	```plt.plot(y)```

	The elements are now plotted as a function of their position in the vector: *y*(1) at *x* = 1, *y*(2) at *x* = 2, etc.

-	Multiple plots can also be displayed in one figure. This can be done using the command [subplot(a,b,c)](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.subplot.html) where $a$, $b$ and $c$ are integers, and $c$ is less than or equal to the product $a*b$. This command divides the figure in $a*b$ sub-figures, organized in $a$ rows and $b$ columns. To obtain 2 figures, one above the other, include and run following lines below your 1st figure:

	```
	plt.figure(2)
	plt.subplot(2,1,1)
	plt.plot(x,y)
	plt.subplot(2,1,2)
	plt.plot(x,y2, 'g')
	plt.show()
	```

-   Include labels and titles to your subplots of the second figure

-	To close a figure use:

	```plt.close()```

	Try this with and without the code ```plt.show()```.

	````{hint}
	You can easily disable a line of code by adding a ```#```.
	````

	````{note}
	You can close the currently opened plot in your figure window by clicking: ![](img/media/image11.png)

	You can close all plots in the figure window by clicking: ![](img/media/image12.png)
	````

-	Numerous options are available to customize your plots, all lised at the official documentation of [matplotlib](https://matplotlib.org/stable/index.html). Some examples are given in {numref}`Table 6`. Try out the example in {numref}`Table 6` to your own script.

```{list-table} Some important matplotlib.pyplot functions for customizing your plots
:header-rows: 1
:name: Table 6

* - Syntax
  - Description
* - ```plt.plot(x,y, color = 'r')```
  - Solid red line
* - ```plt.plot(x,y, color = 'r', linestyle= '--')```
  - Dashed red line
* - ```plt.plot(x,y, color = 'r', linestyle = '--', linewidth= 2)```
  - Thick dashed red line
* - ```plt.plot(x,y, color = 'g', marker = '*')```
  - Green asterisks with line
* - ```plt.plot(x,y, color = 'g', marker = '*', linestyle = 'none')```
  - Green asterisks without line
* - ```plt.plot(x,y, color = 'magenta', marker = 's', linestyle = 'dashdot')```
  - Magenta squares with a dashdot line
```

-	There are many colours available, using either letters, full names or colour codes. Google _matplotlib color_ or _seaborn color_ to get an idea of what colours are available. The figure below also indicates a wide range of colour options. If you are using several lines it may be nice to use a colour palette using seaborn palettes. An example of how to do this is as follow:

	```sns.set_palette("Spectral", 18)```

	In this case _Spectral_ is the name of the palette and _18_ is the number of lines you will use in your plot. Google _seaborn palettes_ to see what is available.

-	Similarly, many marker and linestyles are available. See the images below for the most common options.

````{note}
If you want to reset the Seaborn settings to original, run:
```
sns.reset_orig
```
If you want to switch off Seaborn, you can reset matplotlib within your script or through the console, by running:
```
import matplotblib as mpl
import importlib
Importlib.reload(mpl); importlib.reload(plt); importlib.reload(sns)
```
````

```{figure} ./img/media/image13.png

```

```{figure} ./img/media/image14.png

```

```{figure} ./img/media/image15.png
:name: Fig. 3

Specs for colors, markers and linestyles in matplotlib
```

---

(EXERCISE-1.3)=
## **EXERCISE 3 - Visualisation of river sediment transport data**

```{important}
**You are expected to hand in this code.**
```

This exercise is based on the dataset contained in the file _MPMtransportdata.xls_. [Meyer-Peter and Mueller (1948)](https://repository.tudelft.nl/islandora/object/uuid:4fda9b61-be28-4703-ab06-43cdc2a21bd7?) (abbreviated MPM) graphically reported gravel transport data from their flume experiments and derived their famous empirical bedload transport predictor from this dataset. [Wong and Parker (2006)](https://ascelibrary.org/doi/full/10.1061/%28ASCE%290733-9429%282006%29132%3A11%281159%29) recovered the original data and re-analysed it to find that the original fit by MPM was wrong. Here you will plot both the data in nondimensional form and plot a predicted transport using a sediment transport predictor. We assume that the density of the water $\rho$ is 1000 kg/m<sup>3</sup> and Earth's gravity acceleration $g$ is 9.81 m/s<sup>2</sup>.

1.  Make a new _.py_ file called _Exercise3_ in which the series of commands necessary to solve this assignment will be written. Do not forget to clear your workspace and close the figures at the beginning of your script.

2.  Download the file _MPMtransportdata.xls_ from Blackboard or Teams and save it in your current work-directory. First you must specify the the path of the file i.e. the folder where you have saved the Excel file. For example:

	```
	path = r"C:\Users\username\Documents\myworkspace"
	```

	```{note}
	The _r_ here refers to _raw_ and makes sure that everything between the quotation marks is read as a 'raw' string, without making other interpretations. This prevents the syntax of the path to cause the script to error when it wants to read a file from the directory.
	```

	You can now load the data using the following line:

	```
	dataMPM = pd.read_excel(path+"\MPMtransportdata.xls")
	```
	The output given here is a _pandas_ [DataFrame](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.html). The DataFrame reads in ALL the information including the text headers, which is not convenient for calculations. Create a _numpy_ [array](https://numpy.org/doc/stable/reference/generated/numpy.array.html) where the _NaN_ and text columns of this DataFrame have been eliminated. You can do this by by specifying a row from where you want the array to start.

3.  Define vectors containing the discharge $Q$ (m<sup>3</sup>/s), channel width $W$ (m), water depth $h$ (m), slope $S$ (m/m), median grain size $D_{50}$ (m), the specific gravity of the sediment $s$ (which is density of sediment divided by density of water), and the sediment transport rate $q_s$ (m<sup>2</sup>/s, or m<sup>3</sup>/s per m width).

	```{hint}
	Check the units of the dataset!
	```

4.  In order to compute sediment transport, it is necessary to know the total bed shear stress $\tau$ (Pa). Calculate a new vector $\tau$ (or _tau_). This can be calculated as follows:

	$$
	\tau = \rho gh\sin{S} = \rho {u\ast}^2
	$$ (Eq_1_3)

	where $u\ast$ is the shear velocity (m/s) defined by the above relation. (Accept this for now... there is a complicated story behind it involving boundary layer theory.)

	````{note}
	The $S$ variable is has the type "Array of object". Although $S$ consists of float elements, the _sin_-function isn't able to recognize these elements as such within an "Array of object". Therefore you will need to type the following in your code to specify that it needs to read the elements as floats:
	```
	np.sin(S.astype(float))
	```
 	This is not only the case for the _sin_-function, but also many other numpy functions!
	````

5.  To compare datasets derived from different scales (e.g. field versus lab measurements), parameters are often made dimensionless. Shear stress $\tau$ can be nondimensionalized into the "Shields parameter" $\theta$, which is the ratio of the flow force driving sediment transport and gravitational force that demobilizes sediment. Calculate $\theta$ following:

	$$
	\theta = \frac{\tau} {\left( \rho_s - \rho \right) g D_{50}}
	$$ (Eq_1_4)

	where $\rho_s = s \rho$ refers to the sediment density.

6.  Sediment transport can be nondimensionalized with the "Einstein parameter" $\phi$. Calculate $\phi$ using:

	$$
	\phi = \frac {q_s} {(Rg)^{1/2}D^{3/2}_{50}}
	$$ (Eq_1_5)

	wherein $R = (\rho_s-\rho)/\rho = (s-1)$ is the relative submerged density.

	```{hint}
	Make sure you use brackets to enclose fractions!
	```

7.  Plot the sediment transport rate $q_s$ (y-axis; this is the effect) as a function of the shear stress $\tau$ (x-axis; this is the cause). Plot the data as _points_ in log-scales for both axes. To do that, the function [plt.plot()](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.plot.html) can be replaced by [plt.loglog()](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.loglog.html). Give an appropriate title to the plot, as well as labels to the x- and y-axes.

	```{note}
	When writing texts for figure titels or axis labels, writing sections of text between two \$-signs will automatically make the text between these signs mathematical, e.g. ```$m^2$``` becomes $m^2$. Similarly, ```$q_s$``` will become $q_s$. To subscript or superscript more than one character, use the parentheses "\{...}", for example ```$D_{50}$``` becomes $D_{50}$.
	```

	````{note}
	To use Greek letters in your titels or axis labels, you use "\$greekletter\$", e.g. ```$\phi$``` becomes $\phi$.
	```{hint}
	_matplotlib.pyplot_ has a built-in interpretation for ```\t```. To prevent this from affecting the texts of Greek letters such as $\tau$ or $\theta$ in your plots, assure by the dollar signs that your texts are interpreted as raw strings.
	```
	````

8.  Plot in a new figure the data in a nondimensional form, i.e. the Einstein parameter $\phi$ (y-axis) as a function of the Shields parameter $\theta$ (x-axis). Give an appropriate title to the plot, as well as labels to the axes.

9.	Compare the figures plotted at **7** and **8**. What is the use of dimensionless variables?

	_Answer open questions as remarks in separate lines starting with: '#'_.

10.	The MPM predictor of [Meyer-Peter and Mueller (1948)](https://repository.tudelft.nl/islandora/object/uuid:4fda9b61-be28-4703-ab06-43cdc2a21bd7?) was derived from flume experiments with bed load transport, meaning that it does not predict suspended load bed material transport. It is given as:

	$$
	\phi_b = 8 \left( \theta^/ - \theta_{cr} \right)^{1.5}
	$$ (Eq_1_6)

	where the lower case "$b$" in $\phi_b$ refers to the Einstein parameter for _bed load_ and $\theta_{cr}$ is the critical Shields value below which sediment transport does not occur. Empirically, MPM uses $\theta_{cr}=0.047$. This value is an asymptote for the transport function: sediment transport only happens (according to the predictor) when the excess dimensionless shear stress is larger than 0.

	```{note}
	$\theta^/$ refers to the dimensionless shear stress that is only related to grain friction, instead of the total shear stress $\tau$ which also involves friction by bedforms such as ripples and dunes ([Kleinhans, 2005](https://agupubs.onlinelibrary.wiley.com/doi/full/10.1029/2005JE002521#)). In this exercise we ignore this and assume $\theta^/=\theta$, which is valid for the MPM experiments where bedforms hardly formed.
	```

	Plot the MPM prediction as an additional red line in the second figure and add a [legend](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.legend.html) to the figure.

	````{hint}
	To plot this line, first define two vectors $x$ and $y$ such that $x$ contains an appropriate range of values for the Shields parameter ($\theta$) and $y$ contains the $\phi_b$ values calculated using the MPM predictor (so insert $x$ in Eq. {eq}`Eq_1_6`). $x$ is thus a series of values and not the same as the values of $\theta$ that you calculated at Eq. {eq}`Eq_1_4`. 
	```{note}
	If you base your range of $x$ values here to include values below $\theta_{cr}$, then you raise negative numbers to a non-integer power, resulting in imaginary numbers, which will lead to an error when you try to plot them.
	```
	````

11. In the same figure, plot a vertical line corresponding to $x = \theta_{cr}$.

	````{note}
	For this you can use the _matplotlib.pyplot_ command [axvline](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.axvline.html).
	```{hint}
	All data should be equal to or larger than $\theta_{cr}$.
	```
	````

12. To further analyse the data, remake the figures of the questions **7** and **8** using the _matplotlib.pyplot_ function [scatter()](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.scatter.html). scatter() is a function which allows you to plot the data as points of different sizes and colors depending on their characteristics. Here we specify a size range based on the specific gravity of the sediment $s$. The lines below provide an example:

	```
	import matplotlib.pyplot as plt
	import seaborn as sns

	plt.figure(3)
	plt.scatter(tau,qs,s=s.astype(float)*50,c=s,cmap="inferno",alpha=0.4)
	plt.xscale('log')
	plt.yscale('log')
	```

	Copy-paste the code above and add a _matplotlib.pyplot_ [colorbar](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.colorbar.html) of the colormap to your figure. Give the colorbar a proper label.

	```{note}
	Importing seaborn here allows you to use the various colormaps available in this package.
	```

	```{note}
	Setting a scale to log may cause _matplotlib.pyplot_ to produce improper ranges of x and y. This error is caused by x- or y-values of 0, which cannot be displayed on a log scale. You can solve this problem by manually defining your [x-limits](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.xlim.html) and/or [y-limits](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.ylim.html).
	```

13. Answer the following questions with respect to the plot you just created:

	- Why do we multiply $s$ by 50?

	- What determines the colours of the data points?

	- What determines the size of the data points?

	- Do you understand the difference between specifying ```c``` and ```cmap```?

	- What is the function of ```alpha```?

	_Answer open questions as remarks in separate lines starting with: '#'_.

14. Aside from shear stress and sediment transport, grain size can also be nondimensionalized into the "Bonnefille number" $D\ast$:

	$$
	D\ast = D_{50} \sqrt[3]{\frac{Rg}{\nu^2}}
	$$ (Eq_1_7)

	where $\nu$ is the kinematic viscosity of water, which we set at $= 1.6 × 10^{−6}$ Pa&#183;s for 3&deg;C.

	Create a new figure, which will be divided into two subplots. In the top subplot of the figure, plot sediment transport $q_s$ (y-axis) as a function of shear stress $\tau$ (x-axis), with a colormap depending on the base 10 logarithm of the Bonnefille number $D\ast$. On the bottom part, plot the same figure but then in its nondimensional form. Add colorbars with proper labels to both plots.

	````{note}
	For a better distribution of the colors, we use the [base 10 logarithm](https://numpy.org/doc/stable/reference/generated/numpy.log10.html) of the Bonnefille number as the "color vector" argument of the function [scatter()](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.scatter.html), instead of just the Bonnefille number.
	````

15. Look at the data plotted in non-dimensional form. One set of points seems to follow a different trend than the others. What range of $D\ast$ does this correspond to?

	_Answer open questions as remarks in separate lines starting with: '#'_.

```{important}
End of Exercise 3.

_Please add this script **and all files you have imported in your script** to the folder that you will zip and send to us._
```

```{note}
There are several ways to load Excel files in Python. In this assignment we use the *pandas* command [read_excel](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.read_excel.html). If your data is stored in a csv-file, you can use [read_csv](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.read_csv.html). Hence there are countless of ways to load your data in a Python script. A quick search online can give you the best commands for importing your data.
```

---


(EXERCISE-1.4)=
## **EXERCISE 4 - Analysis of the Rhine flow discharge measured at Lobith**

```{important}
**You are expected to hand in this code.**
```

In this exercise, we will perform some analysis on a dataset containing the flow discharge of the Rhine measured at Lobith (where the Rhine enters the Netherlands) for the previous century 1901-2000 AD. The dataset is provided on Blackboard as a the text-file _LobithDischargeData.asc_. Each element of this dataset is the discharge in m<sup>3</sup>/s for one day, and each column corresponds to one year (first column = 1901, last column = 2000).

**Preliminary analysis**

1.  Make a new _.py_ file called _Exercise4_ in which the assignments of this exercise are executed. Start the script by clearing your workspace and closing the windows.

2.  Load the new dataset. As the data are stored as a text (_ASCII_) file, the following command should be used:

	```
	Q = pd.read_table(path+"\LobithDischargeData.asc",header=None)
	```

	Open the DataFrame in the Variable Explorer, do you understand how it is organised? Why do you think ```header=None``` is used?

	_Answer open questions as remarks in separate lines starting with: '#'_.

3.  The data corresponding to the 29th of February are included for each year, leading to 366 rows. Display the first 20 elements of the row corresponding to the 29th of February, what do you notice?

	_Answer open questions as remarks in separate lines starting with: '#'_.

	```{note}
	NaN stands for "Not a Number". It is often used to represent missing values in datasets.
	```

4.  To get an overview of the data use:

	```
	plt.figure(1)
	plt.plot(Q)
	```
	In the commands above, the function [plt.plot()](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.plot.html) is applied to a [DataFrame](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.html) instead of a vector. This plot handles each column (and therefore each year of data) separately. As a result, each line appearing in the figure corresponds to the evolution of the discharge $Q$ for a given year. Give an appropriate title to the plot, as well as labels to the axes.

5.  Zoom in on the figure around the 29th of February. How are the NaN-values handled by the plot?

	_Answer open questions as remarks in separate lines starting with: '#'_.

	```{hint}
	For zooming, you can use the "zoom" buttons above your plots, or redefine the [x-limits](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.xlim.html).
	```

6.  Create a vector called "years" containing the years when the data were collected, as well as a vector "days" containing the day numbers (1 = first of January).

**Analysis of one year of data**

7.  Create a new vector called "Lobith1916" containing the flow measured at Lobith in 1916.

	```{hint}
	Don't forget that in Python we start counting rows and columns at 0 and not at 1.
	```

8.  Determine the mean and median discharges for this year. Compute also the maximum and minimum values of the discharge.

9.	What are the dates (dd/mm/yyyy) of when these maximum and minimum values at **8** were observed?

	_Answer open questions as remarks in separate lines starting with: '#'_.

**Statistics over the entire dataset**

10. Build a vector of size 1 *×* 366, where each element is the discharge for a given day averaged over 100 years.

11. Plot this vector as a function of the time. Plot in the same figure the maximum and minimum values for each day (use different type of lines an line colors to differentiate the curves). Give an appropriate title to the plot, as well as labels to the axes and a legend to the graph. In which month are the highest mean discharges occurring?

	_Answer open questions as remarks in separate lines starting with: '#'_.

12. Create a vector containing the annual flood discharges for the 100 years of data.

	```{note}
	Annual flood discharge is defined here as the maximum discharge value of each year.
	```

13. Compute the mean annual flood discharge over the entire period.

	```{note}
	The mean annual flood discharge is the mean of all annual flood discharges.
	```

14. Compute the median value of the annual flood discharge data as well as the 75th, 90th and 95th percentiles.

15. We will now use the annual flood discharge data to build a flood-frequency curve, which is a graph showing the relationship between flood magnitude and their recurrence interval for a specified site.

	The recurrence interval $Tr$ of a flood is a statistical measure for how often a flood of a given magnitude $QTr$ is likely to be equalled or exceeded. For instance, the "fifty-year flood" $Q50$ is a discharge value which will on the average be equalled or exceeded once in any fifty-year period.

	Follow the following procedure to compute the recurrence interval:

	-	Create a vector $QTr$ containing the annual flood discharges sorted in ascending order.

	-	Define a vector $R$ of the same length as $QTr$ containing the "indices" of the discharges. The largest value of $QTr$ should have an index equal to 1, and the smallest value an index equal to N, where N is the number of years for which we have flood data (=100).

	-	The recurrence interval $Tr$ (in years) can then be computed using the formula:

		$$
		Tr = (N + 1)/R
		$$ (Eq_1_8)

	Plot the flood-frequency curve, which is the plot of $QTr$ (y-axis) against $Tr$ (x-axis). Use logarithmic axis for a better display of the data. Give an appropriate title to the plot as well as labels to the axes.

16. Read in the figure what is the magnitude of the 50-year and 100-year flood.

	_Answer open questions as remarks in separate lines starting with: '#'_.

	`````{note}
	To be able to read the data in a plot, you are required to plot your figures in a window outside of the plot window ({numref}`Fig. 1`). You can do this by running the following lines in your console:
	````
	import matplotlib
	%matplotlib qt5
	````
	Now if you move the cursor along the plot line, the x-, and y values will be given in the upper right of the window.
	````{note}
	This setting is not temporary. If you want to reset matplotlib so that your plots will occur in the file/variable navigator again, you can run the lines of code in your console:
	```
	import matplotlib as mpl
 	import importlib
	importlib.reload(mpl); importlib.reload(plt);
	```
	````
	`````

```{important}
End of Exercise 4.

_Please add this script **and all files you have imported in your script** to the folder that you will zip and send to us._
```

---

## **PRODUCTS TO HAND IN**

The following exercises have to be handed in for the practical of Chapter 1:

- {ref}`EXERCISE-1.1`

- {ref}`EXERCISE-1.2`

- {ref}`EXERCISE-1.3`

- {ref}`EXERCISE-1.4`

```{important}
We expect the scripts in one zip file named **YourSurname_GEO4-4436_Chapter1**. Also include to your zip file all the separate files that you have imported in your scripts. Moreover, each script should be well labelled and contain the answers to questions as comments. Please note that only the relevant information should be displayed when running the scripts, so do not print every variable.
```

```{important} 
The final grade for the exercises of Chapter 1 is determined as follows:

- Does the program run? (20%)

- Are the comments such that we can understand what the code means and should do? (20%)

- Does the program do what the assignment asked it to do? (20%)

- Are the interpretations and answers to the questions correct? (20%)

- Does the program produce clean figures? (20%)

Each of the sub-grades is graded between 0 (poor) and 5 (well done). The final grade for the exercises of Chapter 1 will make up 5% of the final grade of the course.
```