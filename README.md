Download Link: https://assignmentchef.com/product/solved-cs204-homework-4-python-program-file-indentation-check-with-stacks
<br>
<strong>Introduction </strong>

In this homework, you are asked to implement a program which analyzes whether a given .py file (python source code) contains indentation errors. Hence, you must check if each line can be bounded by an indentation level correctly. To achieve this, the program must use a

<em>stack </em>data structure. The details of the methods, algorithms and the data structure to be used will be given in the subsequent sections of this homework specification.




<strong>Program Flow, Input and Output </strong>

At first, the program asks for the name of the .py file to be analyzed. You should check whether the file has been opened successfully or not. In case of a file open failure, ask for a different file name until it is opened successfully. While reading the content of the .py file, your program is going to print the content information and indentation correctness for each line. As soon as a syntax error related to indentation is detected, your program will display an error message and will stop without checking the rest of the file. If all of the lines are checked correctly, then a general success message will be displayed at the end.




In Python language, code blocks are grouped according to their indentation levels, instead of using symbols like { and }, which are used to identify blocks in C++. Thus, there are specific rules for indentation in Python.




<strong>Indentation Rules to be Checked by Your Program and Other Assumptions: </strong>

<ol>

 <li>Initial indentation level has depth zero (i.e. there must not be any leading blanks to start with).</li>

 <li>Code lines belonging to the same indentation level (i.e. the code lines of the same block) must have the same number of spaces at the beginning of the lines.</li>

 <li>The lines proceeding a keyword-containing line (keywords are explained below) must start a new indentation level. This new level is going to have a greater depth than the previous level. As long as the new level has more spaces than the previous one, new level depth is going to be valid.</li>

 <li>A keyword-containing line is defined as a line that starts with a keyword (after some blanks, if any). You are responsible for checking 5 keywords, which are if, else, elif, for and while.</li>

 <li>You are not required to check the syntax related to the correctness of the order of these keywords. For example, your program will not check whether an else or elif has a preceding if.</li>

 <li>It is possible to have nested blocks. That means, before ending a block, a new block may start. This way, nested indentation levels may be created.</li>

 <li>When a block is finished, a python code may continue with one of the outer blocks (i.e. one of the previous indentation levels; one or more previous levels can be gone back in one line).</li>

 <li>You are not going to check for Python syntax errors other than indentation errors. For instance, checking for incomplete assignment (x =), is not in the scope of this homework (we are not going to create a compiler J).</li>

 <li>You can assume that the input file does not contain any comments and does not contain any empty lines.</li>

 <li>You can assume that no tab characters are used in .py files. Indentation level depths are counted by the number of leading spaces (blank characters) at the beginning of the lines.</li>

</ol>

<strong> </strong>

<strong>Data Structure to be Used </strong>

<strong>In this homework you are going to use <em>STACKS ONLY</em></strong>. It is used to keep track of the indentation level depth of the input .py file. The stack class that we provide together with the lecture notes, <strong>DynIntStack.cpp</strong> and <strong>DynIntStack.h</strong>, must be used in your program and they <strong>must not be modified</strong>. Your main program must be written as another cpp file.




You should delete all of the remaining nodes in the stack before finishing the program.




<u>You cannot use any other multiple data container (vector, built-in array, dynamic array, other</u> <u>linked lists, etc.) in this homework.</u>




<strong>Algorithmic Hint </strong>

You will only need a single <em>stack</em> to keep track of the indentation levels. At first, push the initial indentation level, which is 0, to the stack. Then,




process the input file line by line.

if the current line contains more leading spaces than the current indentation level and a KEYWORD is observed just BEFORE this line.

the line is correctly indented with a new indentation level. Push the new indentation level (number of leading spaces of the current line) to the stack.

else if a KEYWORD is observed just BEFORE this line, but the amount of spaces at the beginning of this line is less than or same as the current indentation level,  this is an error case.

