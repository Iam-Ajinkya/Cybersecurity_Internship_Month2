# transposition-trial

- [Challenge information](#challenge-information)
- [Solution](#solution)
- [Learning Outcome from the Transposition Trial Challenge](#learning-outcome)
- [References](#references)

## Challenge information
```
Points: 100
Tags: picoCTF 2022, Cryptography, cryptography
Author: WILL HONG

Description:
Our data got corrupted on the way here. 
Luckily, nothing got replaced, but every block of 3 got scrambled around! 

The first word seems to be three letters long, maybe you can use that to recover the rest of the message.
Download the corrupted message here.

Hints:
1. Split the message up into blocks of 3 and see how the first block is scrambled
```
Challenge link: [https://play.picoctf.org/practice/challenge/312](https://play.picoctf.org/practice/challenge/312)

## Solution

The message given looks like this
```
heTfl g as iicpCTo{7F4NRP051N5_16_35P3X51N3_V091B0AE}2
```

It looks like in each block of three characters the first is shifted to the end of the block.

Let's write a small Python script called `solve.py` to decode this
```python
#!/usr/bin/python
# -*- coding: latin-1 -*-

encrypted_msg = "heTfl g as iicpCTo{7F4NRP051N5_16_35P3X51N3_V091B0AE}2"

i = 0
flag = ""

while i < len(encrypted_msg):
    flag += encrypted_msg[i+2]
    flag += encrypted_msg[i]
    flag += encrypted_msg[i+1]
    i += 3

print(flag)
```

Then make the script executable and run it
```bash
┌──(kali㉿kali)-[/picoCTF/picoCTF_2022/Cryptography/Transposition_trial]
└─$ chmod +x solve.py     
                                               
┌──(kali㉿kali)-[/picoCTF/picoCTF_2022/Cryptography/Transposition_trial]
└─$ ./solve.py
The flag is picoCTF{<REDACTED>}
```
# Learning Outcome

- Understand the principles of transposition ciphers and how data can be scrambled without any characters being replaced.
- Learn to identify patterns in scrambled data, particularly by analyzing how characters are rearranged within blocks.
- Gain experience in writing a Python script to decode messages by manipulating string indices.
- Develop problem-solving skills in reversing encryption processes through logical reasoning and experimentation.
- Familiarize with the application of block processing in cryptography, particularly in constructing and reconstructing messages.


For additional information, please see the references below.

## References

- [Wikipedia - Transposition cipher](https://en.wikipedia.org/wiki/Transposition_cipher)