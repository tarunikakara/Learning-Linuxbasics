# Linux Basics Tutorial

A comprehensive guide to essential Linux commands and concepts for beginners, students, and anyone starting their career in technology.

---

## Table of Contents

1. [Introduction](#introduction)
2. [Files & Directories](#files--directories)
3. [Basic Linux Commands](#basic-linux-commands)
4. [System Information Commands](#system-information-commands)
5. [File & Folder Operations](#file--folder-operations)
6. [Editing Files with vi Editor](#editing-files-with-vi-editor)
7. [Permissions](#permissions)
8. [Users & Ownership](#users--ownership)
9. [Delete Files & Folders](#delete-files--folders)
10. [System Monitoring](#system-monitoring)
11. [Disk Usage](#disk-usage)
12. [Search Files](#search-files)
13. [User Management](#user-management)
14. [Package Management](#package-management)
15. [Key Takeaways](#key-takeaways)

---

## Introduction

Understanding basic **Linux/Unix commands** is very important for any technology professional, whether working with middleware, DevOps, Cloud, AI, or any other tech role.

If you're a beginner, student, or just starting your career, mastering these fundamental concepts will significantly help you succeed in your tech journey.

---

## Files & Directories

### Core Concepts

- Data is stored in **files**
- Files are managed inside **folders (directories)**

In Linux, everything is organized in a hierarchical directory structure, similar to filing cabinets and folders.

---

## Basic Linux Commands

### 1. Check Current Directory

Print your current location in the file system:

```bash
pwd
```

**Output:** Shows the full path of your current working directory (e.g., `/home/username/documents`)

### 2. List Files and Directories

View contents of the current directory:

```bash
ls
```

For a more detailed view:

```bash
ls -l
```

**Output:** Shows files with permissions, owner, size, and modification date

### 3. Change Directory

Navigate to different directories:

```bash
cd <folder_name>       # Move into a specific folder
cd ..                  # Go back to parent directory
cd /                   # Jump to root directory
cd ~                   # Jump to home directory
```

**Examples:**
```bash
cd /etc                # Go to /etc directory
cd Desktop             # Go to Desktop folder in current directory
cd ../..               # Go up two directory levels
```

---

## System Information Commands

Get information about your system:

```bash
uname -a               # Shows OS details (kernel name, version, hardware platform)
whoami                 # Displays current logged-in user
who -b                 # Shows last system reboot time
```

**Example Output:**
```
$ uname -a
Linux hostname 5.10.0-14-generic #1 SMP x86_64 GNU/Linux

$ whoami
john

$ who -b
 system boot  2024-03-20 09:15
```

---

## File & Folder Operations

### Create a Directory

```bash
mkdir basicsLinux
```

Creates a new folder named `basicsLinux`

### Create Files

```bash
touch file1.txt
touch file2.txt
```

Creates empty files with the specified names

### View/List Files

```bash
ls
ls -ltr                # Shows files sorted by modification time (oldest first)
```

---

## Editing Files with vi Editor

The `vi` (or `vim`) editor is a powerful, terminal-based text editor essential for Linux users.

### Open File for Editing

```bash
vi file1.txt
```

### Edit Modes

| Action | Command |
|--------|---------|
| Enter Insert Mode | Press `i` |
| Exit Insert Mode | Press `Esc` |
| Save & Exit | `:wq` |
| Exit without Saving | `:q!` |
| Delete entire line | `dd` |
| Search for word | `/word` then press `n` to go to next match |
| Undo last change | `u` |

### Step-by-Step Example

```
1. Type: vi file1.txt
2. Press i to enter Insert mode
3. Type your content
4. Press Esc to exit Insert mode
5. Type :wq to save and exit
```

---

## Permissions

Linux uses a three-level permission system: **User (Owner) | Group | Others**

### Permission Types

- `r` (read) = 4
- `w` (write) = 2
- `x` (execute) = 1

### View Permissions

```bash
ls -l
```

**Output Example:**
```
-rw-r--r-- 1 john team 1024 Mar 20 10:30 file1.txt
```

**Breaking down permissions:**
- `-rw-r--r--` = User(rw-) Group(r--) Others(r--)
- User: read & write (6)
- Group: read only (4)
- Others: read only (4)

### Change Permissions

```bash
chmod 777 file1.txt    # User, Group, Others: all permissions
chmod 755 file1.txt    # User: all, Group & Others: read & execute
chmod 644 file1.txt    # User: read & write, Group & Others: read only
```

### Permission Chart

| Value | Permission | Meaning |
|-------|-----------|---------|
| 7 | rwx | Read, Write, Execute |
| 6 | rw- | Read & Write |
| 5 | r-x | Read & Execute |
| 4 | r-- | Read only |
| 0 | --- | No permissions |

---

## Users & Ownership

### Change File Owner

```bash
chown user file1.txt
```

⚠️ **Note:** The user must exist on the system before assigning ownership. You typically need `sudo` or root privileges to change ownership.

### Example

```bash
sudo chown john file1.txt      # Change owner to john
sudo chown john:team file1.txt # Change owner to john and group to team
```

---

## Delete Files & Folders

### Delete a File

```bash
rm file.txt
```

### Delete a Folder and its Contents

```bash
rm -rf folderName
```

⚠️ **Warning:** `rm -rf` is permanent and cannot be undone. Use with caution!

---

## System Monitoring

### Check CPU & Memory Usage

```bash
top
```

This opens an interactive dashboard showing:
- CPU usage
- Memory usage
- Running processes
- Process details (PID, user, resource consumption)

Press `q` to exit.

### View Running Processes

```bash
ps -ef | grep <process_name>
```

**Example:**
```bash
ps -ef | grep nginx    # Find all nginx processes
```

---

## Disk Usage

### Check Overall Disk Usage

```bash
df -h
```

**Output:** Shows disk space usage for all mounted filesystems in human-readable format (KB, MB, GB)

### Check Folder Size

```bash
du -sh
```

**Examples:**
```bash
du -sh /home           # Total size of /home directory
du -sh /var/log/*      # Size of each file/folder in /var/log
```

---

## Search Files

Find files by name in the file system:

```bash
find /path -name file1.txt
```

**Examples:**
```bash
find / -name "*.txt"                    # Find all .txt files
find /home -name "config*"              # Find files starting with "config"
find /var/log -type f -name "*.log"     # Find all .log files
```

---

## User Management

### Add a New User

```bash
adduser username
```

This command will prompt you for:
- Password
- Full name
- Room number
- Work phone
- Home phone
- Other information

### Switch to Another User

```bash
su - username
```

You'll be prompted to enter the user's password.

### Check Current User

```bash
whoami
```

---

## Package Management

Different Linux distributions use different package managers:

| Distribution | Package Manager | Update Command |
|-------------|-----------------|-----------------|
| Amazon Linux | yum | `yum update -y` |
| CentOS / RHEL | yum / dnf | `yum update -y` |
| Ubuntu / Debian | apt | `apt update` |

### Update System Packages

**For Amazon Linux / CentOS:**
```bash
yum update -y
```

**For Ubuntu / Debian:**
```bash
apt update
apt upgrade -y
```

### Install a Package (Example: Nginx)

**For Amazon Linux / CentOS:**
```bash
yum install nginx -y
```

**For Ubuntu / Debian:**
```bash
apt install nginx -y
```

### Start a Service

```bash
systemctl start nginx
```

### Enable Service to Start on Boot

```bash
systemctl enable nginx
```

This ensures the service automatically starts when the system reboots.

### Check Service Status

```bash
systemctl status nginx
```

**Example Output:**
```
● nginx.service - The NGINX HTTP and reverse proxy server
   Loaded: loaded (/usr/lib/systemd/system/nginx.service; enabled)
   Active: active (running) since Wed 2024-03-20 10:15:30 UTC
```

### Other Service Commands

```bash
systemctl restart nginx   # Restart the service
systemctl stop nginx      # Stop the service
systemctl reload nginx    # Reload configuration without stopping
```

---

## Key Takeaways

### Essential Skills

1. **You don't need to be a Linux expert** – but you must know the basics
2. **Master these core areas:**
   - ✅ File handling (create, delete, navigate)
   - ✅ Permissions (understand and modify)
   - ✅ User management (add, switch users)
   - ✅ Package installation (install software, manage services)

### Why These Matter

These fundamental Linux skills are **essential** for careers in:
- 🚀 DevOps
- ☁️ Cloud Computing & AWS
- 🤖 AI/Machine Learning
- 🔧 Middleware & Systems Administration
- 📱 Any modern tech role

### Next Steps

1. **Practice regularly** – Try these commands in a terminal
2. **Experiment safely** – Use a test environment or Linux box
3. **Learn by doing** – Create files, modify permissions, manage users
4. **Explore more** – Check man pages: `man command_name`

---

## Useful Resources

### Get Help on Any Command

```bash
man <command>          # Opens manual pages
<command> --help       # Shows help information
```

### Examples

```bash
man ls                 # Learn about the ls command
man chmod              # Learn about permission changes
ls --help              # Quick help for ls command
```

---

## Cheat Sheet

| Task | Command |
|------|---------|
| Show current directory | `pwd` |
| List files | `ls -l` |
| Change directory | `cd /path` |
| Create directory | `mkdir dirname` |
| Create file | `touch filename` |
| Edit file | `vi filename` |
| Show permissions | `ls -l` |
| Change permissions | `chmod 755 filename` |
| Change owner | `chown user filename` |
| Delete file | `rm filename` |
| Delete directory | `rm -rf dirname` |
| Show CPU/Memory | `top` |
| Show disk usage | `df -h` |
| Install package | `yum install pkgname` or `apt install pkgname` |
| Start service | `systemctl start servicename` |
| Check status | `systemctl status servicename` |

---

## Contact & Questions

For more information, tips, and advanced Linux tutorials, feel free to reach out or contribute to this repository!

Happy Learning! 🚀

---

**Last Updated:** March 2024  
**Version:** 1.0
