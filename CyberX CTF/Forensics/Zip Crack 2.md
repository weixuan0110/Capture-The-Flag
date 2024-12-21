# ZipCrack 2: The Champion Lock
## Step by Step Solve
---
* this make me frustrated and at the end just found out a word in upper case causing fail .....
1. First download the attachment for the challenge.
2. Same as the last question it need to use 7z to unzip. But this time, hint is using the LOL Champions name.
3. Im not a LOL player so, i go online search what is champion and blablabla~, and found out champions is a character of the LOL Games.
4. Ok now have the hint, i try go GPT to let it list it our for me all champions name 100+ and make it a wordlist (.txt)
5. Last, use john to bruteforce the zipfile answer using the command
   ```zip2john champion.zip > hash_flag2.txt```
   ```john --wordlist=lol_wordlist.txt hash_flag2.txt```
6. And we found out the password for this file is
   - ![image](https://github.com/user-attachments/assets/02af9e4f-3dc4-455b-83b1-e3937200acbd)
   - Credit to my teammates Ching Yang to find out, as my wordlist is with uppercase in the first character.......
7. use 7z to unzip it and we can see the flag is inside Yay!
   - ![image](https://github.com/user-attachments/assets/747118fd-d46b-4736-95b8-055d58d15c86)
8. There you go the flag!!

