Download Link: https://assignmentchef.com/product/solved-csc402-homework6-c-templates-and-operator-overloading
<br>
Setup Stage 1:  Installing a C++ environment

Among your choices for a C++ IDE are JetBrains CLion (similar to JetBrains IntelliJ and JetBrains Rider) or Microsoft Visual Studio (which some of you may have used in CSC 362 or CSC 501).  I’ve test both options and either works fine for our purposes.

To install JetBrains Rider I followed the first 7 minutes of this video:  <a href="https://www.youtube.com/watch?v=HSf-GiJr1Bs">https://www.youtube.com/watch?v=HSf</a><a href="https://www.youtube.com/watch?v=HSf-GiJr1Bs">–</a><a href="https://www.youtube.com/watch?v=HSf-GiJr1Bs">GiJr1Bs</a><a href="https://www.youtube.com/watch?v=HSf-GiJr1Bs">.</a>  The CLion download page is https://www.jetbrains.com/clion/download/ and the video will step you through the setup.  You will have to select which compiler you want to use:  I suggest choosing MinGW.  The process of installing the compiler is integrated into the process of setting up the IDE, as you will see in the video.

<strong> </strong>Setup Stage 2:  Running the examples provided on Canvas

Download from Canvas the following files:  PolynomialOfDouble.h, PolynomialOfDouble.cpp, TestPolynomialOfDouble.cpp, Polynomial.h, TestPolynomial.cpp, MatrixOfDouble.h, MatrixOfDouble.cpp, TestMatrixOfDouble.cpp, and TestMatrix.cpp.

Create a project named PolynomialOfDouble.  With CLion you would do this via File-&gt;’New Project’.  Select  ‘C++ Executable’.  Change the ‘untitled’ part of the location to ‘PolynomialOfDouble’.  The default ‘Language standard’ that CLion selects is C++14, which will work fine for us.  CLion will create a main.cpp file with code to print a “Hello, World!” message.  You can select Build-&gt;’Build PolynomialOfDouble’ to build the project and Run&gt;’Run PolynomialOfDouble’ to run it.  Once that works, copy each of the PolynomialOfDouble files mentioned above and paste them into the PolynomialOfDouble folder in the project explorer.  Right-click on the main.cpp file and ‘Delete’ it.  Double-click the CMakeLists.txt file so that it opens up for editing.  Enter ‘PolynomialOfDouble’, ‘PolynomialOfDouble.cpp’, and ‘TestPolynomialOfDouble.cpp’ in the add_executable macro if they are not there already:

Select Build-&gt;’Rebuild Project’ and run the project.  The code is discussed in one of the videos provided with this assignment.

Creating a project with these files using Microsoft Visual Studio is similar, if you are using that IDE.

Likewise create and run the provided code for a ‘Polynomial’ project, which demonstrates a class template that can be used to represent polynomials over types of values other than doubles only.

Also create and run the provided code for a ‘MatrixOfDouble’ class.

Besides the video on the ‘PolynomialOfDouble’ project, there are also videos on ‘Polynomial’ and ‘MatrixOfDouble’.

Similar to the way in which the Polynomial class template generalizes the PolynomialOfDouble class, your task in this assignment is to write a Matrix class template that generalizes MatrixOfDouble…

<h1>Your assignment:  A Class Template for Matrices</h1>




Create a project called Matrix.  Then, in a file called Matrix.h implement a Matrix class template that takes three template parameters:




<ol>

 <li>the type, T, of the entries</li>

 <li>the number of rows in each matrix</li>

 <li>the number of columns in each matrix</li>

</ol>

The advantage of having the dimensions of a matrix as part of its type is that it allows the <em>compiler</em> to verify that the Matrix operations are applied only to objects with appropriate dimensions.  So, we have two advantages with this approach:  (1) Matrix can be used with a wide variety of element types, and (2) all dimension checking can be done by the compiler – we will never have an exception thrown at runtime due to an attempt to perform an operation on matrices with incompatible dimensions.

The Matrix class template should provide the following operators:




<ol>

 <li>a constructor that takes an optional value and initializes all of the matrix elements to that value; if the optional value is omitted from the call then the value should be the default value for T</li>

</ol>




<ol start="2">

 <li>a [] operator that takes an index i and returns a reference to i-th row of the matrix</li>

 <li>a [] operator like the one above, but declared const and returning a reference to const</li>

 <li>a unary + operator</li>

 <li>a unary – operator</li>

 <li>a += operator</li>

 <li>a -= operator</li>

 <li>a binary + operator</li>

 <li>a binary – operator</li>

 <li>a binary matrix multiplication operator template</li>

</ol>




<ol start="11">

 <li>a print operator</li>

</ol>




You should also provide a global stream output operator:







(“Global means that it is not declared as a member of the class.)




As mentioned above, the number of rows and number of columns are now <em>compile-time constants</em>.  Hence, you do not need the numRows() and numCols() methods as members of the class.  You can remove calls to those from the other methods and replace them with the compile-time constants <em>rows</em> and <em>cols</em>, respectively.




The file MatrixTest.cpp has been provided on Canvas to test your operations.  The correct output from main.cpp is given below:




Testing Matrix&lt;int,_,_&gt; m0:  0 0 0 0 0  0 0 0 0 0 m1:  5 5  5 5 m2:  3 3  3 3 m3:  30 30  30 30 m4:

2 2

2 2

2 2

m4[1][1]: 2

m5[0][0]: 10 m5:  10 1  1 1 m6[0][0]: 22 m6:  22 4

22 4  22 4 m4 + m6:  24 6

24 6  24 6 m6 += m4:  24 6

24 6

24 6 m6 -= m4:  22 4

22 4

22 4

+m4:

2 2

2 2

2 2 -m4:

-2 -2

-2 -2

-2 -2




Testing Matrix&lt;double,_,_&gt; mA:  0.7 0.7 0.7  0.7 0.7 0.7  0.7 0.7 0.7

0.7 0.7 0.7 mB:

0.8 0.8 0.8 0.8 0.8 0.8 0.8 0.8  0.8 0.8 0.8 0.8 0.8 0.8 0.8 0.8

0.8 0.8 0.8 0.8 0.8 0.8 0.8 0.8 mC:

1.68 1.68 1.68 1.68 1.68 1.68 1.68 1.68  1.68 1.68 1.68 1.68 1.68 1.68 1.68 1.68  1.68 1.68 1.68 1.68 1.68 1.68 1.68 1.68

1.68 1.68 1.68 1.68 1.68 1.68 1.68 1.68




Testing Matrix&lt;complex,_,_&gt; mD:

(1.1,-2.1) (1.1,-2.1) (1.1,-2.1) (1.1,-2.1)

(1.1,-2.1) (1.1,-2.1) (1.1,-2.1) (1.1,-2.1)  (1.1,-2.1) (1.1,-2.1) (1.1,-2.1) (1.1,-2.1)

mE:

(0.2,3.5) (0.2,3.5)

(0.2,3.5) (0.2,3.5)

(0.2,3.5) (0.2,3.5)  (0.2,3.5) (0.2,3.5) mD * mE:

(30.28,13.72) (30.28,13.72)

(30.28,13.72) (30.28,13.72)

(30.28,13.72) (30.28,13.72)




Testing Matrix&lt;string,_,_&gt; m7:

Hi Hello Hello Hello

Hello    Hi Hello Hello

Hello Hello    Hi Hello


