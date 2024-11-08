# Python Wrangling

- [Challenge information](#challenge-information)
- [Solution](#solution)
- [Learning Outcome from the Python Wrangling Challenge](#learning-outcome-from-the-python-wrangling-challenge)
- [References](#references)

## Challenge information
```
Points: 10
Tags: picoCTF 2021, General Skills
Author: SYREAL

Description:
Python scripts are invoked kind of like programs in the Terminal... 
Can you run this Python script using this password to get the flag?
 
Hints:
1. Get the Python script accessible in your shell by entering the following command in the Terminal prompt: 
   $ wget https://mercury.picoctf.net/static/1b247b1631eb377d9392bfa4871b2eb1/ende.py
2. $ man python
```
Challenge link: [https://play.picoctf.org/practice/challenge/166](https://play.picoctf.org/practice/challenge/166)

## Solution

Given in the challenge are:
* A python script to run
* A file with a password
* A file with an encrypted flag

Check out the Python script if you like but there is no need for that to solve the challenge.  
This challenge is just an exercise in running Python scripts.

Run the Python script like this
```bash
┌──(kali㉿kali)-[/mnt/…/picoCTF/picoCTF_2021/General_Skills/Python_Wrangling]
└─$ python ende.py         
Usage: ende.py (-e/-d) [file]
```

Ah, we need to supply the script with parameters. The `-e` probably stands for encrypt and `-d` for decrypt and we want to decrypt.

So get the password
```bash
┌──(kali㉿kali)-[/mnt/…/picoCTF/picoCTF_2021/General_Skills/Python_Wrangling]
└─$ cat pw.txt 
dbd1bea4dbd1bea4dbd1bea4dbd1bea4
```

And then decrypt the flag
```bash
┌──(kali㉿kali)-[/mnt/…/picoCTF/picoCTF_2021/General_Skills/Python_Wrangling]
└─$ python ende.py -d flag.txt.en 
Please enter the password:dbd1bea4dbd1bea4dbd1bea4dbd1bea4
picoCTF{<REDACTED>}
```

And there we have the flag.

## Learning Outcome from the Python Wrangling Challenge

- Learned to execute Python scripts in the command line with specific arguments.
- Gained experience using flags (`-d` for decryption) with Python scripts to perform operations on encrypted files.
- Practiced retrieving and using password data stored in text files for program input.
- Reinforced understanding of basic decryption steps and using command-line utilities for CTF challenges.

For additional information, please see the references below.

## References

- [cat - Linux manual page](https://man7.org/linux/man-pages/man1/cat.1.html)
- [python - Linux manual page](https://linux.die.net/man/1/python)