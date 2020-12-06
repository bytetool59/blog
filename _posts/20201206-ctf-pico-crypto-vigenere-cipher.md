---
title: 'Easy1 - Vigenère Cipher - picoCTF'
coverImage: '/assets/blog/hello-world/20201206-Vigenere-Cipher.png'
excerpt: "Have you ever heard of the Vigenère Cipher? It's a very interesting cryptographic method and what this challenge is all about."
date: '2020-12-06'
author:
  name: Mr. Byte 
  picture: '/assets/blog/authors/mr-byte.jpeg'
ogImage:
  url: '/assets/blog/hello-world/20201206-Vigenere-Cipher.png'
---

## Description
The one time pad can be cryptographically secure, but not when you know the key. Can you solve this? We've given you the encrypted flag, key, and a table to help **UFJKXQZQUNB** with the key of **SOLVECRYPTO**. Can you use this table to solve it?.

<script src="https://gist.github.com/bytetool59/24da2fc80fe55de9ffba8534550801c1.js"></script>

## Solution
As the name implies this is a lookup table. This means we need to find a corresponding combination to get to the key.

The table provided matches to the [Vigenère Cipher](https://pages.mtu.edu/~shene/NSF-4/Tutorial/VIG/Vig-Base.html). Let me show you how it works:
> **Tip**: if you are using VIM/NVIM as your editor, you can highlight the current color and row with ':set cursorline' and ':set cursorcolumn'

1. The table has all the letters in the English Alphabet in both axis (x and y)

2. You need a *key* and a *message* to be encrypted.

3. Both of them need to be the same size.
>> Wait, what? How can I transmit the key for a really long message? It is unpractical! Don't worry, we'll see that in a bit.

3. The encrypted message is the intersection of the two corresponding columns. At the Y pos you use the encrypted key and the X the message you want to encrypt.

## Let's go pratical
**Message:** UFJKXQZQUNB (X axis)
**Key:**     SOLVECRYPTO (Y axis)

> Remember when I said they needed to have equal lengths? That's where it will come handy.
## Step by step
To decrypt the next, you need to have the encrypted message and the key.
Let's take the letter *U* from the enc_message, for example.

1. The corresponding letter in the key (put them one bellow the other; repeat if it is shorter than the message) is S.

2. Find the letter *U* in the line *S*

3. The column you are in is the decrypted letter, in our case, *C*. Easy right?
---
Let's do this process letter by letter.

UFJKXQZQUNB -> encrypted message

SOLVECRYPTO -> key

CRYPTOISFUN -> decrypted message
## Flag
picoCTF{CRYPTOISFUN}

