# substitution1

- [Challenge information](#challenge-information)
- [Solution](#solution)
- [Learning Outcome from the Substitution1 Challenge](#learning-outcome)
- [References](#references)

## Challenge information
```
Points: 100
Tags: picoCTF 2022, Cryptography, Substitution_cipher
Author: WILL HONG
 
Description:
A second message has come in the mail, and it seems almost identical to the first one. 
Maybe the same thing will work again.

Download the message here.

Hints:
1. Try a frequency attack
2. Do the punctuation and the individual words help you make any substitutions?
```
Challenge link: [https://play.picoctf.org/practice/challenge/308](https://play.picoctf.org/practice/challenge/308)

## Solution

The message we were given looks like this (with line breaks added)
```
WYHg (gzray hra wimybas yzs hvij) ias i yums rh wrombysa gswbakyu wromsykykrl. Wrlysgyilyg ias 
masgslysn dkyz i gsy rh wzivvsljsg dzkwz ysgy yzska wasiykxkyu, yswzlkwiv (iln jrrjvklj) gckvvg, 
iln marqvso-grvxklj iqkvkyu. Wzivvsljsg bgbivvu wrxsa i lboqsa rh wiysjraksg, iln dzsl grvxsn, 
siwz uksvng i gyaklj (wivvsn i hvij) dzkwz kg gbqokyysn yr il rlvkls gwraklj gsaxkws. WYHg ias 
i jasiy diu yr vsial i dkns iaaiu rh wrombysa gswbakyu gckvvg kl i gihs, vsjiv slxkarlosly, iln 
ias zrgysn iln mviusn qu oilu gswbakyu jarbmg iarbln yzs dravn hra hbl iln maiwykws. 
Hra yzkg marqvso, yzs hvij kg: mkwrWYH{HA3FB3LWU_4774WC5_4A3_W001_7II384QW}
```

Compared to the [previous challenge](substitution0.md) there is no key this time.

Let's use [quipqiup](https://quipqiup.com/) to solve this as before.

Input the entire message in the `Puzzle` text field and press `Solve` (with the default setting).

After a short while, you have the flag at the top of the possible solutions.

# Learning Outcome

- Recognize the similarities and differences between various substitution cipher challenges.
- Understand the process of frequency analysis and how it can be applied when a key is not provided.
- Gain experience in using online tools like Quipqiup to automate the decryption of substitution ciphers.
- Analyze the role of punctuation and word patterns in deciphering messages.
- Develop critical thinking skills in approaching cryptographic challenges with limited information.


For additional information, please see the references below.

## References

- [Wikipedia - Frequency analysis](https://en.wikipedia.org/wiki/Frequency_analysis)
- [Wikipedia - Letter frequency](https://en.wikipedia.org/wiki/Letter_frequency)
- [Wikipedia - Substitution cipher](https://en.wikipedia.org/wiki/Substitution_cipher)