else if NO KEYWORD is observed just BEFORE this line and the current indentation level has more spaces than the current line’s number of leading spaces,  pop the current indentation level(s) from the stack <u>until</u> a correct block is found. If a correct level cannot be found, then this is an error.

else if NO KEYWORD is observed just BEFORE this line and the current indentation level has less spaces than the current line’s number of leading spaces,  this is an error case.

else if NO KEYWORD is observed just BEFORE this line and the current indentation level has the same amount spaces as the current line’s number of leading spaces,  the line is correctly indented and belongs to current indentation level.




<strong>Sample Runs </strong>

Some sample runs are given below, but these are not comprehensive, therefore you have to consider <strong>all possible cases</strong> to get full mark. The sample input files are provided in the .zip package of this homework.

<strong> </strong>

<strong> </strong>

<strong>Sample Run 1: </strong>

<strong>File: t1.py </strong>

<table width="673">

 <tbody>

  <tr>

   <td width="673">import sys  import random<sub>             </sub> ans = True<sub>    </sub> while ans:question = raw_input(“Ask the magic 8 ball a question: (press enter to quit) “)      answers = random.randint(1,8)      if question == “”:sys.exit()      elif answers == 1:print “It is certain”      elif answers == 2:print “Outlook good”      elif answers == 3:<sup>          </sup>print “You may rely on it”     <sup> </sup>elif answers == 4:<sup>        </sup>print “Ask again later”     <sup> </sup>elif answers == 5:                <sup>  </sup>print “Concentrate and ask again” elif answers == 6: print “Reply hazy, try again” elif answers == 7: print “My reply is no” <sub> </sub>elif answers == 8:<sub>        </sub>print “My sources say no” print “End”</td>

  </tr>

 </tbody>

</table>







Please enter the file name that is going to be analyzed.

<strong>t1.py </strong>

Starting file analysis…

Initial indentation level is pushed to the stack as 0.




Line number: 1

Line: import sys

0 number of spaces observed before the start of the line. Current Level = 0 This Line = 0 Line belongs to current block.




Line number: 2

Line: import random

0 number of spaces observed before the start of the line. Current Level = 0 This Line = 0 Line belongs to current block.




Line number: 3

Line: ans = True

0 number of spaces observed before the start of the line.

Current Level = 0 This Line = 0

Line belongs to current block.




Line number: 4

Line: while ans:

0 number of spaces observed before the start of the line. Current Level = 0 This Line = 0 Line belongs to current block.

Keyword while found on this line.




Line number: 5

Line:     question = raw_input(“Ask the magic 8 ball a question: (press enter to quit) “) 4 number of spaces observed before the start of the line.

This line proceeds a keyword containing line.

Current Level = 0 This Line = 4

Line correct. Depth 4 added to the stack.




Line number: 6

Line:     answers = random.randint(1,8)

4 number of spaces observed before the start of the line. Current Level = 4 This Line = 4 Line belongs to current block.




Line number: 7

Line:     if question == “”:

4 number of spaces observed before the start of the line. Current Level = 4 This Line = 4 Line belongs to current block.

Keyword if found on this line.




Line number: 8

Line:         sys.exit()

8 number of spaces observed before the start of the line.

This line proceeds a keyword containing line.

Current Level = 4 This Line = 8

Line correct. Depth 8 added to the stack.




Line number: 9

<h1><a name="_Toc22220"></a>Line:     elif answers == 1:</h1>

4 number of spaces observed before the start of the line.

<h1><a name="_Toc22221"></a>Current Level = 8 This Line = 4</h1>

<h1><a name="_Toc22222"></a>Current line is smaller than Current indentation level; checking if line belongs to outer indentation.</h1>

Current Level = 4 This Line = 4

<h1><a name="_Toc22223"></a>Line belongs to outer block. Keyword elif found on this line.</h1>




<h1><a name="_Toc22224"></a>Line number: 10</h1>

Line:         print “It is certain”

