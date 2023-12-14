# New Caesar
## Description
We found a brand new type of encryption, can you break the secret code? (Wrap with picoCTF{})
**kjlijdliljhdjdhfkfkhhjkkhhkihlhnhghekfhmhjhkhfhekfkkkjkghghjhlhghmhhhfkikfkfhm** **new_caesar.py**

## Approach
![image](https://github.com/pixie-nukes/picoCTF/assets/94845416/65ffee58-d9cf-4b46-b871-9f3b4d813129)

1. The assert statements show that the key needs to be one character and be a letter between a to p.
2. Using enumerate loops through the values of b16, assigning i to the index at a particular point and c the value.
3. The function shift returns a value in ALPHABET at the index ascii value of the c minus 97 plus the ascii value of the key minus 97 mod 16.

I edited the code a bit like this and applie dthe cipher text like this:
![image](https://github.com/pixie-nukes/picoCTF/assets/94845416/ece5a059-d615-46c0-8f12-7c97834cd81f)

After running the code, I got this:
![image](https://github.com/pixie-nukes/picoCTF/assets/94845416/7a8de320-fc5c-4f67-9175-7ca0fad2b020)


## Output
**picoCTF{et_tu?_1ac5f3d7920a85610afeb2572831daa8}**

# miniRSA
## Description
What happens if you have a small exponent? There is a twist though, we padded the plaintext so that (M ** e) is just barely larger than N. Let's decrypt this: **ciphertext**

## Approach
![image](https://github.com/pixie-nukes/picoCTF/assets/94845416/3f4f0cf9-3dc3-460a-85f2-77cce960ee11)


In RSA, `M**3` mod n = c. 
This can also be written as M**3 = tn + c for some t.
So, this means that M = iroot(tn+c, 3). 
I just need to find the right t. 
Given that (M ** 3) is only "barely" larger than n.
> I wrote a python code to decode the cipher text.

> ` sudo apt-get install -y python3-gmpy2` if you don't have gmpy2
![image](https://github.com/pixie-nukes/picoCTF/assets/94845416/08bc0c25-1290-48ef-ba4b-07fb07d2b112)

Found the Flag!

## Output
![image](https://github.com/pixie-nukes/picoCTF/assets/94845416/4d23ac27-c029-4b0c-b4b9-fff0d19a2fd3)
 **picoCTF{e_sh0u1d_b3_lArg3r_a166c1e3}**

# Baseic-Mod1
## Description
We found this weird message being passed around on the servers, we think we have a working decryption scheme.
Download the message here.
Take each number mod 37 and map it to the following character set: 0-25 is the alphabet (uppercase), 26-35 are the decimal digits, and 36 is an underscore.
Wrap your decrypted message in the picoCTF flag format (i.e. picoCTF{decrypted_message})

## Approach
What is Mod 37?
> To find 37 mod 37 using the Modulo Method, we first divide the Dividend (37) by the Divisor (37).
>  Second, we multiply the Whole part of the Quotient in the previous step by the Divisor (37).
>  Then finally, we subtract the answer in the second step from the Dividend (37) to get the answer. Here is the math to illustrate how to get 37 mod 37 using our Modulo Method:
>  37 ÷ 37 = 1
>  1 × 37 = 37
>  37 - 37 = 0
>  Thus, the answer to "What is 37 mod 37?" is 0.

Doing this manually is not a good solution so I wroe a Python script to do all these steps to decrypt this message.
![Screenshot from 2023-11-10 09-27-41](https://github.com/pixie-nukes/picoCTF/assets/94845416/58187cce-ba70-4920-99b9-31c1823b4aaa)

For the python script i referred to this [website](https://programmingfire.com/picoctf-2022-cryptography-basic-mod1)


## Output 
> picoCTF{R0UND_N_R0UND_79C18FB3}
