(**NOTE:** This is based on a fictional scenario.) <br/>
# Scenario
You are a cybersecurity analyst working at a company that specializes in providing IT services for clients. Several customers of clients reported that they were not able to access the client company website www.yummyrecipesforme.com, and saw the error “destination port unreachable” after waiting for the page to load. 

You are tasked with analyzing the situation and determining which network protocol was affected during this incident. To start, you attempt to visit the website and you also receive the error “destination port unreachable.” To troubleshoot the issue, you load your network analyzer tool, tcpdump, and attempt to load the webpage again. To load the webpage, your browser sends a query to a DNS server via the UDP protocol to retrieve the IP address for the website's domain name; this is part of the DNS protocol. Your browser then uses this IP address as the destination IP for sending an HTTPS request to the web server to display the webpage  The analyzer shows that when you send UDP packets to the DNS server, you receive ICMP packets containing the error message: “udp port 53 unreachable.” 
<br/>
<br/>
**Logs:**<br/>
13:24:32.192571 IP 192.51.100.15.52444 > 203.0.113.2.domain: 35084+ A?<br/>
yummyrecipesforme.com. (24)<br/>
13:24:36.098564 IP 203.0.113.2 > 192.51.100.15: ICMP 203.0.113.2 <br/>
udp port 53 unreachable length 254<br/>
<br/>
13:26:32.192571 IP 192.51.100.15.52444 > 203.0.113.2.domain: 35084+ A?<br/>
yummyrecipesforme.com. (24)<br/>
13:27:15.934126 IP 203.0.113.2 > 192.51.100.15: ICMP 203.0.113.2 <br/>
udp port 53 unreachable length 320<br/>
<br/>
13:28:32.192571 IP 192.51.100.15.52444 > 203.0.113.2.domain: 35084+ A?<br/>
yummyrecipesforme.com. (24)<br/>
13:28:50.022967 IP 203.0.113.2 > 192.51.100.15: ICMP 203.0.113.2 <br/>
udp port 53 unreachable length 150<br/>
<br/>
***
# Cybersecurity Incident Report: Network Traffic Analysis
## Part One: Summary of issue located in the DNS and ICMP Traffic Log
The network protocol analyzer logs indicate that a DNS request from the Client to the server at IP 203.0.113.2 on UDP port 53 failed, as shown by an ICMP error message stating "udp port 53 unreachable." This suggests that the DNS server is not listening on port 53, likely due to misconfiguration or the service being down, causing repeated delivery errors.<br/>
<br/>
## Part Two: Explanation of the Analysis and Possible Causes
#### Time Incident Occurred:
The incident occurred at 1:24 p.m., specifically at 13:24:32.192571, as indicated by the timestamps in the log.<br/>
#### How the IT Team Became Aware:
Several customers of clients reported being unable to access the website www.yummyrecipesforme.com, encountering the error "destination port unreachable."<br/>
After receiving the report, I tried to visit the site and got the same error, which prompted further investigation.<br/>
#### Actions Taken:
**Initial Testing**: Verified the issue by attempting to access the website and receiving the same error.<br/>
**Network Analysis**: Used tcpdump to capture network traffic while attempting to load the webpage.<br/>
**Protocol Examination**: Analyzed the DNS request using UDP and identified ICMP error messages indicating "udp port 53 unreachable."<br/>
<br/>
#### Key Findings:
**Affected Port**: Port 53, designated for DNS services, was not reachable.<br/>
**DNS Server**: The server at IP 203.0.113.2 was unresponsive to DNS requests on port 53.<br/>
**ICMP Errors**: Repeated ICMP messages indicated the DNS service was unavailable.<br/>
<br/>
### Likely Cause of the Incident:
The most probable cause was a misconfiguration of the DNS server, potentially due to incorrect firewall settings or the DNS service being inadvertently stopped or not started. <br/>
Other possible causes include network firewall rules blocking UDP traffic on port 53, a DNS service crash, port misconfiguration, hardware failure, or a security breach leading to deliberate service disruption.<br/>
<br/>
#### Recommended Next Steps
**DNS Server Check**: Verify the configuration of the DNS server and check its operational status.<br/>
**Network Testing**: Conduct tests to confirm connectivity and port availability.<br/>
