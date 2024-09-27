# manage-file-permissions

# Managing File Permissions in Linux

## Overview

In this lab, we explored file and directory permissions in a Linux environment, focusing on understanding and modifying access controls for various files. Below is a detailed breakdown of the steps we took to identify and resolve permission issues.

---

## Part 1: Verification of Files and Permissions

1. **File Ownership and Group Verification**:
   - Verified the files in the `/home/research2/projects` directory.
   - Noted that all files are owned by the user `researcher2` and the group `research_team`.
   - Discovered hidden files using the command:
     ```bash
     ls -l
     ```
     ![Screen Shot 2024-09-26 at 8 57 25 AM](https://github.com/user-attachments/assets/225050db-6944-4918-a80a-4ec05065e924)

































2. **Identifying Incorrect Permissions**:
   - Noted inappropriate access levels, particularly for `project_k.txt`, which had write permissions for others.

3. **Correcting Permissions**:
   - Removed write permissions for others on `project_k.txt`:
     ```bash
     chmod o-w project_k.txt
     ```
     ![Screen Shot 2024-09-26 at 9 07 05 AM](https://github.com/user-attachments/assets/f0717016-0634-4d82-b762-215cf0d759c7)


4. **Handling Restricted Files**:
   - Examined `project_m.txt`, ensuring it was only accessible by the user:
     ```bash
     chmod g=- project_m.txt
     ```
![Screen Shot 2024-09-26 at 9 12 04 AM](https://github.com/user-attachments/assets/a6577578-f07f-41a8-b83f-efc48155929b)
![Screen Shot 2024-09-26 at 9 24 26 AM](https://github.com/user-attachments/assets/a97899f2-d933-4ba3-b6f1-7f9c49b8968e)

5. **Managing Hidden Files**:
   - Adjusted permissions for the hidden file `.project_x.txt` to be readable only:
     ```bash
     chmod u=r,g=r .project_x.txt
     ```
![Screen Shot 2024-09-26 at 9 25 52 AM](https://github.com/user-attachments/assets/fe1385bd-3fae-48b1-8416-7de5e79c7afb)

---

## Part 2: Modifying Directory Permissions

6. **Directory Permissions for Drafts**:
   - Focused on the `drafts` directory, initially checking permissions.
   - Removed group execute permission to restrict access:
     ```bash
     chmod g-x /home/research2/projects/drafts
     ```

---

## Conclusion

Through this lab, we gained practical experience in using basic Linux Bash shell commands to:
- Examine file and directory permissions.
- Change permissions on files and directories to enhance security.

Understanding and managing file permissions is critical in Linux for protecting sensitive data and ensuring that only authorized users have access. This exercise marks a significant milestone in our journey toward mastering Linux administration and managing authorization effectively.
