# Poslaju
## Step by Step Solve
---
1. download the attachment given by the challenge.
2. Open the pcap file using wireshark(https://www.wireshark.org/#downloadLink)
3. Choose one port of http and right click, follow the http stream.
4. You can see there is a C in front of the HTTP/1.1.
   - ![image](https://github.com/user-attachments/assets/561fba6a-e20b-446f-b1ac-90ef149fec8c)
5. Looks like there is a flag there maybe, so lets try increase the stream.
   - ![image](https://github.com/user-attachments/assets/de8fd55d-4ff7-425a-ae4e-e0b8fee270ed)
6. Looks like there is a y, so lets record it (flag type = CyberX{})
   - ![image](https://github.com/user-attachments/assets/98c918b7-5db8-401a-af80-ccecd7c52f51)
7. And there is it the flag!
