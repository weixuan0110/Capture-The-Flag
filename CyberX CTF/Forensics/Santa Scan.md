# Santa Scan
## Step by Step Solve
---
1. First download the attachment given by the challenge.
2. It is a file call santa_scan.pcap.
3. Open the file using wireshark(https://www.wireshark.org/#downloadLink)
4. The hint given by the challenge is TCP, so let us type TCP in the seach box.
5. As you can see there is a lot of port with TCP Protocol.
6. Now lets find where is the flag, but hey see, there is something at the down-right corner (highlighted)
   - ![image](https://github.com/user-attachments/assets/1b897044-3b61-41b2-aa43-81fae3a7dd67)
7. After pressing few TCP Ports and we can sure that it is the Flag for us (TCP Stream with port length 60)
   - ![image](https://github.com/user-attachments/assets/c3c72452-1e08-4f89-8639-392042818d83)
8. Thats the flag!! Hooray, Happy Christmas HoHoHo!!!
