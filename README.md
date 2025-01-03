<h1>Google Cybersecurity Certification Project: Use Linux Commands to Manage File Permissions</h1>

<h2>Description</h2>
My task is to examine existing permissions on the file system of the organization’s research  team. I’ll determine if the permissions match the authorization that should be given. If they do not match, I’ll modify the permissions to authorize the appropriate users and remove any unauthorized access.


<h2>Check file and directory details</h2>

![image](https://github.com/user-attachments/assets/5a625e0d-59fa-43b1-bcd7-d48ebc58ad2d)



Used ``ls -la`` to list file and directory permissions in the projects folder of user researcher2, including hidden files. The output shows that ``.project_x.txt`` is a hidden file, one directory is named ``drafts``, and there are 4 other files in this folder.The 10-character string in the first
column represents the permissions set on each file or directory.

<h2> Describe the permissions string </h2>

![image](https://github.com/user-attachments/assets/5f77df71-4732-4aa6-8018-4fd1f2c37b8b)

The permissions string of ``.project_x.txt`` says ``-rx- -w - - - -``. The (``-``) at the beginning of the string indicates this is a file and not a directory (which would be denoted as (``d``)). 
The first 3 characters after that indicate the permissions of the user. The next 3 characters indicate the permissions of the group. The last 3 characters indicate the permissions of others who are not the user or in the group.  If there is a (``-``), that indicates a lack of permission
Regarding the permissions of ``.project_x.txt`` , it means:

- User (``u``)= read (``r``), write (``w``)
- Group (``g``) = write (``w``)
- Other (``o``)= none 
 
<h2>Change file permissions</h2>

![image](https://github.com/user-attachments/assets/955cfcab-252d-4471-b828-6a99ed784731)


The organization does not allow for other to have write permissions. The list showed that ``project_k.txt`` had write permissions for other.  To remove write permissions, I used ``chmod o-w project_k.txt`` to remove other write permissions. The command ``chmod`` allows me to update permissions. ``ls -l`` was used to review the permissions changes of non hidden files and directories. 

<h2>Change file permissions on a hidden file</h2>

![image](https://github.com/user-attachments/assets/f17f35f8-96b8-4588-ac9b-e36fc617e9f1) 

Since ``.project_x.txt`` is an archived file, no one should be able to modify it but user and group should be able to read the file. First, I used ``ls -la`` to review permissions of the files and directories, including hidden files. Then I used ``chmod u-w,g-w,g+r .project_x.txt`` to remove write permissions from user and group and add read permissions to group for ``.project_x.txt.``.  ``ls -la`` command was used again to review the updates I made.

<h2>Change directory permissions</h2>

![image](https://github.com/user-attachments/assets/a1b79966-8e56-40d5-ac67-48d324072d21)


Researcher2 is the only user that should be able to access the files and contents for the drafts directory.  This means that no one other than researcher2 should have execute
permissions. Using ``ls -la`` , I was able to review the permissions of the ``drafts`` directory and see that group has execute permissions. 
I removed execute permissions from group for the ``drafts`` directory using ``chmod g-x drafts``.

<h2>Summary</h2>

Using ``ls -la``, I was able to conclude that some permissions for files and directories in the projects folder for user researcher2 did not match the appropriate authorization that was supposed to be given. Using the ``chmod`` command, I was able to update those permissions to be appropriate. 
