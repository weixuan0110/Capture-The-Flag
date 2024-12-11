### CanYouSee Challenge Writeup

#### Steps to Solve:

1. **Download the Challenge File:**

   - Obtain the file provided by picoCTF.

2. **Extract the ZIP File:**

   - Unzip the file using an archive extraction tool.
     ```bash
     unzip <filename>.zip
     ```
     ![image](https://github.com/user-attachments/assets/bfa0e5d3-2e7d-4d0e-99dd-7b8f02faefd0)
     
3. **Inspect the Image:**

   - Open the image file to see if any visible data is present.
    ![image](https://github.com/user-attachments/assets/99034d4b-79c2-4b3d-885a-1ab7bf5899e4)

4. **Analyze Metadata:**

   - Use `exiftool` to analyze the image metadata:
     ```bash
     exiftool <filename>
     ```
     ![image](https://github.com/user-attachments/assets/a8f2f901-9c3e-48a2-8392-a3c4b4265179)

5. **Identify Hidden Data:**

   - Look for any unusual fields in the metadata, such as an attribution URL.

6. **Decode the Hidden Data:**

   - Copy the hidden data and decode it using an online tool like [CyberChef](https://gchq.github.io/CyberChef/).

7. **Retrieve the Flag:**

   - After decoding, the flag will be revealed.
   - <img width="634" alt="image" src="https://github.com/user-attachments/assets/04ae9550-1ffd-4ef6-bac4-311b922689bb" />

#### Outcome:

By following these steps, the hidden data in the metadata was decoded, and the flag was successfully retrieved!

