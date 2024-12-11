### PicoCTF Challenge Writeup

#### Steps to Solve:

1. **Log in via SSH:**
   - Access the target system using the provided SSH credentials given by picoCTF.

2. **Locate the Target Files:**
   - Identify the files in the challenge environment using the given SHA-256 hash.
   - Use the following command to search for the file:
     ```bash
     sha256sum files/* | grep <SHA256 hash>
     ```
     ![image](https://github.com/user-attachments/assets/f9136076-251b-466f-9873-56a84adeb644)

3. **Decrypt the File:**
   - Once the target file is found, use OpenSSL to decrypt it. The specific command for decryption is:
     ```bash
     openssl enc -d -aes-256-cbc -pbkdf2 -iter 100000 -salt -in files/<filename> -k picoCTF
     ```
     Replace `<filename>` with the actual file name obtained from the previous step.

4. **Retrieve the Flag:**
   - After executing the above command, the decrypted content will reveal the flag.
   ![image](https://github.com/user-attachments/assets/753b994d-62ee-40b4-80d1-de8d256f203b)
#### Outcome:
By following these steps, the flag was successfully retrieved and the challenge was completed!




