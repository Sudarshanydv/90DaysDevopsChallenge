# 100 Days of DevOps Challenge

# Day 01 - Linux Fundamentals

## Introduction 
 
Today I started my **100 Days of DevOps Challenge** with Linux fundamentals.

Linux is one of the most important foundations of DevOps. Most cloud servers, web servers, containers, CI/CD environments, and production systems use Linux.

As a DevOps Engineer, Linux is required for working with technologies such as:

- AWS
- Docker
- Kubernetes
- Jenkins
- Terraform
- Ansible
- Nginx
- CI/CD Pipelines
- Monitoring and Logging

The goal of Day 1 was to understand the basic Linux commands and learn how to manage a Linux server.

---

## What is Linux?

Linux is an open-source operating system widely used for:

- Servers
- Cloud infrastructure
- Web applications
- Containers
- Networking
- Development
- DevOps environments

In DevOps, Linux is commonly used to deploy applications, manage servers, troubleshoot problems, monitor resources, analyze logs, and automate infrastructure.

---

# 1. Linux File System

Linux uses a hierarchical file system.

Everything starts from the root directory:

```text
/
```

Some important Linux directories are:

| Directory | Purpose |
|---|---|
| `/` | Root of the Linux file system |
| `/home` | Home directories of normal users |
| `/etc` | Configuration files |
| `/var` | Logs and frequently changing data |
| `/tmp` | Temporary files |
| `/usr` | User programs and utilities |
| `/bin` | Essential Linux commands |
| `/root` | Home directory of the root user |
| `/opt` | Optional application/software files |

Understanding the Linux file system is important because configuration files, logs, applications, and system files are stored in different locations.

---

# 2. Basic Linux Commands

## pwd

`pwd` means **Print Working Directory**.

It shows the directory where you are currently working.

```bash
pwd
```

Example output:

```text
/home/ec2-user
```

---

## ls

`ls` is used to list files and directories.

```bash
ls
```

Useful options:

```bash
ls -l
ls -a
ls -lh
```

### Options

- `ls -l` → Shows detailed information
- `ls -a` → Shows hidden files
- `ls -lh` → Shows human-readable file sizes

---

## cd

`cd` means **Change Directory**.

```bash
cd /var/log
```

Go to the parent directory:

```bash
cd ..
```

Go to the home directory:

```bash
cd ~
```

---

# 3. Creating Files and Directories

## mkdir

`mkdir` is used to create a directory.

```bash
mkdir devops
```

This creates a directory called `devops`.

---

## touch

`touch` is used to create an empty file.

```bash
touch notes.txt
```

This creates:

```text
notes.txt
```

---

# 4. Copy, Move and Delete

## cp

`cp` is used to copy files or directories.

```bash
cp notes.txt backup.txt
```

This creates a copy of `notes.txt` named `backup.txt`.

---

## mv

`mv` is used to move or rename files.

Rename a file:

```bash
mv notes.txt linux-notes.txt
```

Move a file:

```bash
mv linux-notes.txt /tmp/
```

---

## rm

`rm` is used to delete files.

```bash
rm linux-notes.txt
```

Delete a directory:

```bash
rm -r devops
```

> **Important:** Be careful while using `rm`, especially when working as the root user.

---

# 5. Reading Files

## cat

`cat` displays the contents of a file.

```bash
cat notes.txt
```

---

## less

`less` is useful for viewing large files.

```bash
less /var/log/messages
```

Use `q` to exit.

---

## head

`head` displays the beginning of a file.

```bash
head notes.txt
```

---

## tail

`tail` displays the end of a file.

```bash
tail notes.txt
```

For monitoring logs in real time:

```bash
tail -f application.log
```

The `-f` option continuously displays new log entries.

---

# 6. Linux Users and Groups

Linux supports multiple users and groups.

Users and groups are important for managing access to servers and applications.

## whoami

Shows the currently logged-in user.

```bash
whoami
```

---

## id

Shows information about the current user.

```bash
id
```

---

## Create a User

```bash
sudo useradd devopsuser
```

---

## Create a Group

```bash
sudo groupadd devops
```

---

## Add User to Group

```bash
sudo usermod -aG devops devopsuser
```

The `-aG` option adds the user to the group without removing the user from existing supplementary groups.

---

# 7. Linux File Permissions

Linux uses permissions to control access to files and directories.

There are three basic permissions:

```text
r = Read
w = Write
x = Execute
```

Permissions are applied to:

```text
Owner
Group
Others
```

Example:

```text
-rwxr-xr--
```

This means:

```text
Owner  → Read + Write + Execute
Group  → Read + Execute
Others → Read
```

---

## Check Permissions

```bash
ls -l
```

---

## chmod

`chmod` is used to change file permissions.

Example:

```bash
chmod 755 script.sh
```

`755` means:

```text
Owner  → Read + Write + Execute
Group  → Read + Execute
Others → Read + Execute
```

---

## chown

`chown` is used to change file ownership.

```bash
chown user:group file.txt
```

Example:

```bash
sudo chown devopsuser:devops file.txt
```

Understanding permissions is extremely important in DevOps because incorrect permissions can cause application and deployment failures.

---

# 8. Process Management

A process is a running program or application.

## ps

Shows running processes.

```bash
ps
```

To display more processes:

```bash
ps aux
```

---

## top

`top` displays processes and system resource usage in real time.

```bash
top
```

It can help identify processes consuming high CPU or memory.

---

## kill

`kill` is used to terminate a process.

First find the Process ID (PID):

```bash
ps aux
```

Then:

```bash
kill <PID>
```

Example:

```bash
kill 1234
```

---

# 9. Service Management

Linux services can be managed using `systemctl`.

For example, Nginx can be managed using:

## Check Service Status

```bash
sudo systemctl status nginx
```

