# File Permissions in Linux

## Activity Summary

In this activity, a portfolio document was created to demonstrate the use of Linux commands
to examine and manage file and directory permissions. This document can be added to a
cybersecurity portfolio and shared with potential employers or recruiters as evidence of
technical skills.

The activity is based on a scenario within a large organization where it is necessary to
verify that file permissions match the appropriate level of authorization in order to
maintain system security.

---

## Scenario

You are a security professional working with a research team in a large organization.
Part of your role is to ensure that users have the correct permissions to access files and
directories.

Your task is to examine existing permissions in the file system, determine whether they
match the required authorization, and modify the permissions to remove any unauthorized
access.

---

## Step 3: Check File and Directory Details

To check the permissions set for files, subdirectories, and hidden files within the
`projects` directory, the following command was used:

    ls -la /home/researcher2/projects

This command displays a detailed list of all files and directories, including hidden files,
along with their current permissions.

---

## Step 4: Describe the Permission String

Each file and directory has a 10-character permission string that indicates the file type
and the permissions assigned.

- **1st character:** File type  
  - `d` indicates a directory  
  - `-` indicates a regular file  

- **Characters 2–4:** User permissions (read, write, execute)  
- **Characters 5–7:** Group permissions  
- **Characters 8–10:** Permissions for others  

### Example

    -rw-rw-r--

This permission string means:
- The item is a regular file
- The user and group have read and write permissions
- Other users have read-only permissions
- No execute permissions are granted

---

## Step 5: Change File Permissions

The organization does not allow other users to have write access to any files. Based on the
current permissions, the file `project_k.txt` was identified as having write permissions for
others.

To remove this permission, the following command was used:

    chmod o-w project_k.txt

After running this command, the permissions were reviewed again to confirm that write access
for other users was successfully removed.

---

## Step 6: Change Permissions on a Hidden File

The file `.project_x.txt` is a hidden file that has been archived. This file should not have
write permissions for anyone, but both the user and the group should have read access.

To assign the correct permissions, the following commands were executed:

    chmod u-w .project_x.txt
    chmod g-w,g+r .project_x.txt

These commands removed write permissions from the user and group and ensured that the group
retained read access.

---

## Step 7: Change Directory Permissions

All files and directories within the `projects` directory belong to the user `researcher2`.
Only this user should be able to access the `drafts` directory and its contents.

To meet this requirement, execute permissions were removed from the group and other users
using the following command:

    chmod g-x,o-x drafts

After applying this change, the directory permissions were reviewed to confirm that only
`researcher2` has access.

---

## Step 8: Final Permission Verification

After all changes were made, the `ls -la` command was used again to verify that the file and
directory permissions aligned with the organization’s security policies.

    ls -la /home/researcher2/projects

---

## Step 9: Conclusion

This activity demonstrated how to examine and modify file and directory permissions using
Linux commands. The `ls -la` command was used to identify incorrect permissions, and the
`chmod` command was used to apply the necessary changes.

Proper permission management helps prevent unauthorized access and is a critical component
of maintaining security in Linux systems.

---

## Final Summary

In this project, file and directory permissions within the `projects` directory were reviewed
and updated to meet organizational security requirements. Using Linux commands ensured that
only authorized users have access to system resources.
