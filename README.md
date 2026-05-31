# Portfolio Project: Linux File Permissions Audit

## Project Description
To maintain a secure file system, users must only have access to the files they absolutely need. In this project—completed as part of a hands-on Google skills lab—I conducted a full security audit of an organization's Linux server. I successfully identified unauthorized access levels and utilized Linux commands to modify permissions, securing both standard and hidden files to align with strict organizational security policies.

## Step 1: Check File and Directory Details
To check the current permissions of the files and directories in the `projects` directory, I used the `ls -la` command. The `ls` command lists the contents of a directory. The `-l` flag displays the output in a long format, revealing detailed information such as file permissions, ownership, and size. The `-a` flag ensures that all files are shown, including hidden files that begin with a dot (.).


<img width="1055" height="642" alt="1st ss" src="https://github.com/user-attachments/assets/a4a8f0fc-b8cb-4ec0-9454-28233b9b14d8" />


## Step 2: Describe the Permissions String
In the output of the `ls -la` command, the 10-character string represents the specific access rights for a file or directory. For example, let's look at the string **`-rw-rw-r--`**:
* **Character 1 (`-`):** Indicates the file type. A hyphen (`-`) means it is a regular file, whereas a `d` would indicate a directory.
* **Characters 2-4 (`rw-`):** Represent the **user** (owner) permissions. In this case, the user has read (`r`) and write (`w`) access, but no execute (`-`) access.
* **Characters 5-7 (`rw-`):** Represent the **group** permissions. The group assigned to this file also has read and write access.
* **Characters 8-10 (`r--`):** Represent the **other** (anyone else on the system) permissions. In this case, others only have read access.

## Step 3: Change File Permissions
The organization's policy dictates that 'others' should not have write access to any files. Upon reviewing the directory, I noticed that a file had write permissions for others. To fix this, I used the `chmod o-w project_k.txt` command. The `chmod` command modifies file permissions, `o-w` specifically removes (`-`) write (`w`) access for others (`o`), and `project_k.txt` is the target file.

<img width="1038" height="783" alt="2nd ss" src="https://github.com/user-attachments/assets/770504a1-49c2-434d-a0bb-7d075db265dc" />



## Step 4: Change File Permissions on a Hidden File
The hidden archive file `.project_x.txt` needed to be secured so that no one has write permissions, but the user and group retain read access. I used the command `chmod a-w .project_x.txt`. The `a-w` argument tells the system to remove (`-`) write (`w`) permissions for all (`a`) users (user, group, and others). Because it is a hidden file, I made sure to include the leading dot in the filename.

<img width="867" height="593" alt="3rd ss" src="https://github.com/user-attachments/assets/783807a3-f484-4fba-8676-cd2d5adfd7e8" />



## Step 5: Change Directory Permissions
The `drafts` directory belongs to `researcher2` and must be restricted so that no one else can access its contents. I used the command `chmod go-rwx drafts`. This command modifies the permissions by removing (`-`) read (`r`), write (`w`), and execute (`x`) access for both the group (`g`) and others (`o`), ensuring that only the owner retains access to the directory.

<img width="833" height="598" alt="4th ss" src="https://github.com/user-attachments/assets/0a510974-0637-4795-9b5f-b9d9bc0a90c2" />



## Summary
To secure the research team's system, I audited the file permissions using the `ls -la` command to uncover both visible and hidden file details. I identified unauthorized access levels and used the `chmod` utility to systematically revoke write privileges from 'others' on standard files, secure hidden archive files, and restrict access to the drafts directory exclusively to its owner. This process successfully aligned the system's permissions with the organization's strict authorization policies.
