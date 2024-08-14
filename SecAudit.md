# Security Audit <br/>
(***Note: This scenario is based on a fictional company***) <br/>
**Company Name**: Botium Toys <br/>
**Location**: United States  <br/>
**Industry**: Toy Development and Sales  <br/>
**Operations**: Single physical location serving as main office, storefront, and warehouse  <br/>
**Growth**: Expanding online presence attracting U.S. and international customers  <br/>
***
## Scope, goals, and Assets
### Scope and goals of the audit
#### Scope
The scope of this audit is defined as the entire security program at Botium Toys. This includes their assets like employee equipment and devices, their internal network, and their systems. You will need to review the assets Botium Toys has and the controls and compliance practices they have in place. <br/>
#### Goals
Assess existing assets and complete the controls and compliance checklist to determine which controls and compliance best practices that need to be implemented to improve Botium Toys’ security posture. <br/>
### Current assets
Assets managed by the IT Department include: <br/>
● On-premises equipment for in-office business needs <br/>
● Employee equipment: end-user devices (desktops/laptops, smartphones), remote workstations, headsets, cables, keyboards, mice, docking stations, surveillance cameras, etc. <br/>
● Storefront products available for retail sale on site and online; stored in the company’s adjoining warehouse <br/>
● Management of systems, software, and services: accounting, telecommunication, database, security, ecommerce, and inventory management <br/>
● Internet access <br/>
● Internal network <br/>
● Data retention and storage <br/>
● Legacy system maintenance: end-of-life systems that require human monitoring <br/>
***
## Risk Assessment and Audit
### Risk assessment
#### Risk description
Currently, there is inadequate management of assets. Additionally, Botium Toys does not have all of the proper controls in place and may not be fully compliant with U.S. and international regulations and standards.
#### Control best practices
The first of the five functions of the NIST CSF is Identify. Botium Toys will need to dedicate resources to identify assets so they can appropriately manage them. Additionally, they will need to classify existing assets and determine the impact of the loss of existing assets, including systems, on business continuity.
#### Risk score
On a scale of 1 to 10, the risk score is 8, which is fairly high. This is due to a lack of
controls and adherence to compliance best practices.
#### Additional comments
The potential impact from the loss of an asset is rated as medium because the IT department does not know which assets would be at risk. The risk to assets or fines from governing bodies is high because Botium Toys does not have all of the necessary controls in place and is not fully adhering to best practices related to compliance regulations that keep critical data private/secure. Review the following bullet points for specific details: <br/>
● Currently, all Botium Toys employees have access to internally stored data and may be able to access cardholder data and customers’ PII/SPII. <br/>
● Encryption is not currently used to ensure confidentiality of customers’ credit card information that is accepted, processed,  transmitted, and stored locally in the company’s internal database.<br/>
● Access controls about least privilege and separation of duties have not been implemented.<br/>
● The IT department has ensured availability and integrated controls to ensure data integrity.<br/>
● The IT department has a firewall that blocks traffic based on an appropriately defined set of security rules.<br/>
● Antivirus software is installed and monitored regularly by the IT department.<br/>
● The IT department has not installed an intrusion detection system (IDS).<br/>
● There are no disaster recovery plans currently in place, and the company does not have backups of critical data.<br/>
● The IT department has established a plan to notify E.U. customers within 72 hours if there is a security breach. Additionally, privacy policies, procedures, and processes have been developed and enforced among IT department members/other employees to document and maintain data properly.<br/>
● Although a password policy exists, its requirements are nominal and inconsistent with current minimum password complexity requirements (e.g., at least eight characters; a combination of letters and at least one number; special characters).<br/>
● There is no centralized password management system that enforces the password policy’s minimum requirements, which sometimes affects productivity when employees/vendors submit a ticket to the IT department to recover or reset a password.<br/>
● While legacy systems are monitored and maintained, there is no regular schedule for these tasks, and the intervention methods are unclear.<br/>
● The store’s physical location, which includes Botium Toys’ main offices, storefront, and warehouse of products, has sufficient locks, up-to-date closed-circuit television (CCTV) surveillance, and functioning fire detection and prevention systems.<br/>

### Controls assessment checklist
(N) Least Privilege - *Not Set up* <br/>
(N) Disaster recovery plans - *No DRP exists* <br/>
(N) Password policies - *Current Policies are not up to current standards* <br/>
(N) Separation of duties - *Not Set up* <br/>
(Y) Firewall <br/>
(N) Intrusion detection system (IDS) - *Do not have* <br/>
(N) Backups - *Not Set up* <br/>
(Y) Antivirus software <br/>
(N) Manual monitoring, maintenance, and intervention for legacy systems -  - *No schedule and Methods are unclear* <br/>
(N) Encryption  - *Not Set up* <br/>
(N) Password management system - *Do not have* <br/>
(Y) Locks (offices, storefront, warehouse) <br/>
(Y) Closed-circuit television (CCTV) surveillance <br/>
(Y) Fire detection/prevention (fire alarm, sprinkler system, etc.) <br/>

### Compliance checklist
#### Payment Card Industry Data Security Standard (PCI DSS) <br/>
(N) Only authorized users have access to customers’ credit card information. - *Everyone has access* <br/>
(Y) Credit card information is stored, accepted, processed, and transmitted internally in a secure environment. <br/>
(N) Implement data encryption procedures to secure credit card transaction touchpoints and data better.  - *Not Set up* <br/>
(N) Adopt secure password management policies. - *Not set up* <br/>
#### General Data Protection Regulation (GDPR) <br/>
(Y) E.U. customers’ data is kept private/secured. <br/>
(Y) There is a plan in place to notify E.U. customers within 72 hours if their data is compromised/there is a breach. <br/>
(Y) Ensure data is properly classified and inventoried. <br/>
(Y) Enforce privacy policies, procedures, and processes to properly document and maintain data. <br/>
#### System and Organizations Controls (SOC type 1, SOC type 2)  <br/>
(Y) User access policies are established. <br/>
(N) Sensitive data (PII/SPII) is confidential/private. - *Available to everyone* <br/>
(Y) Data integrity ensures the data is consistent, complete, accurate, and has been validated. <br/>
(N) Data is available to individuals authorized to access it. - *Available to everyone* <br/>
***
## Summary of Findings
Currently, Botium Toys faces significant challenges in managing its assets effectively, lacking both identification and classification processes. This deficiency contributes to non-compliance with U.S. and international regulations, as well as insufficient controls for ensuring data privacy and security. <br/>
The risk score is high at 8, primarily due to the absence of necessary controls and adherence to best practices. There is a medium impact from potential asset loss because the IT department is unaware of which assets are at risk, and high regulatory fines are a possibility due to non-compliance. <br/>

Specific security gaps include: <br/>
- Unrestricted employee access to sensitive data. <br/>
- Recovery measures such as Disaster Recovery Plans (DRPs) and Backups are not implemented. <br/>
- Current Password Policies do not meet standards, and there is No Password Management System is available. <br/>
- Lack of Separation of Duties increases risk. <br/>
- No Intrusion Detection System (IDS) is in place. <br/>
- Manual monitoring for legacy systems is unscheduled and unclear. <br/>
- Data is not encrypted. <br/>

## Recommendations
To tackle these security gaps, start by ensuring only the right people can access sensitive data and make sure it's encrypted both when stored and during transmission. Clearly divide responsibilities among staff to reduce risks. Strengthen your password policies and use a management system to keep them secure and organized. It's essential to develop and regularly test disaster recovery plans, along with setting up automated backups to safeguard important data. An intrusion detection system will help monitor for any unusual network activity. For older systems, establish clear schedules and methods for regular maintenance.
