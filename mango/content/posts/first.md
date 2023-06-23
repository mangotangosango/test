---
title: "OverTheWire.org Bandit Level11 Walkthrough"
date: 2023-01-13T8:03:45+03:00
draft: false
---

Hello! OverTheWire.org is a series of challenges that helps you develop security concepts in for of games. I had a slight difficulty with Bandit Level 11 so I’ve decided to write it out here.

In this level we are told that the password is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions. When we run ```cat data.txt```, this is what we get:

```Gur cnffjbeq vf WIAOOSFzMjXXBC0KoSKBbJ8puQm5lIEi```

As we are told, all of the lowercase and uppercase letters are rotated by 13 positions, or in other words [`ROT13`](https://simple.wikipedia.org/wiki/ROT13). Below is a visual explanation of ```ROT13```.

![ROT13](/first/41806.png)

So, in order to get the password, we need to decode the encoded letters back by 13 positions.

Alright how can we do that? If we go back to the website, we are given some commands as hints.
![Commands](/first/screenshot-2023-01-14-014526.png)

We used the ```base64``` command in level 10 so we cancel that and what’s before it. And with a simple ```whatis tr``` command, we can assume that the ```tr``` command will be used.

In the end, the command ```tr "A-Za-z" "N-ZA-Mn-za-m"``` will be used to retreive our command.

To break down the command in simple terms, we will be using the command to:
Bring out the alphabets from A-Z and a-z, and swap it with N-Z(note that letter N is the 14th letter and M is the 13th letter) and A-M and likewise with the lower case letters.

Here is a visual explanation of A-Z swapping with N-M.
![swap](/images/first/azswap.png)

Result after we enter ```tr "A-Za-z" "N-ZA-Mn-za-m"``` : 
```The password is JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv```