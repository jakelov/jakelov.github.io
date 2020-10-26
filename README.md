# Jugs Problem Program



[TOC]


### <u>**Introduction**</u> 

This program solves the famous Jug problem.

You are given two jugs, an **A** sized Jug and a **B** sized jug, the program provides a pump which has unlimited water which you can use to fill the **jug**, and the ground on which water may be poured. You can fill a **jug** from the pump, can pour water out of a **jug** to the ground, or you can pour water from one **jug** to another. The goal of this program is to have both of the Jugs amounts added together to equal a sum that is defined as variable **C**.

This program takes three arguments, referred to as **A**, **B**, and **C**. 

This program also has fields for an iterator (**ptr**), sizes for **A, B, and C** **(aMax, bMax, c)**, a **String** array called **history** , and a two dimensional **Boolean** array called **visited**.

To solve the problem, **A** and **B** both must be summed together to be equivalent to **C**. 

### <u>Installation</u>

1. Download the Jugs.java file [HERE.](https://github.com/jakelov/DataStructures-Algorithms)
2. Load the Jugs.java file into your favorite IDE or Java Compiler.
3. Compile the program (Linux: javac Jugs.java, IDE: F5 or Compile Button).

### <u>Requirements</u>

1. Java JDK 11 or higher.
2. Java Compiler or IDE.

### <u>Usage Instructions</u>

After following the **Installation Steps**

1. After Compiling, your program should generally run if your on an IDE like **Visual Studio Code**. 

   If on Linux, use the command (java Jugs)

2. The program should ask you for input one at a time, **A **is the max size of the first Jug, **B** is the size of the second Jug, and **C** is the value that you want **A and B** to have to add up too with the amounts of water in their Jugs combined.

3. The program will run the Depth-First-Search Algorithm to attempt to find valid solutions to the given input. If a solution is found, it will print *"Yay! Found a solution."* and print the steps the program took to find the solution from **history**.



### <u>Depth-First-Search Algorithm</u>

Using a ***depth-first-search*** algorithm, the program will try every solution possible to find a solution, by emptying jugs, filling jugs, and pouring jugs. The program will track what steps it takes to find a solution in an array labelled **history** as String output. For every *recursive* call to **depth-first-search** (referred to as **dfs**), the algorithm is as follows:

1. Check the variables of **A, B, and C**. If any of them are out of bounds, return *false.* If a solution between **A + B = C** is found, return *true.* If the program has already visited with these values of **A and B**, return *false.*

   > Otherwise, the bounds are fine, we haven't already calculated this subproblem, and there is a possible solution farther down in the recursion. 

2. Mark these values of **A and B** visited in the visited array to true, and make a local variable called **valid** and mark it as false.

3. Call **dfs** on **aMax** and the current value of **B** and set **valid**. This will **FILL** Jug *1* to the max size defined in **aMax**, and keep the current value of **B**. This part will go along the recursion and see if there is a path to the solution with filling Jug 1. If this is a valid operation, push the step onto history.

4. Call **dfs** on **bMax** and the current value of **A** and set **valid**. This will **FILL** Jug *2* to the max size defined in **bMax**, and keep the current value of **B**. This part will go along the recursion and see if there is a path to the solution with filling Jug 2. If this is a valid operation, push the step onto history.

5. Call **dfs** on 0 for Jug 1 and the current value of **B** for Jug 2 and set **valid**. This will **EMPTY** Jug 1 to 0, keep the current value of **B**. This part will go along the recursion and see if there is a path to the solution with emptying Jug 1. If this is a valid operation, push the step onto history.

6. Call **dfs** on 0 for Jug 2 and the current value of **A** for Jug 1 and set **valid**. This will **EMPTY** Jug 2 to 0, keep the current value of **A**. This part will go along the recursion and see if there is a path to the solution with emptying Jug 2. If this is a valid operation, push the step onto history.

   > If we get past this step in the recursion, we know that we cannot reach a solution yet by emptying all the way or filling all the way, so now we must start trying to pour A->B and B->A with different values to see if we can reach a possible solution.

7. Pour **A into B** until the **bMax** constraint is reached or **B** is **empty**, then call **dfs** on these new values of **A** and **B** and set **valid** to this return value from **dfs**. If this is a valid operation, push the step onto history.

8. Pour **B into A** until the **aMax** constraint is reached or **B** is **empty**, then call **dfs** on these new values of **A** and **B** and set **valid** to this return value from **dfs**. If this is a valid operation, push the step onto history.

9. Otherwise, there is no valid steps to take and return *false* as there is no solution. 

   Source Code Example is depicted *below*:[]()

   ![dfs](https://i.gyazo.com/62c5044375597ef74652367504314570.png)

### <u>Examples</u>

Example 1: Solution!

<img src="https://i.gyazo.com/dbb477f83f6d2d1bb71fe96d42e307ef.png" alt="solution" style="zoom:200%;" />

Example 2: A little bit more Steps...

![Steps](https://i.gyazo.com/620d43472dfdd6b3271e8dd37b19c348.png)

Example 3: No Solution / Impossible

<img src="https://i.gyazo.com/38951b0fa733f5a7a77003fd06d1af9a.png" alt="Impossible" style="zoom:200%;" />

### <u>FAQ</u>

1. Question: What values can I put in for **A, B, and C**?

   Answer: As long as they are numerical numbers that are not fractional, the program should work perfectly fine with any values that are **non zero.** 

2. Question: I tried it with ***x,y,z*** arguments and couldn't find a solution! Why is that?

   Answer: The program will try every possible combination of emptying, filling, and pouring. So if no solution is found, there is actually no possible solution!

3. Question: What is the **depth-first-search algorithm** doing that is so important?

   Answer: The **depth-first-search** algorithm is what tries all possible combinations of pouring, emptying, and filling and keeps track of the steps. It is the main driving force of the program!

### <u>Troubleshooting and Contribution</u>

If you are having any issues not outlined in the FAQ, Installation, of Usage Instructions, feel free to contact me at lovingoodja1@appstate.edu with any questions or concerns.

If you would like to contribute to this project and have any suggestions/concerns, feel free to contact me at lovingoodja1@appstate.edu.

### <u>Licensing</u>

Copyright (c) 2020 Jacob Lovingood

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

