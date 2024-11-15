# User Management and Access Control on Linux

This guide covers essential commands for adding and deleting users, listing all users, and setting Access Control Lists (ACLs) for specific files and directories.

---

## 1. Adding a New User

To create a new user with a home directory and set their default shell, use the following command:

\`\`\`bash
useradd -m -s /usr/bin/zsh <username>
\`\`\`

- **`-m`**: Creates a home directory for the new user.
- **`-s /usr/bin/zsh`**: Sets Zsh as the default shell for the user.

### Set a Password for the User

After creating the user, assign them a password:

\`\`\`bash
passwd <username>
\`\`\`

### Add the User to the Sudoers Group

To grant sudo privileges to the user:

\`\`\`bash
usermod -aG sudo <username>
\`\`\`

---

## 2. Listing All Users

To view a list of all users on the system, use:

\`\`\`bash
cat /etc/passwd | awk -F: '{print $1}'
\`\`\`

This command extracts and displays the usernames from the `/etc/passwd` file.

---

## 3. Deleting a User

To delete a user and their associated configuration files, use:

\`\`\`bash
userdel -r <username>
\`\`\`

- **`-r`**: Deletes the user's home directory and mail spool, along with any configuration files.

---

## 4. Setting Access Control Lists (ACL)

ACLs allow you to define more granular permissions for files and directories. Use the `setfacl` command to specify permissions for users and groups on specific directories.

### Grant User and Group-Specific Permissions on Directories

#### Example 1: Set Full Access for `user_b_s` and Limited Access for `secret` Group

\`\`\`bash
sudo setfacl -m u:user_b_s:rwx,g:secret:r-x,o::--- 2_secret/
\`\`\`

- **`u:user_b_s:rwx`**: Grants read, write, and execute permissions to `user_b_s`.
- **`g:secret:r-x`**: Grants read and execute permissions to members of the `secret` group.
- **`o::---`**: Removes all permissions for others (users not part of the specified user or group).

#### Example 2: Set Read and Execute Permissions for the `secret` Group

\`\`\`bash
sudo setfacl -m g:secret:r-x 3_confidential/
\`\`\`

#### Example 3: Another Directory with Limited Access for the `secret` Group

\`\`\`bash
sudo setfacl -m g:secret:r-x 4_unclassified/
\`\`\`

---

## Summary of Commands

| Command                                          | Description                                                  |
|--------------------------------------------------|--------------------------------------------------------------|
| `useradd -m -s /usr/bin/zsh <username>`          | Adds a new user with a home directory and default shell.     |
| `passwd <username>`                              | Sets a password for the specified user.                      |
| `usermod -aG sudo <username>`                    | Adds the user to the sudoers group.                          |
| `cat /etc/passwd | awk -F: '{print $1}'`         | Lists all users on the system.                               |
| `userdel -r <username>`                          | Deletes a user and their configuration files.                |
| `sudo setfacl -m u:user_b_s:rwx,g:secret:r-x,o::--- <directory>` | Sets ACLs for users and groups on directories. |

---

## Notes

- **Sudo Privileges**: Adding a user to the `sudo` group enables them to execute administrative commands with elevated privileges.
- **ACLs**: ACLs provide flexible permission settings for files and directories, allowing you to assign specific permissions to individual users and groups.
