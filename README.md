Download Link: https://assignmentchef.com/product/solved-encm-369-lab-1
<br>









Lab instructions and other documents for ENCM 369 can be found at <a href="https://people.ucalgary.ca/~norman/encm369winter2018/">http://people.ucalgary.ca/</a><a href="https://people.ucalgary.ca/~norman/encm369winter2018/">~</a><a href="https://people.ucalgary.ca/~norman/encm369winter2018/">norman/encm369winter2018/</a>

<h1>Editing and running C programs using a text editor and the gcc command line</h1>

In many lab assignments in ENCM 369, you will be expected to work with C code in some way, so it is important that you know how to edit C code, and build executables from it in the lab.

Most students in ENCM 369 in Winter 2018 took ENCM 339 in Fall 2017 or Spring 2017; those students should be quite familiar with using text editors such as Geany or Notepad++ to edit C source code, and using Cygwin Terminal to build and run executables. However, there may be a few students in ENCM 369 this term who have transfer credit for ENCM 339 and may not be familiar with the tools used for programming in that course.

Instead of inserting into this document a lot of text about how to edit and run C programs in the lab, I’ll just post a link to the “Lab Information” page for Section 01 of ENCM 339 in Fall 2017:

<a href="https://people.ucalgary.ca/~norman/encm339fall2017/lab_information/">http://people.ucalgary.ca/</a><a href="https://people.ucalgary.ca/~norman/encm339fall2017/lab_information/">~</a><a href="https://people.ucalgary.ca/~norman/encm339fall2017/lab_information/">norman/encm339fall2017/lab_information/</a>

You should consider clicking on that link and doing some reading and coding if one or the other of the following is true:

<ul>

 <li>you’re not at all familiar with the programming tools used in recent versions of ENCM 339;</li>

 <li>you took ENCM 339 in Spring or Fall 2017, but you did most of your lab work on your own computer, and you would like to review the basics of editing and running C code in ICT 320.</li>

</ul>

The key documents to read are “Editing and Running Programs in the ENCM 339 Lab” and the Lab 1 Instructions.

<h1>Exercise A: Practice editing C code and building an executable</h1>

<h2>Read This First</h2>

There are no marks for this exercise, but I <em>strongly </em>recommend that you make a serious effort to get it done before your first lab period. If you are unsuccessful, please be ready to ask questions at the <em>beginning </em>of the lab period.

<h2>What to do, Part I</h2>

If necessary, read the instructions for ENCM 339 Fall 2017 Section 01 Lab 1, and work through some of the exercises.

<h2>What to do, Part II</h2>

Open a Cygwin Terminal window. Within /cygdrive/h, create a directory called encm369. Within your encm369 directory, create a directory called lab01, and within that create a directory called exA.

<strong>Figure 1: </strong>C code for Exercise A.

<table width="422">

 <tbody>

  <tr>

   <td width="422">#include &lt;stdio.h&gt;int main(void){int n = 0; int power = 1;printf(“%12s%12s%12s
”, “n  “, “2**n  “, “2**n”); printf(“%12s%12s%12s
”, “decimal”, “decimal”, “hex “); while (n &lt;= 16) {printf(“%12d%12d%12x
”, n, power, power); power = power + power; n++;} return 0;}</td>

  </tr>

 </tbody>

</table>

Start up Geany or Notepad++ (or some other text editor, if you know that text editor well). Type in the first line from Figure 1, then use a Save as … command to save the file with name exA.c, in your encm369/lab01/exA directory. Use the ls command to confirm that a file called exA.c exists within that directory.

Return to the text editor, and finish typing in the rest of the code from Figure 1.

When you have finished, save the file and return to your terminal window. In the terminal window, build an executable with the command gcc -Wall exA.c

If there are errors or warnings, go back to the text editor, try to fix the errors, then try again to build an executable. If there are no errors or warnings, run the command

./a.exe

You should see a table of powers of 2<em><sup>n </sup></em>for values of <em>n </em>from 0 to 16, displayed in both base ten and base sixteen.

<em>Keep working on this exercise until you are sure you know what you are doing—if you do not, you will have serious problems with all of the remaining exercises!</em>

<strong>What to Hand In</strong>

Nothing.

<h1>How to download files for ENCM 369 labs</h1>

Most lab exercises in this course will require you to download one or more files containing C code, assembly language code, or data.

