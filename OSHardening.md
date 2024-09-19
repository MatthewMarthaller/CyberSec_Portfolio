(NOTE: This is based on a fictional scenario.)

# Scenario
You are a cybersecurity analyst for yummyrecipesforme.com, a website that sells recipes and cookbooks. A former employee has decided to lure users to a fake website with malware. 

The baker executed a brute force attack to gain access to the web host. They repeatedly entered several known default passwords for the administrative account until they correctly guessed the right one. After they obtained the login credentials, they were able to access the admin panel and change the website’s source code. They embedded a javascript function in the source code that prompted visitors to download and run a file upon visiting the website. After embedding the malware, the baker changed the password to the administrative account. When customers download the file, they are redirected to a fake version of the website that contains the malware. <br/>
<br/>
Several hours after the attack, multiple customers emailed yummyrecipesforme’s helpdesk. They complained that the company’s website had prompted them to download a file to access free recipes. The customers claimed that, after running the file, the address of the website changed and their personal computers began running more slowly. 

In response to this incident, the website owner tries to log in to the admin panel but is unable to, so they reach out to the website hosting provider. You and other cybersecurity analysts are tasked with investigating this security event.<br/>
<br/>
To address the incident, you create a sandbox environment to observe the suspicious website behaviour. You run the network protocol analyzer tcpdump, then type in the URL for the website, yummyrecipesforme.com. When the website loads, you are prompted to download an executable file to update your browser. You accept the download and allow the file to run. You then observe that your browser redirects you to a different URL, greatrecipesforme.com, which contains the malware.  <br/>
<br/>
The logs show the following process:
1. The browser initiates a DNS request: It requests the IP address of the yummyrecipesforme.com URL from the DNS server.<br/>
2. The DNS replies with the correct IP address. <br/>
3. The browser initiates an HTTP request: It requests the yummyrecipesforme.com webpage using the IP address sent by the DNS server.<br/>
4. The browser initiates the download of the malware.<br/>
5. The browser initiates a DNS request for greatrecipesforme.com.<br/>
6. The DNS server responds with the IP address for greatrecipesforme.com.<br/>
7. The browser initiates an HTTP request to the IP address for greatrecipesforme.com.<br/>
<br/>
A senior analyst confirms that the website was compromised. The analyst checks the source code for the website. They notice that javascript code had been added to prompt website visitors to download an executable file. Analysis of the downloaded file found a script that redirects the visitors’ browsers from yummyrecipesforme.com to greatrecipesforme.com. <br/>
<br/>
The cybersecurity team reports that the web server was impacted by a brute force attack. The disgruntled baker was able to guess the password easily because the admin password was still set to the default password. Additionally, there were no controls in place to prevent a brute force attack. <br/>
<br/>
Your job is to document the incident in detail, including identifying the network protocols used to establish the connection between the user and the website.  You should also recommend a security action to take to prevent brute force attacks in the future.<br/>

### tcpdump Traffic Log
14:18:32.192571 IP your.machine.52444 > dns.google.domain: 35084+ A? yummyrecipesforme.com. (24)<br/>
14:18:32.204388 IP dns.google.domain > your.machine.52444: 35084 1/0/0 A 203.0.113.22 (40)<br/>
<br/>

14:18:36.786501 IP your.machine.36086 > yummyrecipesforme.com.http: Flags [S], seq 2873951608, win 65495, options [mss 65495,sackOK,TS val 3302576859 ecr 0,nop,wscale 7], length 0<br/>
14:18:36.786517 IP yummyrecipesforme.com.http > your.machine.36086: Flags [S.], seq 3984334959, ack 2873951609, win 65483, options [mss 65495,sackOK,TS val 3302576859 ecr 3302576859,nop,wscale 7], length 0<br/>
14:18:36.786529 IP your.machine.36086 > yummyrecipesforme.com.http: Flags [.], ack 1, win 512, options [nop,nop,TS val 3302576859 ecr 3302576859], length 0<br/>
14:18:36.786589 IP your.machine.36086 > yummyrecipesforme.com.http: Flags [P.], seq 1:74, ack 1, win 512, options [nop,nop,TS val 3302576859 ecr 3302576859], length 73: HTTP: GET / HTTP/1.1<br/>
14:18:36.786595 IP yummyrecipesforme.com.http > your.machine.36086: Flags [.], ack 74, win 512, options [nop,nop,TS val 3302576859 ecr 3302576859], length 0<br/>
…<a lot of traffic on the port 80>... <br/>
<br/>

