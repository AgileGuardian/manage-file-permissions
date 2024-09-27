# Managing File Permissions in Linux

## Introduction

As a security professional at a large organization, my primary responsibility involves working closely with the research team to ensure that all users are granted appropriate permissions on our file systems. This task is crucial in maintaining the integrity and security of sensitive research data.

In this role, I routinely examine existing permissions across various directories and files to determine if they align with the designated access controls. If discrepancies are found, it is my duty to modify the permissions accordingly, ensuring that only authorized personnel can access or modify the data. By implementing strict permission management practices, I help safeguard our systems against unauthorized access and potential data breaches, ultimately supporting the organization's commitment to security and compliance.

---

## Overview

In this lab, we explored file and directory permissions in a Linux environment, focusing on understanding and modifying access controls for various files. Below is a detailed breakdown of the steps we took to identify and resolve permission issues.

---

## Part 1: Verification of Files and Permissions

### 1. File Ownership and Group Verification

The first step involved verifying the files and their permissions in the `/home/research2/projects` directory. We used the `ls -la` command to list all files, including hidden files, and to display detailed information about file permissions, ownership, and group associations.

```bash
ls -la /home/research2/projects
```

The output displayed a 10-character string, which represents file permissions, ownership, and group. Each part of the string can be broken down as follows:

- The first character indicates the type of file: `-` for regular files, `d` for directories, and `l` for symbolic links.
- The next nine characters are split into three groups:
  - User permissions (first three characters)
  - Group permissions (next three characters)
  - Other permissions (last three characters)

Example output:
```
-rw-r--r--  1 researcher2 research_team  4096 Sep 25 08:57 project_k.txt
```

This shows:
- `-rw-r--r--`: The first character `-` indicates a regular file, `rw-` means the owner has read and write permissions, `r--` means the group has read-only permissions, and `r--` means others have read-only permissions.
- `researcher2`: This is the file owner.
- `research_team`: This is the file group.

### 2. Identifying Incorrect Permissions

Upon reviewing the permissions, we identified inappropriate access levels for certain files. Specifically, `project_k.txt` was found to have write permissions enabled for others (`o`).

### 3. Correcting Permissions

To fix this issue, we removed write permissions for others using the `chmod` command:

```bash
chmod o-w project_k.txt
```

Now, the updated permissions restrict write access to the file owner and deny it for others.

### 4. Handling Restricted Files

Another file, `project_m.txt`, required further restriction, ensuring it was only accessible by the user. We removed all group permissions with the following command:

```bash
chmod g=- project_m.txt
```

This command explicitly removes all permissions for the group.

### 5. Managing Hidden Files

Hidden files (files starting with a `.`) are often used for configuration or sensitive data storage. In this case, we modified the permissions for the hidden file `.project_x.txt` to be readable only by both the owner and the group:

```bash
chmod u=r,g=r .project_x.txt
```

This ensures the file cannot be modified but can still be read.

---

## Part 2: Modifying Directory Permissions

### 6. Directory Permissions for Drafts

For the `drafts` directory, we reviewed its permissions and removed the group execute permission to restrict directory access:

```bash
chmod g-x /home/research2/projects/drafts
```

This action ensures that only the file owner can access the directory contents, improving overall security.

---

## Conclusion

In this lab, we practiced essential file and directory permission management in Linux. We utilized `chmod` to update permissions and `ls -la` to check and interpret the current state of file and directory permissions. Key concepts covered include:

- Interpreting the 10-character string that represents file permissions.
- Identifying and resolving incorrect permissions on both files and directories.
- Handling hidden files and applying appropriate access controls.
- Understanding the critical role of file permissions in securing sensitive data.

Effective management of file permissions is a cornerstone of Linux administration, supporting the security and integrity of an organization’s data. Through this exercise, we enhanced our ability to protect sensitive information by ensuring that only authorized personnel have the correct access levels.
