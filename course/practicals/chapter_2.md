# **Chapter 2 - Tests, loops and functions**

```{important}
***NOTES ABOUT CHAPTER 2***

-   The exercises in this chapter will be graded on the following criteria: (1) does the program run? (2) Can we understand it (=enough comments)? (3) Does it do the right thing as specified in assignment? See the end of this chapter for the full rubric.

-   You will receive an individual grade based on the competency of your coding and understanding of how this code relates to reality.

-   There are 6 exercises that you must hand that increase in difficulty and required time for completion.

-   Try to schedule your workload accordingly.

-   Please note for this exercise you must submit the scripts (with appropriate comments) as ***.zip*** file which will be used to determine your grade.

-   The deadline for this Chapter is at 9:00 before the start of next practical.
```

(Section-2.1)=
## 2.1 Relational and logical operators

### 2.1.1 Relational operators

A relational operator compares two numbers (or arrays) to determine if a comparison statement (e.g. $a>b$) is true (returning _True_) or false (returning _False_).

-	Try for example in your console:

	```print(3<2)```

	```print(3<6)```

-	Such comparisons are generally performed on arrays and can be very useful to analyse datasets. Define an array $A$ such as:

	```A = (np.arange(1, 11, 2), np.arange(10, 0, -2))```

	```A = np.array(A)```

	```E = (A<5)```

	This command returns a new array $E$, which has the same size as $A$ but contains only _True_ (when the element is smaller than 5) and _False_ (when the element is more than or equal to 5).

-	Use the function ```sum()``` to determine how many elements of A are smaller than 5. What does this produce? This method can be useful to characterize large datasets where it is not possible to count the relational conditions one-by-one.

-	Relational operators can also be used to compare two arrays. Run the following:

	```B = ([3,7,1,8,3], [1,45,0,2,9])```

	```B = np.array(B)```

	```F = (A<B)```

	Analyse the results. The comparison between $A$ and $B$ is done element-by-element. The results are stored in a third array $F$, which has the same size as $A$ and $B$. Each of element of $F$ is equal to _True_ if the comparison is true at this location, and equal to _False_ otherwise.

-	These operations can be performed using any operator described in {numref}`Table 7`. Run for instance:

	```G = A==B```

	Do you understand the output?

-	Arrays such as $E$, $F$ and $G$ resulting from relational and {ref}`logical operations <logical_operators>` are called _Boolean_ or "logical" arrays (also see {numref}`Table 2`). They can be used to select elements from another array. Run:

	```a = A[E]```

	A new vector $a$, is defined and contains the elements of $A$ corresponding to the locations where the Boolean matrix $E$ was equal to _True_. It therefore contains the elements of $A<5$. The matrix $E$ can be used to extract elements from any other matrix, as long as all the matrices have the same size. Run for instance:

	```b = B[E]```

	Interpret the resulting vector $b$.

-	It is also possible to write directly (without defining separately the Boolean array $E$). Run:

	```a = A[A<5]```

	```b = B[B<5]```

````{list-table} Relational operators in Python
:header-rows: 1
:name: Table 7

* - Description
  - Symbol
* - Less than
  - ```<```
* - More than
  - ```>```
* - Less than or equal to
  - ```<=```
* - More than or equal to
  - ```>=```
* - Equal to
  - ```==```
* - Not equal to
  - ```!=```
````

(logical_operators)=
### 2.1.2 Logical operators

Comparison statements can be combined using the logical operators _AND_, _OR_ and _NOT_ ({numref}`Table 8`).

-	Run for instance:

	```H = (B>2)&(B<10)```

	$H$ only returns _True_ if the elements of $B$ are larger than 2 **and** smaller than 10. The two comparison statements should be _True_ at the same time to return a _True_.

-	When the operator _OR_ is used, the output is _True_ if either one or both comparison statements are _True_. Replace the ```&``` in the previous command by the _OR_ symbol ```|``` and run the edited statement. Did you expect the output?

-	The third logical operator _NOT_ can be used to a Boolean array to return the opposite. Run the following:

	```~H```

````{list-table} Logical operators in Python
:header-rows: 1
:name: Table 8

* - Description
  - Symbol
* - AND
  - ```&```
* - OR
  - ```|```
* - NOT
  - ```~```
````

---

(EXERCISE-2.1)=
## **EXERCISE 1 - Relational and logical operations**

```{important}
**You are expected to hand in this code.**
```

Make a new _.py_ file called _Exercise1_ in your work-directory, where the commands need to solve the following assignments. The script doesn't have to display the results, but should store all variables. Each of the following tasks can be done with 1 line of code.

1.	Create the following _numpy_ array $A$:

$$
A = \begin{pmatrix}
  1 & 3 & 5 & 7 & 9\\
  10 & 8 & 6 & 4 & 2
