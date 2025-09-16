# **Chapter 2 - Tests, loops and functions**

```{important}
***NOTES ABOUT CHAPTER 2***

-   The exercises in this chapter will be graded on the following criteria: (1) does the program run? (2) Can we understand it (=well commented)? (3) Does it do the right thing as specified in assignment? See the end of this chapter for the full rubric.

-   You will receive an individual grade based on the competency of your coding and understanding of how this code relates to reality.

-   There are 6 exercises that you must hand that increase in difficulty and required time for completion.

-   Try to schedule your workload accordingly.

-   Please note for this exercise you must submit the scripts (with appropriate comments) as ***.zip*** file which will be used to determine your grade.

-   The deadline for this Chapter is at 9:00 before the start of next practical.
```

(Section-2.1)=
## 2.1 Relational and logical operators

### 2.1.1 Relational operators

A relational operator compares two numbers (or arrays) to determine if a comparison statement (e.g. $a>b$) is true (returning `True`) or false (returning `False`).

-	Try for example in your console:

	```print(3 < 2)```

	```print(3 < 6)```

-	Such comparisons are generally performed on arrays and can be very useful to analyse datasets. Create the following arrays:

	```array_1 = np.array((np.arange(1, 11, 2), np.arange(10, 0, -2)))```

	```array_2 = array_1 < 5```

	`array_2` has the same size as `array_1` but contains only `True` (when the element is smaller than 5) and `False` (when the element is more than or equal to 5).

-	Use the ```sum()``` method to determine how many elements of `array_1` are smaller than 5. What does this produce? This method can be useful to characterize large datasets where it is not possible to count the relational conditions one-by-one.

-	Relational operators can also be used to compare two arrays. Run the following:

	```array_3 = np.array(([3,7,1,8,3], [1,45,0,2,9]))```

	```array_4 = array_1 < array_3```

	Analyse the results. The comparison between `array_1` and `array_3` is done element-by-element. The results are stored in a third array `array_4`, which has the same size as `array_1` and `array_3`. An element of `array_4` is equal to `True` if the comparison is true at this location, and equal to `False` otherwise.

-	These operations can be performed using any operator described in {numref}`Table 7`. Run for instance:

	```array_5 = array_1 == array_3```

	Do you understand the output?

-	Arrays such as `array_2`, `array_4` and `array_5` resulting from relational and {ref}`logical operations <logical_operators>` are called _Boolean_ or "logical" arrays (also see {numref}`Table 2`). They can be used to select elements from another array. Run:

	```array_a = array_1[array_2]```

	The new `array_a` contains the elements of `array_1` corresponding to the locations where the Boolean array `array_2` is `True`. It therefore contains the elements of `array_1 < 5`. The `array_2` can be used to extract elements from any other matrix, as long as all the matrices have the same size. Run for instance:

	```array_b = array_3[array_2]```

	Interpret the resulting `array_b`.

-	It is also possible to write directly (without defining separately the Boolean array `array_2`). Run:

	```array_a = array_1[array_1 < 5]```

	```array_b = array_3[array_3 < 5]```

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

Comparison statements can be combined using the logical operators AND, OR, and NOT ({numref}`Table 8`).

-	Run for instance:

	```array_6 = (array_3 > 2) & (array_3 < 10)```

	`array_6` only returns `True` if the elements of `array_3` are larger than 2 **and** smaller than 10. Only where _both_ statements are `True` will `array_6` contain `True`.

-	When the operator OR is used, the output is `True` if either one or both comparison statements are `True`. Replace the ```&``` in the previous command with the OR symbol ```|``` (called "pipe") and run the edited statement. Did you expect the output?

-	The third logical operator NOT (`~`) can be applied to a Boolean array to return the opposite. Run the following:

	```~array_6```

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

Make a new file called `Exercise1.py` in your working directory, where the commands need to solve the following assignments. The script doesn't have to display the results, but should store all variables. Each of the following tasks can be done with 1 line of code.

1.	Create a NumPy array as follows:

$$
array\_1 = \begin{pmatrix}
  1 & 3 & 5 & 7 & 9\\
  10 & 8 & 6 & 4 & 2
\end{pmatrix}
$$

2.  Compute the average value of the elements of `array_1` that are larger than 2 and smaller than 6. Store this value as `mean_1`.

