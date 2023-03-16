# 2: Arrays, Strings, CL Arguments, Exit Statuses, Scope

***Compiling***

There are four steps to running a computer program. 

- **Preprocessing**
- **Compiling**
- **Assembling**, this step turns the code into 0s and 1s.
- **Linking**, this step will link, for example, hello.c, stdio.h and cs50.h together

Collectively, they’re all known as compiling. 

Before human-like computer languages existed, people had to write code in assembly language, using 0s and 1s!!!!!!

***Debugging***

Choicely placed printf statements can help to debug. 

But the debugger in VS Code is better. This is the command to run the cs50 debugger.

```bash
make buggy0
debug50 ./buggy0
```

***Arrays***

There are three parts to an array declaration. Unlike strings and ints, arrays are always passed by reference/called as hard copies, so any changes made after the call will be passed back to the original. 

```c
#include <stdio.h>

type name[size];
int studentGrades[40];
double memorySizes[8];
bool truthTable[10];
bool truthTable[3] = { false, true, true };
```

There are two dimensional lists too.

```c
bool battleship[10][10];
```

In practice… 

```c
#include <cs50.h>
#include <stdio.h>

const int N = 3;

float average(int array[]);

int main(void) {
		int scores[N];
		for (int i = 0; i < N; i++) {
				scores[i] = get_int("Score: ");
		}
		printf("Average: %f\n", average(N, scores));
}

float average(, int length, int array[]) {
		
		int sum = 0;

		for (int i = 0; i < N; i++) {
				sum += array[i];
		}

		return sum / (float) length;
}

```

***Strings***

Strings are actually arrays of characters that are ‘strung’ together - hence the name. A string array differs from a normal array by always have a final element of of ‘\0’ as shown below. A string of 3 characters is stored in memory as 4 bytes because of the ‘\0’ character. 

```c
"Hi!" = ['H', 'i', '!', '\0']
```

For this reason, you can index strings. 

```c
int main(void) {
	string s = "HI!";
    printf("%i %i %i %i\n", s[0], s[1], s[2], s[3]);
}

// this prints out "72 73 33 0", the %i placeholder
// gets the ASCII number reference for 'H', I' '!" etc. 

int main(void) {
	string s = "HI!";
    printf("%c %c %c %c\n", s[0], s[1], s[2], s[3]);
}

// this prints out "H I ! ", the %c placeholder
// gets the character version of 'H', I' '!" etc,
// which is itself 

int main(void) {
	string s = "HI!";
    printf("%c %c %c %i\n", s[0], s[1], s[2], s[3]);
}

// this prints out "H I ! 0", the %c placeholder
// gets the character version of 'H', I' '!" etc,
// which is itself, and %i placeholder gets the
// ASCII or integer version of '\0'.
```

A handy function for returning the length of a string. This function takes advantage of the ‘\0’ character at the end of every single string. 

```c
string name = get_string("what's your name? ");

int n = 0;
while (name[n] != '\0') {
		n++;
}

print("%i\n", n);
```

A handy to uppercase a lowercase every letter in a string

```c
string s = get_string("Before: ");
printf("After:  ");

// this is where the function starts proper. 
for (int i = 0, n = strlen(s); i < n; i++)
{
		if (s[i] >= 'a' && s[i] <= 'z') 
		{
				printf("%c", s[i] - 32);
		}
		else 
		{
				printf("%c", s[i]);

		}
}
printf("\n");
```

***Command Line Arguments***

- *argc* = argument count
- *argv* = argument vector
    - *argv[0]* will always be the name of the program, something like ‘./greedy’.
    - argv[argc-1] will always be the last argument given at the command line.
    - Every argument given at the command line will be stored as a string, even if it’s something like 2048 that looks like a integer. You can’t put “” or ‘’ on the command line but it’s assumed it’s a string.

```c
#include <stdio.h>
#include <cs50.h>
#include <string.h>

int main(int argc, string argv[])
{
    if (argc == 2) {
        printf("hello, %s!\n", argv[1]);
    }
    else {
        printf("hello, world\n");
    }
}

// command lines
make greet
./greet Cormac

// prints out 'hello, Cormac!'
```

***Exit Statuses***

The return1 and return 0 lines here are known as exit statuses. They can be accessed using ‘echo $?’ after a program has be run.

```c
#include <stdio.h>
#include <cs50.h>
#include <string.h>

int main(int argc, string argv[])
{
    if (argc != 2) {
        printf("missing command line argument!!!!!!!!!!!\n");
				return 1;
    }
    else {
        printf("hello, %s!\n", argv[1]);
				return 0;
    }
}

// command lines
make greet
./greet
echo $?

// prints out 'missing command line argument!!!!!!!!!!'
// returns 1

// command lines
make greet
./greet Cormac
echo $?

// prints out 'hello, Cormac!'
// returns 0

```

***Functions***

While functions and methods do very similar things, that is, take a couple inputs, processed them and gives outputs, functions are independent while methods need to be attached to specific objects. 

When developers use functions, they don’t really care how they work after they’ve been made. They only care that they ***do*** work, and, to some extent, what inputs they can take. 

All functions follow this format 

```c
return type name (arguments)
```

```c
int multiplyTwoInts(int num1, int num2)

float multiplyTwoFloats(float num1, float num2)
{
	return num1 * num2;
}

int addTwoInts(int num1, int num2) 
{
	return num1 + num2;
}
```

***Scope***

- In C, variables are only accessible within the set of curly braces in which they’re declared. They can go inward but they can’t got outward.
- When calling a local variable, a soft copy of the variable is made so the original will always remain unchanged. local variables can of course be changed by new assignments.
- There are of course global variables and constants which are both fully accessible anywhere in the program.
- When calling a global variable, a hard copy is made and any changes to that variable made hence will effect the global variable. This is different to a constant which is also fully accessible but also immutable and unchangeable.