---

## Start Service

```bash
sudo systemctl start nginx
```

---

## Stop Service

```bash
sudo systemctl stop nginx
```

---

## Restart Service

```bash
sudo systemctl restart nginx
```

---

## Enable Service at Boot

```bash
sudo systemctl enable nginx
```

This is useful when managing services such as:

- Nginx
- Docker
- Jenkins
- SSH
- Application services

---

# 10. Disk Management

## df

`df` shows disk space usage.

```bash
df -h
```

The `-h` option displays the information in a human-readable format.

Example:

```text
Filesystem      Size  Used Avail Use%
/dev/xvda1       20G   10G   10G  50%
```

---

## du

`du` shows how much disk space a file or directory is using.

```bash
du -sh /var/log
```

This is useful when troubleshooting disk-space problems.

---

# 11. Memory Management

## free

`free` displays memory and swap usage.

```bash
free -m
```

Example:

```text
              total   used   free
Mem           4096    1500   2596
```

This is useful for identifying memory-related issues.

---

# 12. Searching in Linux

## grep

`grep` searches for specific text inside files.

Example:

```bash
grep "ERROR" application.log
```

This searches for lines containing:

```text
ERROR
```

Another example:

```bash
grep "failed" application.log
```

`grep` is extremely useful when analyzing application and system logs.

---

## find

`find` searches for files and directories.

Example:

```bash
find /var/log -name "*.log"
```

This searches for files ending with `.log` inside `/var/log`.

Another example:

```bash
find /home -name "test.txt"
```

---

# 13. SSH

SSH stands for:

**Secure Shell**

SSH is used to securely connect to remote Linux servers.

Basic syntax:

```bash
ssh username@server-ip
```

Example:

```bash
ssh ec2-user@192.168.1.10
```

---

## SSH with AWS EC2

When connecting to an AWS EC2 Linux instance using a private key:

```bash
ssh -i my-key.pem ec2-user@<EC2-IP>
```

SSH is extremely important for DevOps because DevOps engineers frequently work with remote cloud servers.

---

# 14. Practical DevOps Troubleshooting Example

Imagine an application is running on an AWS EC2 Linux server.

Users report:

```text
Application is not working.
```

As a DevOps Engineer, we can troubleshoot the server step by step.

---

## Step 1: Connect to the Server

```bash
ssh -i my-key.pem ec2-user@<EC2-IP>
```

---

## Step 2: Check Disk Usage

```bash
df -h
```

If the disk is full, applications may fail.

---

## Step 3: Check Memory

```bash
free -m
```

If available memory is very low, applications may become slow or stop working.

---

## Step 4: Check Running Processes

```bash
ps aux
```

This helps determine whether the application is running.

---

## Step 5: Check the Application Service

```bash
sudo systemctl status nginx
```

If the service is stopped:

```bash
sudo systemctl start nginx
```

---

## Step 6: Check Application Logs

```bash
tail -f /var/log/application.log
```

---

## Step 7: Search for Errors

```bash
grep "ERROR" /var/log/application.log
```

This helps identify the root cause of the problem.

---

# 15. Important Linux Commands Learned

| Command | Purpose |
|---|---|
| `pwd` | Show current directory |
| `ls` | List files |
| `cd` | Change directory |
| `mkdir` | Create directory |
| `touch` | Create file |
| `cp` | Copy files |
| `mv` | Move/rename files |
| `rm` | Delete files |
| `cat` | Display file contents |
| `less` | View large files |
| `head` | Show beginning of file |
| `tail` | Show end of file |
| `grep` | Search text |
| `find` | Find files/directories |
| `whoami` | Show current user |
| `id` | Show user information |
| `chmod` | Change permissions |
| `chown` | Change ownership |
| `ps` | Show processes |
| `top` | Monitor processes |
| `kill` | Stop a process |
| `systemctl` | Manage services |
| `df` | Check disk usage |
| `du` | Check directory size |
| `free` | Check memory |
| `ssh` | Connect to remote server |

---

# 16. Why Linux is Important for DevOps

Linux is the foundation for many DevOps activities.

A DevOps Engineer may use Linux to:

- Deploy applications
- Manage cloud servers
- Configure web servers
- Analyze application logs
- Troubleshoot production issues
- Manage users and permissions
- Monitor CPU, memory, and disk
- Run Docker containers
- Manage Kubernetes nodes
- Configure CI/CD servers
- Automate infrastructure
- Manage production environments

---

# 17. DevOps Learning Roadmap

The learning path I am following:

```text
Linux
   ↓
Git & GitHub
   ↓
AWS
   ↓
Docker
   ↓
Jenkins / CI-CD
   ↓
Terraform
   ↓
Ansible
   ↓
Kubernetes
   ↓
Monitoring & Logging
   ↓
Real-World DevOps Projects
```

---

# 18. Key Takeaways

From Day 1, I learned that Linux is more than just memorizing commands.

The important concepts are:

1. Understanding the Linux file system
2. Creating and managing files and directories
3. Managing users and groups
4. Understanding file permissions
5. Managing processes
6. Managing Linux services
7. Monitoring disk and memory
8. Searching and analyzing logs
9. Connecting to remote servers using SSH
10. Troubleshooting real-world server issues

These fundamentals will help me understand and work with advanced DevOps technologies.

---

# Day 1 Completed

## Linux Fundamentals

Today I built my Linux foundation as part of my **100 Days of DevOps Challenge**.

Next, I will continue building my knowledge step by step and apply these concepts through hands-on practice.

**Day 1 Completed — Learning DevOps one day at a time.**

---

## Tags

#DevOps #Linux #AWS #CloudComputing #GitHub #DevOpsEngineer #CloudEngineer #LinuxCommands #100DaysOfDevOps
