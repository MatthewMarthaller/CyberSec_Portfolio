# Portfolio Activity: Use Linux commands to manage file permissions
## Scenario
You are a security professional at a large organization. You mainly work with their research team. Part of your job is to ensure users on this team are authorized with the appropriate permissions. This helps keep the system secure. <br/>
Your task is to examine existing permissions on the file system. You’ll need to determine if the permissions match the authorization that should be given. If they do not match, you’ll need to modify the permissions to authorize the appropriate users and remove any unauthorized access.<br/>
***
***
## Project Description
In this scenario, we audited and modified file permissions in a research team's Linux environment, specifically focusing on the /home/researcher2/projects directory which contained five files and one subdirectory. <br/> Our main task was to review and adjust permissions to meet security requirements. <br/>
***
## Check File and Directory Details
Within the /home/researcher2/projects directory, there are five files and one sub-directory. <br/> To check the permissions, we use the ls command `ls -la /home/researcher2/projects`. <br/> This is what the files and directory show for permissions: <br/>
- project_k.txt - rw-rw-rw- (666)
- project_m.txt - rw-r----- (640)
- project_r.txt - rw-rw-r-- (664)
- project_t.txt - rw-rw-r-- (664)
- .project_x.txt - rw--w---- (620)
- /drafts - rwx--x--- (710)
***
## Describe the Permissions String
The 10-character string represents file or directory permissions in Linux/Unix systems: <br/>
First character: File type <br/>
- For project_k.txt: \- indicates a regular file
- For drafts: d indicates a directory
<br/>
Remaining 9 characters: Divided into 3 sets of 3 characters each, representing permissions for User, Group, and Other (in that order): <br/>
- r = read permission <br/>
- w = write permission <br/>
- x = execute permission (for directories, this means ability to enter/access) <br/>
- \- = permission not granted <br/>
<br/>
So for project_k.txt (rw-rw-rw-): <br/>
User (owner): rw- (can read and write)
Group: rw- (can read and write)
Other: rw- (can read and write) <br/>
<br/>
For drafts (rwx--x---): <br/>
User (owner): rwx (can read, write, and execute/access)
Group: --x (can only execute/access)
Other: --- (no permissions at all) <br/>

#### The numeric (octal) permission system
Each permission type (read, write, execute) is assigned a number: <br/>
- Read (r) = 4
- Write (w) = 2
- Execute (x) = 1
These numbers are added together for each group (User, Group, Others) to create a three-digit number. <br/> Let's break down the permissions: <br/>
- 666 (project_k.txt: rw-rw-rw-)
  - User: rw- = 4+2+0 = 6
  - Group: rw- = 4+2+0 = 6
  - Others: rw- = 4+2+0 = 6
- 710 (drafts: rwx--x---)
  - User: rwx = 4+2+1 = 7
  - Group: --x = 0+0+1 = 1
  - Others: --- = 0+0+0 = 0
***
## Changing Permissions
### No Others Permitted
The organization does not allow others to have write access to any files. Looking at the permissions, project_k.txt is the only file that allows write access to "others" (the last "w" in rw-rw-rw-). <br/>
To remove write access for others on project_k.txt, we can use the chmod command: <br/>
`chmod o-w /home/researcher2/projects/project_k.txt` <br/>
<br/>
This will change project_k.txt permissions from rw-rw-rw- (666) to rw-rw-r-- (664). <br/>
### Archived Hidden File
The research team has archived .project_x.txt, which is why it’s a hidden file. This file should not have write permissions for anyone, but the user and group should be able to read the file. Looking at .project_x.txt's current permissions (rw--w----), we need to: 1) Remove write permissions for user and group and 2) Add read permissions for group. <br/>
<br/>
To set these permissions, we can use the chmod command:<br/>
`chmod u=r,g=r,o= /home/researcher2/projects/.project_x.txt` <br/> or <br/> `chmod 440 /home/researcher2/projects/.project_x.txt` <br/>
### Personal Drafts Directory
The files and directories in the projects directory belong to the researcher2 user, and Only researcher2 should be allowed to access the drafts directory and its contents. Looking at the current permissions for the drafts directory (rwx--x---), we need to remove all permissions for group while maintaining full access for researcher2. <br/>
<br/>
To set these permissions, we can use the chmod command:
`chmod 700 /home/researcher2/projects/drafts` (Which sets the permissions) <br/> or <br/> `chmod g-x /home/researcher2/projects/drafts` (Which removes the execute (x) permission from the group while leaving all other permissions unchanged) <br/>
***
## Summary
As a security professional working with a research team, I needed to examine and modify file system permissions to ensure proper authorization within the /home/researcher2/projects directory. <br/> My tasks involved enforcing three key security requirements: preventing "others" from having write access to files (specifically project_k.txt), setting appropriate read-only permissions for an archived file (.project_x.txt), and restricting access to the drafts directory to only the owner (researcher2). <br/> Using Linux chmod commands, I successfully implemented these permission changes to maintain system security while preserving necessary access for authorized users.