8 number of spaces observed before the start of the line.

This line proceeds a keyword containing line.

Current Level = 4 This Line = 8

Line correct. Depth 8 added to the stack.




Line number: 11

Line:     elif answers == 2:

4 number of spaces observed before the start of the line.

Current Level = 8 This Line = 4

Current line is smaller than Current indentation level; checking if line belongs to outer indentation.

Current Level = 4 This Line = 4

Line belongs to outer block.

Keyword elif found on this line.




Line number: 12

Line:         print “Outlook good”

8 number of spaces observed before the start of the line.

This line proceeds a keyword containing line.

Current Level = 4 This Line = 8

Line correct. Depth 8 added to the stack.




Line number: 13

<a href="#_Toc22220">Line:     elif answers == 3:                                                                                                                   </a>

<a href="#_Toc22221">Current Level = 8 This Line =                                                                                                              4 </a>

<a href="#_Toc22222">Current line is smaller than Current indentation level; checking if line belongs to outer indentation. Current Level = 4 This Line =                                                                                                                                       4 </a>

<a href="#_Toc22223">Line belongs to outer block. Keyword elif found on this line.                                                                        </a>

<a href="#_Toc22224">Line number:                                                                                                                                  14 </a>




4 number of spaces observed before the start of the line.

Line:                                                  print “You may rely on it” 49 number of spaces observed before the start of the line.

This line proceeds a keyword containing line.

Current Level = 4 This Line = 49

Line correct. Depth 49 added to the stack.




Line number: 15

Line:     elif answers == 4:

4 number of spaces observed before the start of the line.

Current Level = 49 This Line = 4

Current line is smaller than Current indentation level; checking if line belongs to outer indentation. Current Level = 4 This Line = 4 Line belongs to outer block.

Keyword elif found on this line.




Line number: 16

Line:         print “Ask again later”

8 number of spaces observed before the start of the line.

This line proceeds a keyword containing line.

Current Level = 4 This Line = 8

Line correct. Depth 8 added to the stack.




Line number: 17

Line:     elif answers == 5:

4 number of spaces observed before the start of the line.

Current Level = 8 This Line = 4

Current line is smaller than Current indentation level; checking if line belongs to outer indentation. Current Level = 4 This Line = 4

Line belongs to outer block.

Keyword elif found on this line.




Line number: 18

Line:                print “Concentrate and ask again” 15 number of spaces observed before the start of the line.

This line proceeds a keyword containing line.

Current Level = 4 This Line = 15

Line correct. Depth 15 added to the stack.




Line number: 19

Line:     elif answers == 6:

4 number of spaces observed before the start of the line.

Current Level = 15 This Line = 4

Current line is smaller than Current indentation level; checking if line belongs to outer indentation. Current Level = 4 This Line = 4 Line belongs to outer block.

Keyword elif found on this line.




Line number: 20

Line:           print “Reply hazy, try again”

10 number of spaces observed before the start of the line. This line proceeds a keyword containing line.

Current Level = 4 This Line = 10

Line correct. Depth 10 added to the stack.




Line number: 21

Line:     elif answers == 7:

4 number of spaces observed before the start of the line.

Current Level = 10 This Line = 4

Current line is smaller than Current indentation level; checking if line belongs to outer indentation. Current Level = 4 This Line = 4

Line belongs to outer block.

Keyword elif found on this line.




Line number: 22

Line:                         print “My reply is no”

24 number of spaces observed before the start of the line.

This line proceeds a keyword containing line.

Current Level = 4 This Line = 24

Line correct. Depth 24 added to the stack.




Line number: 23

Line:     elif answers == 8:

4 number of spaces observed before the start of the line.

Current Level = 24 This Line = 4

Current line is smaller than Current indentation level; checking if line belongs to outer indentation. Current Level = 4 This Line = 4 Line belongs to outer block.

Keyword elif found on this line.




Line number: 24

Line:         print “My sources say no”

