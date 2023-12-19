# Memories of Christmas Past 
## Scenario:
Throughout the merger, we have detected some worrying coding practices from the South Pole elves. To ensure their code is up to our standards, some Frostlings from the South Pole will undergo a quick training session about memory corruption vulnerabilities, all courtesy of the B team. Welcome to the training!

## Tasks:
### 1. If the coins variable had the in-memory value in the image below, how many coins would you have in the game?
![image](https://github.com/pixie-nukes/JTP23-WriteUps/assets/94845416/529307e1-3133-44f3-8586-99be1f4785dc)
I used a hex editor to decode `53504f4f`

Ans: 1397772111

### 2. What is the value of the final flag?
First I need to fix the valueinside the memory space.

Change the Value of the name to
1. 12 times A
2. 4 times B
3. 12 times C
4. 12 times D
5. 4 times E
6. 123456789abcdef0

By interacting with the tree, i got the flag.
Ans: THM{mchoneybell_is_the_real_star}
