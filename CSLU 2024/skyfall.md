# Skyfall
# Step by step solve
---
*Pain killer, My Skill issue... XD*
1. Download the file attach by the challenge.
   -capture.pcapng
2. Use wireshark to open the pcapng files
3. See the clue given, Love the EDITED LEWIS VERSION files and lost the flag.
   - ![image](https://github.com/user-attachments/assets/9ec25fe0-ecd3-4587-a4e7-5887377fbfbe)
4. File -> Export -> Http, and save all the files.
5. we can see there is 5 files exported, 2 text file with word ```File received successfully!``` and ```file_data=16ae9187d13259788a97aef16a7d50f8b6376fbcba92a0f53e7e68d9f562a3a6576a3183a8dc8631c64fbd9147c8b608```
   - usefull for later
6. And there is a file with big data 24,345kb and let us see what file is that.
  - ![image](https://github.com/user-attachments/assets/395b8f53-8888-4af0-bf28-ae6f5b156992)
7. Looks like it is a elf file
  ![image](https://github.com/user-attachments/assets/a9223eb5-5494-4476-b76e-94ca61886bab)
8. I manage to find a website to extract the elf file [EzyZIP](https://www.ezyzip.com/open-extract-elf-file.html#)
9. We can see the largest file is here after extract
  - ![image](https://github.com/user-attachments/assets/d61f4dc0-bd2e-4e85-922c-cbaaa903fb5e)
    After have a long time searching, i cant found any ways to extract pydata... skill issue XD
10. After the end of the day, my friend told me there is something call ```Pyinstxtractor``` that can extract it.
    - ![image](https://github.com/user-attachments/assets/647ba1e4-5257-4eae-8e27-94885a3b018b)
    - This is what i found
11. okayyyy here is it
    - ![image](https://github.com/user-attachments/assets/839516f6-2d26-4c28-af8e-cfbd172314e6)
12. Theres alot files inside, but the one the name ```skyfall-lewis-edited-version.pyc``` is the most suspicious.
    - ![image](https://github.com/user-attachments/assets/b3e6721f-12fd-4eba-a1fc-7d8d92ac3bc0)
13. With the use of this website [Pylingual](https://pylingual.io/), i transfer pyc files to py
    - ![image](https://github.com/user-attachments/assets/575f7882-fe26-4d1c-91f5-69de17c6099c)
14. We can see it is a AES encyption function and the key is the time which the user encrypt when downloaded, so lets go back to wireshark and find the date when she successfuly download.
    - ![image](https://github.com/user-attachments/assets/f286e913-9441-4f6b-8273-1b7df152b17d)
    - We can find out that the epoch for the time she download the file is ```1733988750```
15. Then use GPT xd find the key out
    - ![image](https://github.com/user-attachments/assets/c5d87093-080a-410e-b361-ce07d7c64747)
    - ps: I also dk why need to use ```1733988749``` just told by my friend to use it cant find any things that support this epoch XD.
15. Okay, then let us go to decrypt it. Use cyberchef
16. ![image](https://github.com/user-attachments/assets/0a6837ae-ddf5-41d3-a810-7318c56a4607)
    Heres the flag.
Okay its maybe abit harder than i though. cry die.


#### acknowledgement
Thx to Bakayang for providing solution at the end of the day