8 number of spaces observed before the start of the line.

This line proceeds a keyword containing line.

Current Level = 4 This Line = 8

Line correct. Depth 8 added to the stack.




Line number: 25

Line: print “End”

0 number of spaces observed before the start of the line.

Current Level = 8 This Line = 0

Current line is smaller than Current indentation level; checking if line belongs to outer indentation.

Current Level = 4 This Line = 0

Current line is smaller than Current indentation level; checking if line belongs to outer indentation. Current Level = 0 This Line = 0 Line belongs to outer block.




Finished file analysis. File structure is correct!

Stack emptied and program ending.




<strong>Sample Run 2: </strong>

<strong>File: t2.py </strong>




<strong> </strong>  if error:print “wrong start”

<strong> </strong> <sub>print “error”</sub>

<strong> </strong>

Please enter the file name that is going to be analyzed.

<strong>t2.txt </strong>

Unable to open file please enter a different file name. <strong>t2.cpp </strong>

Unable to open file please enter a different file name.

<strong>t2.py </strong>

Starting file analysis…

Initial indentation level is pushed to the stack as 0.




Line number: 1

Line:   print “wrong start”

2 number of spaces observed before the start of the line. Current Level = 0 This Line = 2

Incorrect file structure.

Current line cannot be greater than the Current indentation level. Stopping file analysis…




Stack emptied and program ending.

<strong> </strong>

<strong>Sample Run 3: </strong>

<strong>File: t3.py </strong>




<table width="386">

 <tbody>

  <tr>

   <td width="386"><strong> </strong>line_start = 0 <strong> </strong>if line_start == 0<strong><sub> </sub></strong> elseline_start = 1<strong> </strong>       print “error” <strong> </strong> print “here”</td>

  </tr>

 </tbody>

</table>

<strong> </strong>

Please enter the file name that is going to be analyzed.

<strong>t3.py </strong>

Starting file analysis…

Initial indentation level is pushed to the stack as 0.




Line number: 1

Line: line_start = 0

0 number of spaces observed before the start of the line. Current Level = 0 This Line = 0 Line belongs to current block.




Line number: 2

Line: if line_start == 0

<ul>

 <li>number of spaces observed before the start of the line. Current Level = 0 This Line = 0 Line belongs to current block.</li>

</ul>

Keyword if found on this line.




Line number: 3

Line:  line_start = 1

<ul>

 <li>number of spaces observed before the start of the line.</li>

</ul>

This line proceeds a keyword containing line.

Current Level = 0 This Line = 1

Line correct. Depth 1 added to the stack.




Line number: 4

Line: else

0 number of spaces observed before the start of the line.

Current Level = 1 This Line = 0

Current line is smaller than Current indentation level; checking if line belongs to outer indentation. Current Level = 0 This Line = 0 Line belongs to outer block.

Keyword else found on this line.




Line number: 5

Line:        print “error”

7 number of spaces observed before the start of the line.

This line proceeds a keyword containing line.

Current Level = 0 This Line = 7

Line correct. Depth 7 added to the stack.




Line number: 6

Line:  print “here”

1 number of spaces observed before the start of the line.

Current Level = 7 This Line = 1

Current line is smaller than Current indentation level; checking if line belongs to outer indentation.

Current Level = 0 This Line = 1

Incorrect file structure.

An indentation level same as the Current line is not found in outer blocks. Stopping file analysis…




Stack emptied and program ending.




<strong> </strong>

<strong>Sample Run 4: </strong>

<strong>File: t4.py </strong>




x = 1 <sup>      </sup><strong> </strong>else <strong> </strong>y = 0 <sup>      </sup><strong> </strong>if x == 1 <sup>  </sup><strong> </strong>

x = 2

if x == 2     <strong> </strong>         print “here”   <strong> </strong>

<strong> </strong>

<strong> </strong>

Please enter the file name that is going to be analyzed. <strong>p4.py </strong>

