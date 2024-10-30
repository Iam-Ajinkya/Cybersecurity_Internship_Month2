# basic-mod1

- [Challenge information](#challenge-information)
- [Solution](#solution)
- [Learning Outcome from the Basic Mod1 Challenge](#learning-outcome)
- [References](#references)

## Challenge information
```
Points: 100
Tags: picoCTF 2022, Cryptography
Author: WILL HONG

Description:
We found this weird message being passed around on the servers, we think we have a working decryption scheme.
Download the message here.
 
Take each number mod 37 and map it to the following character set: 0-25 is the alphabet (uppercase), 
26-35 are the decimal digits, and 36 is an underscore.
 
Wrap your decrypted message in the picoCTF flag format (i.e. picoCTF{decrypted_message})

Hints:
1. Do you know what mod 37 means?
2. mod 37 means modulo 37. It gives the remainder of a number after being divided by 37.
```
Challenge link: [https://play.picoctf.org/practice/challenge/253](https://play.picoctf.org/practice/challenge/253)

## Solution

Let's use the instructions above to create a small Python script called `get_flag.py` to solve this challenge

```python
#!/usr/bin/python

# Read the encoded flag as string
with open("message.txt", 'r') as fh:
    enc_string = fh.read().strip()

# Convert to array of numbers
enc_numbers = map(int, enc_string.split())

# Create decode array
base_37 = []
for i in range(26):
    base_37 += chr(ord('A') + i)
for i in range(10):
    base_37 += chr(ord('0') + i)
base_37 += '_'

# Decode flag and print it
flag = []
for x in enc_numbers:
    flag += base_37[x % 37]
print('picoCTF{%s}' % "".join(flag))
```

Then make the script executable and run it
```
┌──(kali㉿kali)-[/picoCTF/picoCTF_2022/Cryptography/Basic_Mod1]
└─$ chmod +x get_flag.py  

┌──(kali㉿kali)-[/picoCTF/picoCTF_2022/Cryptography/Basic_Mod1]
└─$ ./get_flag.py
picoCTF{<REDACTED>}
```

# Learning Outcome

- Understand the concept of modular arithmetic, specifically modulo 37, and its application in decoding messages.
- Learn how to map numeric values to a specific character set, including uppercase letters, digits, and special characters.
- Gain experience in reading from files and processing strings in Python to manipulate encoded data.
- Develop skills in constructing algorithms to decode messages based on provided schemes.
- Familiarize with the picoCTF flag format and how to wrap decoded messages appropriately.


For additional information, please see the references below.

## References

- [Wikipedia - Modulo](https://en.wikipedia.org/wiki/Modulo)