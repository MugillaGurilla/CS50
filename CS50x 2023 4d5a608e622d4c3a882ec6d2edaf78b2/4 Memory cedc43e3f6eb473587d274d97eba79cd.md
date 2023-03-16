# 4: Memory

***RGB***

RGB uses up to 255 bit or exactly 8 bytes to render colours. 255, 255, 255 is white.

***Hexadecimal***

Hexadecimal, or base 16, uses 16 single digits - 1,2,3,4,5,6,7,8,9,A,B,C,E,D,F. 

- 0D = 13
- 0A = 10
- 0F = 15
- 10 = 16
- 1F = 31
- FF = 255

Hexadecimal is basically just a more succinct and user friendly way to express binary. So 11111111 is also FF because F is 1111. #FFFFFF is basically just a redefinition of RGB 255, 255, 255 - each set of FF means 255. 

Memory locations are defined using hexadecimal. You may recognize something like 0x7e or 0x1f or 0x123 (pronounced Oh Ex Twelve Three)

***Pointers***

In C, you can get a memory location using a & and you can go to a memory location using a . C is a very low level language and most languages don't have these pointers.

```c
// Both these print the exact same 

int n = 50;
printf("%p\n", &n)
// p stands for pointer

int *p = &n
printf("%p\n", p)
// the star here tells C, that p is a special 
// type of integer - a memory address
```

You could theoretically have a pointer to a pointer, because a pointer is just an integer with a value equivalent to a memory address, something like int **p would get the memory address of the pointer *p. This information is readily available but mostly useless. 

***Memory Addresses***

For a string s = “HI!\0”, which has four characters, the memory addresses could be 0x123, 0x124, 0x125, 0x126. Therefore it could be redefined as char *s = “HI!\0”

For CS50 purposes, this was used to redefine ‘’char **” as ‘’string”. This just creates a synonym for cha*r *

```c
typedef char *string
```

```c
int *p = &n
printf("%i\n", *p)
// this prints the memory location

char *s = "HI!"; 
printf("%p", s);
// this prints a memory location

char *s = "HI!"; 
printf("%s", s); 
// this prints "HI!"

char *s = "HI!";
printf("%p", &s[0]); 
printf("%p", &s[1]);
printf("%p", &s[2]);
printf("%p", &s[3]);
// this prints a series of memory addresses

char *s = "HI!";
printf("%c", &(s+2)); 
// this prints '!'
// when indexing a string, rhis is what actually happens under the hood

char *s = "HI!";
printf("%s", s+1); 
// this prints 'I!', or every character until it hts a '\0'
```

***Copying*** 

In C, = makes a hard copy. If t = s, any change made to t will be made to s, or vice versa.

***Malloc() & Free()***

The follow code assigns a new memory address equivalent to strlen(s) + 1 bytes for a string t. 

Whenever you allocate memory, you should always free memory after it's done with

```c
char *t = malloc(strlen(s) +1);

// do stuff with t

// finished with t

free(t)

//-------//

int *x= malloc(3 * sizeof(int));
x[0] = 72;
x[1] = 73;
x[2] = 33;

free(x)

// x = 'HI!'
```

Valgrind is good for figuring out memory related efficiency issues. 

```c
for (int i = 0, n = strlen(s) + 1; i < n; i++)
{
// blah

```

*Three rules.*

- *Every bit of memory that you malloc(), you should free()*
- *Only things that you malloc() should be free()d*
- *And never free memory more than once*

***Garbage Values***

A memory address or variable from previous programs can retain a previous value. 

It might well happen that when you define a new variable, it's memory address will coincidentally be the same as a previous variable's. If this address wasn't freed or reset to 0 or if you program doesn't initialize the new variable to 0, then this ‘’garbage value” could well be taken for the new variable's value. 

Try run the below and there may well be garbage values.. 

```c
int scores[1024];
for (int i = 0; i < 1024; i++)
{
    printf("%i\n", scores[i];
}
```

Most values will be 0 but a significant amount will be variable positive and negative integers. 

Ways to defend against this is free memory and always initialize variables 

***Heap and Stack***

These are important to learn about. Heap and Stack overflows come from these.

***Passing Values by Reference***

```c

int x = 1; 
int y = 2; 

print(x, y);
swap(&x,&y);
print(x,y);

// prints 1,2
// printa 2,1

void swap (int *a, int b*) 
{
    int tmp = *a; 
    *a = *b;
    *b = tmp;
}

// this doesnt change any values, it just changes where a and b are pointing
```

***get_string() but annoying*** 

```c
char s[4];
printf("s: ");
scanf("%s", s); 
printf("s: %s", s);
```