Unable to open file please enter a different file name.

<strong>t4.py </strong>

Starting file analysis…

Initial indentation level is pushed to the stack as 0.




Line number: 1

Line: x = 1

0 number of spaces observed before the start of the line. Current Level = 0 This Line = 0 Line belongs to current block.




Line number: 2

Line: else

0 number of spaces observed before the start of the line. Current Level = 0 This Line = 0 Line belongs to current block.

Keyword else found on this line.




Line number: 3

Line: y = 0

0 number of spaces observed before the start of the line.

This line proceeds a keyword containing line.

Current Level = 0 This Line = 0

Incorrect file structure.

Current line must be greater than the Current indentation level. Stopping file analysis…




Stack emptied and program ending.







<strong>Sample Run 5: </strong>

<strong>File: t5.py </strong>




<table width="386">

 <tbody>

  <tr>

   <td width="386">if True:    <strong> </strong>     while True: <strong> </strong>          for x in range(1,20):   <strong> </strong>else                           l =</td>

  </tr>

 </tbody>

</table>

Please enter the file name that is going to be analyzed.

<strong>t5.py </strong>

Starting file analysis…

Initial indentation level is pushed to the stack as 0.




Line number: 1 Line: if True:

0 number of spaces observed before the start of the line. Current Level = 0 This Line = 0 Line belongs to current block.

Keyword if found on this line.




Line number: 2

Line:      while True:

5 number of spaces observed before the start of the line.

This line proceeds a keyword containing line. Current Level = 0 This Line = 5

Line correct. Depth 5 added to the stack.

Keyword while found on this line.




Line number: 3

Line:           for x in range(1,20):

10 number of spaces observed before the start of the line.

This line proceeds a keyword containing line. Current Level = 5 This Line = 10

Line correct. Depth 10 added to the stack.

Keyword for found on this line.




Line number: 4

Line:                     else

20 number of spaces observed before the start of the line.

This line proceeds a keyword containing line.

Current Level = 10 This Line = 20

Line correct. Depth 20 added to the stack.

Keyword else found on this line.




Line number: 5

Line:                           l =

26 number of spaces observed before the start of the line.

This line proceeds a keyword containing line. Current Level = 20 This Line = 26 Line correct. Depth 26 added to the stack.




Finished file analysis. File structure is correct!

Stack emptied and program ending.







<strong>Sample Run 6: </strong>

<strong>File: t6.py </strong>




if True: <sup>   </sup><strong> </strong>     while True: <strong> </strong>          for x in range(1,20):     <strong> </strong>                  if True:    <strong> </strong>                      while True:                            else <strong> </strong>                                   l = <sup> </sup>print “End”







Please enter the file name that is going to be analyzed.

<strong>t6.py </strong>

Starting file analysis…

Initial indentation level is pushed to the stack as 0.




Line number: 1

Line: if True:

0 number of spaces observed before the start of the line. Current Level = 0 This Line = 0 Line belongs to current block.

Keyword if found on this line.




Line number: 2

Line:      while True:

5 number of spaces observed before the start of the line.

This line proceeds a keyword containing line.

Current Level = 0 This Line = 5

Line correct. Depth 5 added to the stack.

Keyword while found on this line.




Line number: 3

Line:           for x in range(1,20):

10 number of spaces observed before the start of the line.

This line proceeds a keyword containing line.

Current Level = 5 This Line = 10

Line correct. Depth 10 added to the stack.

Keyword for found on this line.




Line number: 4

Line:                   if True:

18 number of spaces observed before the start of the line.

This line proceeds a keyword containing line. Current Level = 10 This Line = 18 Line correct. Depth 18 added to the stack.

Keyword if found on this line.




Line number: 5

Line:                       while True:

22 number of spaces observed before the start of the line.

This line proceeds a keyword containing line. Current Level = 18 This Line = 22

Line correct. Depth 22 added to the stack.

Keyword while found on this line.




