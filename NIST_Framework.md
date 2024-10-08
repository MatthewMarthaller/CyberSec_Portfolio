# Scenario  <br/>
You are a cybersecurity analyst working for a multimedia company that offers web design services, graphic design, and social media marketing solutions to small businesses. <br/>
Your organization recently experienced a DDoS attack, which compromised the internal network for two hours until it was resolved. <br/>
 <br/>
During the attack, your organization’s network services suddenly stopped responding due to an incoming flood of ICMP packets. Normal internal network traffic could not access any network resources. The incident management team responded by blocking incoming ICMP packets, stopping all non-critical network services offline, and restoring critical network services.  <br/>
 <br/>
The company’s cybersecurity team then investigated the security event. They found that a malicious actor had sent a flood of ICMP pings into the company’s network through an unconfigured firewall. This vulnerability allowed the malicious attacker to overwhelm the company’s network through a distributed denial of service (DDoS) attack.  <br/>
 <br/>
To address this security event, the network security team implemented:  <br/>
  1. A new firewall rule to limit the rate of incoming ICMP packets <br/>
  2. Source IP address verification on the firewall to check for spoofed IP addresses on incoming ICMP packets <br/>
  3. Network monitoring software to detect abnormal traffic patterns <br/>
  4. An IDS/IPS system to filter out some ICMP traffic based on suspicious characteristics <br/>
****
# Incident report analysis <br/>
### Summary of Incident <br/>
The organization experienced a Distributed Denial of Service (DDoS) attack, characterized by a flood of ICMP packets, which took down the internal network for two hours. <br/>
### Identify the Cause <br/>
Upon investigation of the Systems, devices, and access policies involved in the attack, the cybersecurity team identified the root cause as an unconfigured firewall that permitted the flood of ICMP packets. This vulnerability enabled the attacker to disrupt normal operations and highlighted a critical gap in our network security posture. <br/>
### Protection <br/>
In response to the incident, we swiftly implemented a new firewall rule designed to limit the rate of incoming ICMP packets. Additionally, source IP verification was activated to detect and block spoofed addresses, enhancing our ability to prevent similar attacks in the future. <br/>
### Detection  <br/>
To improve our detection capabilities, we deployed advanced network monitoring tools. These tools are configured to identify abnormal traffic patterns in real-time. Furthermore, an Intrusion Detection/Prevention System (IDS/IPS) was installed to scrutinize ICMP traffic for any suspicious characteristics, allowing for proactive threat management. <br/>
### Respond <br/>
Our immediate response included blocking incoming ICMP packets and strategically shutting down non-critical services. This allowed us to concentrate efforts on restoring essential functions. We are currently updating our incident response plan to incorporate specific procedures for handling DDoS attacks, ensuring a swift and effective response in future scenarios. <br/>
### Recover <br/>
Following the containment of the attack, all systems were successfully restored to normal operations. Comprehensive data integrity checks were performed, and necessary backups were completed to safeguard against data loss. This incident underscores the importance of robust firewall configurations and proactive monitoring to mitigate potential disruptions and enhance our overall cybersecurity resilience. <br/>