\end{pmatrix}
$$

2.  Compute the average value of the elements of $A$ larger than 2 and smaller than 6. Store this value as $meanA$.

3.  Create array $A2$, using relational and logical operators to replace the elements of $A<3$ by 0.

	```{hint}
	You can use Boolean arrays for numeric calculations, where ```False == 0``` and ```True == 1```.
	```

4.  Create array $A3$, using relational and logical operators to replace the elements of $A>=9$ by 2 times their value.

5.  Provide us with an example of when this sort of logical testing could be applied in the study of rivers.

	_Answer open questions as remarks in separate lines starting with: '#'_.

```{Important}
End of Exercise 1.

_Please add this script to the folder that you will zip and send to us._
```

---

## 2.2 Flow control

In a simple program, the commands are executed one after the other, independently from the output of the previous one. However, it is sometimes necessary to include some sort of decision-making in the programme. For example, we can decide to compute sediment transport using different predictors depending on the sediment characteristics and flow conditions. The programme should therefore be able to choose the appropriate calculation and forgo the others. It is also sometimes required to repeat a sequence of commands several times, until a certain condition is reached. The order in which commands or groups of commands are executed, is also called the *flow of the program*, and can be controlled in several ways in Python. In the following sections, the three basic flow control methods will be presented: if-statements, for-loops and while-loops.

## 2.3 IF-statements

**Purpose:**

If-statements are used when a decision must be taken depending on the outcome of a comparison statement (also called conditional expression). If the comparison is _True_, then the group of commands is executed. If the comparison is _False_, the group of commands is skipped.

**Format:**

The simplest if-statement is the following example:

```
x = 2
if x<5:
    print('x is less than 5')
```

-	Execute the if-statement above and interpret the result.

```{note}
For **all** of the flow control methods (e.g. If-statements), you are required to indent the group of commands that are conditional to your statement, as is shown above. The default for indenting is 1 TAB / 4 spaces.
```

```{note}
As the entire indented block is part of the if-statement, it is not possible to select only the line with your if-statement and run it in your console using **F9**. If you want to use **F9**, you are required to select both the if-statement and the indented block, or run lines within the indented block separately.
```

-	Replace ```x = 2``` by ```x = 5``` and re-run the programme.

When the programme has to choose between two alternatives, an if-else construction can be used. Read carefully the piece of code present below (note that in this example ```Theta``` is a scalar)

```
if Theta<Theta_cr:
    Phi = 0
else:
    Phi = 8*(Theta-Theta_cr)**1.5
```

Based on the outcome of the comparison statement ```Theta<Theta_cr```, either the commands after ```if```, or the commands after ```else``` are executed. This small programme is therefore simply expressing the fact that _if_ the Shields parameter _Theta_ is below a critical Shields value there is no sediment transport predicted (though due to turbulence and other sources of stochasticity there may be transport in reality!) and otherwise the sediment transport is calculated using the MPM predictor {ref}`EXERCISE-1.3`. Note the distinction: the Shields number represents sediment mobility, and the critical Shields number represents the threshold conditions for mobility, a.k.a. the beginning of sediment motion.

If you want to include more comparison statements, you can include as many ```elif``` statements as you want between ```if``` and ```else```:

```
if Comparison_1:
    Statements_1
elif Comparison_2:
    Statements_2
elif Comparison_3:
    Statements_3
elif Comparison_n:
    Statements_n
else:
    Statements_final
```

The general structure of the if-statement is as follows. Only the commands associated with the first true expression are evaluated, the others are skipped. The conditional expressions can be defined using the operators presented in {ref}`Section-2.1`.

## 2.4 FOR-loops

**Purpose:**

For-loops are used to repeat a command or group of commands for a fixed, predetermined number of times.

**Format:**

The general structure of a for-loop is as follows:

```
for index in range:
    Statements to be executed in the for-loop
```

-	Let's start with a simple example to understand how these loops are working. Run the following lines and interpret the results:

	```
	for index in range(0,8):
	    print("Hello, World!")
	```

-	Loops can be used to define lists and arrays. Run the following script:

	```
	t=[]
	for index in range (1,10):
	    t.append(index**2)
	    print(t)
	print(t)
	```

	Examine the output carefully. Do you understand what happens?

	The for-loop above is executed for each index in the range which starts at ```1``` and increases by ```1``` until it reaches ```9```. At each step, the calculation is performed and the result is stored at that index in list $t$. In other words, this small script computes the squares of the numbers from 1 to 9.

	````{note}
	It is important to first define the variable ```t = []``` as an empty list, otherwise it would not be recognized in the for-loop.
	````

-	Instead of running the for-loop above, you can also run:

	```
	loopRange = np.arange(1,10,1)
	t = loopRange**2
	```

	The difference here is the type of variable that is stored in $t$ (which you can easily change using _numpy_), so the two ways of solving the problem are interchangeable. However, to reduce the computation time, it is recommend to avoid loops when it is possible.