Links for downloading these files can be found on the same Web page where you find lab instructions. You have the option of clicking through links to get files one at a time or downloading all the files you need for one lab in a single .zip archive. When you are told to make a copy of, for example, encm369w18lab01/exB/globals.c, you should look for it starting on the ENCM 369 Lab Information web page.

<h1>Exercise B: Global variables, review of pointer arithmetic</h1>

<h2>Read This First</h2>

Most variables you saw or created in programs in ENCM 339 were <em>local variables. </em>A local variable can be directly accessed only within the function definition in which it appears. (A local variable of one function can be <em>indirectly </em>accessed by another function, if that other function has a pointer to the variable.)

C variables declared outside of all function definitions in a C source file are called <em>global variables </em>or <em>external variables. </em>Unlike local variables, global variables can be directly accessed from many different function definitions.

There are two kinds of global variables: those declared to be static and those <em>not </em>declared to be static. Global variables declared to be static can be directly accessed by all functions in the source file where the variable is declared. (This use of the keyword static is confusing, because it has nothing to do with static memory allocation.) Global variables <em>not </em>declared to be static can be directly accessed by all functions in a program.

(If you are working on a program where a global variable is in fact accessed from more than one source file, you need to know the rules regarding the extern keyword. See a good C text for details, and read carefully.)

Global variables, regardless of whether they are declared as static, are always statically allocated. So, according to rules you should have learned in ENCM 339, global variables are found in the static storage region, are allocated and initialized before main starts, and remain allocated as long as the program runs.

Unlike <em>automatic </em>variables (which are the “normal” kind of local variables of functions) global variables that don’t have initializers are initialized to zero. For example, consider this variable declaration:

int arr[5];

If arr were local to some function, you could not count on the elements of arr to have any particular values. But if arr were a global variable, its elements would all be initialized to zero.

<h2>What to do</h2>

<strong>Part 1</strong>

Copy the file encm369w18lab01/exB/globals.c

Study the file carefully and make sure you understand the diagram of program state at point one given in Figure 2.

Make a similar diagram to show the state of the program when it reaches point three. (<em>Note: </em>In ENCM 369, whenever you are asked to hand in diagrams, you may draw them neatly by hand or by computer, whichever you find more convenient.) Figure 3 should give you a hint about how to draw part of the diagram.

<strong>Figure 2: </strong>The state of the Exercise B program at the moment when point one is reached. At that moment, functions update_cc and reverse are not active, so their parameters and local variables do not exist. The notation ?? is used to indicate uninitialized local variables. <strong>Important note for ENCM 369: </strong>As the course progresses, we will see that some of the local variables and parameters of a program are in a region of main memory called <em>the stack</em>, and other local variables and parameters are in <em>registers</em>; we’ll see later in the course that for MIPS the arrays dd and ee would be allocated on the stack, but the integers and pointers belonging to copy would be in general-purpose registers, <em>not </em>in memory at all!

<strong>Figure 3: </strong>Example of a pointer pointing “just beyond” the last element of an array. Here the <em>element </em>arr[3] does not exist, but the <em>address </em>of arr[3] <em>does </em>exist. This concept is useful for setting up a condition to quit a loop, when the loop uses pointer arithmetic to step through an array.

10 arr[0]

// fragment of a C function int arr[] = { 10, 11, 12 };

int *p;                                                                                    12 arr[2]

p = arr + 3;

p

<strong>Figure 4: </strong>Table for Exercise B, Part 2.

<table width="373">

 <tbody>

  <tr>

   <td width="156"><strong>instant in time</strong></td>

   <td width="73">to</td>

   <td width="73">from</td>

   <td width="73">pastend</td>

  </tr>

  <tr>

   <td width="156">point two, first time point two, second time point two, third time point two, last time</td>

   <td width="73">0x100090</td>

   <td width="73"></td>

   <td width="73"></td>

  </tr>

 </tbody>

</table>

<strong>Part 2</strong>

Instead of using arrows to show what addresses are contained by pointers, let’s track pointers as actual numbers.

We’ll assume that the size of an int is 4 bytes. We’ll use hexadecimal numbers, writing them in C language notation. For example, 0x7ffe18 represents a number we would have written as 7FFE18<sub>16 </sub>in ENEL 353.

Suppose that the address of ee[0] is 0x7ffe78. Then the addresses of elements 1, 2, 3 in the array must be 0x7ffe7c, 0x7ffe80, and 0x7ffe84—each address is 4 greater than the previous one. (Here is a fact you will use often in this course: In base sixteen, adding 0xc and 4 generates a sum digit of zero and a carry out of one.)

