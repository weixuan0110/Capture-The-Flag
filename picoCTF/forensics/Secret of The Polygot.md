### Secret of The Polyglot Challenge Writeup

#### Steps to Solve:

1. **Download the Challenge File:**
   - Obtain the `flag2o2-final.pdf` file provided in the challenge.

2. **Inspect the PDF File:**
   - First let us open the PDF file to check its contents. Some text or patterns might appear, but i not sure what is this.
   - ![image](https://github.com/user-attachments/assets/5d679cf4-fc43-45a3-95bd-e541c90c0c9b)

3. **Analyze the File:**
   - Use `binwalk` to analyze the file for embedded content:
     ```bash
     binwalk flag2o2-final.pdf
     ```

4. **Identify Embedded Files:**
   - The `binwalk` results show the presence of embedded files, such as a PNG image.
   - ![image](https://github.com/user-attachments/assets/5f4b6685-28b9-4b60-b36e-7d7604a522c8)

5. **Extract and Rename the File:**
   - Extract the embedded files and change the file type of the identified PNG:
     ```bash
     binwalk --extract flag2o2-final.pdf
     mv flag2o2-final.pdf flag2o2-final.png
     ```
     Replace `<filename>` with the actual file name extracted.

6. **Retrieve the Flag:**
   - Open the extracted PNG file and analyze its content. Combine the visible information to derive the flag.
   - ![image](https://github.com/user-attachments/assets/29b4af1e-3fcf-460f-9681-e70ef9f33f81)

#### Outcome:
By following these steps, the embedded PNG file was accessed, and the flag was successfully retrieved by combining the displayed information!