-	Loops can also be nested, as in the following example, where we define a new _array_ $B$ and fill it in element-by-element:

	```
	B = np.zeros((2,3))
	for i in range(0,2):
	    for j in range(0,3):
	        ij = (i+1)*(j+1)
	        B[i,j] = ij
	        print(B)
	    print(B)
	print(B)
	```

	In this case, every time ```i``` increases by ```1```, the nested loop is executed three times from ```j = 0``` to ```j = 2```. Run this script to check in which order the array is filled in. Do you understand why?

	````{note}
	The square brackets in ```B[i,j]``` are required here to determine the proper index in rows and columns of $B$, so that for each different iteration, a different element of $B$ is defined.
	````

	```{note}
	In this example, we first defined $B$ as a 2 × 3 array of zeros and then filled it within the for-loop. This initialising step is important in Python. It pre-allocates memory so that Python knows the beginning size of the array you are building up and does not need to re-size it every iteration. The programme will therefore run faster which is important when working with large arrays.
	```

	```{note}
	For nested loops, it is important that each loop has it's own indented block. This can be only another loop.
	```

	````{note}
	In the example above, we defined the ranges with integers (in this case the length of rows for ```i``` (=2) and length of columns for ```j``` (=3). However, this will require updating of your code every time you want to run your calculations with an input array of different size. It is therefore recommended to **ALWAYS** define your ranges using the [len()](https://docs.python.org/3/library/functions.html#len) function. ```len(B)``` will return the number or rows of your array. If you want to return the number of columns, you can obtain that number by running the function by specifying it over one specific row (e.g. ```len(B[0])```. So it is recommended to run the above example as:

	```
	B = np.zeros((2,3))
	for i in range(len(B)):
	    for j in range(len(B[0])):
	        ij = (i+1)*(j+1)
	        B[i,j] = ij
	        print(B)
	    print(B)
	print(B)
	```
 
	````

-	For-loops can be combined with if-statements as in the following example:

	```
	s = np.array([2,1,-4,23,0])
	for i in range(len(s)):
	    if s[i] >= 2:
	        s[i] = 3*s[i]
	        print(s)
	    print(s)
	print(s)
	```

	Run this script and interpret the output.

	````{hint}
	The above loops contain a lot of ```print```-statements. This is not useful in the final version of a script, but is a great tool for debugging and understanding what is going on in your loops.
	````

Some additional remarks about for-loops:

-   In the first iteration of the for-loop, the index variable is assigned the first value in the ```range(start, end, increment)```. From the second time onwards, Python automatically assigns to the variable the second value in the range etc. Unless specified otherwise, the start is by default ```0``` and the increment is by default ```1```. So ```range(end)``` will make your loop start at ```0```, with an increment of ```1``` until ```end``` is reached. If you give two input arguments, Python will interpret it as ```range(start, end)```, with the default increment of ```1```.

-   The number of times a loop is executed, equals the number of values in the range.

-   After the loop is finished executing, the loop variable still exists in memory and its value is the last value used inside the loop.

---

(EXERCISE-2.2)=
## **EXERCISE 2 - Radioactive decay of C14**

```{important}
**You are expected to hand in this code.**
```

Make a new _.py_ file called _Exercise2_ in your work-directory, where the commands need to solve the following assignments.

This exercise deals with the computation of the evolution of Carbon 14 ($C14$) in a sample due to radioactive decay. Each thousand years, a fraction $α$ of $C14$ is lost. This means that, calling $C_0$ the initial mass of $C14$, the mass remaining in the sample will be:

\-	$C_1 = C_0(1 - α)$ in 1 thousand years

\-	$C_2 = C_1(1 - α)$ in 2 thousand years

\-	$C_3 = C_2(1 - α)$ in 3 thousand years

We want to calculate the quantity of $C14$ still in the sample after 25.000 years. Write a script which creates a range of $C$ such that its first element ```C[0]``` is the initial amount, ```C[1]``` the amount after 1,000 years etc. The last element of the vector should contain the amount of $C14$ after 25 thousand years. $C_0 = 0.5$ kg, $α = 0.117$. You can use the following script lines as a basis and complete them:

```
#Initialisation
???
???

#Definition of a time vector in thousand years
t = np.arange(0,26)

#Calculation of the radioactive decay
for i in range (1,26)
    ???#Computation of the i^th element of the vector C

#Visualisation
plt.figure()
plt.plot(t,C/C[0])
plt.title('Relative radioactive decay of C14 sample')
plt.xlabel('t($10^3$ years)')
plt.ylabel('$C_{t}/C_{0}$')
```

Answer the following questions:

1.  Is a for loop or an if loop more appropriate in this situation? Why?

2.  Can you think of an example where an if loop is appropriate but a for loop is not?

3.  Can you think of an example where you need to combine an if and for loop?

	_Answer open questions as remarks in separate lines starting with: '#'_.

```{hint}
Try to Google some examples.
```

```{Important}
End of Exercise 2.

_Please add this script to the folder that you will zip and send to us._
```

---

(EXERCISE-2.3)=
## **EXERCISE 3 - Grain-related sediment transport**

```{important}
**You are expected to hand in this code.**
```

```{important}
You cannot do this assignment if you haven't done {ref}`EXERCISE-1.3` of practical 1.
```

Let's come back to {ref}`EXERCISE-1.3` concerning the analysis of the dataset from [Meyer-Peter and Mueller (1948)](https://repository.tudelft.nl/islandora/object/uuid:4fda9b61-be28-4703-ab06-43cdc2a21bd7?). We observed that part of the data was following a different trend than the others after non-dimensionalisation. A closer look shows that these data points correspond to experiments performed using a very fine sediment ($D_{50}$ = 0.3402 mm). In this case, bedforms probably developed. Therefore, the use of a grain related shear stress $\tau_c$ instead of total shear stress $\tau$ (Eq. {eq}`Eq_1_3`) is more appropriate and might improve the prediction. We again assume that the density of the water $\rho$ is 1000 kg/m<sup>3</sup> and Earth's gravity acceleration $g$ is 9.81 m/s<sup>2</sup>.

$\tau_c$ is calculated as follows:

$$
\tau_c = \frac{1}{8} \rho f u^2_c = \rho g \left( \frac{u^2}{C^{/2}}\right)
$$ (Eq_2_9)

where $u_c$ is the flow velocity of the current, which we consider equal to the flow velocity $u$ (Eq. {eq}`Eq_1_1`; subscript w could be for orbital velocity amplitude of waves). Note that $C^/$ implies a Chezy for grain friction and is therefore not equal to $C$ (you can therefore not use Eq. {eq}`Eq_1_2` here). Finding a good predictor for the friction factor $f$ or $C^/$ is a challenging problem in civil engineering, because of the interactions between flow, flow turbulence, the added resistance of transported sediment, and most importantly roughness elements such as grains on the bed and bed forms. $f$, $C$ or $C^/$ is therefore commonly used as calibration parameter in flow models, or derived from measurements of other parameters in. Therefore, there is a large number of available predictors for $f$, which have applicability ranges determined by the data set they were derived from. Here we use the general and well-verified predictor called the Colebrook-White function, which is semi-empirical and is related to boundary layer theory for flow over rough bed ([Silberman et al., 1963](https://ascelibrary.org/doi/10.1061/JYCEAJ.0000865)):

$$
\sqrt{\frac{8}{f}} = \frac{C^/}{\sqrt{g}} = 5.74 \log_{10} \left( 12.2
\frac{h}{k_s}\right) = 5.74 \log_{10} \left( \frac{h}{k_s}\right)
+6.24
$$ (Eq_2_10)

wherein $k_s$ is the Nikuradse roughness length related to grains, which is approximately the standard deviation of the bed surface elevation at the scale of grains, approximated as:

$$
k_s \approx D_{84} \approx 2.5 D_{50}
$$ (Eq_2_11)

1.  Copy the data file _MPMtransportdata.xls_ in your current work directory and open a new _.py_ file, which you'll save as _Exercise3_.

2.  Create a new vector $tau2$ containing the total shear stress $\tau$ when $D_{50}$ >= 1 mm and the grain related shear stress $\tau_c$ otherwise ($D_{50}$ < 1 mm). You can use part of the script you wrote at {ref}`EXERCISE-1.3`.

	```{note}
	[np.log()](https://numpy.org/doc/1.18/reference/generated/numpy.log.html) is natural logarithmic whilst [np.log10()](https://numpy.org/doc/1.18/reference/generated/numpy.log10.html) is base-10 logarithmic.
	```

3.  Calculate the associated Shields parameter $\theta$ for $tau2$ (Eq. {eq}`Eq_1_4`).

4.  Use the function [scatter](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.scatter.html) to plot the Einstein parameter $\phi$ (using the measured transport rates; Eq. {eq}`Eq_1_5`) against the newly computed Shields Parameter. Make the colours again dependent on the [base 10 logarithm](https://numpy.org/doc/stable/reference/generated/numpy.log10.html) of the nondimensionalized grain size $D\ast$ (Bonnefille number; Eq. {eq}`Eq_1_7`) and use the specific gravity of the sediment $s*10$ to set the size of the scatter points.

5.	Now answer the following questions as brief comments in your scripts:

	1.	Compare the plot you just created with the one you made in {ref}`EXERCISE-1.3`. What do you notice?

	2.	In the previous chapter, you were using the Meyer-Peter and Mueller transport predictor. When is this typically used? In what cases can the MPM predictor NOT be used?

	3.	Is your Shields parameter value reasonable? How does it compare with the total shear stress in the experimental data?

	_Answer open questions as remarks in separate lines starting with: '#'_.

	```{hint}
	Hint: look at your lecture notes and reading list
	```

```{Important}
End of Exercise 3.

_Please add this script to the folder that you will zip and send to us._
```

---

## 2.5 WHILE-loops

**Purpose:**

While-loops are used to repeat a command or group of commands, an indefinite number of times until the condition specified by the while-statement is no longer satisfied.

**Format:**

The general structure for a while-loop is as follows:

When the programme reaches the first line of the block, the conditional expression is checked. If it is _True_, Python executes the group of commands. Then Python jumps back to the while command and checks again the expression, if it is still _True_, the commands are executed again. The looping process will stop when the expression becomes _False_.

-	Execute the following script and interpret the output:

	```
	x=1
	while x<14:
	    x=x+4
	```

	How many times are the commands executed and why?

-	Execute now:

	```
	x=1
	while x<14:
	    x=x-4
	    print(x)
	```

	Do you understand what is happening?

	```{note}
	To terminate a computation press ![](img/media/image16.png) in your console. This command can be very useful in case of programming errors leading to never-ending loops.
	```

Some additional remarks about while-loops:

-   The variables used in the expression must be defined BEFORE the while loop, so you can use it to enter the loop.

-   At least one variable used in expression must change inside the while loop, or you will never exit the loop.

-   After the loop is finished executing, the loop variables still exist in memory and their values are the same as in the final iteration of the while-loop.

---

(EXERCISE-2.4)=
## **EXERCISE 4 - Characterize flow in experimental conditions**

```{important}
**You are expected to hand in this code.**
```

Make a new _.py_ file called _Exercise4_ in your work-directory, where the commands need to solve the following assignments. We consider a laboratory flume, of which the channel width $W = 0.3$ m and the slope $S = 0.006$ m/m. The Nikuradse roughness length $k_s = 0.0013$ m. Earth's gravity acceleration $g$ is 9.81 m/s<sup>2</sup>. We try to answer the following questions: (1) how deep is the water when the flow discharge $Q = 1 × 10^{−3}$ m<sup>3</sup>/s? And (2) what will the flow velocity $u$ be at that moment?

This problem will be solved using an iteration process. We start with a first guess of the water depth $h$, and correct it at each loop to make it more accurate. The looping process will stop when the desired accuracy has been reached. Execute the following steps:

-   Importing relevant packages and initialisation of parameters

-   Make a first guess by defining $h$ (such that $h_{min} < h < h_{max}$, with $h_{min} = 0.01$ mm and $h_{max} = 3$ cm). Use if-statements to make sure the computation is only executed for these conditions.

-   Define $h_{temp}$ to allow for the first loop to start, e.g. $h_{temp} = 0.9h$. Continue looping as long as the absolute value of $h - h_{temp}$ is larger than $1 × 10^{−6}$ m.

-   Computation of velocity $u$ using the Chezy equation (Eq. {eq}`Eq_1_2`).

	```{note}
	Eq. {eq}`Eq_1_2` makes use of the Chezy roughness coefficient $C$, which is equivalent to the Darcy-Weisbach friction coefficient $f$ when calculated as follows:

	$$
	C = \sqrt{\frac{8g}{f}}\\
	$$ (Eq_2_12)

	where $f$ is the friction factor (Eq. {eq}`Eq_2_10`) for total roughness, which is larger than the grain-related roughness used sediment transport calculation. See sections 2.2 and 2.5 in Kleinhans [2005](https://agupubs.onlinelibrary.wiley.com/doi/full/10.1029/2005JE002521#))
	```

-   Update the value of $h_{temp}$ using the principles of mass conservation (Eq. {eq}`Eq_1_1`).

-   Make a new guess for $h$: this should be contained between $h$ and $h_{temp}$, for instance $h = (h+h_{temp})/2$.

-   At some point during the iteration, a good estimation of $h$ should be found with a corresponding flow velocity $u$.

Following the protocol (in the bullet points) above, each iteration starts with a new, presumably more accurate, value of the flow depth $h$. We then compute the flow velocity $u$ associated to $h$. This flow velocity is then used to compute a second estimation of the water depth called $h_{temp}$. $h$ and $h_{temp}$ are then compared. They should be nearly equal if our last estimation of $h$ was good enough.

To check your code, run the script with different guesses for the initial water depth $h$. If the iterative loop is correctly coded, it should always return a value for $h$ that's within the defined accuracy range ($1 × 10^{−6}$ m).

````{hint}
When subtracting $h$ and $h_{temp}$, use ```abs()``` to avoid unending loops.
````

```{hint}
When something goes wrong, print $h_{temp}$ and possibly other parameters during each iteration so you can see what happens over time.
```

-	Now answer the following questions as comments in your script:

	1.  Why are we using a while-loop in this situation?

	2.  What is happening inside the while-loop? You can use the previous hint for this as well.

	3.  How did you determine your first guess value? What effect does increasing this value or decreasing this value have on the outcome?

	4.  Is your calculated flow velocity reasonable compared with nature?


	_Answer open questions as remarks in separate lines starting with: '#'_.

```{Important}
End of Exercise 4.

_Please add this script to the folder that you will zip and send to us._
```

---

## 2.6 User-defined functions

We have already discussed {ref}`functions<functions_intro>` that are built into Python or its {ref}`packages<packages_intro>` (e.g. np.mean). As you start to write your own programmes, you will need to create your own functions that take one or more input arguments, operate on this input and then return a result (output). Function files are simply text files with a _.py_ extension and can be written as script files using the Python editor.

They are organised in the following way:

-	The first line of a function must be of the following form

	```
	def functionname(parameter list):
	```

	This line always starts with the word ```def```, followed by the name you want to gave your function and which you will use to call this function. Then the input parameters used are given in brackets, separated by commas.

	```{note}
	You import the functions made in separate .py files the same way you import {ref}`packages<packages_intro>`. Make sure your functions are therefore located in the same working directory!
	```

-   The definition line of a function file must be followed by some comments, containing at least the following fields: (i) a short description of the function aim; and (ii) definitions of the input and output variables (see example below).

-   The body of the function can then start. It is made of a succession of commands which ultimately defines the output variables using a _return_ statement. These commands have to be an indented block from the function.

For illustrative purposes, let's start with an example of a function that is so simple that you would normally not write a function for it. Copy the following lines into two new _.py_ files and save them in your current directory as *cyclinder_volume.py* and *cylinder_surface_area.py*:

-	*cylinder_volume.py*:

	```
	#Function to compute the volume of a cylinder
	def cylinder_volume(R,h):
	# input R radius(m)
	# h cylinder height(m)
	    import numpy as np
	    return np.pi*(R**2)*h
	```

-	*cylinder_surface_area.py*:

	```
	#Function to compute the surface area of a cylinder
	def cylinder_surface_area(R,h):
	# input R radius(m)
	# h cylinder height(m)
	    import numpy as np
 	    # first calculate the area of the circles at the top and base
	    a_circ = 2*np.pi*(R**2)
	    # then calculate the area of the side of the cylinder (= lateral area)
	    a_lat = 2*np.pi*R*h
  	    # return the entire cylinder area as a sum of both
	    return a_lat+a_circ
	```

-	Now try call upon these functions specifying a radius of ```2``` and a height of ```3```. Do you understand the results?

	````{note}
	The intermediate variables (=variables not defined as outputs), such as ```a_lat``` and ```a_circ``` only exist within a function and do not appear in the workspace. The use of functions is therefore important since it avoids to overload the workspace with variables which are not going to be used later.
	````

-	These functions can be used in a script file as any built-in function in Python. Modify the function files of *cylinder_volume.py* and *cylinder_surface_area.py* so it allows for non-scalar input arguments. You should then be able to run the following script:

	```
	#Computation of volumes and surface areas of cylinder with increasing radius
	import numpy as np
	import os
	from cylinder_surface_area import cylinder_surface_area as CSA
	from cylinder_volume import cylinder_volume as CV
	#Initialisation
	h = 3 #Constant height of the cylinders(m)
	R = np.arange(1,7) #Increasing radius of the cylinders(m)

	#Computation of the areas S_all and volumes V_all
	S_all = CSA(R,h)
	V_all = CV(R,h)
	```

	Do you understand what is happening?

```{note}
**Reasons why you should use functions in your scripts:**

-   Script files in which all the calculations are entered in one unique file can become too long and difficult to understand. By using function files you can better organize your programme and make it easier to read and understand.

-   A function can be called several times within a script with different input arguments. This way you do not need to write similar calculations over and over again.
```

---

(EXERCISE-2.5)=
## **EXERCISE 5 - Comparison of sediment transport predictors**

```{important}
**You are expected to hand in this code and all the functions you created.**
```

We continue from {ref}`EXERCISE-2.3`. Here, the objective is to compare the sediment transport measured by Meyer-Peter and Mueller in their flume experiments to the predictions given by the _MPM_ and the _EH_ predictors (semi-empirical model formulations), using several user-defined functions.

```{important}
You cannot do this assignment if you haven't done {ref}`EXERCISE-1.3` of practical 1 and {ref}`EXERCISE-2.3` of practical 2.
```

1.	In {ref}`EXERCISE-1.3`, we introduced the total shear stress $\tau$ (Eq. {eq}`Eq_1_3`) and in {ref}`EXERCISE-2.3` the grain related shear stress $\tau_c$ (Eq. {eq}`Eq_2_9`). The total shear of the flow is related to the total friction of the channel. For the computation of near-bed sediment transport, however, only the shear force on the grains is needed. [Einstein (1950)](https://books.google.nl/books?hl=nl&lr=&id=xIhtv2wpR9oC&oi=fnd&pg=PA1&dq=Einstein,+H.+(1950)), [Soulsby (1997)](https://www.icevirtuallibrary.com/doi/abs/10.1680/doms.25844.fm), and others conceptually divided the total shear stress $\tau$ into bed form-related shear stress $\tau_b$ and grain-related shear stress $\tau_c$, of which the latter is relevant for sediment transport.

	Create two functions, one that calculates the total Shields parameter $\theta$ and one that calculates the grain-related Shields parameter $\theta^/$ with Eq. {eq}`Eq_1_4`, using $\tau$ and $\tau_c$, respectively. Think about all the input parameters that are needed.

2.  In {ref}`EXERCISE-1.3` you calculated the non-dimensional **bed load** sediment transport $\phi_b$ using the MPM predictor of [Meyer-Peter and Mueller (1948)](https://repository.tudelft.nl/islandora/object/uuid:4fda9b61-be28-4703-ab06-43cdc2a21bd7?) (Eq. {eq}`Eq_1_6`). A different predictor is proposed by [Engelund & Hansen (1967)](https://repository.tudelft.nl/islandora/object/uuid:81101b08-04b5-4082-9121-861949c336c9) (abbreviated as EH), which is derived for suspension-dominated conditions in flume experiments and therefore accounts for the total load (sum of bed load and suspended load). The EH predictor is calculated as follows:

	$$
	\phi_s = \frac {0.1}{f} \theta^{2.5}
	$$ (Eq_2_13)

	where the lower case “$s$” in $\phi_s$ refers to the Einstein parameter for **suspended load**. As is discussed in {ref}`EXERCISE-2.3`, there are numerous available predictors for $f$. As the EH predictor accounts for suspended load as well, the White-Colebrook function (as used in Eq. {eq}`Eq_2_10`) is not suitable here, because the $k_s$ roughness length of the bed form roughness is unknown. Instead, for the EH predictor, $f$ is calculated using the Darcy-Weisbach equation from other known quantities of the river:

	$$
	u = \sqrt{\frac {8g h S} {f}}
	$$ (Eq_2_14)

	where $g$ is Earth’s gravity acceleration (9.81 m/s<sup>2</sup>), $h$ the flow depth and $S$ the channel slope. This means that the accurateness of the determination of the water surface slope along the channel, which is a small number, determines the uncertainty of the friction factor.

	Create two functions which calculate the non-dimensional sediment transport according to the MPM and EH relations. The input arguments for the MPM function should be the grain-related Shields parameter $\theta^/$ and its critical value $\theta_{cr}$. Choose the adequate arguments for the EH function.

	```{hint}
	For the MPM predictor, do not forget to account for the fact that the sediment is only transported _if_ the critical value ($\theta_{cr} = 0.047$ empirically determined by Meyer-Peter and Mueller) is being exceeded.
	```

3.  Create a function converting non-dimensional transport into dimensional transport $qs$ (in m<sup>2</sup>/s) using Eq. {eq}`Eq_1_5` and call it *conv_phi_qs.py*.

4.  Make a new _.py_ file called _Exercise5_ in your work-directory. This script should call all the functions you created above and ultimately plots the predictions of both the MPM and EH predictors against the measured sediment transport rates from the MPM dataset in one figure with log scales. Add a line corresponding to x = y on the figure. Give the figure proper labels, titles and a legend.

5.	Now answer the following questions as brief comments in your script:

	1.	Why is creating a function outside of your script preferable to creating the function within your script?

	2.	MPM is only valid in certain cases, is this the same for EH? When is MPM used and when is EH used?

	_Answer open questions as remarks in separate lines starting with: '#'_.

```{Important}
End of Exercise 5.

_Please add this script and all the functions to the folder that you will zip and send to us._
```

---

(EXERCISE-2.6)=
## **EXERCISE 6 - Sediment transport of the Rhine at Lobith**

```{important}
**You are expected to hand in this code.**
```

Let's continue with the dataset of daily-averaged discharge the Rhine you used at {ref}`EXERCISE-1.4`. Create again a new _.py_ file called _Exercise6_ in your work-directory, where you load _LobithDischargeData.asc_ and the commands needed to solve the following assignments.

```{important}
You cannot do this assignment if you haven't done {ref}`EXERCISE-1.4` of practical 1.
```

### Morphologically relevant statistics of the discharge dataset

1.  Calculate the maximum and minimum daily discharge of the entire dataset.

2.  Calculate the percentage of days in the year 1916 where $Q$ exceeds the mean annual flood discharge calculated in {ref}`EXERCISE-1.4`.

	```{note}
	For leap years there is one day more than for others. Try to deal with this without a for loop.
	```

3.  Compute the same percentage for each year in the dataset and store the results in a single vector of 100 elements.

4.  Plot the percentage of days where $Q$ exceeds the mean annual flood discharge threshold value as a function of the year (give a title and names to the axis).

5.  Now compute the same percentage but over the whole data set (over the 100 years of data).

6.	The bankfull discharge $Q_b$ as the maximum discharge that a river can have before it starts to flood. Here we assume $Q_b$ to be 2 times the mean value of $Q$ over the entire dataset. Calculate $Q_b$.

7.	We define $Q_c$ as the discharge that occurs within the main river channel. $Q_c$ usually equals $Q$. However, if $Q > Q_b$, then $Q$ consists of a fraction within the main river channel ($= Q_c$), but also a fraction above the floodplain. If we consider a river channel width $W = 550$ m and a floodplain width $W_f = 3000$ m, then we can calculate $Q_c$ as follows:

	$$
	Q_c =
	\begin{cases}
		Q, & Q<=Q_b \\
		Q_b + (Q - Q_b) * (W / W_f), & Q > Q_b
	\end{cases}
	$$

	Compute $Q_c$ for the entire dataset.

	```{hint}
	$Q_c$ has the same size as $Q$.
	```

### Sediment transport calculations

Additional data: channel slope $S = 1.5 × 10^{-4}$ m/m; median diameter of the sediment $D_{50} = 2 × 10^{-3}$ m; density of the sediment $\rho_s = 2650$ kg/m<sup>3</sup>; water density $\rho = 1000$ kg/m<sup>3</sup>.

8.	Calculate the water level from the discharge using the $QH$ (stage discharge) relation given below:

	$$
	H = (384.73 \ln{Q} - 1949.3)/100
	$$

	where $H$ is the elevation in meters above mean sea level and $Q$ the total discharge. This relation was empirically determined by simultaneous stage (water level) measurement and flow velocity measurement integrated over the width, and may change over time as morphology or roughness changes but we assume this relation to hold for the whole century.

9.	Calculate the water depth $h$ knowing that the average bed elevation is 3 meters above sea level. Does this value seem reasonable? How does it compare to data from the Rhine?

	_Answer open questions as remarks in separate lines starting with: '#'_.

10.	Apply the EH relation {ref}`EXERCISE-2.5` to compute the sediment transport rate associated to the channel discharge $Q_c$. Use the functions you defined in {ref}`EXERCISE-2.5` to calculate the sediment transport $q_S$.

11.	Calculate the sediment discharge $Q_s$ in m<sup>3</sup>/s by multiplying $q_s$ with $W$. Why, or why not, do these values seem reasonable?

	_Answer open questions as remarks in separate lines starting with: '#'_.

12.	Plot $Q_s$ as a function of $Q_c$ for the whole dataset. Choose the best representation (log axis or not). (Conclude for yourself: how many times smaller than the flow discharge is the sediment discharge in this river?)

13.	Calculate the average volume of sediment transported through Lobith per year. To do that, you should first compute the total volume of sediment transported through Lobith for each year of the dataset and then average those values.

```{Important}
End of Exercise 6.

_Please add this script to the folder that you will zip and send to us._
```

## **PRODUCTS TO HAND IN**

The following exercises have to be handed in for the practical of Chapter 2:

- {ref}`EXERCISE-2.1`

- {ref}`EXERCISE-2.2`

- {ref}`EXERCISE-2.3`

- {ref}`EXERCISE-2.4`

- {ref}`EXERCISE-2.5`

- {ref}`EXERCISE-2.6`

```{important}
We expect the scripts in one zip file named **YourSurname_GEO4-4436_Chapter2**. Also include to your zip file all the separate files that you have imported in your scripts. Moreover, each script should be well labelled and contain the answers to questions as comments. Please note that only the relevant information should be displayed when running the scripts, so do not print every variable.
```

```{important} 
The final grade for the exercises of Chapter 2 is determined as follows:

- Does the program run? (20%)

- Are the comments such that we can understand what the code means and should do? (20%)

- Does the program do what the assignment asked it to do? (20%)

- Are the interpretations and answers to the questions correct? (20%)

- Does the program produce clean figures? (20%)

Each of the sub-grades is graded between 0 (poor) and 5 (well done). The final grade for the exercises of Chapter 2 will make up 5% of the final grade of the course.
```