Now suppose that &amp;bb[0] is 0x100090 and &amp;ee[0] is 0x7ffe78. Use that information to fill in all of the addresses in all of the cells in a copy of the table of Figure 4.

<strong>What to Hand In</strong>

Hand in a diagram for Part 1 and a completed table for Part 2.

<h1>Using your own computer for Exercises C–H</h1>

We (your instructors and your TAs) expect that most students will do Exercises C to H on Linux workstations in ICT 320. However, all of the exercises can be done on your own computer, if you have a reasonably up-to-date C development system installed.

All students should do at least two or three of the exercises in ICT 320, just to get comfortable with the process of editing C code and building executables using a text editor and a command line.

<h1>Exercise C: goto statements</h1>

<h2>Read This First</h2>

goto statements are available in C and C++, and their equivalents are available in most programming languages.

You can have a long career writing high-quality C and C++ code for a huge variety of applications and never once use a goto statement. Just about everything you can do with goto can be done more clearly some other way. Use of goto tends to make code unreasonably hard to understand and debug.

Nevertheless, it’s useful to know what goto does, for the following reasons:

<ul>

 <li>You might find goto in code that somebody else wrote.</li>

 <li>C code generated by a program (as opposed to code written by a human being) may have goto statements in it.</li>

 <li>Writing goto statements is similar to writing branch instructions in assembly language.</li>

</ul>

It’s reason (3) that makes the goto statement relevant to ENCM 369.

Consider the following simple program:

#include &lt;stdio.h&gt; int main(void)

{ int i; for (i = 0; i &lt; 4; i++)

printf(“i is %d. “, i);

printf(“
”); return 0;

}

Obviously, the output is

i is 0. i is 1. i is 2. i is 3.

Here is an equivalent program written using goto statements:

#include &lt;stdio.h&gt; int main(void)

{ int i; i = 0; loop_beginning:

if (!(i &lt; 4)) goto past_loop_end; printf(“i is %d. “, i);

i++; goto loop_beginning; past_loop_end: printf(“
”); return 0;

}

The output is exactly the same as that of the earlier program with the for loop.

The identifiers loop_beginning and past_loop_end are examples of what are called <em>labels</em>. A label is used to name a particular statement; a colon must appear between a label and the statement it names. A goto statement has the following syntax:

goto <em>label</em>;

A goto statement causes the flow of statement execution to jump to whatever statement is named by the label. This should be reasonably clear from the example.

<h2>What to Do</h2>

Determine the output of the following program by tracing its execution line by line with a pencil and paper.

#include &lt;stdio.h&gt; int main(void)

{ int outer, inner; outer = 3; outer_loop:

if (outer == 0) goto quit_outer_loop; inner = 0; inner_loop:

if (inner &gt; outer) goto quit_inner_loop; printf(” %d”, 100 * outer + inner); inner++; goto inner_loop;

quit_inner_loop: printf(” **
”); outer–; goto outer_loop; quit_outer_loop: printf(“*****
”); return 0;

}

Check your work by typing in the program, compiling it, and running it. (If it doesn’t compile, goes into an infinite loop when it runs, or crashes, you have made a typing error.)

<strong>What to Hand In</strong>

Nothing.

<h1>Goto-C: Read this before starting Exercises D–H</h1>

From now on in this course, the term “Goto-C” refers to a programming language that is C with the following modifications:

<ul>

 <li>The only kind of if statement allowed in Goto-C is the following:</li>

</ul>

if (<em>expression</em>) goto <em>label</em>;

<ul>

 <li>Goto-C does not have the following keywords and operators:</li>

</ul>

else while for do switch &amp;&amp; ||

<ul>

 <li>Goto-C does not have ?:, the conditional operator.</li>

</ul>

As you will soon see, Goto-C is an annoying language, significantly harder to read and write than normal C. However, working with Goto-C will help you learn how to code algorithms in assembly language.

Consider the following simple fragment of normal C:

if (x &gt;= 0)

y = x; else

y = -x;

The above is illegal in Goto-C for two reasons: the if statement is not in an acceptable form, and the banned keyword else is used. One way to translate the fragment to Goto-C is as follows:

if (x &lt; 0) goto else_code; y = x;

goto end_if; else_code:

y = -x; end_if:

<strong>Technical Note: </strong>The C standard does not permit code like the following:

void f(int i)

{ if (<em>condition</em>) goto L; <em>code</em>

L:

}

