Linux Filesystem and Basic Commands
Important Path Symbols

    / is the root of the entire Linux filesystem.
    ~ represents the current user's home directory.
    . represents the current directory.
    .. represents the parent directory.

My home directory is:

/home/karim
Absolute and Relative Paths

An absolute path starts from the root directory.

Example:

/home/karim/devops/linux-operations-toolkit

A relative path starts from the current directory.

Example:

docs/linux-filesystem.md
Commands
pwd

Displays the current working directory.
ls

Lists the visible files and directories in the current directory.
ls -la

Lists all files, including hidden files, with details such as permissions, owner, size, and modification date.
cd

Changes the current directory.

Examples:

    cd directory enters a directory.
    cd .. moves to the parent directory.
    cd ~ returns to the home directory.

mkdir

Creates a new directory.

The -p option creates missing parent directories when necessary.

Example:

mkdir -p ~/devops/practice/logs
touch

Creates an empty file or updates an existing file's timestamp.

Example:

touch notes.txt
cp

Copies a file or directory.

Example:

cp original.txt copy.txt
mv

Moves or renames a file or directory.

Example:

mv old-name.txt new-name.txt
rm

Permanently removes a file.

Example:

rm file.txt

The -r option removes a directory and everything inside it.

The -i option asks for confirmation before deletion.

Example:

rm -ri practice-directory
tree

Displays files and directories in a tree structure.
file

Attempts to identify the type of a file.
stat

Displays detailed information about a file, including its size, ownership, permissions, and timestamps.
Important Linux Directories

    /home contains normal users' personal directories.
    /etc contains system and application configuration.
    /var contains changing application data and logs.
    /var/log contains system and application logs.
    /tmp contains temporary files.
    /dev represents devices as files.
    /proc provides information about processes and the running system.
    /boot contains files required to start Linux.
    /usr contains installed programs, libraries, and shared resources.

What I Learned

Linux uses one filesystem starting from /.

Terminal commands operate inside the current working directory unless an absolute path is provided.
The rm command must be used carefully because deleted files normally do not go to a recycle bin.
