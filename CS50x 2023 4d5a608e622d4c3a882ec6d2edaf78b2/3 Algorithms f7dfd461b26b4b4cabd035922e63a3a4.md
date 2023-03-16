# 3: Algorithms

An algorithm is basically what a function does, under the hood. It’s good to think about code efficiency and this is the most efficiency to search a (sorted) array.

This binary search algorithm will know if a target value isn’t within the array when the end index value becomes smaller than the start array i.e the sub-array has a length of les than 0.

![pseudocode - binary search](3%20Algorithms%20f7dfd461b26b4b4cabd035922e63a3a4/Screenshot_2023-02-04_at_09.44.47.png)

pseudocode - binary search

***Big O Notation***

As you zoom further and further out, red and yellow start to look basically the same. 

The efficiency of the code above is shown by the green line. Look at that for scalability. 

![Screenshot 2023-02-04 at 09.49.30.png](3%20Algorithms%20f7dfd461b26b4b4cabd035922e63a3a4/Screenshot_2023-02-04_at_09.49.30.png)

***Big O***

In Big O notation, there are a few different way to abstract  code’s efficiency. Going from bad to good…

- O(n^2)
- O(n log n)
- O(n)^
- O(log n)*
- O(1)

**this is for binary search ^this is for linear search*

***Ω***

There is also Ω notation. Big O describes the worst case scenario for efficiency, while Ω notation describes the best case scenario for efficiency. 

- Ω(n^2)
- Ω(n log n)
- O(n)
- Ω(log n)
- Ω(1)*^

**this is for binary search and for linear search*

***Θ***

Finally, there is Θ notation which is a bit esoteric but it describes when efficiency is the same in the worst case as it is in the best case. An algorithm to count a group of people one at a time would be an example of this

- ***Θ***(n^2)
- ***Θ***(n log n)
- O(n)
- ***Θ***(log n)
- ***Θ***(1)

***Primitives***

In C, primitives are ints, floats, strings, longs, doubles etc. You can combine these together to make new data types or objects. C isn’t Object Oriented but this idea is the basis of Object Oriented Programming in other languages.

The code below defines a new data structure called person with a name and number string. 

```c
typedef struct
{
		string name;
		string number;
}
person;
```

*********************Sorting*********************

There are a few ways to sort an unsorted array.

- ***Selection sort***. This involves finding the smallest number in the array and swapping it with the first element. Then repeating by finding the second smallest and swapping that with the second element. Then repeating with third, fourth, fifth etc.
- *********************************************************************************Bubble sort.********************************************************************************* This involves taking the first two elements of the array and continually swapping until the list is sorted. The largest elements will ‘bubble’ its way up to the top of the list, hence the name. The computer will know when its sorted when it runs through the list and doesn’t have to do anything. It’s hard to explain but [watch this (good)](https://youtu.be/SXujiYWM9l8?t=4030) or [watch this (better)](https://youtu.be/RT-hUXUWQ2I?t=103). If a pass is made at an array and the swap counter still finishes at 0, you know that the array is sorted.

*Here follows a tangent……*

```c
For i from 0 to n-1
    Find smallest number between numbers[i] and numbers[n-1]
    Swap smallest number with numbers[i]
```

```c
Repeat n-1 times
    For i from 0 to n-2
        If numbers[i] and numbers[i+1] out of order
            Swap them
```

- O(n^2)*^
- O(n log n)
- O(n)
- O(log n)
- O(1)

**this is for selection sort  ^this is for bubble sort*

- Ω(n^2)*
- Ω(n log n)
- Ω(n)^
- Ω(log n)
- Ω(1)

**this is for selection sort  ^this is for bubble sort*

- ***Θ***(n^2)*
- ***Θ***(n log n)
- ***Θ***(n)
- ***Θ***(log n)
- ***Θ***(1)

**this is only for selection sort - it’s the same for O and* Ω

***TL;DR Both are shite, but bubble sort’s kinda better.***

***Recursion***

This function uses recursion to draw a half pyramid of #s. It makes use of the call stack to stack up a number of calls to draw() and then execute them with incrementing values of n. 

```c
void draw(int n)
{
    if (n <= 0 )
    {
        return;
    }
    
    draw(n - 1);

    for (int i = 0; i < n; i++)
    {
        printf("#");
    }
    printf("\n");
}
```

Right before the function actually prints anything this is what the call stack looks like. 

![Call Stack](3%20Algorithms%20f7dfd461b26b4b4cabd035922e63a3a4/Screenshot_2023-02-04_at_11.56.16.png)

Call Stack

![Output](3%20Algorithms%20f7dfd461b26b4b4cabd035922e63a3a4/Screenshot_2023-02-04_at_12.06.08.png)

Output

***Merge Sort***

So far we’ve had 

- **Bubble Sort**
- **Selection Sort**

But a far better way is 

- **Merge Sort.** Think of this as not one 6-element array, but six 1-element array and in this way it sorts the left half of an array, sorts the right half and then merges both. You take the smallest from the number from the two halves and put it into a new array until the two initial arrays and empty and the new array is full. This happens recursively until an array of any size is only of a number of arrays of size 1. Conceptually, merge sort only requires ‘positive strokes,’ it’s never going back and forth. [Watch this.](https://youtu.be/Ns7tGNbtvV4?t=213)
    
    ![pseudocode - merge sort](3%20Algorithms%20f7dfd461b26b4b4cabd035922e63a3a4/Screenshot_2023-02-04_at_12.08.58.png)
    
    pseudocode - merge sort
    
    ![visually - merge sort](3%20Algorithms%20f7dfd461b26b4b4cabd035922e63a3a4/Screenshot_2023-02-04_at_12.10.37.png)
    
    visually - merge sort
    
- O(n^2)
- O(n log n)*
- O(n)
- O(log n)
- O(1)

**this is for merge sort*

- Ω(n^2)
- Ω(n log n)
- Ω(n)^
- Ω(log n)
- Ω(1)

**this is for merge sort*

- ***Θ***(n^2)
- ***Θ***(n log n)*
- ***Θ***(n)
- ***Θ***(log n)
- ***Θ***(1)

**this is for merge sort - it’s the same for O and* Ω

TL;DR….

Technically, merge sort will use more RAM because it’ll need a lot of different arrays. There are trades offs with everything. With early computers, RAM was very very expensive so merge sort, while it may have been known about, wasn’t used. On large datasets, merge sort is definitely the way to go. It will require some up front capital but in the long run, it’s definitely worth it. 

[This is good for visualising the way and speed of sorting algorithms](https://www.cs.usfca.edu/~galles/visualization/ComparisonSort.html)