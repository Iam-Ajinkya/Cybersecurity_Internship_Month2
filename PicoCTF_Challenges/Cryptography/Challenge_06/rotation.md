# rotation

- [Challenge information](#challenge-information)
- [CyberChef solution](#cyberchef-solution)
- [Python solution](#python-solution)
- [Learning Outcome from the Rotation Challenge](#learning-outcome)
- [References](#references)

## Challenge information
```
Points: 100
Tags: picoCTF 2023, Cryptography
Author: LOIC SHEMA
 
Description:
You will find the flag after decrypting this file

Download the encrypted flag here.

Hints:
1. Sometimes rotation is right
```
Challenge link: [https://play.picoctf.org/practice/challenge/373](https://play.picoctf.org/practice/challenge/373)

## CyberChef solution

Open the file in [CyberChef](https://gchq.github.io/CyberChef/) and use the 'ROT13' recipe.  
The default rotation is 13 steps. Change the amount until you find the flag. The correct amount is 18.

## Python solution

Even though it takes a bit longer time it's more fun to write a small python script called `solve.py` to bruteforce the challenge.

```python
#!/usr/bin/python

import string

alphabet = string.ascii_lowercase
alpha_len = len(alphabet)

def shift(cipher_text, key):
    result = ''
    for c in cipher_text:
        if c.islower():
            result += alphabet[(alphabet.index(c) + key) % alpha_len]
        elif c.isupper():
            result += alphabet[(alphabet.index(c.lower()) + key) % alpha_len].upper()
        else:
            result += c
    return result

# Read the encoded flag
with open("encrypted.txt", 'r') as fh:
    enc_flag = fh.read().strip()

for i in range(1, alpha_len+1):
    plain = shift(enc_flag, i)
    if ('picoCTF' in plain):
        print("ROT-%02d: %s" % (i, plain))
```

Then make the script executable and run it
```
┌──(kali㉿kali)-[/picoCTF/picoCTF_2023/Cryptography/rotation]
└─$ chmod +x solve.py

┌──(kali㉿kali)-[/picoCTF/picoCTF_2023/Cryptography/rotation]
└─$ ./solve.py
ROT-18: picoCTF{<REDACTED>}
```
# Learning Outcome

- Understand the concept of rotation ciphers and how they are used for encryption and decryption.
- Learn how to apply the ROT13 and other rotation techniques using tools like CyberChef.
- Gain experience in writing a Python script to automate the process of brute-forcing rotation ciphers.
- Develop skills in identifying patterns in encrypted text that lead to the flag, particularly recognizing keywords.
- Familiarize with the practical application of string manipulation and indexing in Python for cryptographic challenges.


For additional information, please see the references below.

## References

- [Wikipedia - ROT13](https://en.wikipedia.org/wiki/ROT13)