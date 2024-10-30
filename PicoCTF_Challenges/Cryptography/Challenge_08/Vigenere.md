# Vigenere

- [Challenge information](#challenge-information)
- [Online solver solution](#online-solver-solution)
- [Python solution](#python-solution)
- [Learning Outcome from the Vigenère Challenge](#learning-outcome)
- [References](#references)

## Challenge information
```
Points: 100
Tags: picoCTF 2022, Cryptography
Author: MUBARAK MIKAIL

Description:
Can you decrypt this message?

Decrypt this message using this key "CYLAB".

Hints:
1. https://en.wikipedia.org/wiki/Vigen%C3%A8re_cipher
```
Challenge link: [https://play.picoctf.org/practice/challenge/316](https://play.picoctf.org/practice/challenge/316)

The message given looks like this
```
rgnoDVD{O0NU_WQ3_G1G3O3T3_A1AH3S_f85729e7}
```

There probably are more ways to solve this challenge, but here are two solutions.

## Online solver solution

You can use an online solver such as [Rumkin](https://rumkin.com/tools/cipher/vigenere/) to solve this challenge.

Set the 'Operating Mode' to `Decrypt` and set the 'Cipher key' to `CYLAB`.  
Then enter the cipher text in the large text field and you get the flag at the bottom of the window.

## Python solution

In addition, let's write a small Python script called `solve.py` to decode this
```python
#!/usr/bin/python
# -*- coding: latin-1 -*-

import string

cipher_text = "rgnoDVD{O0NU_WQ3_G1G3O3T3_A1AH3S_f85729e7}"
key = 'CYLAB'

universe = string.ascii_uppercase
uni_len = len(universe)

flag = ''
k_len = len(key)

i = 0
for c in cipher_text:
    if c.islower():
        txt_index = universe.index(c.upper())
        key_index = universe.index(key[i % k_len])
        i += 1
        flag += universe[(txt_index - key_index) % uni_len].lower()
    elif c.isupper():
        txt_index = universe.index(c)
        key_index = universe.index(key[i % k_len])
        i += 1
        flag += universe[(txt_index - key_index) % uni_len]
    else:
        flag += c    

print(flag)
```

Then make the script executable and run it
```bash
┌──(kali㉿kali)-[/picoCTF/picoCTF_2022/Cryptography/Vigenere]
└─$ chmod +x solve.py       

┌──(kali㉿kali)-[/picoCTF/picoCTF_2022/Cryptography/Vigenere]
└─$ ./solve.py         
picoCTF{<REDACTED>}
```

# Learning Outcome

- Understand the principles of the Vigenère cipher and its encryption/decryption mechanisms using a key.
- Learn how to use both online tools and custom Python scripts to solve cryptographic challenges.
- Gain practical experience in string manipulation and indexing in Python to implement decryption algorithms.
- Familiarize with the concept of character universes in encryption and how to handle both uppercase and lowercase letters.
- Develop problem-solving skills in applying cryptographic concepts to decode messages.


For additional information, please see the references below.

## References

- [Wikipedia - Vigenère cipher](https://en.wikipedia.org/wiki/Vigen%C3%A8re_cipher)