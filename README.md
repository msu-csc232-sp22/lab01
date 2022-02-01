# LAB01 - Arrays and Addresses

_Note: The contents of this README is taken directly (with slight modifications) from Lab Manual to Accompany ADTs, Data Structures, and Problem Solving with C++, Second Edition by Larry Nyhoff, Lab 3.1 Arrays and Addresses, pp 37-44, (c) 2006 Pearson Education, Inc. ISBN: 0-13-148758-2._

**Background**: The C++ programming language is based on the C programming language and provides all the features of C. While some of these features have been superseded by modern counterparts that are more consistent with object-oriented programming, some with which C++ programmers need to be familiar are commonly overlooked in introductory courses. This is especially true of C-style arrays. The _array_ is an important data structure because it provides an efficient storage structure for implementing many ADTs.

**Objective**: This lab exercise provides a review of C-style arrays. It explores one-dimensional arrays, how they are declared and processed. Multidimensional arrays are considered briefly at the end of the exercise and in HW01. Additional information about arrays can be found in Appendix A (Section A.6 - Arrays).

**Approach**: This lab exercise proceeds in four tasks:

1. Explore one-dimensional arrays
2. Explore the indices and addresses of arrays
3. Explore what happens when arrays are indexed improperly
4. Look briefly at multidimensional arrays

You'll be doing experiments on arrays, their addresses and behaviors. In some places you will intentionally introduce errors to see how the system responds.

## Getting Started

