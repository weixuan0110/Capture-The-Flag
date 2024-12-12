## IntroToBurp Writeup
### Steps to Solve

1. Open BurpSuites and switch to Proxy, Http History.
  - ![image](https://github.com/user-attachments/assets/9407b0db-0f2e-4d9f-b997-9a3547613291)
   
2. Press the open browser button and put in the link given to the browser pop-up
3. Next, just fill it what you want on the register page.
  - ![image](https://github.com/user-attachments/assets/c6f0e148-5e7e-47c7-a6f4-de35d7833002)

4. Then we will get a page showing input otp.
  - ![image](https://github.com/user-attachments/assets/889fd87e-9039-45d1-bb99-14f61d04d502)

5. We dont have it but now so just input some word what you want.

6. then we will get a "invalid OTP" in the page.

7. go back to the burpsuite.

8. Press on send to repeater on the last row
   - ![image](https://github.com/user-attachments/assets/5ac310f3-a9e3-4eee-8b6c-d46a7dad3106)

9. In repeater tab, gonna have something like this.
    - ![image](https://github.com/user-attachments/assets/755665e2-de72-40ad-8570-b5453e9e626d)

10. Just delete the otp=(CodeYouType) and will get the flag after you press send.
    - <img width="341" alt="image" src="https://github.com/user-attachments/assets/38defe48-3019-4445-96ec-f50bae2a0e7a" />