14:20:32.192571 IP your.machine.52444 > dns.google.domain: 21899+ A? greatrecipesforme.com. (24)<br/>
14:20:32.204388 IP dns.google.domain > your.machine.52444: 21899 1/0/0 A 192.0.2.17 (40)<br/>
<br/>
14:25:29.576493 IP your.machine.56378 > greatrecipesforme.com.http: Flags [S], seq 1020702883, win 65495, options [mss 65495,sackOK,TS val 3302989649 ecr 0,nop,wscale 7], length 0<br/>
14:25:29.576510 IP greatrecipesforme.com.http > your.machine.56378: Flags [S.], seq 1993648018, ack 1020702884, win 65483, options [mss 65495,sackOK,TS val 3302989649 ecr 3302989649,nop,wscale 7], length 0<br/>
14:25:29.576524 IP your.machine.56378 > greatrecipesforme.com.http: Flags [.], ack 1, win 512, options [nop,nop,TS val 3302989649 ecr 3302989649], length 0<br/>
14:25:29.576590 IP your.machine.56378 > greatrecipesforme.com.http: Flags [P.], seq 1:74, ack 1, win 512, options [nop,nop,TS val 3302989649 ecr 3302989649], length 73: HTTP: GET / HTTP/1.1<br/>
14:25:29.576597 IP greatrecipesforme.com.http > your.machine.56378: Flags [.], ack 74, win 512, options [nop,nop,TS val 3302989649 ecr 3302989649], length 0<br/>
…<a lot of traffic on the port 80>... <br/>
***
# Security incident report
### Section 1: Network Protocols <br/>
During the investigation of the security incident, the following network protocols were identified from the tcpdump log:<br/>
DNS (Domain Name System): Used to resolve domain names to IP addresses.<br/>
HTTP (Hypertext Transfer Protocol): Used for web page requests and downloads.<br/>
<br/>
###Section 2: Incident Summary
##### Incident Summary:
A former employee executed a brute force attack on the admin account of yummyrecipesforme.com. The attacker used default passwords to gain access to the admin panel, where they embedded malicious JavaScript code into the website. This code prompted users to download a file containing malware, which redirected their browsers to a fake website, greatrecipesforme.com. <br/>
<br/>
##### Incident Details: <br/>
Initial Access: The attacker used a brute force attack to guess the admin password, which was set to a default value. <br/>
Payload Deployment: Malicious JavaScript was added to the website's source code, prompting visitors to download a file. <br/>
Execution: The downloaded file contained a script that redirected users to greatrecipesforme.com, which hosted additional malware. <br/>
Customer Impact: Users reported being prompted to download a file for "free recipes," after which their computers slowed down, indicating malware infection. <br/>
Response: The website owner was locked out of the admin panel. A cybersecurity team was engaged to investigate. <br/>
<br/>
###### Sources of Information:
Customer complaints to the helpdesk.
Network traffic analysis using tcpdump.
Examination of the website's modified source code.
###### Network Activity:
DNS Requests: <br/>
yummyrecipesforme.com resolved to IP 203.0.113.22. <br/>
greatrecipesforme.com resolved to IP 192.0.2.17. <br/>
HTTP Requests: <br/>
Initial HTTP request to yummyrecipesforme.com to access the webpage. <br/>
Subsequent HTTP request to greatrecipesforme.com after redirection. <br/>
<br/>
### Section 3: Recommendation for Brute Force Attack Prevention
#### Recommended Action: Implement and Mandate Two-Factor Authentication (2FA) for all administrative accounts.
Justification:
Two-Factor Authentication adds an additional security layer by requiring not only a password and username but also something that only the user has on them (e.g., a physical token or a mobile app). This makes it significantly more difficult for attackers to gain unauthorized access, even if they manage to obtain the password through brute force or other methods. Implementing 2FA can greatly reduce the risk of unauthorized access to sensitive systems and information.