3.  Create array `array_2`, using relational and logical operators to replace the elements of `array_1 < 3` with 0.

	```{hint}
	You can use Boolean arrays for numeric calculations, where ```False == 0``` and ```True == 1```.
	```

4.  Create array `array_3`, using relational and logical operators to replace the elements of `array_1 >= 9` with double their value.

5.  Provide an example of when this sort of logical testing could be applied in the study of rivers.

	_Include answers to open questions as strings and print them to the console._

```{Important}
End of Exercise 1.

_Please add this script to the folder that you will zip and send to us._
```

---

## 2.2 Flow control

In a simple program, the commands are executed one after the other, independently from the output of the previous one. However, it is sometimes necessary to include some sort of decision-making in the programme. For example, we can decide to compute sediment transport using different predictors depending on the sediment characteristics and flow conditions. The programme should therefore be able to choose the appropriate calculation and forgo the others. It is also sometimes required to repeat a sequence of commands several times, until a certain condition is reached. The order in which commands or groups of commands are executed, is also called the *flow of the program*, and can be controlled in several ways in Python. In the following sections, the three basic flow control methods will be presented: `if`-statements, `for`-loops and `while`-loops.

## 2.3 `if`-statements

**Purpose:**

`if`-statements are used when a decision must be taken depending on the outcome of a comparison statement (also called _conditional expression_). If the comparison is `True`, then the sequence of commands is executed. If the comparison is `False`, the commands are skipped.

**Format:**

The simplest `if`-statements resemble the following:

```
x = 2
if x < 5:
    print('x is less than 5')
```

-	Execute the `if`-statement above and interpret the result.

```{note}
**All** flow control methods (e.g. `if`-statements) require you to indent the sequence of commands that are conditional on your statement, as is shown above. The default for indenting is 1 TAB / 4 spaces.
```

```{note}
As the entire indented block is part of the if-statement, it is not possible to select only the line with your `if`-statement and run it in your console using **F9**. If you want to use **F9**, you will need to select both the `if`-statement and the indented block (you _can_ run lines within the indented block separately, but they will not be dependent on the `if`-statement).
```

-	Replace ```x = 2``` with ```x = 5``` and re-run the programme.

When the programme has to choose between two alternatives, an if-else construction can be used. Read the following code carefully (note that in this example ```Theta``` is a scalar):

```
if Theta < Theta_cr:
    Phi = 0
else:
    Phi = 8 * (Theta - Theta_cr) ** 1.5
```

Based on the outcome of the comparison statement ```Theta < Theta_cr```, either the commands after ```if```, or the commands after ```else``` are executed. This small programme is therefore simply expressing the fact that _if_ the Shields parameter _Theta_ is below a critical Shields value there is no sediment transport predicted (though due to turbulence and other sources of stochasticity there may be transport in reality!) and otherwise the sediment transport is calculated using the MPM predictor, as in {ref}`EXERCISE-1.3`. Note the distinction: the Shields number represents sediment mobility, and the critical Shields number represents the threshold conditions for mobility, _i.e._, the beginning of sediment motion.

If you want to include more comparison statements, you can include as many ```elif``` statements as you want between ```if``` and ```else```:

```
if Comparison_1:
    Statement_1
elif Comparison_2:
    Statement_2
elif Comparison_3:
    Statement_3

...

elif Comparison_n:
    Statement_n
else:
    Statement_final
```

Once the Python interpreter reaches an `if`- or `elif`-statement that evaluates to `True`, all subsequent `elif`- and `else`-statements in the sequence will be skipped. You can define your conditional expressions for these statements using the operators described in {ref}`Section-2.1`.

## 2.4 `for`-loops

**Purpose:**

`for`-loops are used to repeat a command or sequence of commands for a fixed, predetermined number of times.

**Format:**

The general structure of a `for`-loop is as follows:

```
for item in sequence:
    Execute commands
```

-	Let's start with a simple example to understand how these loops are working. Run the following lines and interpret the results:

	```
	for i in range(0, 8):
	    print("Hello, World!")
	```

