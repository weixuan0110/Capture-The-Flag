# ZipCrack 1: The Hidden Lock
## Step By Step Solve
---
1. Download the zip file from the attachment.
2. unzip the file, but hemm, look like normally unzip is not suitable(see the attach picture)
   - ![image](https://github.com/user-attachments/assets/42a109a3-89bd-483f-ad01-1ca00d3d6c75)
3. So use command ```7z e flag.zip``` 7zip is a better unzip tools in this case. But ohno there is a password.
   - ![image](https://github.com/user-attachments/assets/72ed79ac-ef55-4727-ae7f-3828b5d96907)
4. So i try to bruteforce it using  ```John The Ripper``` .

   - because it is a zipfile, we need to use command ```zip2john flag.zip > hash.txt``` to make the zip file a hash text then we can use to bruteforce finding the same hash to find out the password.
5. Use this command ```john -w usr/share/wordlists/rockyou.txt hash.txt```
6. And we will found out that the password for this file is ```rainbow1```
   - ![image](https://github.com/user-attachments/assets/86d78732-768b-4f18-b9ad-26d4d356e3a6)
7. And now let use use the password to go inside and take a look of the flag.txt file
   - ![image](https://github.com/user-attachments/assets/e50f85c5-f31d-486a-a1e5-cd5bce1e2238)
8. Thats it!! the flag for this question!!

