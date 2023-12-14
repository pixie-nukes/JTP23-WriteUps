# Keygenme-py 
## Description
Description
[keygenme-trial.py]

## Approach
I opened the file using `cat keygenme-trial.py` and read the code.
- this part was looking off
  ```python
    key_part_static1_trial = "picoCTF{1n_7h3_|<3y_of_"
    key_part_dynamic1_trial = "xxxxxxxx"
    key_part_static2_trial = "}"
    key_full_template_trial = key_part_static1_trial + key_part_dynamic1_trial + key_part_static2_trial
  ```

- After reading the code completely i understood that, first part of the flag is "picoCTF{1n_7h3_|<3y_of_" and key is the same length as "picoCTF{1n_7h3_|<3y_of_xxxxxxxx}".
- The code is saying that there are 8 more if statements left to write in the function, and each if statement will check the value of the variable `x` against a different character in the string `45362718`.
  The code then uses a loop to iterate over the remaining characters in the string, and for each character, it sets the value of the variable `key[i]` to the corresponding character.
- I ran the following code in an online compiler
  ```python
  import hashlib
  username_trial = "GOUGH"
  bUsername_trial = b"GOUGH"

  key_part_static1_trial = "picoCTF{1n_7h3_|<3y_of_"
  key_part_dynamic1_trial = "xxxxxxxx"
  key_part_static2_trial = "}"
  key_full_template_trial = key_part_static1_trial + key_part_dynamic1_trial + key_part_static2_trial

  #I used bUsername_trial because enter_liscence used it as well but after testing afterwards, they output the same answer
  print(hashlib.sha256(bUsername_trial).hexdigest()[4]) 
  print(hashlib.sha256(bUsername_trial).hexdigest()[5])
  print(hashlib.sha256(bUsername_trial).hexdigest()[3])
  print(hashlib.sha256(bUsername_trial).hexdigest()[6])
  print(hashlib.sha256(bUsername_trial).hexdigest()[2])
  print(hashlib.sha256(bUsername_trial).hexdigest()[7])
  print(hashlib.sha256(bUsername_trial).hexdigest()[1])
  print(hashlib.sha256(bUsername_trial).hexdigest()[8])
  ```

The output is `f911a486`

## Output
We can now complete the flag: `picoCTF{1n_7h3_|<3y_of_xxxxxxxx} --> picoCTF{1n_7h3_|<3y_of_f911a486}`
So the flag is `picoCTF{1n_7h3_|<3y_of_f911a486}`

# GDB Baby Step 1
## Description
Can you figure out what is in the eax register at the end of the main function?
Put your answer in the picoCTF flag format: picoCTF{n} where n is the contents of the eax register in the decimal number base.
If the answer was 0x11 your flag would be picoCTF{17}. Disassemble this.

## Approach
> file debugger0_a
![Screenshot from 2023-11-10 08-39-01](https://github.com/pixie-nukes/picoCTF/assets/94845416/14a9e9ee-e71c-4a28-bb47-48756d1a7307)

Let’s begin by opening the downloaded file by passing it as an argument to GDB:
> gdb debugger0_a

for knowing more of the functions:
> info functions

The prime target here is the ‘main‘ function (address 0x1129).
Before proceeding, the gdb syntax is set to AT&T by default so i need to change it to intel which is more familliar to me.
> set disassembly-flavor intel
> disassemble main
![Screenshot from 2023-11-10 08-43-04](https://github.com/pixie-nukes/picoCTF/assets/94845416/e9eaf994-bbac-48aa-b174-3e8c6a74cba4)

I now found the eax registered value, so i used an python compiler to transform to hexadecimal value into a deimal, I did the following:
> print(int(0x86342))
Result: 549698


## Output
picoCTF{549698}

# ARMssembly 0
## Description
What integer does this program print with arguments 182476535 and 3742084308? 

File: `chall.S` Flag format: picoCTF{XXXXXXXX} -> (hex, lowercase, no 0x, and 32 bits. ex. 5614267 would be picoCTF{0055aabb})

## References
I used this sites to know about how arm assembly works
1. [Instruction Set](https://azeria-labs.com/arm-instruction-set-part-3/)
2. [Architecture](https://developer.arm.com/documentation/ddi0487/latest)

I used the below site to learn how to cross compile ARM assembly on x86
1. [ARMv8 via Command Line](https://github.com/joebobmiles/ARMv8ViaLinuxCommandline)

## Approach
Installing a Cross Compiler
> `$ sudo apt install binutils-aarch64-linux-gnu`

Compiling ARMv8
> `aarch64-linux-gnu-as -o chall.o chall.S`
> `aarch64-linux-gnu-gcc -static -o chall chall.o`

I need to install a version of QEMU that runs statically in the background with `sudo apt install qemu-user-static` so I can run ARM binaries like normal programs.

Finally, I can run the challenge binary with the two provided arguments: `./chall 182476535 3742084308`

>Result: 3742084308

The flag format should be in hexadecimal according to the question so I can use a hexadecimal convertor like [Rapid Tables](https://www.rapidtables.com/convert/number/decimal-to-hex.html)

>Result: df0bacd4

## Output
Flag format: picoCTF{XXXXXXXX} -> (hex, lowercase, no 0x, and 32 bits
So,
>picoCTF{df0bacd4}
