Linux Users, Groups, Ownership, and Permissions
Users and Groups

Linux uses users and groups to control access to files and system resources.
whoami

Displays the username currently using the terminal.
id

Displays the user's ID, primary group ID, and supplementary groups.
groups

Displays all groups to which a user belongs.
root

root is the Linux administrator account and has full control over the system.
sudo

Runs one command with administrator privileges.

Example:

sudo apt update

The normal user account should be used for everyday work. sudo should only be used when administrator privileges are necessary.
Creating Users and Groups
adduser

Creates a new user, home directory, and primary group.

Example:

sudo adduser testuser
groupadd

Creates a new group.

Example:

sudo groupadd developers
usermod -aG

Adds an existing user to a supplementary group.

Example:

sudo usermod -aG developers testuser

    -a means append the group without removing existing memberships.
    -G specifies a supplementary group.

deluser

Deletes a user.

Example:

sudo deluser --remove-home testuser
groupdel

Deletes a group.

Example:

sudo groupdel developers
File Ownership

Every file has:

    An owner
    An owning group
    Permissions for other users

The ls -l command displays ownership and permissions.

Example:

-rw-r--r-- 1 karim karim notes.txt

The first karim is the owner.

The second karim is the owning group.
chown

Changes a file's owner.

Example:

sudo chown testuser notes.txt

It can also change the owner and group together.

Example:

sudo chown testuser:developers notes.txt
chgrp

Changes the owning group.

Example:

sudo chgrp developers notes.txt
Linux Permissions

Linux has three basic permissions:

    r means read.
    w means write.
    x means execute.
    - means the permission is not granted.

Permissions apply to:

    u for the owner or user
    g for the group
    o for others
    a for everyone

Example:

-rwxr-xr-x

This means:

    The owner can read, write, and execute.
    The group can read and execute.
    Others can read and execute.

Symbolic Permissions
chmod

Changes file permissions.

Give the owner execute permission:

chmod u+x script.sh

Give the owner all permissions:

chmod u+rwx script.sh

Remove write permission from the group:

chmod g-w file.txt

Give everyone read permission:

chmod a+r file.txt
Numeric Permissions

The numeric values are:

    Read: 4
    Write: 2
    Execute: 1

The values are added:

    7 means read, write, and execute.
    6 means read and write.
    5 means read and execute.
    4 means read only.
    0 means no permissions.

Permission 600

chmod 600 private.txt

    Owner can read and write.
    Group has no permission.
    Others have no permission.

This is suitable for private files.
Permission 644

chmod 644 notes.txt

    Owner can read and write.
    Group can read.
    Others can read.

This is suitable for normal documents.
Permission 755

chmod 755 script.sh

    Owner can read, write, and execute.
    Group can read and execute.
    Others can read and execute.

This is commonly used for executable scripts and directories.
Main Difference Between Commands

    chmod changes permissions.
    chown changes the owner.
    chgrp changes the owning group.
    sudo runs a command with administrator privileges.

Security Principle

Users should receive only the permissions necessary to perform their tasks. This is known as the principle of least privilege.
Giving everyone full permissions, such as 777, should normally be avoided because it allows any user to modify and execute the file.
