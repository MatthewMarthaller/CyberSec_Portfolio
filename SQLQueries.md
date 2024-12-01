# Portfolio Activity: Apply filters to SQL queries

## Scenario
You are a security professional at a large organization. Part of your job is to investigate security issues to help keep the system secure. You recently discovered some potential security issues that involve login attempts and employee machines. <br/>
<br/>
Your task is to examine the organization’s data in their employees and log_in_attempts tables. You’ll need to use SQL filters to retrieve records from different datasets and investigate the potential security issues. <br/>
***
## Project Description
As a security professional at a large organization, I needed to investigate several potential security issues involving login attempts and employee machines. <br/>
Through SQL queries, I analyzed login patterns to identify suspicious after-hours activity, investigated specific dates of concern, and filtered login attempts by country of origin. <br/>
<br/>
I also helped prepare for various security updates by identifying employee machines based on department and location requirements.
## QUERY ONE: After-Hours Failed Logins
During an audit, I identified several after-hours failed login attempts in our system. <br/>
To investigate this issue, I ran the following query: <br/>
`SELECT * FROM log_in_attempts WHERE login_time > '18:00' AND success = 0;` <br/>
<br/>
This query searched our log_in_attempts table for any failed login attempts occurring after 18:00 (6:00 PM). By filtering on both the time and failed status (success = 0), the query revealed 19 unsuccessful login attempts outside of business hours. 

## QUERY TWO: Login Attempts on Specific Dates
During my security investigation of a suspicious event on 2022-05-09, I needed to analyze login patterns from both the day of the event and the previous day. I executed the following query: <br/>
`SELECT * FROM log_in_attempts WHERE login_date = '2022-05-08' OR login_date = '2022-05-09';` <br/>
<br/>
This query examines our log_in_attempts table for any login activity on either May 8th or May 9th, 2022. <br/> By using the OR operator with these two specific dates, the query returns 75 login attempts from both days, allowing me to establish a timeline of events and identify any potential security anomalies around the time of the suspicious event.

## QUERY THREE: Login Attempts outside of Mexico
As part of our ongoing investigation into suspicious login activity, We managed to remove Mexico from our points of Origin. Wanting to analyze all login attempts originating outside of Mexico, I executed the following query: <br/>
`SELECT * FROM log_in_attempts WHERE NOT country LIKE 'MEX%';` <br/>
<br/>
This query searches our log_in_attempts table for all login attempts where the country code does not begin with "MEX". Using LIKE with 'MEX%' ensures we exclude both "MEX" and "MEXICO" entries from our results. <br/> The NOT operator filters out these Mexican-origin attempts, allowing us to focus our investigation on login attempts from all other countries.

## QUERY FOUR: Determining Marketing Machines for Updating
In preparation for security updates on the Marketing department's machines in the East building, I ran the following query: <br/>
`SELECT * FROM employees WHERE department = 'Marketing' AND office LIKE 'East%';` <br/>
<br/>
This query searches our employees table for all staff members who work in the Marketing department and are located in the East building. The first filter matches the exact department name 'Marketing', while the second filter uses LIKE with 'East%' to capture all office numbers in the East building (such as East-170, East-320). <br/> This allows our team to efficiently identify which Marketing employee machines need security updates based on their location.

## QUERY FIVE: Determining Finance and Sales Machines for Updating
To identify machines in the Sales and Finance departments to push security updates, I executed the following query: <br/>
`SELECT * FROM employees WHERE department = 'Sales' OR department = 'Finance';` <br/>
<br/>
This query examines our employees table to locate all staff members who work in either the Sales or Finance departments. <br/> By using the OR operator, the query returns employees from both departments in a single result set, allowing our team to efficiently plan and implement the necessary security updates on their machines.

## QUERY SIX: Determining Non-IT Machines for Updating
To get a list of all employees that will be getting the system update, excluding those in Information Technology who already received it, I executed the following query: <br/>
`SELECT * FROM employees WHERE NOT department = 'Information Technology';` <br/>
Note: This query could also be written using the inequality operator as `WHERE department != 'Information Technology'`. Both approaches (using NOT with = or using !=) are logically equivalent and will produce the same results. <br/>
<br/>
This query searches our employees table for all staff members who are not in the Information Technology department. Using NOT with the equality operator excludes IT department entries from the results, allowing our team to identify all remaining employees whose machines need the security update.

## Summary
The SQL queries I developed helped investigate multiple security concerns and coordinate system updates across the organization. <br/> 
Initial investigations focused on analyzing failed login attempts after business hours, examining specific dates related to a security event, and investigating login attempts from locations outside Mexico. <br/>
<br/>
Following this, I created queries to identify employee machines needing different security updates based on department and building location, ensuring our security measures were properly implemented across the organization.
