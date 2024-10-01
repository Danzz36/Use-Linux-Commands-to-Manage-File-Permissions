# Use-Linux-Commands-to-Manage-File-Permissions

## Project description 

The research team at the sample organization needs to update the file permissions for certain files and directories within the projects directory. The permissions do not currently reflect the level of authorization that should be given. Checking and updating these permissions will help keep their system secure. To complete this task, I performed the steps below. This was a guided project in the Google Cybersecurity Certificate. 

## Skills Learned

- **Linux File Management**: Gained practical experience using Linux command-line tools to manage files and directories.
- **File Permissions in Linux**: Acquired a deep understanding of the 10-character permission string, including user, group, and other access levels.
- **File Permission Modification**: Demonstrated the ability to use the `chmod` command to change read, write, and execute permissions on files and directories.
- **Hidden File Management**: Learned how to identify and modify permissions for hidden files, using commands such as `ls -la` and `chmod`.
- **Directory Permissions**: Applied knowledge of directory-specific permissions to restrict access, ensuring only authorized users could execute files.
- **Security Best Practices**: Ensured compliance with security protocols by restricting write and execute permissions where necessary to maintain system integrity.

## Steps

### Check file and directory details

The following code demonstrates how I used Linux commands to determine the existing permissions set for a specific directory in the file system.

![image](https://github.com/user-attachments/assets/96129dae-3c43-4147-aa02-c2b15e1457f2)

The first line of the screenshot displays the command I entered, and the other lines display the output. The code lists all contents of the `projects` directory. I used the `ls` command with the `-la` option to display a detailed listing of the file contents that also returned hidden files. The output of my command indicates that there is one directory named `drafts`, one hidden file named `.project_x.txt`, and five other project files. The 10-character string in the first column represents the permissions set on each file or directory.

### Describe the permissions string

The 10-character string can be deconstructed to determine who is authorized to access the file and their specific permissions. The characters and what they represent are as follows:

●	1st character: This character is either a `d` or hyphen (`-`) and indicates the file type. If it’s a `d`, it’s a directory. If it’s a hyphen (`-`), it’s a regular file.

●	2nd-4th characters: These characters indicate the read (`r`), write (`w`), and execute (`x`) permissions for the user. When one of these characters is a hyphen (`-`) instead, it indicates that this permission is not granted to the user.

●	5th-7th characters: These characters indicate the read (`r`), write (`w`), and execute (`x`) permissions for the group. When  one of these characters is a hyphen (`-`) instead, it indicates that this permission is not granted for the group.

●	8th-10th characters: These characters indicate the read       (`r`), write (`w`), and execute (`x`) permissions for other. This owner type consists of all other users on the system apart from the user and the group. When one of these characters is a hyphen (`-`) instead, that indicates that this permission is    not granted for other.

For example, the file permissions for `project_t.txt` are `-rw-rw-r--`. Since the first character is a hyphen (`-`), this indicates that `project_t.txt` is a file, not a directory. The second, fifth, and eighth characters are all `r`, which indicates that user, group, and other all have read permissions. The third and sixth characters are `w`, which indicates that only the user and group have write permissions. No one has execute permissions for `project_t.txt`.

### Change file permissions

The organization determined that other shouldn't have write access to any of their files. To comply with this, I referred to the file permissions that I previously returned. I determined `project_k.txt` must have the write access removed for other.

The following code demonstrates how I used Linux commands to do this:

![image](https://github.com/user-attachments/assets/30893d12-9197-46b0-b2fd-0333ed9eeef4)

The first two lines of the screenshot display the commands I entered, and the other lines display the output of the second command. The `chmod` command changes the permissions on files and directories. The first argument indicates what permissions should be changed, and the second argument specifies the file or directory. In this example, I removed write permissions from other for the `project_k.txt` file. After this, I used `ls -la` to review the updates I made.

### Change file permissions on a hidden file

The research team at the organization recently archived `project_x.txt`. They do not want anyone to have write access to this project, but the user and group should have read access. 

The following code demonstrates how I used Linux commands to change the permissions:

![image](https://github.com/user-attachments/assets/aad330dd-5daf-43e2-900d-9199b0975925)

The first two lines of the screenshot display the commands I entered, and the other lines display the output of the second command. I know `.project_x.txt` is a hidden file because it starts with a period (`.`). In this example, I removed write permissions from the user and group, and added read permissions to the group. I removed write permissions from the user with `u-w`. Then, I removed write permissions from the group with `g-w`, and added read permissions to the group with `g+r`. 

### Change directory permissions

The organization only wants the `researcher2` user to have access to the `drafts` directory and its contents. This means that no one other than `researcher2` should have execute permissions.

The following code demonstrates how I used Linux commands to change the permissions:

![image](https://github.com/user-attachments/assets/cbec4ec4-3a2e-4e59-a940-f6b264c081cc)

The first two lines of the screenshot display the commands I entered, and the other lines display the output of the second command. I previously determined that the group had execute permissions, so I used the `chmod` command to remove them. The `researcher2` user already had execute permissions, so they did not need to be added.

## Summary

I changed multiple permissions to match the level of authorization the organization wanted for files and directories in the `projects` directory. The first step in this was using `ls -la` to check the permissions for the directory. This informed my decisions in the following steps. I then used the `chmod` command multiple times to change the permissions on files and directories.