The reason is that the label L is followed by a closing brace, which is not a statement. To write standard-compliant code, use an empty statement—a semicolon all by itself …

void f(int i)

{ if (<em>condition</em>) goto L; <em>code</em>

L:

;

}

<h1>Exercise D: Translating if / else-if / else code to Goto-C</h1>

<h2>What to Do</h2>

Copy the file encm369w18lab01/exD/temperature.c

Read the file temperature.c. Make an executable and run it. Then recode the function report in Goto-C. Make sure that the output of your modified program exactly matches the output of the original program.

<strong>What to Hand In</strong>

Nothing.

<h1>Exercise E: Simple loops in Goto-C</h1>

<h2>Read This First</h2>

Simple C while and for loops are easy to code in Goto-C. You need a statement of the form if (<em>condition</em>) goto <em>label</em>;

at the top of the loop to skip past the end of the loop when appropriate and you need a statement of the form goto <em>label</em>;

to jump backwards after the loop body has been executed. For example, this code:

while (i &gt;= 0) {

printf(“%d
”, i); i–;

}

can be written as:

loop_top:

if (i &lt; 0) goto past_end; printf(“%d
”, i); i–; goto loop_top;

past_end:

Remember that the condition to quit looping is the opposite of the condition to continue looping.

<h2>What to Do</h2>

Copy the file encm369w18lab01/exE/simple_loops.c

Read the file and follow the instructions in the comment at the top of the file.

<strong>What to Hand In</strong>

Nothing.

<h1>Exercise F: &amp;&amp; and || in Goto-C</h1>

<h2>Read This First</h2>

You should recall from ENCM 339 that <em>short-circuit evaluation </em>is used when the &amp;&amp; and || operators are encountered in C code. (This also happens with &amp;&amp; and || in C++, and with and and or in Python.) For example, the right-hand operand of &amp;&amp; is not evaluated if the left-hand operand is false. It’s quite easy to translate expressions with &amp;&amp; into Goto-C. For example,

if (y &gt; 0 &amp;&amp; x / y &gt;= 10) { foo(x); bar(y);

} can be coded as

if (y &lt;= 0) goto end_if; if (x / y &lt; 10) goto end_if;

foo(x); bar(y);

end_if:

Expressions with || can be coded in goto-C using a simple adjustment of the technique used for expressions with &amp;&amp;.

<h2>What to Do</h2>

Copy the file encm369w18lab01/exF/logical_or.c

Read the file and follow the instructions in the comment at the top of the file.

<strong>What to Hand In</strong>

Nothing.

<h1>Exercise G: A more complicated program in Goto-C</h1>

<h2>What to Do</h2>

Copy the file encm369w18lab01/exG/exG.c

Read the file carefully. Make an executable using the following command:

gcc -Wall exG.c

Run the executable eight times, using the following text as input:

<table width="266">

 <tbody>

  <tr>

   <td width="65">input</td>

   <td width="201">description</td>

  </tr>

  <tr>

   <td width="65">1.0 x</td>

   <td width="201">first run, test with invalid input</td>

  </tr>

  <tr>

   <td width="65">1.0 0</td>

   <td width="201">second run, also invalid input</td>

  </tr>

  <tr>

   <td width="65">1.0 3</td>

   <td width="201">third run</td>

  </tr>

  <tr>

   <td width="65">1.0 4</td>

   <td width="201">fourth run</td>

  </tr>

  <tr>

   <td width="65">1.5 10</td>

   <td width="201">fifth run</td>

  </tr>

  <tr>

   <td width="65">1.6 10</td>

   <td width="201">sixth run</td>

  </tr>

  <tr>

   <td width="65">-4.3 10</td>

   <td width="201">seventh run</td>

  </tr>

  <tr>

   <td width="65">-4.4 10</td>

   <td width="201">eighth run</td>

  </tr>

 </tbody>

</table>

Translate the definitions of main and polyval to Goto-C. Be careful to translate <em>every </em>use of a C feature that is not allowed in Goto-C.

Test your modified program with the same input given above for the original program. Make sure it always generates <em>exactly </em>the same output as the original program.

<h1>Exercise H: Nested loops in Goto-C</h1>

<h2>What to Do</h2>

Copy the file encm369w18lab01/exH/exH.c

Read the file, then make an executable and run it to check what the program does.

Translate the definitions of print_array and sort_array to Goto-C. Be careful to translate <em>every </em>use of a C feature that is not allowed in Goto-C.

Make sure your modified program generates <em>exactly </em>the same output as the original program.


