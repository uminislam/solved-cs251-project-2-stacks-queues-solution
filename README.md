Download Link: https://assignmentchef.com/product/solved-cs251-project-2-stacks-queues-solution
<br>
<ol>

 <li>Overview</li>

</ol>

Project 2 is split into three parts. In the first part, you will implement a stack class. In the second part, you will use your stack to solve a word-search problem. Finally, in the third part you will write a specialized type of queue called a circular double-ended queue.




<ol start="2">

 <li>Detailed Description</li>

</ol>




Part 1) Implement a stack that stores ordered pairs (i.e (2,3) or (5,8)).   (20 points)




<ul>

 <li>Your task in part 1a will be to implement a growable stack using a linked list format. See the lecture slides for details on this data structure.</li>

 <li>You may not use C++ STL classes or any of Java’s built-in classes (linked list, stacks, Pair etc.) for this section. Implement this on your own!</li>

</ul>




Part 2) Use your stack to solve a word search problem.   (40 points)




In this part, you are going to solve a word-search problem, but with a bit of a twist. Normally in these puzzles, you are looking for a word that is written out in a straight line, such as below:




<u>S</u> A B C D

E <u>T</u> F G H I J <u>A</u> K L

M N O <u>C</u> P

Q R S T <u>K</u>




However we want to solve something a bit trickier. In this project, we want to allow the words to be hidden in more interesting patterns, which may not be a line. Such as below:




A B C D E <u>S</u> G <u>A</u> I J

K <u>T</u> M <u>C</u> O

P Q R <u>K</u> T

U V W X Y




Unlike above, we allow ourselves to move any direction we want from any letter. Our objective, in this case, is to print out the location of the letters that make up the specified word. Moreover, the output should be in an ordered pair format. The solution for the above example is:




<ul>

 <li>0</li>

 <li>1</li>

 <li>2</li>

 <li>3</li>

 <li>3</li>

</ul>




The first number per line is the row number and the second number per line is the column number (both starting at zero from the top or the left, respectively). Thankfully, stacks provide a solution to problems like this! The basic algorithm to solve this problem works as follows:




<ul>

 <li>Begin by searching for the first letter in the word.</li>

 <li>If you find it, push the location onto your stack, and begin inspecting the immediately surrounding 8 (eight) cells for the next letter. If you are at the boundary of the matrix of letters, do not wrap around to the other side.</li>

 <li>If you find the next letter, push that location onto the stack and repeat until finished. If, at any point, you do NOT find the letter you want, pop the last location off the stack and resume the search from the previous stage.</li>

 <li>If the word is found, print out the ordered pairs in the correct order. If not, print “not found” (without quotes).</li>

</ul>




Additional notes for this section:

<ul>

 <li>Letters can be re-used in the search. In the given example DAD would be acceptable with the answer being:

  <ul>

   <li>3</li>

   <li>2</li>

  </ul></li>

</ul>

0 3




<ol start="3">

 <li>Circular Double-ended Queue. (40 points)</li>

</ol>




In a standard queue, objects are inserted at the back and pulled from the front in a First In First Out (FIFO) fashion. There is a variation of a standard queue called a circular doubleended queue, often shortened to circular deque. As you may expect from the name, rather than inserting/deleting only on one side of the queue, these deques allow insertion or deletion from both sides on a circular array. The basic methods you will need to implement for this part are:




<ul>

 <li>enqueue_front: Add an item to the front of the queue</li>

 <li>enqueue_back: Add an item to the back of the queue</li>

 <li>dequeue_front: Take an item off the front of the queue</li>

 <li>dequeue_back: Take an item off the back of the queue</li>

 <li>print_array_size: Print the total size of the allocated array (i.e., how many items could the array store when totally full)</li>

 <li>print_front_index: Print the index of the front pointer</li>

 <li>print_rear_index: Print the index of the rear pointer</li>

</ul>




Your task is to implement a circular double-ended queue using the array-doubling strategy. As in part 1, you cannot use C++ STL classes or predefined java interfaces like deques. You must write your own. You should start with an initial array size of 2.




Regarding front and rear position,

<ul>

 <li>If there are no elements, then front and rear index should be reset to -1.</li>

 <li>The first element should be put into index 0 and front, rear should be pointed to index 0.</li>

 <li>While doubling the array you should put the previous contents into the new array and relocate the elements such that the element pointed by front starts from index 0. Therefore, the new front index should be point to 0 and rear should be point to index of the last element.</li>

</ul>




Example:  ‘e’ or ‘d’ represents enqueue or dequeue followed by another character ‘f’ or ‘b’ that represents the operation on the front or back of the queue followed by an integer to use in the operation ( “-” denotes that the cell is empty ).







<table width="524">

 <tbody>

  <tr>

   <td width="86">Command</td>

   <td width="94">Front Index</td>

   <td width="89">Rear Index</td>

   <td width="255">Queue Contents</td>

  </tr>

  <tr>

   <td width="86"></td>

   <td width="94">-1</td>

   <td width="89">-1</td>

   <td width="255">[-,-] (Initial size of Empty queue : 2)</td>

  </tr>

  <tr>

   <td width="86">e f 1</td>

   <td width="94">0</td>

   <td width="89">0</td>

   <td width="255">[1,-]</td>

  </tr>

  <tr>

   <td width="86">e b 2</td>

   <td width="94">0</td>

   <td width="89">1</td>

   <td width="255">[1,2]</td>

  </tr>

  <tr>

   <td width="86">e f 3</td>

   <td width="94">3</td>

   <td width="89">1</td>

   <td width="255">[1,2,-,3]</td>

  </tr>

  <tr>

   <td width="86">e f 4</td>

   <td width="94">2</td>

   <td width="89">1</td>

   <td width="255">[1,2,4,3]</td>

  </tr>

  <tr>

   <td width="86">e b 5</td>

   <td width="94">0</td>

   <td width="89">4</td>

   <td width="255">[4,3,1,2,5,-,-,-]</td>

  </tr>

  <tr>

   <td width="86">e f 6</td>

   <td width="94">7</td>

   <td width="89">4</td>

   <td width="255">[4,3,1,2,5,-,-,6]</td>

  </tr>

  <tr>

   <td width="86">d b</td>

   <td width="94">7</td>

   <td width="89">3</td>

   <td width="255">[4,3,1,2,-,-,-,6]</td>

  </tr>

  <tr>

   <td width="86">d f</td>

   <td width="94">0</td>

   <td width="89">3</td>

   <td width="255">[4,3,1,2,-,-,-,-]</td>

  </tr>

 </tbody>

