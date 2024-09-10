(**NOTE:** This is based on a fictional scenario.) <br/>
# Scenario
You work as a security analyst for a travel agency that advertises sales and promotions on the company’s website. Employees regularly access the company’s sales webpage to search for vacation packages their customers might like. <br/>
One afternoon, you receive an automated alert from your monitoring system indicating a problem with the web server. You attempt to visit the company’s website but receive a connection timeout error message in your browser.<br/>
<br/>
You use a packet sniffer to capture data packets in transit to and from the web server. You notice many TCP SYN requests coming from an unfamiliar IP address. The web server appears overwhelmed by the volume of incoming traffic and is losing its ability to respond to the abnormally large number of SYN requests. You suspect a malicious actor is attacking the server. <br/>
<br/>
You temporarily take the server offline so the machine can recover and return to a normal operating status. You also configured the company’s firewall to block the IP address that sent the abnormal SYN requests. You know your IP blocking solution won’t last long, as an attacker can spoof other IP addresses to get around this block. You need to alert your manager about this problem quickly and discuss the next steps to stop this attacker and prevent this problem from happening again. You must be prepared to tell your boss about the type of attack you discovered and how it affected the web server and employees.<br/>
<br/>
***
# Cybersecurity Incident Report: Network Attack Analysis
## Part One: Identify the attack
One potential explanation for the website's connection timeout error message is the excessive packets from IP address ***203.0.113.0***, as shown in the logs. This pattern suggests a SYN flood attack, where repeated SYN requests are sent without completing the handshake, indicating a potential DoS (Denial of Service) attack.<br/>
<br/>
## Part Two: Malfunction Explanation <br/>
### TCP Three-Way Handshake <br/>
When visitors attempt to connect to our web server, the TCP protocol uses a three-way handshake to establish a reliable connection. This process involves three steps:
1. **SYN (Synchronize)** <br/>
    The client sends a SYN packet to the server to initiate a connection. This packet includes an initial sequence number, which the server uses to track the data flow.<br/>
2. **SYN-ACK (Synchronize-Acknowledge)** <br/>
    The server responds with a SYN-ACK packet. This acknowledges the receipt of the SYN packet and also includes its own sequence number, allowing the client to synchronize its data flow with the server.<br/>
3. **ACK (Acknowledge)** <br/>
   Finally, the client sends an ACK packet back to the server, confirming the receipt of the SYN-ACK packet. This completes the handshake, establishing the connection and allowing data to be exchanged between the client and server.<br/>

### SYN Flood Attack <br/>
In a SYN flood attack, a malicious actor or attacker sends a large number of SYN packets to the server, often using spoofed IP addresses. The server, expecting legitimate connections, allocates resources for each packet and responds with SYN-ACK packets. However, since the final ACK is never received, the server's resources remain tied up, awaiting a response that doesn't arrive. This leads to resource exhaustion and impacts server performance. <br/>

### Results from the Logs <br/>
The analysis of Packet Sniffer logs indicates an abnormal number of SYN packets originating from IP address 203.0.113.0. This pattern suggests an SYN flood attack, which results in connection timeout errors for new connections and performance degradation for users already connected. In severe cases, it can cause a complete denial of service.

## Recommendations <br/>
To enhance our network security and prevent similar incidents, I recommend the following actions:<br/>
- **Implement Rate Limiting**: Introduce rate limiting to control the number of requests from any single IP address. This will help mitigate the effects of potential SYN flood attacks.<br/>
- **Adjust Firewall Rules**: While we've already blocked the identified IP, it's important to continuously update our firewall settings to automatically block any new IPs exhibiting malicious behaviour.<br/>
- **Enhance Monitoring**: Increase our network monitoring capabilities to quickly detect and respond to any anomalies. This proactive approach will help us manage threats more effectively.<br/>
