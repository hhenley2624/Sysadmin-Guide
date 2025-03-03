# Unix/Linux Sysadmin Command Reference Guide

## Table of Contents
- [File System Navigation](#file-system-navigation)
- [File Operations](#file-operations)
- [Directory Operations](#directory-operations)
- [File Permissions](#file-permissions)
- [Text Viewing and Editing](#text-viewing-and-editing)
- [System Information](#system-information)
- [User and Group Management](#user-and-group-management)
- [Process Management](#process-management)
- [Networking Commands](#networking-commands)
- [SSH and Remote Access](#ssh-and-remote-access)
- [File Compression](#file-compression)
- [Input/Output Redirection](#inputoutput-redirection)
- [File Searching and Pattern Matching](#file-searching-and-pattern-matching)
- [Package Management](#package-management)
- [System Services](#system-services)
- [Disk and Storage Management](#disk-and-storage-management)
- [Date and Time](#date-and-time)
- [Shell Scripting Basics](#shell-scripting-basics)

## File System Navigation

| Command | Description | Example Usage |
|---------|-------------|---------------|
| `pwd` | Print working directory | `pwd` |
| `cd` | Change directory | `cd /path/to/directory` |
| `cd ~` | Change to home directory | `cd ~` |
| `cd ..` | Move up one directory level | `cd ..` |
| `cd -` | Return to previous directory | `cd -` |
| `ls` | List directory contents | `ls` |
| `ls -l` | List with detailed format | `ls -l` |
| `ls -a` | List all files (including hidden) | `ls -a` |
| `ls -la` | Combine list all and long format | `ls -la` |
| `ls -lh` | Show file sizes in human-readable format | `ls -lh` |
| `find` | Search for files and directories | `find /path -name "filename"` |
| `whereis` | Locate binary, source, and manual page files | `whereis command` |
| `which` | Find executables in PATH | `which command` |

## File Operations

| Command | Description | Example Usage |
|---------|-------------|---------------|
| `cat` | Display file contents | `cat filename` |
| `cp` | Copy files or directories | `cp source destination` |
| `cp -r` | Copy directories recursively | `cp -r source_dir destination_dir` |
| `mv` | Move/rename files or directories | `mv oldname newname` |
| `rm` | Remove files | `rm filename` |
| `rm -f` | Force remove files without confirmation | `rm -f filename` |
| `rm -r` | Remove directories and their contents recursively | `rm -r directory` |
| `touch` | Create empty file or update timestamp | `touch filename` |
| `file` | Determine file type | `file filename` |
| `stat` | Display file or file system status | `stat filename` |
| `ln` | Create hard links | `ln target linkname` |
| `ln -s` | Create symbolic (soft) links | `ln -s target linkname` |
| `readlink` | Print resolved symbolic links | `readlink linkname` |
| `dd` | Convert and copy a file | `dd if=input of=output bs=1M` |
| `scp` | Secure copy (remote file copy) | `scp file user@host:/path` |

## Directory Operations

| Command | Description | Example Usage |
|---------|-------------|---------------|
| `mkdir` | Create directory | `mkdir dirname` |
| `mkdir -p` | Create parent directories as needed | `mkdir -p /path/to/directory` |
| `rmdir` | Remove empty directories | `rmdir dirname` |
| `du` | Estimate file space usage | `du -h filename` |
| `du -sh` | Summarize disk usage of directory | `du -sh directory` |
| `tree` | List contents of directories in a tree-like format | `tree /path` |

## File Permissions

| Command | Description | Example Usage |
|---------|-------------|---------------|
| `chmod` | Change file mode bits (permissions) | `chmod 755 filename` |
| `chmod +x` | Make file executable | `chmod +x filename` |
| `chmod -R` | Change permissions recursively | `chmod -R 755 directory` |
| `chown` | Change file owner and group | `chown user:group filename` |
| `chown -R` | Change ownership recursively | `chown -R user:group directory` |
| `chgrp` | Change group ownership | `chgrp group filename` |
| `umask` | Set default permissions for new files | `umask 022` |

## Text Viewing and Editing

| Command | Description | Example Usage |
|---------|-------------|---------------|
| `vi` / `vim` | Text editor | `vi filename` |
| `nano` | Simple text editor | `nano filename` |
| `emacs` | Advanced text editor | `emacs filename` |
| `less` | View text files with pagination | `less filename` |
| `more` | View text files with pagination | `more filename` |
| `head` | Output the first part of files | `head filename` |
| `tail` | Output the last part of files | `tail filename` |
| `tail -f` | Follow log file additions | `tail -f /var/log/syslog` |
| `grep` | Search for patterns in files | `grep "pattern" filename` |
| `grep -i` | Case-insensitive search | `grep -i "pattern" filename` |
| `grep -r` | Recursive search in directories | `grep -r "pattern" directory` |
| `sed` | Stream editor for filtering and transforming text | `sed 's/old/new/g' filename` |
| `awk` | Pattern scanning and processing language | `awk '{print $1}' filename` |
| `sort` | Sort lines of text files | `sort filename` |
| `uniq` | Report or omit repeated lines | `uniq filename` |
| `wc` | Count lines, words, and characters | `wc filename` |
| `diff` | Compare files line by line | `diff file1 file2` |
| `diff -u` | Output differences in unified format | `diff -u file1 file2` |
| `patch` | Apply a diff file to an original | `patch file < patch_file` |

## System Information

| Command | Description | Example Usage |
|---------|-------------|---------------|
| `uname` | Print system information | `uname -a` |
| `hostname` | Show or set system hostname | `hostname` |
| `whoami` | Print effective user ID | `whoami` |
| `id` | Print user and group information | `id` |
| `w` | Show who is logged on and what they are doing | `w` |
| `who` | Show who is logged on | `who` |
| `last` | Show a listing of last logged in users | `last` |
| `uptime` | Tell how long the system has been running | `uptime` |
| `free` | Display amount of free and used memory | `free -h` |
| `df` | Report file system disk space usage | `df -h` |
| `dmesg` | Print or control the kernel ring buffer | `dmesg` |
| `lsblk` | List block devices | `lsblk` |
| `lsusb` | List USB devices | `lsusb` |
| `lspci` | List PCI devices | `lspci` |
| `lsmod` | Show the status of modules in the Linux kernel | `lsmod` |
| `lshw` | List hardware | `lshw` |
| `vmstat` | Report virtual memory statistics | `vmstat` |
| `sysctl` | Configure kernel parameters at runtime | `sysctl -a` |

## User and Group Management

| Command | Description | Example Usage |
|---------|-------------|---------------|
| `useradd` | Create a new user | `useradd username` |
| `userdel` | Delete a user account | `userdel username` |
| `usermod` | Modify a user account | `usermod -aG groupname username` |
| `passwd` | Change user password | `passwd username` |
| `chfn` | Change user information | `chfn -f "Full Name" username` |
| `chsh` | Change login shell | `chsh -s /bin/bash username` |
| `groupadd` | Create a new group | `groupadd groupname` |
| `groupdel` | Delete a group | `groupdel groupname` |
| `groupmod` | Modify a group | `groupmod -n newname oldname` |
| `gpasswd` | Administer the /etc/group file | `gpasswd -a user group` |
| `su` | Switch user | `su username` |
| `sudo` | Execute a command as another user | `sudo command` |
| `sudoedit` | Edit files using sudo and the default editor | `sudoedit filename` |

## Process Management

| Command | Description | Example Usage |
|---------|-------------|---------------|
| `ps` | Report process status | `ps aux` |
| `ps -ef` | Full process listing | `ps -ef` |
| `pgrep` | Look up processes based on name | `pgrep process_name` |
| `pstree` | Display a tree of processes | `pstree` |
| `top` | Display and update sorted process information | `top` |
| `htop` | Interactive process viewer | `htop` |
| `kill` | Send a signal to a process | `kill PID` |
| `killall` | Kill processes by name | `killall process_name` |
| `pkill` | Signal processes based on name and other attributes | `pkill process_name` |
| `renice` | Alter priority of running processes | `renice +10 -p PID` |
| `bg` | Place jobs in the background | `bg` |
| `fg` | Bring jobs to the foreground | `fg` |
| `jobs` | List active jobs | `jobs` |
| `nohup` | Run a command immune to hangups | `nohup command &` |
| `nice` | Run a program with modified scheduling priority | `nice -n 10 command` |
| `time` | Time a command | `time command` |

## Networking Commands

| Command | Description | Example Usage |
|---------|-------------|---------------|
| `ping` | Send ICMP ECHO_REQUEST to network hosts | `ping hostname` |
| `traceroute` | Print the route packets trace to network host | `traceroute hostname` |
| `tracepath` | Similar to traceroute | `tracepath hostname` |
| `netstat` | Network connections, routing tables, interface statistics | `netstat -tuln` |
| `ss` | Another utility to investigate sockets | `ss -tuln` |
| `ip` | Show / manipulate routing, devices, policy routing and tunnels | `ip addr show` |
| `ifconfig` | Configure a network interface | `ifconfig eth0` |
| `iwconfig` | Configure a wireless network interface | `iwconfig wlan0` |
| `route` | Show / manipulate the IP routing table | `route -n` |
| `arp` | Manipulate the system ARP cache | `arp -a` |
| `host` | DNS lookup utility | `host domain.com` |
| `dig` | DNS lookup utility | `dig domain.com` |
| `nslookup` | Query DNS servers | `nslookup domain.com` |
| `whois` | Client for the whois directory service | `whois domain.com` |
| `wget` | Non-interactive network downloader | `wget URL` |
| `curl` | Transfer data from or to a server | `curl URL` |
| `nc` / `netcat` | TCP/IP swiss army knife | `nc -zvw3 host port` |
| `nmap` | Network exploration tool and security scanner | `nmap IP_address` |
| `iptables` | Administration tool for IPv4 packet filtering and NAT | `iptables -L` |
| `tcpdump` | Dump traffic on a network | `tcpdump -i eth0` |

## SSH and Remote Access

| Command | Description | Example Usage |
|---------|-------------|---------------|
| `ssh` | OpenSSH SSH client | `ssh user@hostname` |
| `ssh-keygen` | Authentication key generation | `ssh-keygen -t rsa` |
| `ssh-copy-id` | Install your identity key in a remote machine | `ssh-copy-id user@hostname` |
| `ssh-agent` | Authentication agent | `ssh-agent bash` |
| `ssh-add` | Add private key identities to the authentication agent | `ssh-add ~/.ssh/id_rsa` |
| `sftp` | Secure file transfer program | `sftp user@hostname` |
| `scp` | Secure copy | `scp file user@host:/path` |
| `rsync` | Fast and versatile file copying tool | `rsync -avz source/ user@host:/path` |

## File Compression

| Command | Description | Example Usage |
|---------|-------------|---------------|
| `gzip` | Compress or expand files | `gzip filename` |
| `gunzip` | Expand compressed files | `gunzip filename.gz` |
| `bzip2` | Block-sorting file compressor | `bzip2 filename` |
| `bunzip2` | Decompress files | `bunzip2 filename.bz2` |
| `xz` | Compress or decompress files | `xz filename` |
| `unxz` | Decompress files | `unxz filename.xz` |
| `tar` | Archive files | `tar -cvf archive.tar dir/` |
| `tar -xf` | Extract files from an archive | `tar -xf archive.tar` |
| `tar -czf` | Create a gzipped tar archive | `tar -czf archive.tar.gz dir/` |
| `tar -xzf` | Extract a gzipped tar archive | `tar -xzf archive.tar.gz` |
| `zip` | Package and compress files | `zip -r archive.zip dir/` |
| `unzip` | Extract files from a ZIP archive | `unzip archive.zip` |

## Input/Output Redirection

| Command | Description | Example Usage |
|---------|-------------|---------------|
| `>` | Redirect output to a file | `command > file` |
| `>>` | Append output to a file | `command >> file` |
| `<` | Redirect input from a file | `command < file` |
| `|` | Pipe output of one command to another | `command1 | command2` |
| `2>` | Redirect stderr to a file | `command 2> error_file` |
| `2>&1` | Redirect stderr to stdout | `command > file 2>&1` |
| `&>` | Redirect both stdout and stderr to a file | `command &> file` |
| `tee` | Read from stdin and write to stdout and files | `command | tee file` |
| `/dev/null` | Discard output | `command > /dev/null` |

## File Searching and Pattern Matching

| Command | Description | Example Usage |
|---------|-------------|---------------|
| `find` | Search for files in a directory hierarchy | `find /path -name "pattern"` |
| `find -type` | Find by file type | `find /path -type f` (files only) |
| `find -mtime` | Find by modification time | `find /path -mtime -7` (modified in last 7 days) |
| `find -size` | Find by file size | `find /path -size +10M` (larger than 10MB) |
| `find -exec` | Execute command on found files | `find /path -name "*.tmp" -exec rm {} \;` |
| `grep` | Print lines matching a pattern | `grep "pattern" file` |
| `grep -r` | Recursive search | `grep -r "pattern" directory` |
| `grep -i` | Case-insensitive search | `grep -i "pattern" file` |
| `grep -l` | List only filenames | `grep -l "pattern" *` |
| `grep -v` | Invert match (lines that don't match) | `grep -v "pattern" file` |
| `locate` | Find files by name | `locate filename` |
| `updatedb` | Update the database for locate | `updatedb` |
| `xargs` | Build and execute command lines from standard input | `find -name "*.txt" | xargs grep "pattern"` |

## Package Management

### Debian/Ubuntu (APT)

| Command | Description | Example Usage |
|---------|-------------|---------------|
| `apt update` | Update package lists | `sudo apt update` |
| `apt upgrade` | Upgrade installed packages | `sudo apt upgrade` |
| `apt install` | Install packages | `sudo apt install package` |
| `apt remove` | Remove packages | `sudo apt remove package` |
| `apt purge` | Remove packages and configuration files | `sudo apt purge package` |
| `apt search` | Search for packages | `apt search keyword` |
| `apt show` | Show package details | `apt show package` |
| `apt list` | List packages | `apt list --installed` |
| `apt autoremove` | Remove automatically installed dependencies | `sudo apt autoremove` |
| `dpkg -i` | Install package from a file | `sudo dpkg -i package.deb` |
| `dpkg -l` | List installed packages | `dpkg -l` |
| `dpkg -r` | Remove package | `sudo dpkg -r package` |

### Red Hat/CentOS (YUM/DNF)

| Command | Description | Example Usage |
|---------|-------------|---------------|
| `yum update` | Update installed packages | `sudo yum update` |
| `yum install` | Install packages | `sudo yum install package` |
| `yum remove` | Remove packages | `sudo yum remove package` |
| `yum search` | Search for packages | `yum search keyword` |
| `yum info` | Show package information | `yum info package` |
| `yum list` | List packages | `yum list installed` |
| `dnf` | Next-generation version of YUM | `sudo dnf command` |
| `rpm -i` | Install package from a file | `sudo rpm -i package.rpm` |
| `rpm -q` | Query installed packages | `rpm -q package` |
| `rpm -e` | Erase (remove) package | `sudo rpm -e package` |

## System Services

| Command | Description | Example Usage |
|---------|-------------|---------------|
| `systemctl` | Control the systemd system and service manager | `systemctl status service` |
| `systemctl start` | Start a service | `sudo systemctl start service` |
| `systemctl stop` | Stop a service | `sudo systemctl stop service` |
| `systemctl restart` | Restart a service | `sudo systemctl restart service` |
| `systemctl enable` | Enable a service to start at boot | `sudo systemctl enable service` |
| `systemctl disable` | Disable a service from starting at boot | `sudo systemctl disable service` |
| `systemctl list-units` | List units | `systemctl list-units --type=service` |
| `service` | Run a System V init script | `sudo service service_name action` |
| `chkconfig` | System V service configuration tool | `chkconfig service_name on` |
| `journalctl` | Query the systemd journal | `journalctl -u service` |
| `logs` | View log files | `less /var/log/syslog` |

## Disk and Storage Management

| Command | Description | Example Usage |
|---------|-------------|---------------|
| `fdisk` | Partition table manipulator | `sudo fdisk /dev/sda` |
| `parted` | Partition manipulation program | `sudo parted /dev/sda` |
| `mkfs` | Build a Linux filesystem | `sudo mkfs.ext4 /dev/sda1` |
| `mkswap` | Set up a swap area | `sudo mkswap /dev/sda2` |
| `swapon` | Enable swap devices | `sudo swapon /dev/sda2` |
| `mount` | Mount a filesystem | `sudo mount /dev/sda1 /mnt` |
| `umount` | Unmount a filesystem | `sudo umount /mnt` |
| `blkid` | Locate/print block device attributes | `sudo blkid` |
| `lsblk` | List block devices | `lsblk` |
| `df` | Report file system disk space usage | `df -h` |
| `du` | Estimate file space usage | `du -sh directory` |
| `fsck` | Check and repair a Linux filesystem | `sudo fsck /dev/sda1` |
| `e2fsck` | Check ext2/ext3/ext4 filesystem | `sudo e2fsck /dev/sda1` |
| `tune2fs` | Adjust tunable filesystem parameters | `sudo tune2fs -l /dev/sda1` |
| `badblocks` | Search a device for bad blocks | `sudo badblocks /dev/sda1` |
| `hdparm` | Get/set SATA/IDE device parameters | `sudo hdparm -i /dev/sda` |
| `smartctl` | Control and monitor S.M.A.R.T. enabled devices | `sudo smartctl -a /dev/sda` |

## Date and Time

| Command | Description | Example Usage |
|---------|-------------|---------------|
| `date` | Display or set date and time | `date` |
| `date -s` | Set the date and time | `sudo date -s "2 OCT 2023 18:00:00"` |
| `hwclock` | Query or set the hardware clock | `sudo hwclock --systohc` |
| `timedatectl` | Control the system time and date | `timedatectl status` |
| `cal` | Display a calendar | `cal` |
| `ntpdate` | Set the date and time via NTP | `sudo ntpdate pool.ntp.org` |

## Shell Scripting Basics

| Command | Description | Example Usage |
|---------|-------------|---------------|
| `#!/bin/bash` | Shebang line for bash scripts | First line of script |
| `echo` | Display a line of text | `echo "Hello World"` |
| `read` | Read a line from standard input | `read -p "Enter value: " variable` |
| `if [ condition ]` | Conditional statement | `if [ "$a" -eq "$b" ]; then echo "Equal"; fi` |
| `for loop` | Loop over a sequence | `for i in {1..5}; do echo $i; done` |
| `while loop` | Loop while condition is true | `while [ $i -le 5 ]; do echo $i; ((i++)); done` |
| `case` | Conditional branch statement | `case "$var" in pattern) commands;; esac` |
| `function` | Define a function | `function_name() { commands; }` |
| `$1, $2, ...` | Positional parameters | `echo "First arg: $1"` |
| `$#` | Number of arguments | `echo "Number of args: $#"` |
| `$@` | All arguments | `echo "All args: $@"` |
| `$?` | Exit status of the last command | `echo "Last command exit status: $?"` |
| `&&` | Logical AND | `command1 && command2` |
| `||` | Logical OR | `command1 || command2` |
| `export` | Set environment variables | `export VAR=value` |
| `source` or `.` | Execute commands from a file | `source file.sh` or `. file.sh` |
| `exit` | Exit the shell | `exit 0` |

## PKI (Public Key Infrastructure) Commands

| Command | Description | Example Usage |
|---------|-------------|---------------|
| `openssl req` | Create certificate signing requests | `openssl req -new -key key.pem -out csr.pem` |
| `openssl genrsa` | Generate RSA private key | `openssl genrsa -out key.pem 2048` |
| `openssl x509` | Certificate display and signing tool | `openssl x509 -in cert.pem -text` |
| `openssl ca` | Sign certificate requests with CA | `openssl ca -in csr.pem -out cert.pem` |
| `openssl verify` | Verify certificate validity | `openssl verify -CAfile ca.pem cert.pem` |
| `openssl s_client` | SSL/TLS client | `openssl s_client -connect host:port` |
| `openssl s_server` | SSL/TLS server | `openssl s_server -key key.pem -cert cert.pem` |
| `keytool` | Java certificate management | `keytool -list -keystore keystore.jks` |
| `certutil` | NSS certificate management | `certutil -d /path/to/db -L` |

## Other Useful Commands

| Command | Description | Example Usage |
|---------|-------------|---------------|
| `alias` | Create command aliases | `alias ll='ls -la'` |
| `history` | Command history | `history` |
| `crontab` | Schedule periodic jobs | `crontab -e` |
| `at` | Execute commands at a specified time | `at now + 1 hour` |
| `watch` | Execute a program periodically | `watch -n 1 command` |
| `screen` | Terminal multiplexer | `screen` |
| `tmux` | Terminal multiplexer | `tmux` |
| `wget` | Download files from the web | `wget URL` |
| `curl` | Transfer data from or to a server | `curl URL` |
| `rsync` | Remote file synchronization | `rsync -avz source/ destination/` |
| `tee` | Redirect output to multiple files | `command | tee file1 file2` |
| `bc` | Calculator | `echo "5 + 5" | bc` |
| `expr` | Evaluate expressions | `expr 5 + 5` |
| `xargs` | Build and execute command lines | `echo "file1 file2" | xargs rm` |
| `md5sum` | Compute MD5 message digest | `md5sum file` |
| `sha256sum` | Compute SHA256 message digest | `sha256sum file` |
| `basename` | Strip directory and suffix from filenames | `basename /path/to/file.txt` |
| `dirname` | Strip last component from file name | `dirname /path/to/file.txt` |
| `seq` | Print sequences of numbers | `seq 1 10` |
| `sleep` | Delay for a specified amount of time | `sleep 10` |
| `yes` | Output a string repeatedly | `yes "y" | command_requiring_confirmation` |
| `shuf` | Generate random permutations | `shuf -i 1-10 -n 5` |
| `strace` | Trace system calls and signals | `strace command` |
| `ltrace` | Library call tracer | `ltrace command` |
| `logger` | Log messages to system log | `logger "Message"` |
| `nohup` | Run a command immune to hangups | `nohup command &` |
| `timeout` | Run a command with a time limit | `timeout 10s command` |
| `wait` | Wait for process to complete | `wait PID` |
| `chroot` | Run command or shell with special root directory | `sudo chroot /path command` |
| `lsof` | List open files | `lsof -p PID` |
| `pidof` | Find process ID of a running program | `pidof program_name` |
| `pmap` | Display memory map of a process | `pmap PID` |
| `vmstat` | Report virtual memory statistics | `vmstat 1` |
| `fuser` | Identify processes using files or sockets | `fuser -m /path` |
| `ionice` | Set I/O scheduling class and priority | `ionice -c 2 -n 0 command` |
| `iotop` | Simple top-like I/O monitor | `iotop` |
