# SCE212 Computer Organization and Architecture (Fall 2019)

## Project #0: Implementing a Command Parser

### Introduction

The purpose of this project is to bootstrap the term project to implement MIPS simulator, and to get familiar with our project assignment submission system.


### Problem Specification

As the term project, we will implement a MIPS instruction simulator. To that end, you should firstly make the simulator to understand user inputs and commands.

In this project, the framework passes input strings, and your task is to **split input strings into command tokens**. A string is defined as a sequence of characters which is terminated with `\0`.  A command token is defined as a sequence of characters without whitespaces, where the whitespaces include spaces(' ') and tab characters('`\t`').

For example, if the input string is " Hello   world ", the command tokes are "Hello" and "world". Note that both tokens do not include any space character. Another example is, if the input string is "add   t0   t1   t2", it should be broken into "add", "t0", "t1", and "t2".

This feature should be implemented in `parse_command()` function. The user input is passed through `command`. After parsing `command` into tokens, they should be assigned to `tokens[]` in order, which is passed as the parameter of the function. Also, the number of tokens should be assigined to `*nr_tokens`.

Below diagram illustrates the correct results for an input string "  add t0  t1  t2  ". Note that each token is also string which should be terminated with `\0`.

```c
char *command   --> "  add t0  t1  t2  "
 
*nr_tokens = 4
tokens[0]  -->  "add"
tokens[1]  -->  "t0"
tokens[2]  -->  "t1"
tokens[3]  -->  "t2"
tokens[4]... = NULL
```


### Skeleton Code

You can start this program assignment by cloning this repository or download zipped file from https://github.com/sslab-ajou/sce212-pa0-2019f . Everything is in `pa0.c`. Please do not modify the main function, but implement your code in in `parse_command` function.

All submission and grading are done automatically through https://sslab.ajou.ac.kr/pasubmit. Please follow the instruction explained in the class.


### Restrictions

- You **should not use any string manipulation function from other libraries**. The restriction includes `strtok, strtok_r, strlen, fscanf`  and/or similars. This means you should implement your own string manipulation function if it is needed. You will get 0 point if you use any of them. Note that `malloc()` and `free()` is OK to use.
- Do not `fprintf(stderr ...)` otherwise the grading system cannot grade your submission properly.


### Logistics

- This is an individual project; you work on the assignement alone.
- This is an OS/architecture-independent project; you may use Visual Studio on Windows or gcc on Linux. However, the grading will be done on a Linux machine. So, write code as neutral as possible to compilers.
- **Due is on 11:59pm, September 18 (Wednesday)**
- Submit only the pa0.c file to the submission server at https://sslab.ajou.ac.kr/pasubmit.
- You can use **up to 4 slip days during this semester**.


### Tips

- Make sure each string is terminated with '\0'.
- Briefly speaking, the implementation might look like this; scans from the beginning of `command` skipping all whitespaces until it meets a non-whitespace character. That will be the beginning of the token. Then, resumes scanning until it meets any whitespace character (' ' or '`\t`'). That will be the end of the token. Repeat this procedure until it finishes scanning `command`.
- May post on QnA board on AjouBb to question about the project.


Good luck and have fun!