Line number: 6

Line:                           else

26 number of spaces observed before the start of the line.

This line proceeds a keyword containing line. Current Level = 22 This Line = 26

Line correct. Depth 26 added to the stack.

Keyword else found on this line.




Line number: 7

Line:                                    l =

35 number of spaces observed before the start of the line.

This line proceeds a keyword containing line. Current Level = 26 This Line = 35

Line correct. Depth 35 added to the stack.




Line number: 8

Line: print “End”

0 number of spaces observed before the start of the line.

Current Level = 35 This Line = 0

Current line is smaller than Current indentation level; checking if line belongs to outer indentation.

Current Level = 26 This Line = 0

Current line is smaller than Current indentation level; checking if line belongs to outer indentation.

Current Level = 22 This Line = 0

Current line is smaller than Current indentation level; checking if line belongs to outer indentation.

Current Level = 18 This Line = 0

Current line is smaller than Current indentation level; checking if line belongs to outer indentation. Current Level = 10 This Line = 0

Current line is smaller than Current indentation level; checking if line belongs to outer indentation.

Current Level = 5 This Line = 0

Current line is smaller than Current indentation level; checking if line belongs to outer indentation. Current Level = 0 This Line = 0 Line belongs to outer block.




Finished file analysis. File structure is correct!

Stack emptied and program ending.




<strong>Sample Run 7: </strong>

<strong>File: t7.py </strong>




if True: <sup>   </sup><strong> </strong>     while True: <strong> </strong>          a = 78 <strong> </strong>          for x in range(1,20):      <strong> </strong>              if x=1:




<strong><sub> </sub></strong>          print “End”print “Muslera”







Please enter the file name that is going to be analyzed. t7.py

Starting file analysis…

Initial indentation level is pushed to the stack as 0.




Line number: 1 Line: if True:

0 number of spaces observed before the start of the line. Current Level = 0 This Line = 0 Line belongs to current block.

Keyword if found on this line.




Line number: 2

Line:      while True:

5 number of spaces observed before the start of the line.

This line proceeds a keyword containing line.

Current Level = 0 This Line = 5

Line correct. Depth 5 added to the stack.

Keyword while found on this line.




Line number: 3

Line:           a = 78

10 number of spaces observed before the start of the line.

This line proceeds a keyword containing line.

Current Level = 5 This Line = 10

Line correct. Depth 10 added to the stack.




Line number: 4

Line:           for x in range(1,20):

10 number of spaces observed before the start of the line. Current Level = 10 This Line = 10

Line belongs to current block.

Keyword for found on this line.




Line number: 5

Line:               if x=1:

14 number of spaces observed before the start of the line.

This line proceeds a keyword containing line. Current Level = 10 This Line = 14 Line correct. Depth 14 added to the stack. Keyword if found on this line.




Line number: 6

Line:           print “Muslera”

10 number of spaces observed before the start of the line.

This line proceeds a keyword containing line. Current Level = 14 This Line = 10

Incorrect file structure.

Current line must be greater than the Current indentation level. Stopping file analysis…




Stack emptied and program ending.




<strong>Some Important Rules </strong>

In order to get a full credit, your programs must be efficient and well presented, presence of any redundant computation or bad indentation, or missing, irrelevant comments are going to decrease your grades. You also have to use understandable identifier names, informative introduction and prompts. Modularity is also important; you have to use functions wherever needed and appropriate. Since using classes is mandated in this homework, a proper object oriented design and implementation will also be considered in grading.




Since you will use dynamic memory allocation in this homework, it is very crucial to properly manage the allocated area and return the deleted parts to the heap whenever appropriate. Inefficient use of memory may reduce your grade.




When we grade your homework we pay attention to these issues. Moreover, in order to observe the real performance of your codes, we may run your programs in <em>Release </em>mode and <strong>we may test your programs with very large test cases</strong>. Of course, your program should work in <em>Debug </em>mode as well.




