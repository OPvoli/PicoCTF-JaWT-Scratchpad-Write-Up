# PicoCTF-JaWT-Scratchpad-Write-Up
Use Burp Suite and JWT Tool<br />
Perform all the steps below using Linux machine.<br />
Step 1: Go to http://jupiter.challenges.picoctf.org:63090 with Firefox.<br />
Step 2: Go to Firefox settings, scroll down and find network settings. Then, click the settings and configure as figure below and click ok.<br />
Step 3: Start Burp Suite.<br />
Step 4: Go to proxy and click the intercept is on in Burp Suite. This is to intercept the traffic send to the server.<br />
Step 5: Register any name at the textbox in the web page and press enter.<br />
Step 6: Go to proxy and click forward until cookie=jwt is displayed in the response in Burp Suite. Then, right click and select “send to repeater”. The request will be send to repeater to be modified it later to send to the server.<br />
Step 7: Open terminal, change directory into the jwt_tool directory.<br />
Step 8: Use command python3 jwt_tool.py with jwt token to view the header and payload of the jwt token. The algorithm is HS256.<br />
Step 9: Use command python3 jwt_tool.py <token> -C -d /usr/share/wordlists/rockyou.txt to perform dictionary attack using rockyou.txt. The jwt secret is ilovepico.<br />
Step 10: Use command python3 jwt_tool.py <token> -T -S hs256 -p "ilovepico" to tamper the token. -T refers to tamper, -S refers to signature and -p refers to secret. <br /> 
Step 11: In Burp Suite, modify the jwt value with tampered token and click send. The flag is displayed in the response.<br />

You may find more details and ways to get the flag through the documentation.<br />
