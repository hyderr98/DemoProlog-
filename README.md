# Prolog Programming 

## Motivation
Artificial Intelligence has gotten more attention in recent years. There are more AI tools available to the public than ever before: Alexa, Siri, Ericka, etc. not to mention services like Google Cloud Machine Learning, Deep Learning on AWS, IBM Cognitive, Microsoft Azure Machine Learning, etc. One of the early attempts to deal with AI was the development of “AI specific” languages. This is the case of Prolog, a declarative language that stores facts and rules (and other constructs as well), and has an interface where the user can query and make questions that Prolog’s engine will answer inferring from the facts and rules that where stored.
Another motivation is to expose coders to a completely different paradigm of programming. Up to this moment, most of you have been working and coding with imperative and object-oriented languages, and a declarative language should pose a new challenge, as it requires a different way to think.

## Description
Write a Prolog program that stores information about geometric objects. You must construct rules for geometric objects. The objects to construct are:
- 2D Point
- Triangle
- Square

The program must be able to answer the following questions:

English | Prolog
------- | ------
Is the line defined by two points vertical? |	`vertical(point2d(x,y), point2d(x,y))`
Is the line defined by two points horizontal? |	`horizontal(point2d(x,y), point2d(x,y))`
Do the given three points define a line? |	`line(point2d(x,y), point2d(x,y), point2d(x,y))`
Do the given three points define a triangle? | `triangle(point2d(x,y), point2d(x,y), point2d(x,y))`
Is the triangle isosceles? |	`isosceles(point2d(x,y), point2d(x,y), point2d(x,y))`
Is the triangle equilateral? |	`equilateral(point2d(x,y), point2d(x,y), point2d(x,y))`
Is the triangle right? |	`right(point2d(x,y), point2d(x,y), point2d(x,y))`
Is the triangle scalene? |	`scalene(point2d(x,y), point2d(x,y), point2d(x,y))`
Is the triangle acute? |	`acute(point2d(x,y), point2d(x,y), point2d(x,y))`
Is the triangle obtuse?	| `obtuse(point2d(x,y), point2d(x,y), point2d(x,y))`
Do the given four points define a square? | `square(point2d(x,y), point2d(x,y), point2d(x,y), point2d(x,y))`

## Requirements
-	A query file will be provided for you to test your program, this test (and additional ones) will be used 
-	Use the rules names given in the table above.

## Delivery Method
your program must be in a file named `fourpoints.pl` 


-	Each program will be loaded in Prolog and tested to check if the functions are in working order.
-	The programs will be “automatically” run using a bash shell script, it is important that you follow the instructions, so the script runs smoothly.

## Extra Challenge
- Use Prolog more advance features in this project: Lists, IO and Structures. You will need to send the test queries to try your code  
- Use points in 3D. You will need to send the test queries to try your code 
- To take advantage of this extra challenget, you must comply with the given tests first, and those tests must work!

## Instructions for Testing
A file named `test.pl` is provided. You will need to append this file to the end of your code, create a new file called `full.pl` that contains your code and then the code from `test.pl`, and then run Prolog from the command line:  

`swipl -q -f full.pl -t main > your-output.txt`

The command tells prolog to run quietly using the file `full.pl` and to execute target `main`. The query main will then run each of the queries. Once the process is finished, there will be a file named `your-output.txt` you can then compare this file with another file that is provided: `output.txt` to check if your results are correct. Before pushing  make sure that your file `fourpoints.pl` does not have test code.

### Steps
1. Copy your `fourpoints.pl` file into a new empty file called `full.pl`
2. Append the file `test.pl` at the end of your code of `full.pl`
   1. Optionally, if you are comfortable using command line: `cat fourpoints.pl test.pl > full.pl`. This will concatenate your file with the test file and create a new file called `full.pl`.
3. Run the following command:
    `swipl -q -f full.pl -t main > your-output.txt`
4. Compare the file `your-ouput.txt` with the provided `output.txt`, you may use `diff` or `fc` to compare the files.
5. If your output matches, then you are ready to push the final version of your work
6. Push the repository  

### Auto Grading your Program
This repository comes with a file `grade-prolog.cpp` this file is a C++ program that opens your output file and the provided key output, and it will compare your answers with the correct answers for each of the queries. To run the program:
```
prompt$ g++ -std=c++14 grade-prolog.cpp -o grade
prompt$ ./grade output.txt your-output.txt
```

The result of running the program should be:
```
Correct Answers:  72
Queries executed: 72
Total tests:      72
Percentage of tests passed: 100
```

This program will tell you the percentage you will get from the unit tests.

## Recommendation

### Mac Users
Install Prolog using Brew: `brew install swi-prolog`. Installing the DMG produced too many problems for me.

### Windows Users
- [Install the Windows Linux Subsystem](https://docs.microsoft.com/en-us/windows/wsl/install-win10)
- [Install Ubuntu interface from the Windows Store](https://www.microsoft.com/en-us/p/ubuntu-1804-lts/9n9tngvndl3q?rtc=1&activetab=pivot:overviewt)
- Once you are in your Ubuntu terminal:
  - `sudo apt-get update`
  - `sudo apt-get install swi-prolog`

### GUI Versions
There are GUI versions for the Prolog Interpreter, but they might not help you with the assignment goals. Use them at your own risk.

## About the Parser

Steps to integrate the parser made in Rust:
1. Create a 4Points Language "program" call it `test.cpl`, define four points, remember to add tests.
1. Run your parser: `go run . test.cpl -p > mytest.pl`
1. Paste your generated test to your prolog program: `cat fourpoints.pl mytest.pl > full.pl`
1. Run your program to check what those point tests in `test.cpl` represent: `swipl -q -f full.pl -t main`