You are allowed to use sample codes shared with the class by the instructor and TAs. However, you cannot start with an existing .cpp or .h file directly and update it; you have start with an empty file. Only the necessary parts of the shared code files can be used and these parts must be clearly marked in your homework by putting comments like the following.  Even if you take a piece of code and update it slightly, you have to put a similar marking (by adding “and updated” to the comments below.










/* Begin: code taken from ptrfunc.cpp */




…




/* End: code taken from ptrfunc.cpp */

<strong> </strong>

<strong> </strong>

<strong>What and where to submit (PLEASE READ, IMPORTANT) </strong>

You should prepare (or at least test) your program using MS Visual Studio 2012 C++. We will use the standard C++ compiler and libraries of the abovementioned platform while testing your homework. It’d be a good idea to write your name and last name in the program (as a comment line of course).

<strong> </strong>

Submissions guidelines are below. Some parts of the grading process are automatic. Students are expected to strictly follow these guidelines in order to have a smooth grading process. If you do not follow these guidelines, depending on the severity of the problem created during the grading process, 5 or more penalty points are to be deducted from the grade. Name your solution, project, cpp file that contains your main program using the following convention (the necessary file extensions such as .sln, .cpp, etc, are to be added to it):




“SUCourseUserName_YourLastname_YourName_HWnumber”




Your SUCourse user name is actually your SUNet user name which is used for checking sabanciuniv e-mails. Do NOT use any spaces, non-ASCII and Turkish characters in the file name. For example, if your SUCourse user name is cago, name is Çağlayan, and last name is Özbugsızkodyazaroğlu, then the file name must be:




Cago_Ozbugsizkodyazaroglu_Caglayan_hw4

<strong> </strong>

In some homework assignments, you may need to have more than one .cpp or .h files to submit. In this case add informative phrases after the hw number. However, do not add any other character or phrase to the file names.




Now let us explain which files will be included in the submitted package. Visual Studio 2012 will create two <em>debug </em>folders, one for the solution and the other one for the project. You should delete these two <em>debug </em>folders. Moreover, if you have run your program in release mode, Visual Studio may create <em>release </em>folders; you should delete these as well. Apart from these, Visual Studio 2012 creates a file extension of <em>.sdf</em>; you will also delete this file. The remaining content of your solution folder is to be submitted after compression. Compress your solution and project folders using WINZIP or WINRAR programs. Please use “zip” compression. “rar” or another compression mechanism is NOT allowed. Our homework processing system works only with zip files. Therefore, make sure that the resulting compressed file has a zip extension. Check that your compressed file opens up correctly and it contains all of the solution, project and source code files that belong to the latest version of your homework. Especially double-check that the zip file contains your cpp and (if any) header files that you wrote for the homework.

<strong> </strong>

Moreover, we strongly recommend you to check whether your zip file will open up and run correctly. To do so, unzip your zip file to another location. Then, open your solution by clicking the file that has a file extension of .sln. Clean, build and run the solution; if there is no problem, you could submit your zip file. Please note that the deleted files/folders may be regenerated after you build and run your program; this is normal, but do not include them in the submitted zip file.




You will receive no credits if your compressed zip file does not expand or it does not contain the correct files. The naming convention of the zip file is the same. The name of the zip file should be as follows:




SUCourseUserName_YourLastname_YourName_HWnumber.zip




For example, zubzipler_Zipleroglu_Zubeyir_hw4.zip is a valid name, but




Hw4_hoz_HasanOz.zip, HasanOzHoz.zip




are <strong>NOT </strong>valid names.

<strong> </strong>

<strong>Submit via SUCourse ONLY! </strong>You will receive no credits if you submit by other means (email, paper, etc.).

Successful submission is one of the requirements of the homework. If, for some reason, you cannot successfully submit your homework and we cannot grade it, your grade will be 0.

Good Luck!

Albert Levi, Taha Atahan Akyıldız