-	Loops can be used to define lists and arrays. Run the following code:

	```
	my_list = []
	for i in range(1, 10):
	    my_list.append(i ** 2)
	    print(my_list)
	print(my_list)
	```

	Examine the output carefully. Do you understand what happens?

	At each _iteration_ (step/ repetition) of the loop, the value of the item variable (`i`) is updated to the next value in the sequence (`range(1, 10)` in the last example), and the contents of the loop (indented lines) are executed. The loop ends after executing the commands for the last item in the sequence.
	In the first iteration of the example above, `i` gets the value 1. The square of `i` (in this iteration, $1^2$) is appended (added on) to the list stored in `my_list`. The loop repeats this for each whole number up to `i = 9` in the last iteration.

	````{note}
	It is important to first define the variable ```my_list = []``` as an empty list, otherwise it would not be recognized in the `for`-loop.
	````

-	Specifically for lists, you can put the `for`-loop syntax in `[]` to create the same list in a single line. This is called _list comprehension_:

	```
	my_list = [i ** 2 for i in range(1, 10)]
	print(my_list)
	```

	This produces the exact same result, but runs in less than half the time. This is only useful if you are trying to create a list (or if you can get your desired result from the list).

-	Loops can also be nested, as in the following example, where we create a new array and fill it in element-by-element:

	```
	my_array = np.zeros((2, 3))
	for i in range(2):
	    for j in range(3):
	        ij = (i + 1) * (j + 1)
	        my_array[i,j] = ij
	        print(my_array)
	    print(my_array)
	print(my_array)
	```

	In this case, every time ```i``` increases by ```1```, the nested loop is executed three times from ```j = 0``` to ```j = 2```. Run this script to check in which order the array is filled in. Do you understand why?

	````{note}
	The square brackets in ```my_array[i, j]``` are required here to determine the proper index in rows and columns of `my_array`, so that for each iteration, a different place the array is filled.
	````

	```{note}
	In this example, we first defined `my_array` as a 2 × 3 array of zeros and then used a `for`-loop to fill it. This initialising step is important in Python. It pre-allocates memory so that Python knows the size of the array you want and does not need to re-size it every iteration. The programme will therefore run faster, which is important when working with large arrays.
	```

	```{note}
	For nested loops, it is important that each loop has it's own indented block. This can be only another loop.
	```

	````{note}
	In the example above, we defined the ranges with integers (in this case the number of rows for ```i``` (= 2) and number of columns for ```j``` (= 3)). However, this will require updating of your code every time you want to run your calculations with an input array of different size.
	You can automatically find the values you need using the function [`len()`](https://docs.python.org/3/library/functions.html#len) for any object, or the `shape` property of arrays and DataFrames:

	- `len(my_list)` will return the length of the list. You can use this to iterate through the list with `for i in range(len(my_list))`.

	- `len(my_array)` will only return the number of rows in this 2D array (or, more generally, the length of the 1st dimension in a multi-dimensional array).

	- You can get the number of columns in the array by checking the length of a single row, _e.g._, len(my_array[0]).

	- Alternatively, you can find the lengths of all dimensions in the array using `my_array.shape`:

	```
	my_array = np.zeros((2, 3))
	shape = my_array.shape
	for i in range(shape[0]): # iterate over rows
	    for j in range(shape[1]): # iterate over columns
	        ij = (i + 1) * (j + 1) # calculate a value
	        my_array[i, j] = ij # store value in desired place in array
	        print(my_array)
	    print(my_array)
	print(my_array)
	```

	We recommend you _always_ automate as much as possible in your code. This makes it easier to adapt when your task becomes more complex, or you want to reuse your code for a different task.
 
	````

-	`for`-loops can be combined with `if`-statements as in the following example:

	```
	new_array = np.array([2, 1, -4, 23, 0])
	for i in range(len(new_array)):
	    if new_array[i] >= 2:
	        new_array[i] = 3 * new_array[i]
	        print(new_array)
	    print(new_array)
	print(new_array)
	```

	Run this script and interpret the output.

	````{hint}
	The above loops contain a lot of ```print```-statements. This is not useful in the final version of a script, but is a great tool for debugging and understanding what is going on in your loops.
	````

Some additional remarks about `for`-loops:

-   In the first iteration of the `for`-loop, the index variable is assigned the first value in ```range(start, end, increment)```. From the second time onwards, Python automatically assigns to the variable the second value in the range etc. Unless specified otherwise, the start is by default ```0``` and the increment is by default ```1```. So ```range(end)``` will make your loop start at ```0```, with an increment of ```1``` until ```end - 1``` is reached. If you give two input arguments, Python will interpret it as ```range(start, end)```, with the default increment of ```1```.

-   The number of times a loop is executed, equals the number of values in the range.

-   After the loop is finished executing, the loop variable still exists in memory and its value is the last value used inside the loop.

---

(EXERCISE-2.2)=
## **EXERCISE 2 - Radioactive decay of C14**

```{important}
**You are expected to hand in this code.**
```

Make a new file called `Exercise2.py` in your working directory, where the commands need to solve the following assignments.

This exercise deals with the computation of the evolution of Carbon 14 ($^{14}C$) in a sample due to radioactive decay. Every thousand years, a fraction $α$ of $^{14}C$ is lost. This means that, calling $C_0$ the initial mass of $^{14}C$, the mass remaining in the sample will be:

\-	$C_1 = C_0(1 - α)$ in 1 thousand years

\-	$C_2 = C_1(1 - α)$ in 2 thousand years

\-	$C_3 = C_2(1 - α)$ in 3 thousand years

We want to calculate the quantity of $^{14}C$ still in the sample after 25000 years. Write a script which creates a range of $C$ such that its first element ```C[0]``` is the initial amount, ```C[1]``` the amount after 1,000 years etc. The last element of the sequence should contain the amount of $^{14}C$ after 25 thousand years. $C_0 = 0.5\ kg$, $α = 0.117$. You can use the following script lines as a basis for your script:

```
# Initialisation
???
???

# Time in thousands of years
time = np.arange(0, 26)

# Calculate radioactive decay
for i in time:
    ???# Computation of the i^th element of C

# Visualisation
plt.figure()
plt.plot(time, C / C[0])
plt.title('Relative radioactive decay of $^{14}C$ sample')
plt.xlabel('Time ($10^3$ years)')
plt.ylabel('$C_{t} / C_{0}$')
```

Answer the following questions:

1.  Is a for loop or an if statement more appropriate in this situation? Why?

2.  Can you think of an example where an if statement is appropriate but a for loop is not?

3.  Can you think of an example where you need to combine an if statement and for loop?

	_Include answers to open questions as strings and print them to the console._

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

Let's come back to {ref}`EXERCISE-1.3` concerning the analysis of the dataset from [Meyer-Peter and Mueller (1948)](https://repository.tudelft.nl/islandora/object/uuid:4fda9b61-be28-4703-ab06-43cdc2a21bd7?). We observed that part of the data was following a different trend than the others after non-dimensionalisation. A closer look shows that these data points correspond to experiments performed using a very fine sediment ($D_{50}$ = 0.3402 mm). In this case, bedforms probably developed. Therefore, the use of a grain related shear stress $\tau_c$ instead of total shear stress $\tau$ (Eq. {eq}`Eq_1_3`) is more appropriate and might improve the prediction. We again assume that the density of the water $\rho = 1000\ kg\ m^{-3}$ and Earth's gravity acceleration $g = 9.81\ m\ s^{-2}$.

$\tau_c$ is calculated as follows:

$$
\tau_c = \frac{1}{8} \rho f u^2_c = \rho g \left( \frac{u^2}{C^{/2}}\right)
$$ (Eq_2_9)

where $u_c$ is the flow velocity of the current, which we consider equal to the flow velocity $u$ (Eq. {eq}`Eq_1_1`; subscript w could be for orbital velocity amplitude of waves). Note that $C^/$ implies a Chezy for grain friction and is therefore not equal to $C$ (you can therefore not use Eq. {eq}`Eq_1_2` here). Finding a good predictor for the friction factor $f$ or $C^/$ is a challenging problem in civil engineering, because of the interactions between flow, flow turbulence, the added resistance of transported sediment, and most importantly roughness elements such as grains on the bed and bed forms. A parameter such as $f$, $C$ or $C^/$ is therefore commonly used as calibration parameter in flow models, or derived from measurements of other parameters. Therefore, there is a large number of available predictors for $f$, which have applicability ranges determined by the data set they were derived from. Here we use the general and well-verified predictor called the Colebrook-White function, which is semi-empirical and is related to boundary layer theory for flow over rough bed ([Silberman et al., 1963](https://ascelibrary.org/doi/10.1061/JYCEAJ.0000865)):

$$
\sqrt{\frac{8}{f}} = \frac{C^/}{\sqrt{g}} = 5.74 \log_{10} \left( 12.2
\frac{h}{k_s}\right) = 5.74 \log_{10} \left( \frac{h}{k_s}\right)
+6.24
$$ (Eq_2_10)

wherein $k_s$ is the Nikuradse roughness length related to grains, which is approximately the standard deviation of the bed surface elevation at the scale of grains, approximated as:

$$
k_s \approx D_{84} \approx 2.5 D_{50}
$$ (Eq_2_11)

1.  Copy the data file _MPMtransportdata.xls_ into your current working directory and create a new file `Exercise3.py`.

2.  Create a new variable `tau_2` containing the total shear stress $\tau$ when $D_{50}$ >= 1 mm and the grain related shear stress $\tau_c$ otherwise ($D_{50}$ < 1 mm). You can use part of the script you wrote at {ref}`EXERCISE-1.3`.

	```{note}
	[np.log()](https://numpy.org/doc/1.18/reference/generated/numpy.log.html) is natural logarithmic whilst [np.log10()](https://numpy.org/doc/1.18/reference/generated/numpy.log10.html) is base-10 logarithmic.
	```

3.  Calculate the associated Shields parameter $\theta$ for $tau2$ (Eq. {eq}`Eq_1_4`).

4.  Use the function [scatter](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.scatter.html) to plot the Einstein parameter $\phi$ (using the measured transport rates; Eq. {eq}`Eq_1_5`) against the newly computed Shields Parameter. Make the colours again dependent on the [base 10 logarithm](https://numpy.org/doc/stable/reference/generated/numpy.log10.html) of the nondimensionalized grain size $D\ast$ (Bonnefille number; Eq. {eq}`Eq_1_7`) and use the specific gravity of the sediment $s*10$ to set the size of the scatter points.

5.	Now answer the following questions _briefly_:

	1.	Compare the plot you just created with the one you made in {ref}`EXERCISE-1.3`. What do you notice?

	2.	In the previous chapter, you were using the Meyer-Peter and Mueller transport predictor. When is this typically used? In what cases can the MPM predictor NOT be used?

	3.	Is your Shields parameter value reasonable? How does it compare with the total shear stress in the experimental data?

	_Include answers to open questions as strings and print them to the console._

	```{hint}
	Hint: look at your lecture notes and reading list
	```

```{Important}
End of Exercise 3.

_Please add this script to the folder that you will zip and send to us._
```

---

## 2.5 `while`-loops

**Purpose:**

`while`-loops are used to repeat a command or sequence of commands an indefinite number of times until the condition specified by the `while`-statement is no longer satisfied.

**Format:**

The general structure for a `while`-loop is as follows:

When the programme reaches the first line of the block, the conditional expression is checked. If it is `True`, Python executes the sequence of commands. Then Python jumps back to the `while` command and checks the expression agail. If it is still `True`, the commands are executed again. The looping process will stop when the expression becomes `False`.

-	Execute the following script and interpret the output:

	```
	x = 1
	while x < 14:
	    x = x + 4
	```

	How many times are the commands executed and why?

-	Now run:

	```
	x = 1
	while x < 14:
	    x = x - 4
	    print(x)
	```

	Do you understand what is happening?

	```{note}
	To terminate a computation press ![](img/media/image16.png) in your console. This command can be very useful in case of programming errors leading to never-ending loops.

	If you are working in the console or Terminal, you can use the keyboard shortcut Ctrl+C to do the same.
	```

Some additional remarks about `while`-loops:

-   The variables used in the expression must be defined BEFORE the `while`-loop.

-   At least one variable used in expression must change inside the while loop, or you will never exit the loop.

-   After the loop is finished executing, the loop variables still exist in memory and their values are the same as in the final iteration of the `while`-loop.

---

(EXERCISE-2.4)=
## **EXERCISE 4 - Characterize flow in experimental conditions**

```{important}
**You are expected to hand in this code.**
```

Make a new file called `Exercise4.py` in your working directory, where the commands need to solve the following assignments. We consider a laboratory flume, of which the channel width $W = 0.3\ m$ and the slope $S = 0.006\ m\ m^{-1}$. The Nikuradse roughness length $k_s = 0.0013\ m$. Earth's gravity acceleration $g = 9.81\ m\ s^{-2}$. We try to answer the following questions: (1) how deep is the water when the flow discharge $Q = 1 \times 10^{−3}\ m^3\ s^{-1}$? And (2) what will the flow velocity $u$ be at that moment?

This problem will be solved using an iteration process. We start with a first guess of the water depth $h$, and correct it at each loop to make it more accurate. The looping process will stop when the desired accuracy has been reached. Execute the following steps:

-   Importing relevant packages and initialisation of parameters

-   Make a first guess by defining $h$ (such that $h_{min} < h < h_{max}$, with $h_{min} = 0.01$ mm and $h_{max} = 3$ cm). Use `if`-statements to make sure the computation is only executed for these conditions.

-   Define $h_{temp}$ to allow for the first loop to start, e.g. $h_{temp} = 0.9h$. Continue looping as long as the absolute value of $h - h_{temp}$ is larger than $1 \times 10^{−6}\ m$.

-   Computation of velocity $u$ using the Chezy equation (Eq. {eq}`Eq_1_2`).

	```{note}
	Eq. {eq}`Eq_1_2` makes use of the Chezy roughness coefficient $C$, which is equivalent to the Darcy-Weisbach friction coefficient $f$ when calculated as follows:

	$$
	C = \sqrt{\frac{8g}{f}}\\
	$$ (Eq_2_12)

	where $f$ is the friction factor (Eq. {eq}`Eq_2_10`) for total roughness, which is larger than the grain-related roughness used sediment transport calculation. See sections 2.2 and 2.5 in Kleinhans [2005](https://agupubs.onlinelibrary.wiley.com/doi/full/10.1029/2005JE002521#))
	```

-   Update the value of $h_{temp}$ using the principles of mass conservation (Eq. {eq}`Eq_1_1`).

-   Make a new guess for $h$: this should be contained between $h$ and $h_{temp}$, for instance $h = \frac{h+h_{temp}}{2}$.

-   At some point during the iteration, a good estimation of $h$ should be found with a corresponding flow velocity $u$.

Following the protocol (in the bullet points) above, each iteration starts with a new, presumably more accurate, value of the flow depth $h$. We then compute the flow velocity $u$ associated to $h$. This flow velocity is then used to compute a second estimation of the water depth called $h_{temp}$. $h$ and $h_{temp}$ are then compared. They should be nearly equal if our last estimation of $h$ was good enough.

To check your code, run the script with different guesses for the initial water depth $h$. If the iterative loop is correctly coded, it should always return a value for $h$ that's within the defined accuracy range ($1 \times 10^{−6}$ m).

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


	_Include answers to open questions as strings and print them to the console._

```{Important}
End of Exercise 4.

_Please add this script to the folder that you will zip and send to us._
```

---

## 2.6 User-defined functions

We have already discussed {ref}`functions<functions_intro>` that are built into Python or its {ref}`packages<packages_intro>` (e.g. `np.mean`). As you start to write your own programmes, you will need to create your own functions that take one or more input arguments, operate on this input and then return a result (output). When you want to use functions in multiple scripts, it can be helpful to store them in a separate functions file. This is simply an additional `.py` file in your folder which contains only functions.

Functions are organised in the following way:

-	The first line of a function must be of the following form

	```
	def functionname(comma, separated, parameters):
	```

	This line always starts with the reserved word ```def``` (as in "define") followed by the name you want to give your function and which you will use to call this function. Then the input parameters used are given in parentheses, separated by commas.

	```{note}
	You import the functions made in separate .py files the same way you import {ref}`packages<packages_intro>`. For this to work, make sure your functions are located in the same working directory!
	```

-   The definition line of a function should be followed by a so-called _doc string_: a string between three pairs of double quotes (`""" """`), containing (i) a short description of the function aim; and (ii) definitions of the inputs (arguments, args for short) and outputs (what the function _returns_) (see example below).

-   The body of the function can then start. It is made of a succession of commands which ultimately yields the output values using a _return_ statement. As with loops, the lines included inside the function must be indented below the `def` line.

For illustrative purposes, let's start with an example of a function that is so simple that you would normally not write a function for it. Copy the following lines into a new files called `functions.py` and save it in your current directory:

```
import numpy as np

def cylinder_volume(R, h):
	"""Computes the volume of a cylinder.

	Args:
		R (numerical or array): cylinder radius in m or sequence thereof.
		h (numerical or array): cylinder height in m or sequence thereof.
	Returns:
		float or array: cylinder volume in m^3 or sequence thereof.
	"""

	return np.pi * (R ** 2) * h

def cylinder_surface_area(R, h):
	"""Computes the surface area of a cylinder.

	Args:
		R (numerical or array): cylinder radius in m or sequence thereof.
		h (numerical or array): cylinder height in m or sequence thereof.
	Returns:
		float or array: cylinder surface area in m^2 or sequence thereof.
	"""

	# Area of circles at top and base of cylinder
	circ_area = 2 * np.pi * (R ** 2)

	# Area of the side of the cylinder (= lateral area)
	lat_area = 2 * np.pi * R * h

	# Return total area
	return lat_area + circ_area
```

-	Now try to call these functions specifying a radius of ```2``` and a height of ```3```. Do you understand the results?

	````{note}
	The intermediate variables (variables not defined as outputs), such as ```lat_area``` and ```circ_area``` only exist within the function and do not appear in the workspace. The use of functions is therefore important, since it avoids overloading the workspace with variables which are not going to be used later.
	````

-	These functions can be used in a script file as any built-in function in Python. You should be able to run the following script:

	```
	# Computation of volumes and surface areas of cylinder with increasing radius
	import numpy as np
	from functions import *

	# Initialisation
	h = 3 # constant height of the cylinders (m)
	R = np.arange(1, 7) # increasing radius of the cylinders (m)

	# Compute cylinder surface areas
	cylinder_areas = cylinder_surface_area(R, h)
	cylinder_vols = cylinder_volume(R, h)
	```

	Do you understand what is happening?

	```{note}
	The statement `from functions import *` tells the script that we want to be able to refer call each funtions in `functions.py` wihtout having to specify the name of the package they came from, _e.g._, `cylinder_volume`. If we use just `import functions`, we would have to call `functions.cylinder_volume`.

	This can be useful, but also dangerous. If you import functions from multiple packages this way, and they contain a function with the same name, this could cause your programme to break. Proceed with caution.
	```

```{note}
**Reasons why you should use functions in your scripts:**

-   A function can be called several times within a script with different input arguments. This way you do not need to write similar calculations over and over again.

-   Script files in which all the calculations are entered in one unique file can become too long and difficult to understand. By using function files you can better organize your programme and make it easier to read and understand.
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

	Define two functions, one that calculates the total Shields parameter $\theta$ and one that calculates the grain-related Shields parameter $\theta^/$ with Eq. {eq}`Eq_1_4`, using $\tau$ and $\tau_c$, respectively. Think about all the input parameters that are needed.

2.  In {ref}`EXERCISE-1.3` you calculated the non-dimensional **bed load** sediment transport $\phi_b$ using the MPM predictor of [Meyer-Peter and Mueller (1948)](https://repository.tudelft.nl/islandora/object/uuid:4fda9b61-be28-4703-ab06-43cdc2a21bd7?) (Eq. {eq}`Eq_1_6`). A different predictor is proposed by [Engelund & Hansen (1967)](https://repository.tudelft.nl/islandora/object/uuid:81101b08-04b5-4082-9121-861949c336c9) (abbreviated as EH), which is derived for suspension-dominated conditions in flume experiments and therefore accounts for the total load (sum of bed load and suspended load). The EH predictor is calculated as follows:

	$$
	\phi_s = \frac {0.1}{f} \theta^{2.5}
	$$ (Eq_2_13)

	where the lower case “$s$” in $\phi_s$ refers to the Einstein parameter for **suspended load**. As is discussed in {ref}`EXERCISE-2.3`, there are numerous available predictors for $f$. As the EH predictor accounts for suspended load as well, the White-Colebrook function (as used in Eq. {eq}`Eq_2_10`) is not suitable here, because the $k_s$ roughness length of the bed form roughness is unknown. Instead, for the EH predictor, $f$ is calculated using the Darcy-Weisbach equation from other known quantities of the river:

	$$
	u = \sqrt{\frac {8g h S} {f}}
	$$ (Eq_2_14)

	where $g$ is Earth’s gravity acceleration (9.81 m/s<sup>2</sup>), $h$ the flow depth and $S$ the channel slope. This means that the accurateness of the determination of the water surface slope along the channel, which is a small number, determines the uncertainty of the friction factor.

	Define two functions which calculate the non-dimensional sediment transport according to the MPM and EH relations. The input arguments for the MPM function should be the grain-related Shields parameter $\theta^/$ and its critical value $\theta_{cr}$. Choose the adequate arguments for the EH function.

	```{hint}
	For the MPM predictor, do not forget to account for the fact that the sediment is only transported _if_ the critical value ($\theta_{cr} = 0.047$ empirically determined by Meyer-Peter and Mueller) is being exceeded.
	```

3.  Define a function converting non-dimensional transport into dimensional transport $qs$ (in $m^2\ s^{-1}) using Eq. {eq}`Eq_1_5` and call it `conv_phi_qs`.

4.  Make a new file called `Exercise5.py` in your working directory. This script should call all the functions you created above and ultimately plot the predictions of both the MPM and EH predictors against the measured sediment transport rates from the MPM dataset in one figure with log scales. Add a line corresponding to $x = y$ on the figure. Give the figure proper labels, titles and a legend.

5.	Now answer the following questions briefly:

	1.	Why is creating a function outside of your script preferable to creating the function within your script?

	2.	MPM is only valid in certain cases, is this the same for EH? When is MPM used and when is EH used?

	_Include answers to open questions as strings and print them to the console._

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

Let's continue with the dataset of daily-averaged discharge the Rhine you used at {ref}`EXERCISE-1.4`. Create again a new file called `Exercise6.py` in your work-directory, where you load `LobithDischargeData.asc` and the commands needed to solve the following assignments.

```{important}
You cannot do this assignment if you haven't done {ref}`EXERCISE-1.4` of practical 1.
```

### Morphologically relevant statistics of the discharge dataset

1.  Calculate the maximum and minimum daily discharge of the entire dataset.

2.  Calculate the percentage of days in the year 1916 where $Q$ exceeds the mean annual flood discharge calculated in {ref}`EXERCISE-1.4`.

	```{note}
	For leap years there is one day more than for others. Try to deal with this without a for loop.
	```

3.  Compute the same percentage for each year in the dataset and store the results in a single sequence of 100 elements.

4.  Plot the percentage of days where $Q$ exceeds the mean annual flood discharge threshold value as a function of the year (give a title and names to the axes).

5.  Now compute the same percentage but over the whole data set (over the 100 years of data).

6.	The bankfull discharge $Q_b$ is the maximum discharge that a river can have before it starts to flood. Here we assume $Q_b$ to be double the mean value of $Q$ over the entire dataset. Calculate $Q_b$.

7.	We define $Q_c$ as the discharge that occurs within the main river channel. $Q_c$ usually equals $Q$. However, if $Q > Q_b$, then $Q$ consists of a fraction within the main river channel ($= Q_c$), but also a fraction above the floodplain. If we consider a river channel width $W = 550\ m$ and a floodplain width $W_f = 3000\ m$, then we can calculate $Q_c$ as follows:

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

Additional data: channel slope $S = 1.5 \times 10^{-4}\ m\ m^{-1}$; median diameter of the sediment $D_{50} = 2 \times 10^{-3}\ m$; density of the sediment $\rho_s = 2650\ kg\ m^3$; water density $\rho = 1000\ kg\ m^3$.

8.	Calculate the water level from the discharge using the $QH$ (stage discharge) relation given below:

	$$
	H = \frac{384.73 \ln{Q} - 1949.3}{100}
	$$

	where $H$ is the elevation in meters above mean sea level and $Q$ the total discharge. This relation was empirically determined by simultaneous stage (water level) measurement and flow velocity measurement integrated over the width, and may change over time as morphology or roughness changes but we assume this relation to hold for the whole century.

9.	Calculate the water depth $h$ knowing that the average bed elevation is 3 meters above sea level. Does this value seem reasonable? How does it compare to data from the Rhine?

	_Include answers to open questions as strings and print them to the console._

10.	Apply the EH relation {ref}`EXERCISE-2.5` to compute the sediment transport rate associated to the channel discharge $Q_c$. Use the functions you defined in {ref}`EXERCISE-2.5` to calculate the sediment transport $q_S$.

11.	Calculate the sediment discharge $Q_s$ in m<sup>3</sup>/s by multiplying $q_s$ with $W$. Why, or why not, do these values seem reasonable?

	_Include answers to open questions as strings and print them to the console._

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
We expect the scripts in one zip file named **YourSurname_GEO4-4436_Chapter2**. Also include to your zip file all the separate files that you have imported in your scripts. Moreover, each script should be well labelled and print the answers to open questions. Please note that only the relevant information should be displayed when running the scripts, don't just print every variable you declare.
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