After accepting this assignment with the provided [GitHub Classroom Assignment link](https://classroom.github.com/a/zmWY7E0R), clone this repository. If you have cloned the repository from the command line prompt, navigate into the newly created directory

```bash
cd lab01-github-username
```

Next, create a branch named develop. Please note: The name of this branch must be as specified and will be, to the grading scripts, case-sensitive.

```bash
git checkout -b develop
```

Make sure you are on the develop branch before you get started. Make all your commits on the develop branch.

```bash
git branch
```

_You may have to type the q character to get back to the command line prompt after viewing the branches listed with this command_.

## Task 1: Exploring One-Dimensional Arrays

**Step 1**: Begin by creating a new source file in the `src` directory named `array.cpp` that contains the following _stub_.

```c++
#include <cstdlib>

int main()
{
    return EXIT_SUCCESS;
}
```

A stub is a complete program fragment that will compile properly but won't necessarily do anything. You could try to compile, link, and execute the stub. If you do, you will discover that nothing happens. It compiles and links, but it doesn't do anything. Not a big surprise, right?

To compile and link this program, execute the following commands (that assume you are at a terminal Window of a Linux WSL distribution, or a Macintosh computer, that has the GNU build tools installed and that you're in the `src` directory in which you created the file `array.cpp` mentioned above). Note that the `$` character is the command line prompt and is not to be typed.

```bash
$ g++ array.cpp -o lab01
$ ./lab01
$
```

When you have finished writing this program and tested that it compiles, links and executes correctly, stage this new file (using `git add`), commit your changes (using `git commit`), and push them (using `git push`) to GitHub. Assuming you're still in the `src` directory, type the following commands:

```bash
$ git add array.cpp
$ git commit -m"Initial import of array program stub."
... output specific to your environment ...
$ git push -u origin develop
... output specific to your environment ...
$
```

NOTE: Since this _should_ be the first time you're pushing changes on this `develop` branch, you need to add the `-u origin develop` arguments to the `git push` command. After this first push, you don't add those arguments and simply type `git push` when instructed to push your changes to GitHub.

**Step 2**: Now add two `typedef` statements of the form

```text
typedef array-element-type custom-type-name[array-size];
```

ahead of `main()` to define the two data types:

1. `IntegerArray` for arrays with 16 integer elements
2. `CharArray` for arrays with 10 character elements

When you have completed this step, stage your changes (using `git add`), commit your changes (using `git commit`), and push them (using `git push`) to GitHub.

**Step 3**: Inside the `main()` function, declare and initialize an `IntegerArray` variable `prime` to be an array contain the 16 integers 2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37, 41, 43, 47, 53, using a declaration of the form:

```text
type-name array-name = {list-of-values};
```

When you have completed this step, stage your changes (using `git add`), commit your changes (using `git commit`), and push them (using `git push`) to GitHub.

**Step 4**: Check that the array has been initialized properly by writing a `for`-loop to display the elements of `prime`. When you have finished updating this program and tested that it compiles, links and executes correctly, stage this updated file (using `git add`), commit your changes (using `git commit`), and push them (using `git push`) to GitHub.

**Step 5**: An initializer list with too many values is an error. Some compilers detect this as an error while others do not. THose that do not may allow the program to actually compile and run, and this will resulr in errors. Now you are to test your particular compiler to determine its behavior.

What happens when you try to compile a statement with too many values in the initializer list? You can find out by adding one or more values to your initializer list for `prime`. Do this and note what happens in [questions.txt](questions.txt) (see question 1).

After answering the question in [questions](questions.txt), save your changes, stage your changes (using `git add`), commit your changes (using `git commit`), and push your changes to GitHub (using `git push`).

**Step 6**: It is not an error to give too few values in the initializer list of an array. What happens in this case? You can find out by changing the initialization of `prime` to use fewer than 16 integers and outputing the array elements. Describe what happens when you do this in [questions.txt](questions.txt) (see question 2).

After answering the question in [questions](questions.txt), save your changes, stage your changes (using `git add`), commit your changes (using `git commit`), and push your changes to GitHub (using `git push`).

**Step 7**: Now you will repeat the experiment performed on the `IntegerArray` using `CharArray`. First comment out the declaration of the integer array `prime` and the `for`-loop that displays the elements.

> Note that the phrase _commenting out_ refers to the process of using the comment syntax to temporarily eliminate some program lines for test purposes, or sometimes to provide for alternative implementations. This can be done by putting a single-line comment delimiter `//` at the beginning of each line you want to eliminate. When several lines are involved, you can use the `/* ... */` comment delimiters.

Once you have commented out the integer array `prime` and the `for`-loop, then declare the `CharArray` variable `animal` initializing it to `'r'`, `'h'`, `'i'`, `'n'`, `'o'`, `'c'`, `'e'`, `'r'`, `'o'`, `'s'`. Check that the array has been initialized properly by adding a `for`-loop that displays the elements of `animal` followed by something like `****`, all on the same line. After you have completed this, compile, link, and execute the code. Describe what happens in [questions.txt](questions.txt) (see question 3).

After answering the question in [questions](questions.txt), save your changes, stage your changes (using `git add`), commit your changes (using `git commit`), and push your changes to GitHub (using `git push`).

**Step 8**: Now check if adding one or more characters, i.e., adding too many initialization values, affects what happens. If so, add one or more characters and repeat the test. Describe what happens in [questions.txt](questions.txt) (see question 4).

After answering the question in [questions](questions.txt), save your changes, stage your changes (using `git add`), commit your changes (using `git commit`), and push your changes to GitHub (using `git push`).

**Step 9**: Now check what happens when there are fewer values in the initializer list. Remove all but the first five characters in the initializer list and compile, link, and execute your program again. Describe what happens in [questions.txt](questions.txt) (see question 5).

After answering the question in [questions](questions.txt), save your changes, stage your changes (using `git add`), commit your changes (using `git commit`), and push your changes to GitHub (using `git push`).

**Step 10**: It may not be completely clear what happened when the uninitialized character array locations were reached. What did the output operator do when the `for`-loop sent it the character array elements that had not been initialized? To see this, modify the output statement in the `for`-loop to display the actual ASCII codes being generated for each character array element. (_Hint_: Use a type cast `static_cast<int>(animal[i])` to convert `char` values into `int` values. You may also want insert a single space character into the stream after each such cast to see the ASCII values of each character more clearly.) Answer question 6 in [questions.txt](questions.txt) to describe what is used to initialize the uninitialized array elements.

After answering the question in [questions](questions.txt), save your changes, stage your changes (using `git add`), commit your changes (using `git commit`), and push your changes to GitHub (using `git push`).

**Step 11**: Now try initializing the character array in a different way. Character arrays can also be initialized by using string literals like `"elephant"` -- so we can initialize the character array `animal` using the string literal in place of the curly brace initializer list syntax. We can also output a character array using `<<` directly, as in

```c++
std::cout << animal << "****\n";
```

Make necessary changes to use the string `"elephant"` and record what happens in [questions.txt](questions.txt) (see question 7).

After answering the question in [questions](questions.txt), save your changes, stage your changes (using `git add`), commit your changes (using `git commit`), and push your changes to GitHub (using `git push`).

**Step 12**: Now repeat the test using the string `"rhinoceros"` instead. Describe what happens in [questions.txt](questions.txt) (see question 8).

After answering the question in [questions](questions.txt), save your changes, stage your changes (using `git add`), commit your changes (using `git commit`), and push your changes to GitHub (using `git push`).

You may have gotten a warning message, even though the array has been declared to to have 10 elements. The reason is that character arrays are terminated by **null characters**, `\0`, whose ASCII code is 0, provided there is room to store this character. Since functions that process character arrays expect to to find this null character at the end of the string that is stored, they may not work properly when there is no such null-terminating character.

Thus, character arrays such as `animal` that are used to store strings should be declared large enough to store at least one extra character at the end of each string value, namely, the null character. This character is used by functions that process strings stored in character arrays to mark the end of the string. To see how this is done:

(i) Change the initialization string of `animal` to `"zebra"`.
(ii) Now write C++ statements in `main()` that could be used to determine the length of the string stored in `animal`, that is, the number of non-null characters. Test that code works by compiling, linking and executing your new code. _Note_: For fun(?) -- see if you can do this using a `for`-loop with an empty body. 

> _Remember_: The end-of-string mark (i.e., the null character `'\0'`) gets placed at the end of each initialization string or a string that is input for a character array (e.g., `cin >> animal;`) provided that the character array has space for it. If it doesn't get stored, one cannot expect string operations to work correctly. Thus, one must be sure the array is large enough so that it has space for this null character.

When you have finished updating this program and tested that it compiles, links and executes correctly, stage this updated file (using `git add`), commit your changes (using `git commit`), and push them (using `git push`) to GitHub.

## Submission Details

Before submitting your assignment, be sure you have pushed all your changes to GitHub. If this is the first time you're pushing your changes, the push command will look like:

```Powershell
git push -u origin develop
```

If you've already set up remote tracking (using the `-u origin develop` switch), then all you need to do is type

```Powershell
git push
```

As usual, prior to submitting your assignment on Blackboard, be sure that you have committed and pushed your final changes to GitHub. Once your final changes have been pushed, create a pull request that seeks to merge the changes in your `develop` branch into your `trunk` branch. Once your pull request has been created, submit the URL of your assignment _repository_ (i.e., _not_ the URL of the pull request) Blackboard using a **Text Submission**. Please note: the timestamp of the submission on Blackboard is used to assess any late penalties if and when warranted, _not_ the date/time you create your pull request. **No exceptions will be granted for this oversight**.

### Due Date

Your assignment submission is due by 11:59 PM, Friday, 28-Jan 2022.

### Grading Rubric

This assignment is worth **3 points**.

Criteria          | Exceeds Expectations        | Meets Expectations             | Below Expectations | Failure                                                 |
------------------|-----------------------------|--------------------------------|--------------------|---------------------------------------------------------|
Pull Request (20%)| Submitted early, correct url| Submitted on-time; correct url | Incorrect URL            | No pull request was created or submitted          |
Code Style (20%)  | Exemplary code style        | Consistent, modern coding style    | Inconsistent coding style| No style whatsoever or no code changes present|
Correctness^ (60%)| All unit tests pass         | At least 80% of the unit tests pass| At least 60% of the unit tests pass| Less than 50% of the unit tests pass|

^ _The Google Test unit runner, if configured, will calculate the correctness points based purely on the fraction of tests passed_.

### Late Penalty

* In the first 24 hour period following the due date, this lab will be penalized 0.6 point meaning the grading starts at 2.4 (out of 3 total possible) points.
* In the second 24 hour period following the due date, this lab will be penalized 1.2 points meaning the grading starts at 1.8 (out of 3 total possible) points.
* After 48 hours, the assignment will not be graded and thus earns no points, i.e., 0 out of 3 possible points.
