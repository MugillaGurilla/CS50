# 0: How Computers Talk

Computer Science is fundamentally about problem solving. Off the back of that, computational thinking will always look something like this…..

![Screenshot 2023-01-18 at 09.58.39.png](0%20How%20Computers%20Talk%20476f7574f4d44bffa8abe20fe63e01cd/Screenshot_2023-01-18_at_09.58.39.png)

************Binary************

Computers use binary as their base language and binary is represented as either 0, or 1. Each grouping is called a bit, and every bit can either be a 0 or a 1. 

Numbers in computers are built up using a combination of 2 to various powers. 

- 2^0 = 1, 2^1 = 2, 2^2 = 4, 2^3 = 8, 2^4 = 16

Taking the first three 2^0, 2^1, 2^2 you can count up to 7, but you can’t get to 8 because 1, 2, 4 can only ever be combined to reach 7. Luckily, if you add in the number in the sequence, 2^3, you can get 8.

This will then run out when you reach 15, but luckily 2^4 is 16. This will run out at 31, but 2^5 is 31. So on and so forth. 

*Note: It’s probably better to think of 2^5 as 2*2*2*2*2, because 5 doesn’t exist in computer languages… (I think?)*

****************************Bits and Bytes****************************

A bit a 0 or 1. A byte is an octet, so 8 bits. 

```css
00000000 = 0
11111111 = 255
01101011 = 153
```

**Letters as bytes**

Letters are represented by numbers in the form of bytes so… The standardisation for all this is called **ASCII**

```css
01000001 = 65 and 65 represents A
01000010 = 66 and 66 represents B
00010001 = 33 and 33 represents !
```

The full ASCII, or *American Standard Code for Information Interchange,* is here… Take a look at the column beginning 64.

![Untitled](0%20How%20Computers%20Talk%20476f7574f4d44bffa8abe20fe63e01cd/Untitled.png)

**UNICODE**

ASCII is great for english but not for any most other languages. Unicode’s goal is expand ASCII to accommodate all language characters. It uses 4 bytes but that represents 32 billion possibilities which is way more than any language will ever need so some of the space is taken up with niche things like emojis. 

```css
11110000100111111001100010000010 = 4036991106 
= 😂
```

If you have ever gotten the empty rectangle emoji it most likely means that the unicode on your phone or device hasn’t been updated to know what the latest emoji characters are.

**RGB**

RGB is also represented with bytes. The max amount of Red, Green or Blue you can have in a colour created using RGB is 255. Remember that number from anywhere? It’s the max value of a byte. To create the colour, the computer literally just puts a certain amount of red, green and blue light together and renders the output. 

RGB (255, 255, 255) is white and RGB (0,0,0) is black. 

**Summary**

There are tonnes of ways to represent things like images, videos, numbers, letters, audio, but there are all built upon bytes and binary data.

**Data Search Algorithms**

Imagine you’ve a phone book with 1000 pages and want to find Jerry Twat. If you went through every single page, you’d have to go through 1000 pages. If you go through every second page, and then change to every first page, as you get closer to ‘J’, you’ll have to go through roughly 500 pages. Both are inefficient and represented by the red and yellow lines. 

However, if you open the phone in the middle and land on page M, you know to go to the middle of the left and you might get ‘H’. then go to the middle of the right and land of ‘J.’ The beauty of this data search method is that it is unbelievable scalable. It’s basically just as fast for big datasets as it is for massive datasets. It’s represented here by the green line and the pseudocode in below. 

![Relationship between solve time and dataset size](0%20How%20Computers%20Talk%20476f7574f4d44bffa8abe20fe63e01cd/Screenshot_2023-01-18_at_10.59.11.png)

Relationship between solve time and dataset size

![Pseudocode for binary tree-esque searching a phone book ](0%20How%20Computers%20Talk%20476f7574f4d44bffa8abe20fe63e01cd/Screenshot_2023-01-18_at_11.05.40.png)

Pseudocode for binary tree-esque searching a phone book