</table>




























<ol start="4">

 <li>Input/Output Format</li>

</ol>




Input and output will be handled using files similar to Project 1. The input and output filepath/filename will be passed as two command line arguments. The provided skeleton code shows how different problems are called based on the first value (Line 1) of the input file. You have to handle remaining portion as per the following description. All your output should be written into a output file passed as an argument.




Line 1: either 1, 2, or 3 declaring which part of the project is being tested.




<em>For project part 1 the input is as follows</em>:




<ul>

 <li>An integer n that represents the number of lines to follow.</li>

 <li>n lines of the following format.</li>

</ul>

The character ‘i’ (for insert) followed by 2 integers. Push these onto the stack as an ordered pair. The character ‘p’ (for pop) followed by nothing. Pop an ordered pair and print the integers separated by one space in between them. If the stack is empty print the string “empty”. (Lowercase and no punctuation please!)




<em>For project part 2 the input is as follows</em>:




<ul>

 <li>A line containing 2 integers “n m“ (no quotes) that describes the size of the word search puzzle.</li>

 <li>n lines each containing m characters</li>

 <li>One line containing the word you are searching for</li>

 <li>Output is the list of ordered pairs that represents the location of the word. Print “not found” if the word is not found.</li>

</ul>




<em>For project part 3 the input is as follows</em>:




<ul>

 <li>An integer n that represents the number of lines to follow</li>

 <li>n lines of the following format</li>

</ul>

Either the character ‘e’ or ‘d’ representing enqueue or dequeue, followed by space and another character ‘f’ or ‘b’ indicating that the operation is on the front or back of the queue, followed by a space and the integer to use in the operation

The character ‘s’ in which case you print the allocated size of the deque, the      front index followed by the rear index delimited by space.

<ul>

 <li>All dequeued objects should be printed. Each dequeue commands dequeues an item either from front or back. You have to print that item in a new line. Check expected output for details.</li>

</ul>




<u>For this project, you can assume that all input we give you is well-formatted and valid.</u>
















Sample test cases:




<table width="236">

 <tbody>

  <tr>

   <td width="101">Input</td>

   <td width="134">Expected output</td>

  </tr>

  <tr>

   <td width="101">1 5 i 5 2 i 4 3 p p p</td>

   <td width="134">4  35  2empty</td>

  </tr>

  <tr>

   <td width="101">25 5A B C D ES G A I JK T M C OP Q R K TU V W X YSTACK</td>

   <td width="134">1  02  11  22  33  3</td>

  </tr>

  <tr>

   <td width="101">3 8 e b 1 e b 2 e f 3 d b d f e b 5 d f s</td>

   <td width="134">2314 1 1</td>

  </tr>

 </tbody>

</table>







<ol start="5">

 <li>Grading and Programming Environment</li>

</ol>

Assignments will be tested in a Linux environment. You will be able to work on the assignments using the Linux workstations in HAAS and LAWSON (use your username and password).










C++ Instructions:




Compilation will be done using g++ and makefiles. Create a folder with your username. Put all the source code (should not have any sub-directories in your submission folder) as well as the Makefile that compiles your provided source code into an executable named

“program”.




Ex: g++ -o program main.cpp stack.cpp circular_deque.cpp -std=c++11

./program &lt;input file&gt; &lt;output_file&gt;




Your project must compile using the standard g++ compiler on data.cs.purdue.edu. For convenience, you are provided with a template Makefile and C++ source file.




Java Instructions:

<ul>

 <li>Compiler we use: javac (v10.0.2)</li>

 <li>Files to submit: Create a folder with your username. Put all java files into the folder. There should not be any sub-directories. Your main program must be named java. We will run that one only. Your project must compile using the javac compiler (v10.0.2) on data.cs.purdue.edu.</li>

</ul>




Compiling process:

<ul>

 <li>To compile Main:

  <ol>

   <li>Go to the project root.</li>

   <li>Type command in console: javac src/*</li>

  </ol></li>

</ul>




<ul>

 <li>To run Main:

  <ol>

   <li>Go to the project root.</li>

   <li>Type command in console: java -cp src/ Main inputfiles/test1.txt outputfiles/output-test1.txt</li>

  </ol></li>

</ul>




The grading process consists of:




<ol>

 <li>Compiling and building your program using your supplied makefile.</li>

 <li>The name of produced executable program must be “program” (must be lowercase)</li>

 <li>Running your program automatically with several test input files we have pre-made according to the strict input file format of the project and verifying correct output files. Thus, follow the above instructions precisely – do not “embellish” the output with additional characters or formatting – if your program produces different output such as extra prompt and space, points will be deducted.</li>

 <li>Inspecting your source code.</li>

</ol>




Input to the programming projects will be via files. The output should be written to the output file passed via command line argument. The output file will be tested for grading.





