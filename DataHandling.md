# Activity: Determine appropriate data handling practices
## Scenario
You work for an educational technology company that developed an application to help teachers automatically grade assignments. The application handles a wide range of data that it collects from academic institutions, instructors, parents, and students. <br/>
Your team was alerted to a data leak of internal business plans on social media. An investigation by the team discovered that an employee accidentally shared those confidential documents with an external business partner. An audit into the leak is underway to determine how similar incidents can be avoided.<br/>
A supervisor provided you with information regarding the leak. It appears that the principle of least privilege was not observed by employees at the company during a sales meeting. You have been asked to analyze the situation and find ways to prevent it from happening again. <br/>
First, you'll need to evaluate details about the incident. Then, you'll review the controls in place to prevent data leaks. Next, you'll identify ways to improve information privacy at the company. Finally, you'll justify why you think your recommendations will make data handling at the company more secure.<br/>

## Data Leak Worksheet
### Incident summary: 
A sales manager shared access to a folder of internal-only documents with their team during a meeting. The folder contained files associated with a new product that has not been publicly announced. It also included customer analytics and promotional materials. After the meeting, the manager did not revoke access to the internal folder but warned the team to wait for approval before sharing the promotional materials with others.<br/>
During a video call with a business partner, a member of the sales team forgot the warning from their manager. The sales representative intended to share a link to the promotional materials so that the business partner could circulate the materials to their customers. However, the sales representative accidentally shared a link to the internal folder instead. Later, the business partner posted the link on their company's social media page, assuming that it was the promotional materials.<br/>
<br/>
|Control|Least Privilege|
|-------|---------------|
|Issues|The data leak occurred because the manager failed to unshare a folder containing sensitive internal documents, violating the principle of least privilege. <br/>Additionally, the customer success representative mistakenly shared the entire folder instead of the intended marketing materials, demonstrating a need for more secure data-handling practices.|
|Review|NIST SP 800-53: AC-6 emphasizes the principle of least privilege, requiring users to have only the minimum access necessary to perform their duties. It also recommends enforcing access controls and periodically reviewing permissions to prevent unauthorized access to sensitive data.|
|Recommendation|Restrict access to sensitive resources based on user role to ensure employees only access information necessary for their duties.<br/>Automatically revoke access to information after a period of time.|
|Justification|Restricting access based on user roles minimizes unnecessary exposure to sensitive data, reducing the risk of accidental sharing. <br/>Automatically revoking access after a set period prevents lingering permissions, ensuring temporary access is promptly removed. Together, these controls enforce stronger security and align with principles of least privilege.|
