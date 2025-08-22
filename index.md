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
- [Advanced Troubleshooting](#advanced-troubleshooting)
- [Performance Monitoring](#performance-monitoring)
- [Manual Pages & Help Commands](#manual-pages-and-help-commands)
- [Configuration Management and Deployment](#configuration-management-and-deployment)
- [OpenShift Container Platform](#openshift-container-platform)

## File System Navigation

| Command           | Description                                  | Example Usage                 |
| ----------------- | -------------------------------------------- | ----------------------------- |
| `pwd`             | Print working directory                      | `pwd`                         |
| `cd`              | Change directory                             | `cd /path/to/directory`       |
| `cd ~`            | Change to home directory                     | `cd ~`                        |
| `cd ..`           | Move up one directory level                  | `cd ..`                       |
| `cd -`            | Return to previous directory                 | `cd -`                        |
| `ls`              | List directory contents                      | `ls`                          |
| `ls -l`           | List with detailed format                    | `ls -l`                       |
| `ls -a`           | List all files (including hidden)            | `ls -a`                       |
| `ls -la`          | Combine list all and long format             | `ls -la`                      |
| `ls -lh`          | Show file sizes in human-readable format     | `ls -lh`                      |
| `ls -lS`          | Sort by file size (largest first)            | `ls -lS`                      |
| `ls -lt`          | Sort by modification time (newest first)     | `ls -lt`                      |
| `ls -ltr`         | Sort by modification time (oldest first)     | `ls -ltr`                     |
| `ls --color=auto` | Show files with color coding                 | `ls --color=auto`             |
| `ls -F`           | Append indicators to entries (\*/=>@\|)      | `ls -F`                       |
| `ls -R`           | List subdirectories recursively              | `ls -R`                       |
| `find`            | Search for files and directories             | `find /path -name "filename"` |
| `whereis`         | Locate binary, source, and manual page files | `whereis command`             |
| `which`           | Find executables in PATH                     | `which command`               |
| `pushd dir`       | Change directory and save previous location  | `pushd /var/log`              |
| `popd`            | Return to previous directory from pushd      | `popd`                        |
| `dirs`            | Display directory stack                      | `dirs -v`                     |

## File Operations

| Command                | Description                                        | Example Usage                                        |
| ---------------------- | -------------------------------------------------- | ---------------------------------------------------- |
| `cat`                  | Display file contents                              | `cat filename`                                       |
| `cat -n`               | Display file with line numbers                     | `cat -n filename`                                    |
| `tac`                  | Display file contents in reverse                   | `tac filename`                                       |
| `cp`                   | Copy files or directories                          | `cp source destination`                              |
| `cp -i`                | Copy with confirmation before overwrite            | `cp -i file1 file2`                                  |
| `cp -p`                | Preserve file attributes (permissions, timestamps) | `cp -p source dest`                                  |
| `cp -r`                | Copy directories recursively                       | `cp -r source_dir destination_dir`                   |
| `cp -a`                | Archive mode (preserve all attributes and links)   | `cp -a source_dir dest_dir`                          |
| `cp -u`                | Copy only when source is newer                     | `cp -u source dest`                                  |
| `mv`                   | Move/rename files or directories                   | `mv oldname newname`                                 |
| `mv -i`                | Move with confirmation before overwrite            | `mv -i file1 file2`                                  |
| `mv -u`                | Move only when source is newer                     | `mv -u source dest`                                  |
| `mv -v`                | Verbose mode showing what is being moved           | `mv -v file1 file2`                                  |
| `rm`                   | Remove files                                       | `rm filename`                                        |
| `rm -f`                | Force remove files without confirmation            | `rm -f filename`                                     |
| `rm -i`                | Interactive mode with confirmation                 | `rm -i filename`                                     |
| `rm -r`                | Remove directories and their contents recursively  | `rm -r directory`                                    |
| `rm -rf`               | Force recursive directory removal                  | `rm -rf directory`                                   |
| `touch`                | Create empty file or update timestamp              | `touch filename`                                     |
| `touch -a`             | Change only access time                            | `touch -a filename`                                  |
| `touch -m`             | Change only modification time                      | `touch -m filename`                                  |
| `touch -t`             | Set specific time stamp                            | `touch -t 202305061200.00 file`                      |
| `file`                 | Determine file type                                | `file filename`                                      |
| `file -b`              | Brief mode (no filename output)                    | `file -b filename`                                   |
| `file -i`              | Output MIME type of file                           | `file -i filename`                                   |
| `stat`                 | Display file or file system status                 | `stat filename`                                      |
| `stat -c`              | Custom format for stat output                      | `stat -c "%a %U:%G %n" file`                         |
| `ln`                   | Create hard links                                  | `ln target linkname`                                 |
| `ln -s`                | Create symbolic (soft) links                       | `ln -s target linkname`                              |
| `ln -sf`               | Force creation of symbolic link                    | `ln -sf target linkname`                             |
| `readlink`             | Print resolved symbolic links                      | `readlink linkname`                                  |
| `readlink -f`          | Follow all symlinks to final target                | `readlink -f linkname`                               |
| `dd`                   | Convert and copy a file                            | `dd if=input of=output bs=1M`                        |
| `dd status=progress`   | Show progress of dd operation                      | `dd if=/dev/sda of=/dev/sdb bs=4M status=progress`   |
| `dd conv=sync,noerror` | Continue dd after errors                           | `dd if=/dev/sda of=disk.img bs=4M conv=sync,noerror` |
| `scp`                  | Secure copy (remote file copy)                     | `scp file user@host:/path`                           |
| `scp -r`               | Recursive secure copy                              | `scp -r dir user@host:/path`                         |
| `rsync -av`            | Synchronize files preserving attributes            | `rsync -av src/ dest/`                               |
| `mmv`                  | Mass move/rename files                             | `mmv '*.txt' '#1.bak'`                               |

## Directory Operations

| Command                  | Description                                        | Example Usage                 |
| ------------------------ | -------------------------------------------------- | ----------------------------- |
| `mkdir`                  | Create directory                                   | `mkdir dirname`               |
| `mkdir -p`               | Create parent directories as needed                | `mkdir -p /path/to/directory` |
| `mkdir -m`               | Set directory permissions                          | `mkdir -m 755 dirname`        |
| `mkdir -v`               | Verbose output                                     | `mkdir -v dirname`            |
| `rmdir`                  | Remove empty directories                           | `rmdir dirname`               |
| `rmdir -p`               | Remove parent directories as well                  | `rmdir -p dir1/dir2/dir3`     |
| `du`                     | Estimate file space usage                          | `du -h filename`              |
| `du -sh`                 | Summarize disk usage of directory                  | `du -sh directory`            |
| `du -sh *`               | Show disk usage of all items in current dir        | `du -sh *`                    |
| `du -h --max-depth=1`    | Show disk usage one level down                     | `du -h --max-depth=1 /var`    |
| `du -h --threshold=100M` | List only items over 100MB                         | `du -h --threshold=100M /var` |
| `tree`                   | List contents of directories in a tree-like format | `tree /path`                  |
| `tree -L 2`              | Limit tree display to 2 levels                     | `tree -L 2 /path`             |
| `tree -d`                | Show directories only                              | `tree -d /path`               |
| `tree -p`                | Show permissions                                   | `tree -p /path`               |
| `tree -s`                | Show file sizes                                    | `tree -s /path`               |
| `tree -h`                | Show file sizes in human-readable format           | `tree -h /path`               |
| `ncdu`                   | Interactive disk usage analyzer                    | `ncdu /var`                   |

## File Permissions

| Command                         | Description                                    | Example Usage                            |
| ------------------------------- | ---------------------------------------------- | ---------------------------------------- |
| `chmod`                         | Change file mode bits (permissions)            | `chmod 755 filename`                     |
| `chmod +x`                      | Make file executable                           | `chmod +x filename`                      |
| `chmod -R`                      | Change permissions recursively                 | `chmod -R 755 directory`                 |
| `chmod u+w`                     | Add write permission for user                  | `chmod u+w filename`                     |
| `chmod g-w`                     | Remove write permission from group             | `chmod g-w filename`                     |
| `chmod o=r`                     | Set other permissions to read-only             | `chmod o=r filename`                     |
| `chmod a+x`                     | Add execute permission for all                 | `chmod a+x filename`                     |
| `chmod --reference=file1 file2` | Apply same permissions as file1 to file2       | `chmod --reference=ref_file target_file` |
| `chown`                         | Change file owner and group                    | `chown user:group filename`              |
| `chown -h`                      | Change ownership of symlinks                   | `chown -h user:group symlink`            |
| `chown -R`                      | Change ownership recursively                   | `chown -R user:group directory`          |
| `chown :group`                  | Change group ownership only                    | `chown :group filename`                  |
| `chgrp`                         | Change group ownership                         | `chgrp group filename`                   |
| `chgrp -R`                      | Change group recursively                       | `chgrp -R group directory`               |
| `umask`                         | Set default permissions for new files          | `umask 022`                              |
| `getfacl`                       | Display file ACLs                              | `getfacl filename`                       |
| `setfacl`                       | Set file ACLs                                  | `setfacl -m u:user:rw file`              |
| `setfacl -R`                    | Set ACLs recursively                           | `setfacl -R -m g:group:rx directory`     |
| `lsattr`                        | List file attributes on Linux ext filesystem   | `lsattr filename`                        |
| `chattr`                        | Change file attributes on Linux ext filesystem | `chattr +i filename` (make immutable)    |

## Text Viewing and Editing

| Command                           | Description                                       | Example Usage                                       |
| --------------------------------- | ------------------------------------------------- | --------------------------------------------------- | -------------------------------- |
| `vi` / `vim`                      | Text editor                                       | `vi filename`                                       |
| `vim -d file1 file2`              | Compare files in vim                              | `vim -d file1 file2`                                |
| `vim +10 file`                    | Open file at line 10                              | `vim +10 /etc/fstab`                                |
| `vim +/pattern file`              | Open file at first matching pattern               | `vim +/root /etc/passwd`                            |
| `vim -R file`                     | Open file in read-only mode                       | `vim -R /etc/passwd`                                |
| `nano`                            | Simple text editor                                | `nano filename`                                     |
| `nano -m`                         | Enable mouse support                              | `nano -m filename`                                  |
| `nano -l`                         | Show line numbers                                 | `nano -l filename`                                  |
| `nano +10`                        | Open file at line 10                              | `nano +10 filename`                                 |
| `emacs`                           | Advanced text editor                              | `emacs filename`                                    |
| `less`                            | View text files with pagination                   | `less filename`                                     |
| `less +F`                         | Follow file additions (like tail -f)              | `less +F /var/log/syslog`                           |
| `less +G`                         | Start at end of file                              | `less +G filename`                                  |
| `less -N`                         | Show line numbers                                 | `less -N filename`                                  |
| `less -p pattern`                 | Start at first pattern match                      | `less -p "error" filename`                          |
| `less -S`                         | Chop long lines (don't wrap)                      | `less -S filename`                                  |
| `more`                            | View text files with pagination                   | `more filename`                                     |
| `head`                            | Output the first part of files                    | `head filename`                                     |
| `head -n 20`                      | Show first 20 lines                               | `head -n 20 filename`                               |
| `head -c 1K`                      | Show first 1KB of file                            | `head -c 1K filename`                               |
| `tail`                            | Output the last part of files                     | `tail filename`                                     |
| `tail -n 50`                      | Show last 50 lines                                | `tail -n 50 filename`                               |
| `tail -f`                         | Follow log file additions                         | `tail -f /var/log/syslog`                           |
| `tail -f --pid=PID`               | Follow until PID dies                             | `tail -f --pid=1234 logfile`                        |
| `tail -F`                         | Follow file, even if renamed                      | `tail -F logfile`                                   |
| `grep`                            | Search for patterns in files                      | `grep "pattern" filename`                           |
| `grep -i`                         | Case-insensitive search                           | `grep -i "pattern" filename`                        |
| `grep -r`                         | Recursive search in directories                   | `grep -r "pattern" directory`                       |
| `grep -v`                         | Invert match (non-matching lines)                 | `grep -v "pattern" filename`                        |
| `grep -w`                         | Match whole words only                            | `grep -w "word" filename`                           |
| `grep -A 2`                       | Show 2 lines after match                          | `grep -A 2 "pattern" filename`                      |
| `grep -B 2`                       | Show 2 lines before match                         | `grep -B 2 "pattern" filename`                      |
| `grep -C 2`                       | Show 2 lines before and after match               | `grep -C 2 "pattern" filename`                      |
| `grep -n`                         | Show line numbers                                 | `grep -n "pattern" filename`                        |
| `grep -l`                         | Only show filenames with matches                  | `grep -l "pattern" *`                               |
| `grep -c`                         | Count matching lines                              | `grep -c "pattern" filename`                        |
| `grep -o`                         | Show only matching part                           | `grep -o "pattern" filename`                        |
| `grep --color=auto`               | Highlight matching text                           | `grep --color=auto "pattern" filename`              |
| `grep -P`                         | Perl-compatible regular expressions               | `grep -P "\d{3}-\d{2}-\d{4}" filename`              |
| `grep -E`                         | Extended regular expressions                      | `grep -E "pattern1                                  | pattern2" filename`              |
| `zgrep`                           | Grep compressed files                             | `zgrep "pattern" file.gz`                           |
| `sed`                             | Stream editor for filtering and transforming text | `sed 's/old/new/g' filename`                        |
| `sed -i`                          | Edit files in place                               | `sed -i 's/old/new/g' filename`                     |
| `sed -i.bak`                      | Edit files in place with backup                   | `sed -i.bak 's/old/new/g' filename`                 |
| `sed -n`                          | Suppress automatic printing                       | `sed -n '10,20p' filename` (print only lines 10-20) |
| `sed '/pattern/d'`                | Delete lines matching pattern                     | `sed '/^#/d' filename` (delete comments)            |
| `sed '1d'`                        | Delete first line                                 | `sed '1d' filename`                                 |
| `sed -n '/pattern/p'`             | Print only lines matching pattern                 | `sed -n '/error/p' filename`                        |
| `awk`                             | Pattern scanning and processing language          | `awk '{print $1}' filename`                         |
| `awk -F:`                         | Set field separator                               | `awk -F: '{print $1}' /etc/passwd`                  |
| `awk '{sum+=$1} END {print sum}'` | Sum first column                                  | `cat numbers.txt                                    | awk '{sum+=$1} END {print sum}'` |
| `awk 'NR % 2'`                    | Print odd numbered lines                          | `awk 'NR % 2' filename`                             |
| `awk '!seen[$0]++'`               | Remove duplicate lines (like uniq)                | `awk '!seen[$0]++' filename`                        |
| `awk 'length > 80'`               | Print lines longer than 80 chars                  | `awk 'length > 80' filename`                        |
| `sort`                            | Sort lines of text files                          | `sort filename`                                     |
| `sort -n`                         | Sort numerically                                  | `sort -n filename`                                  |
| `sort -r`                         | Sort in reverse order                             | `sort -r filename`                                  |
| `sort -k 2`                       | Sort by second field                              | `sort -k 2 filename`                                |
| `sort -k 2,2 -k 3,3`              | Sort by multiple fields                           | `sort -k 2,2 -k 3,3 filename`                       |
| `sort -u`                         | Sort and remove duplicates                        | `sort -u filename`                                  |
| `sort -h`                         | Sort human-readable sizes (1K, 2M, etc.)          | `ls -lh                                             | sort -k 5 -h`                    |
| `sort -V`                         | Sort version numbers                              | `sort -V version_list.txt`                          |
| `uniq`                            | Report or omit repeated lines                     | `uniq filename`                                     |
| `uniq -c`                         | Count occurrences                                 | `sort filename                                      | uniq -c`                         |
| `uniq -d`                         | Only print duplicate lines                        | `sort filename                                      | uniq -d`                         |
| `uniq -u`                         | Only print unique lines                           | `sort filename                                      | uniq -u`                         |
| `wc`                              | Count lines, words, and characters                | `wc filename`                                       |
| `wc -l`                           | Count lines only                                  | `wc -l filename`                                    |
| `wc -w`                           | Count words only                                  | `wc -w filename`                                    |
| `wc -c`                           | Count bytes only                                  | `wc -c filename`                                    |
| `wc -m`                           | Count characters only                             | `wc -m filename`                                    |
| `diff`                            | Compare files line by line                        | `diff file1 file2`                                  |
| `diff -y`                         | Side-by-side comparison                           | `diff -y file1 file2`                               |
| `diff -w`                         | Ignore whitespace                                 | `diff -w file1 file2`                               |
| `diff -b`                         | Ignore changes in amount of whitespace            | `diff -b file1 file2`                               |
| `diff -B`                         | Ignore blank lines                                | `diff -B file1 file2`                               |
| `diff -u`                         | Output differences in unified format              | `diff -u file1 file2`                               |
| `diff -r`                         | Recursively compare directories                   | `diff -r dir1 dir2`                                 |
| `diff -q`                         | Brief mode (only report if files differ)          | `diff -q file1 file2`                               |
| `vimdiff`                         | Open files in vim with differences highlighted    | `vimdiff file1 file2`                               |
| `colordiff`                       | Colorized diff output                             | `colordiff file1 file2`                             |
| `patch`                           | Apply a diff file to an original                  | `patch file < patch_file`                           |
| `patch -p1`                       | Strip one level of path when patching             | `patch -p1 < patch_file`                            |
| `cut -d: -f1`                     | Cut by delimiter, get first field                 | `cut -d: -f1 /etc/passwd`                           |
| `cut -c1-10`                      | Cut by character position                         | `cut -c1-10 filename`                               |
| `fmt`                             | Simple text formatter                             | `fmt -w 80 filename`                                |
| `fold -w 80`                      | Wrap lines to specified width                     | `fold -w 80 filename`                               |
| `nl`                              | Number lines of files                             | `nl filename`                                       |
| `expand`                          | Convert tabs to spaces                            | `expand filename`                                   |
| `unexpand`                        | Convert spaces to tabs                            | `unexpand filename`                                 |
| `tee`                             | Read from stdin and write to stdout and files     | `command                                            | tee filename`                    |
| `column -t`                       | Format output in columns                          | `cat /etc/passwd                                    | column -t -s:`                   |
| `pr`                              | Format file for printing                          | `pr -h "Header" filename`                           |
| `join`                            | Join lines of two files on a common field         | `join file1 file2`                                  |
| `paste`                           | Merge lines of files                              | `paste file1 file2`                                 |
| `split`                           | Split a file into pieces                          | `split -b 1M largefile prefix`                      |
| `csplit`                          | Split a file into context-determined pieces       | `csplit file '/^SECTION/' {*}`                      |
| `tr`                              | Translate or delete characters                    | `tr 'A-Z' 'a-z' < input` (lowercase)                |
| `tr -d`                           | Delete characters                                 | `tr -d '\r' < file` (remove carriage returns)       |
| `hexdump -C`                      | Display file in hex and ASCII                     | `hexdump -C filename`                               |
| `xxd`                             | Create a hex dump or convert back                 | `xxd filename`                                      |
| `strings`                         | Print printable characters in files               | `strings binary_file`                               |

## System Information

| Command                                | Description                                    | Example Usage                          |
| -------------------------------------- | ---------------------------------------------- | -------------------------------------- | ------ | ------------ |
| `uname`                                | Print system information                       | `uname -a`                             |
| `uname -r`                             | Print kernel release                           | `uname -r`                             |
| `uname -m`                             | Print machine hardware name                    | `uname -m`                             |
| `hostname`                             | Show or set system hostname                    | `hostname`                             |
| `hostname -f`                          | Show fully qualified domain name               | `hostname -f`                          |
| `hostname -I`                          | Show all IP addresses                          | `hostname -I`                          |
| `whoami`                               | Print effective user ID                        | `whoami`                               |
| `id`                                   | Print user and group information               | `id`                                   |
| `id user`                              | Print info for specific user                   | `id username`                          |
| `w`                                    | Show who is logged on and what they are doing  | `w`                                    |
| `w -f`                                 | Toggle from/to field                           | `w -f`                                 |
| `w -i`                                 | Show IP addresses instead of hostnames         | `w -i`                                 |
| `who`                                  | Show who is logged on                          | `who`                                  |
| `who -a`                               | Show all information                           | `who -a`                               |
| `who -b`                               | Show time of last system boot                  | `who -b`                               |
| `last`                                 | Show a listing of last logged in users         | `last`                                 |
| `last -n 20`                           | Limit to 20 entries                            | `last -n 20`                           |
| `last reboot`                          | Show system reboot history                     | `last reboot`                          |
| `lastlog`                              | Show the most recent login of all users        | `lastlog`                              |
| `lastlog -u user`                      | Show last login of specific user               | `lastlog -u root`                      |
| `uptime`                               | Tell how long the system has been running      | `uptime`                               |
| `free`                                 | Display amount of free and used memory         | `free -h`                              |
| `free -m`                              | Show memory usage in MB                        | `free -m`                              |
| `free -g`                              | Show memory usage in GB                        | `free -g`                              |
| `free -s 5`                            | Update every 5 seconds                         | `free -s 5`                            |
| `df`                                   | Report file system disk space usage            | `df -h`                                |
| `df -H`                                | Use powers of 1000 not 1024                    | `df -H`                                |
| `df -T`                                | Show filesystem type                           | `df -T`                                |
| `df -i`                                | Show inode information                         | `df -i`                                |
| `dmesg`                                | Print or control the kernel ring buffer        | `dmesg`                                |
| `dmesg -T`                             | Show human-readable timestamps                 | `dmesg -T`                             |
| `dmesg -l err,warn`                    | Show only error and warning messages           | `dmesg -l err,warn`                    |
| `dmesg                                 | grep -i usb`                                   | Filter for USB messages                | `dmesg | grep -i usb` |
| `lsblk`                                | List block devices                             | `lsblk`                                |
| `lsblk -f`                             | Show filesystem info                           | `lsblk -f`                             |
| `lsblk -o name,size,fstype,mountpoint` | Customize output                               | `lsblk -o name,size,fstype,mountpoint` |
| `lsusb`                                | List USB devices                               | `lsusb`                                |
| `lsusb -v`                             | Verbose listing                                | `lsusb -v`                             |
| `lsusb -t`                             | Display device hierarchy as a tree             | `lsusb -t`                             |
| `lspci`                                | List PCI devices                               | `lspci`                                |
| `lspci -v`                             | Verbose listing                                | `lspci -v`                             |
| `lspci -k`                             | Show kernel drivers handling each device       | `lspci -k`                             |
| `lspci -nn`                            | Show PCI vendor and device IDs                 | `lspci -nn`                            |
| `lsmod`                                | Show the status of modules in the Linux kernel | `lsmod`                                |
| `lshw`                                 | List hardware                                  | `lshw`                                 |
| `lshw -short`                          | Brief listing                                  | `lshw -short`                          |
| `lshw -C network`                      | Show only network hardware                     | `lshw -C network`                      |
| `lshw -html > hw.html`                 | Output in HTML format                          | `lshw -html > hw.html`                 |
| `lscpu`                                | Display CPU information                        | `lscpu`                                |
| `lsmem`                                | List memory ranges                             | `lsmem`                                |
| `vmstat`                               | Report virtual memory statistics               | `vmstat`                               |
| `vmstat 1`                             | Update every second                            | `vmstat 1`                             |
| `vmstat -s`                            | Display memory statistics                      | `vmstat -s`                            |
| `vmstat -d`                            | Display disk statistics                        | `vmstat -d`                            |
| `sysctl -a`                            | Configure kernel parameters at runtime         | `sysctl -a`                            |
| `sysctl -w param=value`                | Set kernel parameter                           | `sysctl -w vm.swappiness=10`           |
| `sysctl net.ipv4.ip_forward`           | Check specific setting                         | `sysctl net.ipv4.ip_forward`           |
| `cat /proc/cpuinfo`                    | CPU information                                | `cat /proc/cpuinfo`                    |
| `cat /proc/meminfo`                    | Memory information                             | `cat /proc/meminfo`                    |
| `cat /proc/version`                    | Kernel version                                 | `cat /proc/version`                    |
| `cat /proc/mounts`                     | Mounted filesystems                            | `cat /proc/mounts`                     |
| `cat /proc/loadavg`                    | System load                                    | `cat /proc/loadavg`                    |
| `cat /etc/*-release`                   | Distribution release info                      | `cat /etc/*-release`                   |
| `hwinfo`                               | Hardware information                           | `hwinfo --short`                       |
| `inxi -F`                              | System information script                      | `inxi -F`                              |
| `dmidecode`                            | DMI table decoder                              | `dmidecode`                            |
| `dmidecode -t memory`                  | Show memory info                               | `dmidecode -t memory`                  |
| `dmidecode -t system`                  | Show system info                               | `dmidecode -t system`                  |
| `dmidecode -t bios`                    | Show BIOS info                                 | `dmidecode -t bios`                    |

## User and Group Management

| Command                    | Description                                  | Example Usage                          |
| -------------------------- | -------------------------------------------- | -------------------------------------- |
| `useradd`                  | Create a new user                            | `useradd username`                     |
| `useradd -m`               | Create home directory                        | `useradd -m username`                  |
| `useradd -G group1,group2` | Add to multiple groups                       | `useradd -G wheel,developers username` |
| `useradd -s /bin/bash`     | Specify login shell                          | `useradd -s /bin/bash username`        |
| `userdel`                  | Delete a user account                        | `userdel username`                     |
| `userdel -r`               | Delete user account with home directory      | `userdel -r username`                  |
| `usermod`                  | Modify a user account                        | `usermod -aG groupname username`       |
| `usermod -L`               | Lock a user account                          | `usermod -L username`                  |
| `usermod -U`               | Unlock a user account                        | `usermod -U username`                  |
| `usermod -s`               | Change user shell                            | `usermod -s /bin/bash username`        |
| `usermod -d`               | Change user home directory                   | `usermod -d /newhome username`         |
| `passwd`                   | Change user password                         | `passwd username`                      |
| `passwd -l`                | Lock user password                           | `passwd -l username`                   |
| `passwd -u`                | Unlock user password                         | `passwd -u username`                   |
| `passwd -e`                | Force password change on next login          | `passwd -e username`                   |
| `passwd -S`                | Show password status                         | `passwd -S username`                   |
| `chfn`                     | Change user information                      | `chfn -f "Full Name" username`         |
| `chsh`                     | Change login shell                           | `chsh -s /bin/bash username`           |
| `groupadd`                 | Create a new group                           | `groupadd groupname`                   |
| `groupadd -g 1000`         | Specify GID                                  | `groupadd -g 1000 groupname`           |
| `groupdel`                 | Delete a group                               | `groupdel groupname`                   |
| `groupmod`                 | Modify a group                               | `groupmod -n newname oldname`          |
| `groupmod -g`              | Change GID                                   | `groupmod -g 1001 groupname`           |
| `gpasswd`                  | Administer the /etc/group file               | `gpasswd -a user group`                |
| `gpasswd -d`               | Remove user from group                       | `gpasswd -d user group`                |
| `gpasswd -A`               | Set group administrators                     | `gpasswd -A user1,user2 group`         |
| `su`                       | Switch user                                  | `su username`                          |
| `su -`                     | Switch user with login environment           | `su - username`                        |
| `su -c 'command'`          | Run command as different user                | `su -c 'ls -la /root' root`            |
| `sudo`                     | Execute a command as another user            | `sudo command`                         |
| `sudo -u user`             | Run command as specific user                 | `sudo -u postgres psql`                |
| `sudo -i`                  | Get interactive shell as root                | `sudo -i`                              |
| `sudo -l`                  | List allowed commands                        | `sudo -l`                              |
| `sudo -k`                  | Invalidate cached credentials                | `sudo -k`                              |
| `sudoedit`                 | Edit files using sudo and the default editor | `sudoedit filename`                    |
| `newgrp`                   | Change primary group ID                      | `newgrp groupname`                     |
| `chage`                    | Change user password expiry information      | `chage -l username`                    |
| `chage -M`                 | Set maximum password age                     | `chage -M 90 username`                 |
| `chage -E`                 | Set account expiration date                  | `chage -E 2023-12-31 username`         |
| `chage -d 0`               | Force password change at next login          | `chage -d 0 username`                  |
| `vipw`                     | Edit the password file                       | `vipw`                                 |
| `vigr`                     | Edit the group file                          | `vigr`                                 |
| `pwck`                     | Verify integrity of password files           | `pwck`                                 |
| `grpck`                    | Verify integrity of group files              | `grpck`                                |
| `getent passwd`            | Get entries from administrative databases    | `getent passwd username`               |
| `getent group`             | Get group entries                            | `getent group groupname`               |
| `pwgen`                    | Password generator                           | `pwgen 12 1`                           |

## Process Management

| Command                                      | Description                                         | Example Usage                                |
| -------------------------------------------- | --------------------------------------------------- | -------------------------------------------- | -------------- | ----------- |
| `ps`                                         | Report process status                               | `ps aux`                                     |
| `ps aux                                      | grep process_name`                                  | Find specific process                        | `ps aux        | grep nginx` |
| `ps -ef`                                     | Full process listing                                | `ps -ef`                                     |
| `ps -efH`                                    | Show process hierarchy                              | `ps -efH`                                    |
| `ps -eo pid,ppid,cmd,%mem,%cpu --sort=-%mem` | Custom format sorting by memory                     | `ps -eo pid,ppid,cmd,%mem,%cpu --sort=-%mem` |
| `ps -eo pid,user,cmd --forest`               | Display process tree                                | `ps -eo pid,user,cmd --forest`               |
| `ps -U username`                             | Show processes for specific user                    | `ps -U username`                             |
| `ps -p PID -o etime=`                        | Show elapsed time for process                       | `ps -p 1234 -o etime=`                       |
| `ps axjf`                                    | Display process tree in BSD format                  | `ps axjf`                                    |
| `ps -ww`                                     | Wide output (don't truncate)                        | `ps aux -ww`                                 |
| `pgrep`                                      | Look up processes based on name                     | `pgrep process_name`                         |
| `pgrep -u user`                              | Find processes by user                              | `pgrep -u root`                              |
| `pgrep -l`                                   | List process name and PID                           | `pgrep -l sshd`                              |
| `pgrep -a`                                   | List command line with process                      | `pgrep -a nginx`                             |
| `pgrep -f`                                   | Match against full command line                     | `pgrep -f "php-fpm: pool"`                   |
| `pgrep -x`                                   | Match exactly with process name                     | `pgrep -x bash`                              |
| `pstree`                                     | Display a tree of processes                         | `pstree`                                     |
| `pstree -p`                                  | Show PIDs                                           | `pstree -p`                                  |
| `pstree -u`                                  | Show user names                                     | `pstree -u`                                  |
| `pstree -a`                                  | Show command line arguments                         | `pstree -a`                                  |
| `pstree user`                                | Show process tree for specific user                 | `pstree root`                                |
| `top`                                        | Display and update sorted process information       | `top`                                        |
| `top -u user`                                | Monitor specific user's processes                   | `top -u mysql`                               |
| `top -p PID1,PID2`                           | Monitor specific processes                          | `top -p 1234,5678`                           |
| `top -b -n 1`                                | Run in batch mode (for scripting)                   | `top -b -n 1                                 | head -20`      |
| `top -o %MEM`                                | Sort by memory usage                                | `top -o %MEM`                                |
| `top -o %CPU`                                | Sort by CPU usage                                   | `top -o %CPU`                                |
| `top -d 0.5`                                 | Update every 0.5 seconds                            | `top -d 0.5`                                 |
| `top -c`                                     | Show command line arguments                         | `top -c`                                     |
| `htop`                                       | Interactive process viewer                          | `htop`                                       |
| `htop -u user`                               | Show only user's processes                          | `htop -u oracle`                             |
| `htop -p PID1,PID2`                          | Show only specified processes                       | `htop -p 1234,5678`                          |
| `htop -s COLUMN`                             | Sort by column (CPU, MEM, etc.)                     | `htop -s MEM`                                |
| `htop --tree`                                | Show processes in tree view                         | `htop --tree`                                |
| `kill`                                       | Send a signal to a process                          | `kill PID`                                   |
| `kill -9`                                    | Force kill (SIGKILL)                                | `kill -9 PID`                                |
| `kill -15`                                   | Graceful terminate (SIGTERM)                        | `kill -15 PID`                               |
| `kill -l`                                    | List available signals                              | `kill -l`                                    |
| `kill -0 PID`                                | Check if process exists                             | `kill -0 PID && echo "Running"`              |
| `killall`                                    | Kill processes by name                              | `killall process_name`                       |
| `killall -i`                                 | Interactive mode with confirmation                  | `killall -i firefox`                         |
| `killall -u user`                            | Kill all user's processes                           | `killall -u username`                        |
| `killall -v`                                 | Verbose output                                      | `killall -v process`                         |
| `killall -w`                                 | Wait for processes to die                           | `killall -w process`                         |
| `pkill`                                      | Signal processes based on name and other attributes | `pkill process_name`                         |
| `pkill -f`                                   | Match against full command line                     | `pkill -f "java -jar app.jar"`               |
| `pkill -9`                                   | Force kill processes                                | `pkill -9 firefox`                           |
| `pkill -e`                                   | Display what's being killed                         | `pkill -e process`                           |
| `pkill -u user`                              | Kill processes by user                              | `pkill -u mysql`                             |
| `pkill -P PPID`                              | Kill child processes of parent                      | `pkill -P 1234`                              |
| `renice`                                     | Alter priority of running processes                 | `renice +10 -p PID`                          |
| `renice -n -5 -u user`                       | Renice all user processes                           | `renice -n -5 -u oracle`                     |
| `nice`                                       | Run a program with modified scheduling priority     | `nice -n 10 command`                         |
| `bg`                                         | Place jobs in the background                        | `bg`                                         |
| `bg %job_id`                                 | Place specific job in background                    | `bg %2`                                      |
| `fg`                                         | Bring jobs to the foreground                        | `fg`                                         |
| `fg %job_id`                                 | Bring specific job to foreground                    | `fg %2`                                      |
| `jobs`                                       | List active jobs                                    | `jobs`                                       |
| `jobs -l`                                    | List jobs with PID                                  | `jobs -l`                                    |
| `jobs -p`                                    | List only PIDs                                      | `jobs -p`                                    |
| `nohup`                                      | Run a command immune to hangups                     | `nohup command &`                            |
| `nohup command > out.log 2>&1 &`             | Run in background with logging                      | `nohup ./script.sh > script.log 2>&1 &`      |
| `time`                                       | Time a command                                      | `time command`                               |
| `time -v`                                    | Verbose timing statistics                           | `time -v command`                            |
| `timeout`                                    | Run a command with a time limit                     | `timeout 10s command`                        |
| `timeout --kill-after=5s 10s command`        | Send KILL if TERM doesn't work                      | `timeout --kill-after=5s 10s command`        |
| `watch`                                      | Execute a program periodically                      | `watch -n 1 'ps aux                          | grep nginx'`   |
| `watch -d`                                   | Highlight differences between runs                  | `watch -d free -m`                           |
| `tload`                                      | Text mode load average monitor                      | `tload`                                      |
| `ltrace`                                     | Library call tracer                                 | `ltrace -p PID`                              |
| `strace`                                     | Trace system calls and signals                      | `strace command`                             |
| `strace -p PID`                              | Attach to running process                           | `strace -p 1234`                             |
| `strace -e open`                             | Trace specific system calls                         | `strace -e open,read,write ls`               |
| `strace -f`                                  | Trace child processes                               | `strace -f command`                          |
| `strace -c`                                  | Count time, calls, and errors for each syscall      | `strace -c ls`                               |
| `strace -o output.txt`                       | Save trace to file                                  | `strace -o trace.txt command`                |
| `lsof`                                       | List open files                                     | `lsof                                        | grep filename` |
| `lsof -p PID`                                | Files opened by process                             | `lsof -p 1234`                               |
| `lsof -i`                                    | List Internet connections                           | `lsof -i`                                    |
| `lsof -i :80`                                | List processes using port 80                        | `lsof -i :80`                                |
| `lsof -u user`                               | Files opened by user                                | `lsof -u apache`                             |
| `lsof -c process`                            | Files opened by command                             | `lsof -c nginx`                              |
| `lsof +D directory`                          | Files open in directory                             | `lsof +D /var/log`                           |
| `fuser`                                      | Identify processes using files or sockets           | `fuser -v /var/log/syslog`                   |
| `fuser -k filename`                          | Kill processes accessing a file                     | `fuser -k /var/log/messages`                 |
| `fuser -n tcp 80`                            | Identify process using TCP port 80                  | `fuser -n tcp 80`                            |
| `pidof`                                      | Find process ID of a running program                | `pidof program_name`                         |
| `pidstat`                                    | Report statistics for Linux tasks                   | `pidstat 1`                                  |
| `pidstat -r`                                 | Report page faults and memory utilization           | `pidstat -r -p PID`                          |
| `pidstat -d`                                 | Report I/O statistics                               | `pidstat -d -p PID`                          |
| `ionice`                                     | Set I/O scheduling class and priority               | `ionice -c 2 -n 0 command`                   |
| `chrt`                                       | Manipulate real-time attributes of a process        | `chrt -f -p 10 PID`                          |
| `taskset`                                    | Set or retrieve a process's CPU affinity            | `taskset -pc 0-2 PID`                        |
| `cgcreate`                                   | Create control groups                               | `cgcreate -g cpu,memory:mygroup`             |
| `cgexec`                                     | Run process in control group                        | `cgexec -g cpu,memory:mygroup command`       |
| `cgset`                                      | Set parameters of control group                     | `cgset -r cpu.shares=512 mygroup`            |

## Networking Commands

| Command                                    | Description                                                    | Example Usage                                                     |
| ------------------------------------------ | -------------------------------------------------------------- | ----------------------------------------------------------------- | ----------- |
| `ping`                                     | Send ICMP ECHO_REQUEST to network hosts                        | `ping hostname`                                                   |
| `ping -c 5`                                | Limit to 5 packets                                             | `ping -c 5 google.com`                                            |
| `ping -i 0.2`                              | Set interval to 0.2 seconds                                    | `ping -i 0.2 google.com`                                          |
| `ping -s 1500`                             | Set packet size to 1500 bytes                                  | `ping -s 1500 google.com`                                         |
| `ping -I eth0`                             | Specify interface                                              | `ping -I eth0 google.com`                                         |
| `ping -f`                                  | Flood ping                                                     | `ping -f localhost`                                               |
| `traceroute`                               | Print the route packets trace to network host                  | `traceroute hostname`                                             |
| `traceroute -n`                            | Don't resolve hostnames                                        | `traceroute -n google.com`                                        |
| `traceroute -T`                            | Use TCP SYN for probes                                         | `traceroute -T -p 443 google.com`                                 |
| `traceroute -I`                            | Use ICMP ECHO for probes                                       | `traceroute -I google.com`                                        |
| `traceroute -w 2`                          | Wait 2 seconds for response                                    | `traceroute -w 2 google.com`                                      |
| `tracepath`                                | Similar to traceroute                                          | `tracepath hostname`                                              |
| `tracepath -n`                             | Don't resolve hostnames                                        | `tracepath -n google.com`                                         |
| `mtr`                                      | Network diagnostic combining ping & traceroute                 | `mtr google.com`                                                  |
| `mtr --report`                             | Generate report mode output                                    | `mtr --report google.com`                                         |
| `mtr -c 10`                                | Send 10 pings per host                                         | `mtr -c 10 google.com`                                            |
| `netstat`                                  | Network connections, routing tables, interface statistics      | `netstat -tuln`                                                   |
| `netstat -anp`                             | Show processes using connections                               | `netstat -anp                                                     | grep nginx` |
| `netstat -r`                               | Show routing table                                             | `netstat -r`                                                      |
| `netstat -s`                               | Show networking statistics                                     | `netstat -s`                                                      |
| `netstat -i`                               | Show network interfaces                                        | `netstat -i`                                                      |
| `netstat -o`                               | Include timer information                                      | `netstat -o`                                                      |
| `ss`                                       | Another utility to investigate sockets                         | `ss -tuln`                                                        |
| `ss -anp`                                  | Show process using sockets                                     | `ss -anp                                                          | grep nginx` |
| `ss -s`                                    | Print statistics                                               | `ss -s`                                                           |
| `ss -K`                                    | Kill connections matching filter                               | `ss -K dst 192.168.1.1`                                           |
| `ss -t state established`                  | Show established TCP connections                               | `ss -t state established`                                         |
| `ss -o state fin-wait-1`                   | Show TCP connections in FIN-WAIT-1 state                       | `ss -o state fin-wait-1`                                          |
| `ip`                                       | Show / manipulate routing, devices, policy routing and tunnels | `ip addr show`                                                    |
| `ip link`                                  | Network device operations                                      | `ip link show`                                                    |
| `ip -s link`                               | Show interface statistics                                      | `ip -s link show dev eth0`                                        |
| `ip addr add`                              | Add address to interface                                       | `ip addr add 192.168.1.100/24 dev eth0`                           |
| `ip addr del`                              | Remove address from interface                                  | `ip addr del 192.168.1.100/24 dev eth0`                           |
| `ip link set dev eth0 up`                  | Bring interface up                                             | `ip link set dev eth0 up`                                         |
| `ip link set dev eth0 down`                | Bring interface down                                           | `ip link set dev eth0 down`                                       |
| `ip route`                                 | Routing table management                                       | `ip route show`                                                   |
| `ip route add`                             | Add route                                                      | `ip route add 192.168.2.0/24 via 192.168.1.1`                     |
| `ip route del`                             | Delete route                                                   | `ip route del 192.168.2.0/24`                                     |
| `ip neighbour`                             | Manage neighbor/ARP tables                                     | `ip neighbour show`                                               |
| `ip monitor`                               | Watch for netlink messages                                     | `ip monitor all`                                                  |
| `ifconfig`                                 | Configure a network interface                                  | `ifconfig eth0`                                                   |
| `ifconfig eth0 up`                         | Bring interface up                                             | `ifconfig eth0 up`                                                |
| `ifconfig eth0 down`                       | Bring interface down                                           | `ifconfig eth0 down`                                              |
| `ifconfig eth0 192.168.1.100`              | Set IP address                                                 | `ifconfig eth0 192.168.1.100`                                     |
| `ifconfig eth0 netmask 255.255.255.0`      | Set netmask                                                    | `ifconfig eth0 netmask 255.255.255.0`                             |
| `ifconfig eth0 promisc`                    | Set promiscuous mode                                           | `ifconfig eth0 promisc`                                           |
| `ifconfig eth0 mtu 9000`                   | Set MTU                                                        | `ifconfig eth0 mtu 9000`                                          |
| `iwconfig`                                 | Configure a wireless network interface                         | `iwconfig wlan0`                                                  |
| `iwconfig wlan0 essid "network"`           | Set ESSID                                                      | `iwconfig wlan0 essid "MyNetwork"`                                |
| `iwconfig wlan0 key 1234567890`            | Set WEP key                                                    | `iwconfig wlan0 key s:passphrase`                                 |
| `iwconfig wlan0 mode`                      | Set wireless mode                                              | `iwconfig wlan0 mode Managed`                                     |
| `iw`                                       | Modern wireless configuration tool                             | `iw dev wlan0 scan`                                               |
| `iw dev wlan0 link`                        | Show link status                                               | `iw dev wlan0 link`                                               |
| `iw dev wlan0 station dump`                | Show connection details                                        | `iw dev wlan0 station dump`                                       |
| `route`                                    | Show / manipulate the IP routing table                         | `route -n`                                                        |
| `route add`                                | Add static route                                               | `route add -net 192.168.2.0/24 gw 192.168.1.1`                    |
| `route del`                                | Delete route                                                   | `route del -net 192.168.2.0/24`                                   |
| `arp`                                      | Manipulate the system ARP cache                                | `arp -a`                                                          |
| `arp -s`                                   | Add ARP entry                                                  | `arp -s 192.168.1.100 00:11:22:33:44:55`                          |
| `arp -d`                                   | Delete ARP entry                                               | `arp -d 192.168.1.100`                                            |
| `host`                                     | DNS lookup utility                                             | `host domain.com`                                                 |
| `host -t mx`                               | Query MX records                                               | `host -t mx gmail.com`                                            |
| `host -t ns`                               | Query NS records                                               | `host -t ns google.com`                                           |
| `host -v`                                  | Verbose output                                                 | `host -v google.com`                                              |
| `dig`                                      | DNS lookup utility                                             | `dig domain.com`                                                  |
| `dig +short`                               | Short answer                                                   | `dig +short google.com`                                           |
| `dig @8.8.8.8`                             | Use specific DNS server                                        | `dig @8.8.8.8 google.com`                                         |
| `dig -x`                                   | Reverse lookup                                                 | `dig -x 8.8.8.8`                                                  |
| `dig +trace`                               | Trace DNS resolution path                                      | `dig +trace google.com`                                           |
| `dig AXFR`                                 | DNS zone transfer                                              | `dig AXFR @ns.example.com example.com`                            |
| `nslookup`                                 | Query DNS servers                                              | `nslookup domain.com`                                             |
| `nslookup -type=mx`                        | Query MX records                                               | `nslookup -type=mx gmail.com`                                     |
| `nslookup -debug`                          | Show debug info                                                | `nslookup -debug google.com`                                      |
| `whois`                                    | Client for the whois directory service                         | `whois domain.com`                                                |
| `whois -h whois.apnic.net`                 | Query specific WHOIS server                                    | `whois -h whois.apnic.net 8.8.8.8`                                |
| `wget`                                     | Non-interactive network downloader                             | `wget URL`                                                        |
| `wget -c`                                  | Continue interrupted download                                  | `wget -c http://example.com/file.iso`                             |
| `wget -r`                                  | Recursive download                                             | `wget -r http://example.com/`                                     |
| `wget -b`                                  | Background download                                            | `wget -b http://example.com/large.iso`                            |
| `wget -P`                                  | Save to specific directory                                     | `wget -P /tmp http://example.com/file.txt`                        |
| `wget --user --password`                   | HTTP authentication                                            | `wget --user=user --password=pass http://example.com/private/`    |
| `wget -q`                                  | Quiet mode                                                     | `wget -q http://example.com/file.txt`                             |
| `wget -O`                                  | Specify output filename                                        | `wget -O custom.html http://example.com/index.html`               |
| `curl`                                     | Transfer data from or to a server                              | `curl URL`                                                        |
| `curl -o`                                  | Save to file                                                   | `curl -o file.html http://example.com`                            |
| `curl -O`                                  | Use remote filename                                            | `curl -O http://example.com/file.txt`                             |
| `curl -C -`                                | Resume download                                                | `curl -C - -O http://example.com/large.iso`                       |
| `curl -L`                                  | Follow redirects                                               | `curl -L http://example.com`                                      |
| `curl -I`                                  | Show headers only                                              | `curl -I http://example.com`                                      |
| `curl -u`                                  | HTTP authentication                                            | `curl -u username:password http://example.com`                    |
| `curl -d`                                  | POST data                                                      | `curl -d "param1=value1&param2=value2" http://example.com`        |
| `curl -X`                                  | Specify HTTP method                                            | `curl -X PUT -d @file.json http://api.example.com`                |
| `curl -H`                                  | Add header                                                     | `curl -H "Content-Type: application/json" http://api.example.com` |
| `nc` / `netcat`                            | TCP/IP swiss army knife                                        | `nc -zvw3 host port`                                              |
| `nc -l`                                    | Listen mode                                                    | `nc -l 1234`                                                      |
| `nc -u`                                    | UDP mode                                                       | `nc -u 192.168.1.1 53`                                            |
| `nc -p`                                    | Specify source port                                            | `nc -p 12345 192.168.1.1 80`                                      |
| `nc -e`                                    | Execute program on connection                                  | `nc -l 1234 -e /bin/bash`                                         |
| `nc -q`                                    | Quit after EOF & delay                                         | `nc -q 5 192.168.1.1 80 < request.txt`                            |
| `nmap`                                     | Network exploration tool and security scanner                  | `nmap IP_address`                                                 |
| `nmap -p 1-1000`                           | Scan port range                                                | `nmap -p 1-1000 192.168.1.1`                                      |
| `nmap -sS`                                 | SYN scan                                                       | `nmap -sS 192.168.1.0/24`                                         |
| `nmap -sU`                                 | UDP scan                                                       | `nmap -sU 192.168.1.1`                                            |
| `nmap -O`                                  | OS detection                                                   | `nmap -O 192.168.1.1`                                             |
| `nmap -A`                                  | Aggressive scan                                                | `nmap -A 192.168.1.1`                                             |
| `nmap -sV`                                 | Service/version detection                                      | `nmap -sV 192.168.1.1`                                            |
| `nmap -T4`                                 | Faster timing template                                         | `nmap -T4 192.168.1.0/24`                                         |
| `nmap -oN`                                 | Output to file                                                 | `nmap -oN scan.txt 192.168.1.1`                                   |
| `iptables`                                 | Administration tool for IPv4 packet filtering and NAT          | `iptables -L`                                                     |
| `iptables -L -v`                           | Verbose listing                                                | `iptables -L -v`                                                  |
| `iptables -nvL`                            | Numeric, verbose listing                                       | `iptables -nvL`                                                   |
| `iptables -F`                              | Flush all rules                                                | `iptables -F`                                                     |
| `iptables -A`                              | Append rule                                                    | `iptables -A INPUT -p tcp --dport 22 -j ACCEPT`                   |
| `iptables -D`                              | Delete rule                                                    | `iptables -D INPUT 1`                                             |
| `iptables -I`                              | Insert rule                                                    | `iptables -I INPUT 1 -p tcp --dport 80 -j ACCEPT`                 |
| `iptables-save`                            | Dump rules to stdout                                           | `iptables-save > /etc/iptables.rules`                             |
| `iptables-restore`                         | Restore saved rules                                            | `iptables-restore < /etc/iptables.rules`                          |
| `iptables -t nat`                          | Work with NAT table                                            | `iptables -t nat -L`                                              |
| `firewall-cmd`                             | FirewallD command                                              | `firewall-cmd --state`                                            |
| `tcpdump`                                  | Dump traffic on a network                                      | `tcpdump -i eth0`                                                 |
| `tcpdump -n`                               | Don't resolve names                                            | `tcpdump -n -i eth0`                                              |
| `tcpdump -w`                               | Write to file                                                  | `tcpdump -w capture.pcap -i eth0`                                 |
| `tcpdump -r`                               | Read from file                                                 | `tcpdump -r capture.pcap`                                         |
| `tcpdump host`                             | Filter by host                                                 | `tcpdump host 192.168.1.1`                                        |
| `tcpdump port`                             | Filter by port                                                 | `tcpdump port 80`                                                 |
| `tcpdump 'tcp[tcpflags] & (tcp-syn) != 0'` | Capture SYN packets                                            | `tcpdump 'tcp[tcpflags] & (tcp-syn) != 0'`                        |
| `tcpdump -A`                               | Print payload in ASCII                                         | `tcpdump -A port 80`                                              |
| `tcpdump -X`                               | Print payload in hex and ASCII                                 | `tcpdump -X port 80`                                              |
| `tcpdump -c`                               | Exit after capturing packets                                   | `tcpdump -c 100 -i eth0`                                          |
| `ethtool`                                  | Display or change ethernet settings                            | `ethtool eth0`                                                    |
| `ethtool -i`                               | Show driver info                                               | `ethtool -i eth0`                                                 |
| `ethtool -S`                               | Show driver statistics                                         | `ethtool -S eth0`                                                 |
| `ethtool -t`                               | Run self-test                                                  | `ethtool -t eth0`                                                 |
| `ethtool -s`                               | Change settings                                                | `ethtool -s eth0 speed 1000 duplex full`                          |
| `iftop`                                    | Display bandwidth usage                                        | `iftop -i eth0`                                                   |
| `bmon`                                     | Bandwidth monitor                                              | `bmon`                                                            |
| `vnstat`                                   | Network traffic monitor                                        | `vnstat -i eth0`                                                  |
| `tcptrack`                                 | Track TCP connections                                          | `tcptrack -i eth0`                                                |
| `iperf`                                    | Network performance measurement                                | `iperf -s` (server), `iperf -c server_ip` (client)                |
| `nmcli`                                    | NetworkManager command-line tool                               | `nmcli device status`                                             |
| `nmcli con show`                           | Show connections                                               | `nmcli con show`                                                  |
| `nmcli con up`                             | Activate connection                                            | `nmcli con up "Wi-Fi connection 1"`                               |
| `nmtui`                                    | Text interface for NetworkManager                              | `nmtui`                                                           |
| `dhclient`                                 | DHCP client                                                    | `dhclient eth0`                                                   |
| `dhclient -r`                              | Release IP address                                             | `dhclient -r eth0`                                                |
| `nft`                                      | nftables packet filtering                                      | `nft list ruleset`                                                |
| `hostnamectl`                              | Control system hostname                                        | `hostnamectl set-hostname new-hostname`                           |
| `ip neigh`                                 | Show neighbor/ARP cache                                        | `ip neigh show`                                                   |

## SSH and Remote Access

| Command                  | Description                                            | Example Usage                                          |
| ------------------------ | ------------------------------------------------------ | ------------------------------------------------------ |
| `ssh`                    | OpenSSH SSH client                                     | `ssh user@hostname`                                    |
| `ssh -p 2222`            | Connect on specific port                               | `ssh -p 2222 user@hostname`                            |
| `ssh -i`                 | Specify identity file                                  | `ssh -i ~/.ssh/custom_key user@hostname`               |
| `ssh -X`                 | Enable X11 forwarding                                  | `ssh -X user@hostname`                                 |
| `ssh -L`                 | Local port forwarding                                  | `ssh -L 8080:localhost:80 user@hostname`               |
| `ssh -R`                 | Remote port forwarding                                 | `ssh -R 8080:localhost:80 user@hostname`               |
| `ssh -D`                 | Dynamic port forwarding (SOCKS proxy)                  | `ssh -D 1080 user@hostname`                            |
| `ssh -J`                 | Jump host                                              | `ssh -J user1@jumphost user2@destination`              |
| `ssh -N`                 | Do not execute remote command                          | `ssh -N -L 8080:localhost:80 user@hostname`            |
| `ssh -f`                 | Background ssh                                         | `ssh -f -N -L 8080:localhost:80 user@hostname`         |
| `ssh -v`                 | Verbose mode                                           | `ssh -v user@hostname`                                 |
| `ssh -t`                 | Force pseudo-terminal allocation                       | `ssh -t user@hostname 'sudo htop'`                     |
| `ssh-keygen`             | Authentication key generation                          | `ssh-keygen -t rsa`                                    |
| `ssh-keygen -t ed25519`  | Generate Ed25519 key                                   | `ssh-keygen -t ed25519`                                |
| `ssh-keygen -b 4096`     | Specify key size                                       | `ssh-keygen -b 4096 -t rsa`                            |
| `ssh-keygen -f`          | Specify output file                                    | `ssh-keygen -f ~/.ssh/custom_key`                      |
| `ssh-keygen -p`          | Change passphrase                                      | `ssh-keygen -p -f ~/.ssh/id_rsa`                       |
| `ssh-copy-id`            | Install your identity key in a remote machine          | `ssh-copy-id user@hostname`                            |
| `ssh-copy-id -i`         | Specify key to copy                                    | `ssh-copy-id -i ~/.ssh/custom_key.pub user@hostname`   |
| `ssh-agent`              | Authentication agent                                   | `ssh-agent bash`                                       |
| `ssh-add`                | Add private key identities to the authentication agent | `ssh-add ~/.ssh/id_rsa`                                |
| `ssh-add -l`             | List keys in agent                                     | `ssh-add -l`                                           |
| `ssh-add -d`             | Remove key from agent                                  | `ssh-add -d ~/.ssh/id_rsa`                             |
| `sftp`                   | Secure file transfer program                           | `sftp user@hostname`                                   |
| `sftp -P 2222`           | Connect on specific port                               | `sftp -P 2222 user@hostname`                           |
| `scp`                    | Secure copy                                            | `scp file user@host:/path`                             |
| `scp -r`                 | Recursive copy                                         | `scp -r directory user@host:/path`                     |
| `scp -P 2222`            | Specify port                                           | `scp -P 2222 file user@host:/path`                     |
| `scp -i`                 | Specify identity file                                  | `scp -i ~/.ssh/custom_key file user@host:/path`        |
| `rsync`                  | Fast and versatile file copying tool                   | `rsync -avz source/ user@host:/path`                   |
| `rsync -avz --delete`    | Synchronize with delete                                | `rsync -avz --delete source/ user@host:/path`          |
| `rsync -e "ssh -p 2222"` | Specify port                                           | `rsync -avz -e "ssh -p 2222" source/ user@host:/path`  |
| `rsync --progress`       | Show progress                                          | `rsync --progress -avz source/ user@host:/path`        |
| `rsync --exclude`        | Exclude files                                          | `rsync -avz --exclude='*.tmp' source/ user@host:/path` |
| `rsync --dry-run`        | Simulate sync                                          | `rsync --dry-run -avz source/ user@host:/path`         |
| `rsync --bwlimit=1000`   | Limit bandwidth (KB/s)                                 | `rsync --bwlimit=1000 -avz source/ user@host:/path`    |
| `rdesktop`               | Remote Desktop Protocol client                         | `rdesktop hostname`                                    |
| `xrdp`                   | Remote Desktop server                                  | `systemctl start xrdp`                                 |
| `vnc4server`             | VNC server                                             | `vnc4server :1`                                        |
| `vncviewer`              | VNC client                                             | `vncviewer hostname:1`                                 |
| `remmina`                | Remote desktop client                                  | `remmina`                                              |
| `teamviewer`             | Remote access software                                 | `teamviewer`                                           |

## File Compression

| Command              | Description                              | Example Usage                                    |
| -------------------- | ---------------------------------------- | ------------------------------------------------ |
| `gzip`               | Compress or expand files                 | `gzip filename`                                  |
| `gzip -d`            | Decompress files                         | `gzip -d filename.gz`                            |
| `gzip -c`            | Write to stdout                          | `gzip -c filename > filename.gz`                 |
| `gzip -1`            | Fast compression                         | `gzip -1 filename`                               |
| `gzip -9`            | Best compression                         | `gzip -9 filename`                               |
| `gzip -l`            | List contents                            | `gzip -l filename.gz`                            |
| `gunzip`             | Expand compressed files                  | `gunzip filename.gz`                             |
| `gunzip -c`          | Write to stdout                          | `gunzip -c filename.gz > filename`               |
| `zcat`               | Cat gzipped files                        | `zcat filename.gz`                               |
| `bzip2`              | Block-sorting file compressor            | `bzip2 filename`                                 |
| `bzip2 -d`           | Decompress files                         | `bzip2 -d filename.bz2`                          |
| `bzip2 -1`           | Fast compression                         | `bzip2 -1 filename`                              |
| `bzip2 -9`           | Best compression                         | `bzip2 -9 filename`                              |
| `bunzip2`            | Decompress files                         | `bunzip2 filename.bz2`                           |
| `bzcat`              | Cat bzipped files                        | `bzcat filename.bz2`                             |
| `xz`                 | Compress or decompress files             | `xz filename`                                    |
| `xz -d`              | Decompress files                         | `xz -d filename.xz`                              |
| `xz -0`              | Fastest compression                      | `xz -0 filename`                                 |
| `xz -9`              | Best compression                         | `xz -9 filename`                                 |
| `xz -l`              | List contents                            | `xz -l filename.xz`                              |
| `unxz`               | Decompress files                         | `unxz filename.xz`                               |
| `xzcat`              | Cat xzipped files                        | `xzcat filename.xz`                              |
| `tar`                | Archive files                            | `tar -cvf archive.tar dir/`                      |
| `tar -xf`            | Extract files from an archive            | `tar -xf archive.tar`                            |
| `tar -czf`           | Create a gzipped tar archive             | `tar -czf archive.tar.gz dir/`                   |
| `tar -xzf`           | Extract a gzipped tar archive            | `tar -xzf archive.tar.gz`                        |
| `tar -cjf`           | Create a bzipped tar archive             | `tar -cjf archive.tar.bz2 dir/`                  |
| `tar -xjf`           | Extract a bzipped tar archive            | `tar -xjf archive.tar.bz2`                       |
| `tar -cJf`           | Create an xzipped tar archive            | `tar -cJf archive.tar.xz dir/`                   |
| `tar -xJf`           | Extract an xzipped tar archive           | `tar -xJf archive.tar.xz`                        |
| `tar -tf`            | List content of archive                  | `tar -tf archive.tar`                            |
| `tar --exclude`      | Exclude files                            | `tar -czf archive.tar.gz --exclude '*.tmp' dir/` |
| `zip`                | Package and compress files               | `zip -r archive.zip dir/`                        |
| `zip -e`             | Encrypt zip file                         | `zip -e -r archive.zip dir/`                     |
| `zip -P password`    | Set password                             | `zip -P password -r archive.zip dir/`            |
| `zip -9`             | Best compression                         | `zip -9 -r archive.zip dir/`                     |
| `zip -j`             | Junk paths (don't store directory names) | `zip -j archive.zip dir/*`                       |
| `unzip`              | Extract files from a ZIP archive         | `unzip archive.zip`                              |
| `unzip -l`           | List archive contents                    | `unzip -l archive.zip`                           |
| `unzip -d directory` | Extract to directory                     | `unzip archive.zip -d /tmp/extract`              |
| `unzip -P password`  | Specify password                         | `unzip -P password archive.zip`                  |
| `unzip -q`           | Quiet mode                               | `unzip -q archive.zip`                           |
| `7z`                 | 7-Zip file archiver                      | `7z a archive.7z dir/`                           |
| `7z x`               | Extract archive                          | `7z x archive.7z`                                |
| `7z l`               | List contents                            | `7z l archive.7z`                                |
| `rar`                | RAR archive utility                      | `rar a archive.rar dir/`                         |
| `unrar`              | Extract RAR archives                     | `unrar x archive.rar`                            |

## Input/Output Redirection

| Command                   | Description                                    | Example Usage                             |
| ------------------------- | ---------------------------------------------- | ----------------------------------------- | ------------ | --------- |
| `>`                       | Redirect output to a file                      | `command > file`                          |
| `>>`                      | Append output to a file                        | `command >> file`                         |
| `<`                       | Redirect input from a file                     | `command < file`                          |
| `                         | `                                              | Pipe output of one command to another     | `command1    | command2` |
| `2>`                      | Redirect stderr to a file                      | `command 2> error_file`                   |
| `2>&1`                    | Redirect stderr to stdout                      | `command > file 2>&1`                     |
| `&>`                      | Redirect both stdout and stderr to a file      | `command &> file`                         |
| `tee`                     | Read from stdin and write to stdout and files  | `command                                  | tee file`    |
| `tee -a`                  | Append to files, don't overwrite               | `command                                  | tee -a file` |
| `<(command)`              | Process substitution (output as file)          | `diff <(ls dir1) <(ls dir2)`              |
| `>(command)`              | Process substitution (input as file)           | `echo "data" > >(grep pattern)`           |
| `/dev/null`               | Discard output                                 | `command > /dev/null`                     |
| `exec 3> file`            | Open file descriptor 3 for writing             | `exec 3> logfile; echo "log entry" >&3`   |
| `exec 4< file`            | Open file descriptor 4 for reading             | `exec 4< datafile; read -u 4 var`         |
| `exec 5<> file`           | Open file descriptor 5 for reading and writing | `exec 5<> datafile`                       |
| `command <<< "string"`    | Here string (input from string)                | `grep pattern <<< "test string"`          |
| `command << EOF`          | Here document (multi-line input)               | `cat << EOF > file.txt`                   |
| `command1 && command2`    | Run command2 only if command1 succeeds         | `mkdir dir && cd dir`                     |
| `command1 \|\| command2`  | Run command2 only if command1 fails            | `ping -c1 server \|\| echo "Server down"` |
| `(command1; command2)`    | Group commands in subshell                     | `(cd dir; ls)`                            |
| `{ command1; command2; }` | Group commands without subshell                | `{ date; uptime; } > system_status.txt`   |

## File Searching and Pattern Matching

| Command                               | Description                                 | Example Usage                                         |
| ------------------------------------- | ------------------------------------------- | ----------------------------------------------------- |
| `find`                                | Search for files in a directory hierarchy   | `find /path -name "pattern"`                          |
| `find -type f`                        | Find only files                             | `find /path -type f`                                  |
| `find -type d`                        | Find only directories                       | `find /path -type d`                                  |
| `find -mtime -7`                      | Find files modified in last 7 days          | `find /path -mtime -7`                                |
| `find -mmin -60`                      | Find files modified in last 60 minutes      | `find /path -mmin -60`                                |
| `find -size +10M`                     | Find files larger than 10MB                 | `find /path -size +10M`                               |
| `find -size -1k`                      | Find files smaller than 1KB                 | `find /path -size -1k`                                |
| `find -user username`                 | Find files owned by user                    | `find /path -user username`                           |
| `find -group groupname`               | Find files owned by group                   | `find /path -group groupname`                         |
| `find -perm 644`                      | Find files with exact permission            | `find /path -perm 644`                                |
| `find -perm -644`                     | Find files with at least these permissions  | `find /path -perm -644`                               |
| `find -perm /u=r`                     | Find files readable by owner                | `find /path -perm /u=r`                               |
| `find -empty`                         | Find empty files or directories             | `find /path -empty`                                   |
| `find -exec command {} \;`            | Execute command on found files (one by one) | `find /path -name "*.tmp" -exec rm {} \;`             |
| `find -exec command {} \+`            | Execute command with all found files        | `find /path -name "*.txt" -exec grep "pattern" {} \+` |
| `find -maxdepth 2`                    | Limit search depth                          | `find /path -maxdepth 2 -name "pattern"`              |
| `find -mindepth 2`                    | Set minimum search depth                    | `find /path -mindepth 2 -name "pattern"`              |
| `find -not -name "pattern"`           | Negate match                                | `find /path -not -name "*.log"`                       |
| `find -name "*.txt" -o -name "*.log"` | OR condition                                | `find /path -name "*.txt" -o -name "*.log"`           |
| `find -regex "pattern"`               | Find using regex                            | `find /path -regex ".*\.\(jpg\|png\)"`                |
| `find -iname "pattern"`               | Case-insensitive name matching              | `find /path -iname "*.JPG"`                           |
| `find -newer file`                    | Find files newer than reference file        | `find /path -newer reference.txt`                     |
| `find . -path "*/subdir/*"`           | Find files in specific subdirectory         | `find . -path "*/logs/*"`                             |
| `grep`                                | Print lines matching a pattern              | `grep "pattern" file`                                 |
| `grep -r`                             | Recursive search                            | `grep -r "pattern" directory`                         |
| `grep -i`                             | Case-insensitive search                     | `grep -i "pattern" file`                              |
| `grep -l`                             | List only filenames                         | `grep -l "pattern" *`                                 |
| `grep -v`                             | Invert match (lines that don't match)       | `grep -v "pattern" file`                              |
| `grep -w`                             | Match whole words only                      | `grep -w "word" file`                                 |
| `grep -A 3`                           | Show 3 lines after match                    | `grep -A 3 "pattern" file`                            |
| `grep -B 3`                           | Show 3 lines before match                   | `grep -B 3 "pattern" file`                            |
| `grep -C 3`                           | Show                                        |

## Package Management

### Debian/Ubuntu (APT)

| Command          | Description                                 | Example Usage              |
| ---------------- | ------------------------------------------- | -------------------------- |
| `apt update`     | Update package lists                        | `sudo apt update`          |
| `apt upgrade`    | Upgrade installed packages                  | `sudo apt upgrade`         |
| `apt install`    | Install packages                            | `sudo apt install package` |
| `apt remove`     | Remove packages                             | `sudo apt remove package`  |
| `apt purge`      | Remove packages and configuration files     | `sudo apt purge package`   |
| `apt search`     | Search for packages                         | `apt search keyword`       |
| `apt show`       | Show package details                        | `apt show package`         |
| `apt list`       | List packages                               | `apt list --installed`     |
| `apt autoremove` | Remove automatically installed dependencies | `sudo apt autoremove`      |
| `dpkg -i`        | Install package from a file                 | `sudo dpkg -i package.deb` |
| `dpkg -l`        | List installed packages                     | `dpkg -l`                  |
| `dpkg -r`        | Remove package                              | `sudo dpkg -r package`     |

### Red Hat/CentOS (YUM/DNF)

| Command       | Description                    | Example Usage              |
| ------------- | ------------------------------ | -------------------------- |
| `yum update`  | Update installed packages      | `sudo yum update`          |
| `yum install` | Install packages               | `sudo yum install package` |
| `yum remove`  | Remove packages                | `sudo yum remove package`  |
| `yum search`  | Search for packages            | `yum search keyword`       |
| `yum info`    | Show package information       | `yum info package`         |
| `yum list`    | List packages                  | `yum list installed`       |
| `dnf`         | Next-generation version of YUM | `sudo dnf command`         |
| `rpm -i`      | Install package from a file    | `sudo rpm -i package.rpm`  |
| `rpm -q`      | Query installed packages       | `rpm -q package`           |
| `rpm -e`      | Erase (remove) package         | `sudo rpm -e package`      |

## System Services

| Command                | Description                                    | Example Usage                         |
| ---------------------- | ---------------------------------------------- | ------------------------------------- |
| `systemctl`            | Control the systemd system and service manager | `systemctl status service`            |
| `systemctl start`      | Start a service                                | `sudo systemctl start service`        |
| `systemctl stop`       | Stop a service                                 | `sudo systemctl stop service`         |
| `systemctl restart`    | Restart a service                              | `sudo systemctl restart service`      |
| `systemctl enable`     | Enable a service to start at boot              | `sudo systemctl enable service`       |
| `systemctl disable`    | Disable a service from starting at boot        | `sudo systemctl disable service`      |
| `systemctl list-units` | List units                                     | `systemctl list-units --type=service` |
| `service`              | Run a System V init script                     | `sudo service service_name action`    |
| `chkconfig`            | System V service configuration tool            | `chkconfig service_name on`           |
| `journalctl`           | Query the systemd journal                      | `journalctl -u service`               |
| `logs`                 | View log files                                 | `less /var/log/syslog`                |

## Disk and Storage Management

| Command     | Description                                    | Example Usage               |
| ----------- | ---------------------------------------------- | --------------------------- |
| `fdisk`     | Partition table manipulator                    | `sudo fdisk /dev/sda`       |
| `parted`    | Partition manipulation program                 | `sudo parted /dev/sda`      |
| `mkfs`      | Build a Linux filesystem                       | `sudo mkfs.ext4 /dev/sda1`  |
| `mkswap`    | Set up a swap area                             | `sudo mkswap /dev/sda2`     |
| `swapon`    | Enable swap devices                            | `sudo swapon /dev/sda2`     |
| `mount`     | Mount a filesystem                             | `sudo mount /dev/sda1 /mnt` |
| `umount`    | Unmount a filesystem                           | `sudo umount /mnt`          |
| `blkid`     | Locate/print block device attributes           | `sudo blkid`                |
| `lsblk`     | List block devices                             | `lsblk`                     |
| `df`        | Report file system disk space usage            | `df -h`                     |
| `du`        | Estimate file space usage                      | `du -sh directory`          |
| `fsck`      | Check and repair a Linux filesystem            | `sudo fsck /dev/sda1`       |
| `e2fsck`    | Check ext2/ext3/ext4 filesystem                | `sudo e2fsck /dev/sda1`     |
| `tune2fs`   | Adjust tunable filesystem parameters           | `sudo tune2fs -l /dev/sda1` |
| `badblocks` | Search a device for bad blocks                 | `sudo badblocks /dev/sda1`  |
| `hdparm`    | Get/set SATA/IDE device parameters             | `sudo hdparm -i /dev/sda`   |
| `smartctl`  | Control and monitor S.M.A.R.T. enabled devices | `sudo smartctl -a /dev/sda` |

## Date and Time

| Command       | Description                      | Example Usage                        |
| ------------- | -------------------------------- | ------------------------------------ |
| `date`        | Display or set date and time     | `date`                               |
| `date -s`     | Set the date and time            | `sudo date -s "2 OCT 2023 18:00:00"` |
| `hwclock`     | Query or set the hardware clock  | `sudo hwclock --systohc`             |
| `timedatectl` | Control the system time and date | `timedatectl status`                 |
| `cal`         | Display a calendar               | `cal`                                |
| `ntpdate`     | Set the date and time via NTP    | `sudo ntpdate pool.ntp.org`          |

## Shell Scripting Basics

| Command            | Description                     | Example Usage                                   |
| ------------------ | ------------------------------- | ----------------------------------------------- | ---------- | --------- | --- | --------- |
| `#!/bin/bash`      | Shebang line for bash scripts   | First line of script                            |
| `echo`             | Display a line of text          | `echo "Hello World"`                            |
| `read`             | Read a line from standard input | `read -p "Enter value: " variable`              |
| `if [ condition ]` | Conditional statement           | `if [ "$a" -eq "$b" ]; then echo "Equal"; fi`   |
| `for loop`         | Loop over a sequence            | `for i in {1..5}; do echo $i; done`             |
| `while loop`       | Loop while condition is true    | `while [ $i -le 5 ]; do echo $i; ((i++)); done` |
| `case`             | Conditional branch statement    | `case "$var" in pattern) commands;; esac`       |
| `function`         | Define a function               | `function_name() { commands; }`                 |
| `$1, $2, ...`      | Positional parameters           | `echo "First arg: $1"`                          |
| `$#`               | Number of arguments             | `echo "Number of args: $#"`                     |
| `$@`               | All arguments                   | `echo "All args: $@"`                           |
| `$?`               | Exit status of the last command | `echo "Last command exit status: $?"`           |
| `&&`               | Logical AND                     | `command1 && command2`                          |
| `                  |                                 | `                                               | Logical OR | `command1 |     | command2` |
| `export`           | Set environment variables       | `export VAR=value`                              |
| `source` or `.`    | Execute commands from a file    | `source file.sh` or `. file.sh`                 |
| `exit`             | Exit the shell                  | `exit 0`                                        |

## PKI (Public Key Infrastructure) Commands

| Command              | Description                              | Example Usage                                  |
| -------------------- | ---------------------------------------- | ---------------------------------------------- |
| `openssl req`        | Create certificate signing requests      | `openssl req -new -key key.pem -out csr.pem`   |
| `openssl genrsa`     | Generate RSA private key                 | `openssl genrsa -out key.pem 2048`             |
| `openssl x509`       | Certificate display and signing tool     | `openssl x509 -in cert.pem -text`              |
| `openssl ca`         | Sign certificate requests with CA        | `openssl ca -in csr.pem -out cert.pem`         |
| `openssl verify`     | Verify certificate validity              | `openssl verify -CAfile ca.pem cert.pem`       |
| `openssl s_client`   | SSL/TLS client                           | `openssl s_client -connect host:port`          |
| `openssl s_server`   | SSL/TLS server                           | `openssl s_server -key key.pem -cert cert.pem` |
| `keytool`            | Java certificate management              | `keytool -list -keystore keystore.jks`         |
| `certutil`           | NSS certificate management               | `certutil -d /path/to/db -L`                   |

## Other Useful Commands

| Command     | Description                                      | Example Usage                     |
| ----------- | ------------------------------------------------ | --------------------------------- | ------------------------------- |
| `alias`     | Create command aliases                           | `alias ll='ls -la'`               |
| `history`   | Command history                                  | `history`                         |
| `crontab`   | Schedule periodic jobs                           | `crontab -e`                      |
| `at`        | Execute commands at a specified time             | `at now + 1 hour`                 |
| `watch`     | Execute a program periodically                   | `watch -n 1 command`              |
| `screen`    | Terminal multiplexer                             | `screen`                          |
| `tmux`      | Terminal multiplexer                             | `tmux`                            |
| `wget`      | Download files from the web                      | `wget URL`                        |
| `curl`      | Transfer data from or to a server                | `curl URL`                        |
| `rsync`     | Remote file synchronization                      | `rsync -avz source/ destination/` |
| `tee`       | Redirect output to multiple files                | `command                          | tee file1 file2`                |
| `bc`        | Calculator                                       | `echo "5 + 5"                     | bc`                             |
| `expr`      | Evaluate expressions                             | `expr 5 + 5`                      |
| `xargs`     | Build and execute command lines                  | `echo "file1 file2"               | xargs rm`                       |
| `md5sum`    | Compute MD5 message digest                       | `md5sum file`                     |
| `sha256sum` | Compute SHA256 message digest                    | `sha256sum file`                  |
| `basename`  | Strip directory and suffix from filenames        | `basename /path/to/file.txt`      |
| `dirname`   | Strip last component from file name              | `dirname /path/to/file.txt`       |
| `seq`       | Print sequences of numbers                       | `seq 1 10`                        |
| `sleep`     | Delay for a specified amount of time             | `sleep 10`                        |
| `yes`       | Output a string repeatedly                       | `yes "y"                          | command_requiring_confirmation` |
| `shuf`      | Generate random permutations                     | `shuf -i 1-10 -n 5`               |
| `strace`    | Trace system calls and signals                   | `strace command`                  |
| `ltrace`    | Library call tracer                              | `ltrace command`                  |
| `logger`    | Log messages to system log                       | `logger "Message"`                |
| `nohup`     | Run a command immune to hangups                  | `nohup command &`                 |
| `timeout`   | Run a command with a time limit                  | `timeout 10s command`             |
| `wait`      | Wait for process to complete                     | `wait PID`                        |
| `chroot`    | Run command or shell with special root directory | `sudo chroot /path command`       |
| `lsof`      | List open files                                  | `lsof -p PID`                     |
| `pidof`     | Find process ID of a running program             | `pidof program_name`              |
| `pmap`      | Display memory map of a process                  | `pmap PID`                        |
| `vmstat`    | Report virtual memory statistics                 | `vmstat 1`                        |
| `fuser`     | Identify processes using files or sockets        | `fuser -m /path`                  |
| `ionice`    | Set I/O scheduling class and priority            | `ionice -c 2 -n 0 command`        |
| `iotop`     | Simple top-like I/O monitor                      | `iotop`                           |

## Advanced Troubleshooting

| Command                               | Description                                   | Example Usage                         |
| ------------------------------------- | --------------------------------------------- | ------------------------------------- | -------------- |
| `dmesg -w`                            | Follow kernel messages                        | `dmesg -w`                            |
| `dmesg -T --level=err,warn`           | Show only errors and warnings with timestamps | `dmesg -T --level=err,warn`           |
| `journalctl -xef`                     | Follow journald logs with explanations        | `journalctl -xef`                     |
| `journalctl -u service`               | Show logs for specific service                | `journalctl -u nginx`                 |
| `journalctl -p err..emerg`            | Filter by priority (error to emergency)       | `journalctl -p err..emerg`            |
| `journalctl --since "1 hour ago"`     | Show last hour of logs                        | `journalctl --since "1 hour ago"`     |
| `journalctl _PID=1234`                | Show logs for specific PID                    | `journalctl _PID=1234`                |
| `systemctl status service`            | Show service status with recent logs          | `systemctl status nginx`              |
| `systemctl list-units --state=failed` | List failed units                             | `systemctl list-units --state=failed` |
| `strace -f -e trace=network`          | Trace network-related syscalls                | `strace -f -e trace=network -p 1234`  |
| `strace -c`                           | Count syscalls and timing                     | `strace -c ls`                        |
| `ltrace -f`                           | Trace library calls with child processes      | `ltrace -f -p 1234`                   |
| `lsof +D /var/log`                    | Find processes using files in directory       | `lsof +D /var/log`                    |
| `lsof -u user`                        | List files opened by user                     | `lsof -u www-data`                    |
| `lsof -p PID`                         | List files opened by PID                      | `lsof -p 1234`                        |
| `lsof -i TCP:80`                      | Find processes using TCP port 80              | `lsof -i TCP:80`                      |
| `lsof -iTCP -sTCP:LISTEN`             | Show all listening TCP ports                  | `lsof -iTCP -sTCP:LISTEN`             |
| `lsof -i UDP`                         | Show all UDP connections                      | `lsof -i UDP`                         |
| `lsof +L1`                            | Find deleted files still in use               | `lsof +L1`                            |
| `fuser -m /path`                      | Show processes using mounted filesystem       | `fuser -m /var`                       |
| `fuser -k /path`                      | Kill processes using file or directory        | `fuser -k /var/log/messages`          |
| `fuser -n tcp 80`                     | Show process using TCP port 80                | `fuser -n tcp 80`                     |
| `ss -tunapl`                          | Detailed socket statistics                    | `ss -tunapl`                          |
| `tcpdump -i eth0 -w capture.pcap`     | Capture traffic to file                       | `tcpdump -i eth0 -w capture.pcap`     |
| `tcpdump -A -s0 'tcp port 80'`        | View HTTP traffic in ASCII                    | `tcpdump -A -s0 'tcp port 80'`        |
| `sysctl -a`                           | Show all kernel parameters                    | `sysctl -a                            | grep net.ipv4` |
| `sysctl -w parameter=value`           | Set kernel parameter                          | `sysctl -w net.ipv4.ip_forward=1`     |
| `perf top`                            | System-wide performance analysis              | `perf top`                            |
| `iotop`                               | Monitor disk I/O                              | `iotop`                               |
| `lshw -short`                         | Brief hardware listing                        | `lshw -short`                         |

## Performance Monitoring

| Command                             | Description                                | Example Usage                                                                |
| ----------------------------------- | ------------------------------------------ | ---------------------------------------------------------------------------- | --------- |
| `vmstat 1`                          | Virtual memory statistics every second     | `vmstat 1`                                                                   |
| `vmstat -a`                         | Active/inactive memory                     | `vmstat -a`                                                                  |
| `vmstat -d`                         | Disk statistics                            | `vmstat -d`                                                                  |
| `vmstat -s`                         | Memory statistics                          | `vmstat -s`                                                                  |
| `mpstat -P ALL 1`                   | CPU usage by processor                     | `mpstat -P ALL 1`                                                            |
| `pidstat 1`                         | Per-process CPU usage                      | `pidstat 1`                                                                  |
| `pidstat -d 1`                      | Per-process I/O usage                      | `pidstat -d 1`                                                               |
| `pidstat -r 1`                      | Per-process memory usage                   | `pidstat -r 1`                                                               |
| `iostat -xz 1`                      | Detailed disk I/O stats                    | `iostat -xz 1`                                                               |
| `iostat -d -p sda 2`                | Partition-specific disk stats              | `iostat -d -p sda 2`                                                         |
| `free -m`                           | Memory usage in MB                         | `free -m`                                                                    |
| `free -g`                           | Memory usage in GB                         | `free -g`                                                                    |
| `free -h`                           | Memory usage in human-readable format      | `free -h`                                                                    |
| `iotop`                             | I/O usage monitor                          | `iotop`                                                                      |
| `iotop -o`                          | Show only processes with I/O activity      | `iotop -o`                                                                   |
| `iftop`                             | Network bandwidth monitor                  | `iftop -i eth0`                                                              |
| `nethogs`                           | Net bandwidth by process                   | `nethogs eth0`                                                               |
| `atop`                              | Advanced system & process monitor          | `atop`                                                                       |
| `htop`                              | Interactive process viewer                 | `htop`                                                                       |
| `glances`                           | Cross-platform monitoring tool             | `glances`                                                                    |
| `btop`                              | Resource monitor with usage graphs         | `btop`                                                                       |
| `nmon`                              | Performance Monitor                        | `nmon`                                                                       |
| `collectl`                          | All-in-one performance monitoring          | `collectl`                                                                   |
| `netdata`                           | Real-time performance monitoring           | `netdata`                                                                    |
| `sar`                               | System activity reporter                   | `sar`                                                                        |
| `uptime`                            | Show load average                          | `uptime`                                                                     |
| `w`                                 | Show logged in users and load              | `w`                                                                          |
| `ps aux --sort=-%cpu`               | Sort processes by CPU usage                | `ps aux --sort=-%cpu                                                         | head -10` |
| `ps aux --sort=-%mem`               | Sort processes by memory usage             | `ps aux --sort=-%mem                                                         | head -10` |
| `watch -n 1 'cat /proc/interrupts'` | Watch hardware interrupts                  | `watch -n 1 'cat /proc/interrupts'`                                          |
| `watch -n 1 'cat /proc/meminfo'`    | Watch memory information                   | `watch -n 1 'cat /proc/meminfo'`                                             |
| `watch -n 1 'cat /proc/net/dev'`    | Watch network traffic                      | `watch -n 1 'cat /proc/net/dev'`                                             |
| `watch -n 1 'df -h'`                | Watch disk usage                           | `watch -n 1 'df -h'`                                                         |
| `ioping -c 10 /`                    | I/O latency test                           | `ioping -c 10 /var`                                                          |
| `fio`                               | Flexible I/O tester                        | `fio --name=test --filename=test --bs=4k --direct=1 --rw=randread --size=1G` |
| `stress-ng`                         | System stress tester                       | `stress-ng --cpu 4 --io 2 --vm 1 --vm-bytes 1G --timeout 60s`                |
| `stress`                            | Workload generator                         | `stress --cpu 8 --io 4 --vm 2 --vm-bytes 128M --timeout 60s`                 |
| `sysstat`                           | Collection of performance monitoring tools | `apt install sysstat`                                                        |

## Manual Pages & Help Commands

| Command               | Description                         | Example Usage           |
| --------------------- | ----------------------------------- | ----------------------- | ---------- | ------------------ |
| `man command`         | Display manual page                 | `man ls`                |
| `man -k keyword`      | Search manpages for keyword         | `man -k partition`      |
| `man -f command`      | Same as whatis                      | `man -f ls`             |
| `man -K keyword`      | Search all manpages for keyword     | `man -K resize`         |
| `man -t command \| ps2pdf - > command.pdf` | Convert man page to PDF | `man -t ls \| ps2pdf - > ls.pdf` |
| `man section command` | View specific manual section        | `man 5 passwd`          |
| `man -w command`      | Show manual file location           | `man -w ls`             |
| `info command`        | Display info documentation          | `info ls`               |
| `apropos keyword`     | Search manpages for keyword         | `apropos partition`     |
| `whatis command`      | Display one-line manual description | `whatis grep`           |
| `command --help`      | Display command help                | `ls --help`             |
| `help builtin`        | Help for bash builtin               | `help cd`               |
| `pinfo command`       | Improved info reader                | `pinfo bash`            |
| `tldr command`        | Simplified man pages                | `tldr tar`              |
| `cheat command`       | Create/view cheatsheets             | `cheat tar`             |

## Configuration Management and Deployment

| Command                          | Description                   | Example Usage                                |
| -------------------------------- | ----------------------------- | -------------------------------------------- |
| `ansible host -m ping`           | Run Ansible ping module       | `ansible webservers -m ping`                 |
| `ansible-playbook playbook.yml`  | Run Ansible playbook          | `ansible-playbook deploy.yml`                |
| `ansible-vault encrypt file.yml` | Encrypt sensitive files       | `ansible-vault encrypt secrets.yml`          |
| `puppet agent --test`            | Run Puppet agent in test mode | `puppet agent --test`                        |
| `puppet apply manifest.pp`       | Apply Puppet manifest         | `puppet apply site.pp`                       |
| `chef-client`                    | Run Chef client               | `chef-client`                                |
| `knife node list`                | List Chef nodes               | `knife node list`                            |
| `git clone repository`           | Clone git repository          | `git clone https://github.com/user/repo.git` |
| `git pull`                       | Pull latest changes           | `git pull origin main`                       |
| `git status`                     | Show working tree status      | `git status`                                 |
| `git add file`                   | Add file to staging           | `git add config.conf`                        |
| `git commit -m "message"`        | Commit changes                | `git commit -m "Update config"`              |
| `git push`                       | Push changes to remote        | `git push origin main`                       |
| `git log`                        | View commit history           | `git log`                                    |
| `git diff`                       | Show changes                  | `git diff`                                   |
| `git branch`                     | List branches                 | `git branch`                                 |
| `terraform init`                 | Initialize Terraform          | `terraform init`                             |
| `terraform plan`                 | Preview changes               | `terraform plan`                             |
| `terraform apply`                | Apply changes                 | `terraform apply`                            |
| `docker ps`                      | List containers               | `docker ps`                                  |
| `docker images`                  | List images                   | `docker images`                              |
| `docker build -t name .`         | Build image                   | `docker build -t myapp .`                    |
| `docker run image`               | Run container                 | `docker run nginx`                           |
| `docker-compose up`              | Start services                | `docker-compose up -d`                       |
| `podman ps`                      | List containers (Podman)      | `podman ps`                                  |
| `podman build`                   | Build image (Podman)          | `podman build -t myapp .`                    |

## OpenShift Container Platform

### Basic OpenShift Commands

| Command                          | Description                   | Example Usage                                |
| -------------------------------- | ----------------------------- | -------------------------------------------- |
| `oc login`                       | Log in to OpenShift cluster   | `oc login https://api.cluster.com:6443` |
| `oc login --token=TOKEN`         | Log in using token            | `oc login --token=sha256~abc123 --server=https://api.cluster.com:6443` |
| `oc whoami`                      | Show current user             | `oc whoami` |
| `oc whoami -t`                   | Show current user's token     | `oc whoami -t` |
| `oc config current-context`      | Show current context          | `oc config current-context` |
| `oc config get-contexts`         | List all contexts             | `oc config get-contexts` |
| `oc config use-context`          | Switch context                | `oc config use-context dev-cluster` |
| `oc logout`                      | Log out from OpenShift        | `oc logout` |
| `oc version`                     | Show OpenShift and client version | `oc version` |
| `oc api-resources`               | List all API resources        | `oc api-resources` |
| `oc api-versions`                | List all API versions         | `oc api-versions` |

### Cluster Health and Status

| Command                          | Description                   | Example Usage                                |
| -------------------------------- | ----------------------------- | -------------------------------------------- |
| `oc status` | Show overview of current project | `oc status` |
| `oc get nodes` | List all nodes | `oc get nodes` |
| `oc get nodes -o wide` | List nodes with additional info | `oc get nodes -o wide` |
| `oc describe node` | Describe node details | `oc describe node worker-1` |
| `oc get clusterversion` | Show cluster version | `oc get clusterversion` |
| `oc get clusteroperators` | Show cluster operator status | `oc get clusteroperators` |
| `oc get co` | Short form for cluster operators | `oc get co` |
| `oc describe co operator-name` | Describe cluster operator | `oc describe co ingress` |
| `oc adm node-logs node` | Get node logs | `oc adm node-logs worker-1` |
| `oc adm node-logs -u kubelet node` | Get kubelet logs for node | `oc adm node-logs -u kubelet worker-1` |
| `oc get events --sort-by=.metadata.creationTimestamp` | Show events sorted by time | `oc get events --sort-by=.metadata.creationTimestamp` |
| `oc get events --field-selector type=Warning` | Show only warning events | `oc get events --field-selector type=Warning` |

### Project/Namespace Management

| Command                          | Description                   | Example Usage                                |
| -------------------------------- | ----------------------------- | -------------------------------------------- |
| `oc projects` | List all accessible projects | `oc projects` |
| `oc project` | Show current project | `oc project` |
| `oc project project-name` | Switch to project | `oc project myapp-dev` |
| `oc new-project` | Create new project | `oc new-project myapp-prod --description="Production environment"` |
| `oc delete project` | Delete project | `oc delete project old-project` |
| `oc get namespaces` | List all namespaces | `oc get namespaces` |
| `oc describe project` | Describe project details | `oc describe project myapp-dev` |
| `oc get limits` | Show resource limits | `oc get limits` |
| `oc get quota` | Show resource quotas | `oc get quota` |
| `oc describe quota` | Describe resource quota | `oc describe quota compute-quota` |

### Pod Management and Troubleshooting

| Command                          | Description                   | Example Usage                                |
| -------------------------------- | ----------------------------- | -------------------------------------------- |
| `oc get pods` | List pods in current project | `oc get pods` |
| `oc get pods -o wide` | List pods with node info | `oc get pods -o wide` |
| `oc get pods --all-namespaces` | List pods across all namespaces | `oc get pods --all-namespaces` |
| `oc get pods -A` | Short form for all namespaces | `oc get pods -A` |
| `oc get pods --field-selector status.phase=Running` | Filter pods by status | `oc get pods --field-selector status.phase=Running` |
| `oc get pods --selector app=myapp` | Filter pods by label | `oc get pods --selector app=myapp` |
| `oc get pods -l app=myapp` | Short form for label selector | `oc get pods -l app=myapp` |
| `oc describe pod` | Describe pod details | `oc describe pod myapp-1-abc123` |
| `oc logs pod-name` | Show pod logs | `oc logs myapp-1-abc123` |
| `oc logs -f pod-name` | Follow pod logs | `oc logs -f myapp-1-abc123` |
| `oc logs pod-name -c container` | Logs from specific container | `oc logs myapp-1-abc123 -c sidecar` |
| `oc logs pod-name --previous` | Show previous container logs | `oc logs myapp-1-abc123 --previous` |
| `oc logs pod-name --since=1h` | Show logs from last hour | `oc logs myapp-1-abc123 --since=1h` |
| `oc logs pod-name --tail=100` | Show last 100 log lines | `oc logs myapp-1-abc123 --tail=100` |
| `oc exec pod-name -- command` | Execute command in pod | `oc exec myapp-1-abc123 -- ls /app` |
| `oc exec -it pod-name -- /bin/bash` | Interactive shell in pod | `oc exec -it myapp-1-abc123 -- /bin/bash` |
| `oc exec -it pod-name -c container -- /bin/bash` | Shell in specific container | `oc exec -it myapp-1-abc123 -c app -- /bin/bash` |
| `oc port-forward pod-name local:remote` | Forward port from pod | `oc port-forward myapp-1-abc123 8080:8080` |
| `oc delete pod` | Delete pod | `oc delete pod myapp-1-abc123` |
| `oc get pod -o yaml` | Get pod definition in YAML | `oc get pod myapp-1-abc123 -o yaml` |
| `oc get pod -o json` | Get pod definition in JSON | `oc get pod myapp-1-abc123 -o json` |

### Service and Route Management

| Command                          | Description                   | Example Usage                                |
| -------------------------------- | ----------------------------- | -------------------------------------------- |
| `oc get services` | List services | `oc get services` |
| `oc get svc` | Short form for services | `oc get svc` |
| `oc describe service` | Describe service | `oc describe service myapp-service` |
| `oc expose service` | Create route for service | `oc expose service myapp-service` |
| `oc get routes` | List routes | `oc get routes` |
| `oc describe route` | Describe route | `oc describe route myapp-route` |
| `oc delete route` | Delete route | `oc delete route myapp-route` |
| `oc get endpoints` | Show service endpoints | `oc get endpoints` |
| `oc get ep` | Short form for endpoints | `oc get ep` |
| `oc port-forward service/name local:remote` | Forward port from service | `oc port-forward service/myapp 8080:80` |

### Deployment and Application Management

| Command                          | Description                   | Example Usage                                |
| -------------------------------- | ----------------------------- | -------------------------------------------- |
| `oc get deployments` | List deployments | `oc get deployments` |
| `oc get deploy` | Short form for deployments | `oc get deploy` |
| `oc get dc` | List deployment configs | `oc get dc` |
| `oc describe deployment` | Describe deployment | `oc describe deployment myapp` |
| `oc describe dc` | Describe deployment config | `oc describe dc myapp` |
| `oc rollout status deployment` | Check rollout status | `oc rollout status deployment/myapp` |
| `oc rollout history deployment` | Show rollout history | `oc rollout history deployment/myapp` |
| `oc rollout undo deployment` | Rollback deployment | `oc rollout undo deployment/myapp` |
| `oc rollout restart deployment` | Restart deployment | `oc rollout restart deployment/myapp` |
| `oc scale deployment --replicas=5` | Scale deployment | `oc scale deployment myapp --replicas=5` |
| `oc scale dc --replicas=3` | Scale deployment config | `oc scale dc myapp --replicas=3` |
| `oc autoscale deployment --min=2 --max=10` | Create horizontal pod autoscaler | `oc autoscale deployment myapp --min=2 --max=10 --cpu-percent=80` |
| `oc get hpa` | List horizontal pod autoscalers | `oc get hpa` |
| `oc get replicasets` | List replica sets | `oc get replicasets` |
| `oc get rs` | Short form for replica sets | `oc get rs` |
| `oc new-app` | Create new application | `oc new-app nginx:latest` |
| `oc new-app --name=myapp` | Create app with specific name | `oc new-app --name=myapp https://github.com/user/repo.git` |

### ConfigMaps and Secrets

| Command                          | Description                   | Example Usage                                |
| -------------------------------- | ----------------------------- | -------------------------------------------- |
| `oc get configmaps` | List config maps | `oc get configmaps` |
| `oc get cm` | Short form for config maps | `oc get cm` |
| `oc describe configmap` | Describe config map | `oc describe configmap app-config` |
| `oc create configmap --from-file` | Create config map from file | `oc create configmap app-config --from-file=config.properties` |
| `oc create configmap --from-literal` | Create config map from literal | `oc create configmap app-config --from-literal=key1=value1` |
| `oc get secrets` | List secrets | `oc get secrets` |
| `oc describe secret` | Describe secret | `oc describe secret mysecret` |
| `oc create secret generic` | Create generic secret | `oc create secret generic mysecret --from-literal=username=admin` |
| `oc create secret docker-registry` | Create docker registry secret | `oc create secret docker-registry regcred --docker-server=registry.com --docker-username=user` |
| `oc extract secret/name --to=.` | Extract secret to files | `oc extract secret/mysecret --to=.` |

### Storage and Persistent Volumes

| Command                          | Description                   | Example Usage                                |
| -------------------------------- | ----------------------------- | -------------------------------------------- |
| `oc get pv` | List persistent volumes | `oc get pv` |
| `oc get pvc` | List persistent volume claims | `oc get pvc` |
| `oc describe pv` | Describe persistent volume | `oc describe pv pv-001` |
| `oc describe pvc` | Describe persistent volume claim | `oc describe pvc data-claim` |
| `oc get storageclass` | List storage classes | `oc get storageclass` |
| `oc get sc` | Short form for storage classes | `oc get sc` |

### Security and RBAC

| Command                          | Description                   | Example Usage                                |
| -------------------------------- | ----------------------------- | -------------------------------------------- |
| `oc get sa` | List service accounts | `oc get sa` |
| `oc get serviceaccounts` | List service accounts (full) | `oc get serviceaccounts` |
| `oc describe sa` | Describe service account | `oc describe sa default` |
| `oc get rolebindings` | List role bindings | `oc get rolebindings` |
| `oc get clusterrolebindings` | List cluster role bindings | `oc get clusterrolebindings` |
| `oc get roles` | List roles | `oc get roles` |
| `oc get clusterroles` | List cluster roles | `oc get clusterroles` |
| `oc describe rolebinding` | Describe role binding | `oc describe rolebinding admin` |
| `oc policy add-role-to-user` | Add role to user | `oc policy add-role-to-user edit developer` |
| `oc policy remove-role-from-user` | Remove role from user | `oc policy remove-role-from-user edit developer` |
| `oc auth can-i` | Check permissions | `oc auth can-i create pods` |
| `oc auth can-i --list` | List allowed actions | `oc auth can-i --list` |
| `oc get scc` | List security context constraints | `oc get scc` |
| `oc describe scc` | Describe security context constraint | `oc describe scc restricted` |

### Image Management

| Command                          | Description                   | Example Usage                                |
| -------------------------------- | ----------------------------- | -------------------------------------------- |
| `oc get images` | List images | `oc get images` |
| `oc get imagestreams` | List image streams | `oc get imagestreams` |
| `oc get is` | Short form for image streams | `oc get is` |
| `oc describe imagestream` | Describe image stream | `oc describe imagestream myapp` |
| `oc tag` | Tag image | `oc tag myapp:latest myapp:stable` |
| `oc import-image` | Import image | `oc import-image myapp --from=registry.com/myapp:latest` |
| `oc get imagestreamtags` | List image stream tags | `oc get imagestreamtags` |

### Build Management

| Command                          | Description                   | Example Usage                                |
| -------------------------------- | ----------------------------- | -------------------------------------------- |
| `oc get builds` | List builds | `oc get builds` |
| `oc get buildconfigs` | List build configs | `oc get buildconfigs` |
| `oc get bc` | Short form for build configs | `oc get bc` |
| `oc describe build` | Describe build | `oc describe build myapp-1` |
| `oc describe buildconfig` | Describe build config | `oc describe buildconfig myapp` |
| `oc start-build` | Start new build | `oc start-build myapp` |
| `oc start-build --from-dir=.` | Build from local directory | `oc start-build myapp --from-dir=.` |
| `oc logs build/name` | Show build logs | `oc logs build/myapp-1` |
| `oc logs -f bc/name` | Follow build config logs | `oc logs -f bc/myapp` |
| `oc cancel-build` | Cancel build | `oc cancel-build myapp-1` |

### Monitoring and Metrics

| Command                          | Description                   | Example Usage                                |
| -------------------------------- | ----------------------------- | -------------------------------------------- |
| `oc adm top nodes` | Show node resource usage | `oc adm top nodes` |
| `oc adm top pods` | Show pod resource usage | `oc adm top pods` |
| `oc adm top pods --containers` | Show container resource usage | `oc adm top pods --containers` |
| `oc get --raw /metrics` | Get cluster metrics | `oc get --raw /metrics` |
| `oc get --raw /api/v1/nodes/node-name/proxy/metrics` | Get node metrics | `oc get --raw /api/v1/nodes/worker-1/proxy/metrics` |

### Troubleshooting Commands

| Command                          | Description                   | Example Usage                                |
| -------------------------------- | ----------------------------- | -------------------------------------------- |
| `oc debug node/name` | Debug node | `oc debug node/worker-1` |
| `oc debug pod/name` | Debug pod | `oc debug pod/myapp-1-abc123` |
| `oc debug deployment/name` | Debug deployment | `oc debug deployment/myapp` |
| `oc rsh pod-name` | Remote shell to pod | `oc rsh myapp-1-abc123` |
| `oc rsync pod-name:remote local` | Sync files from pod | `oc rsync myapp-1-abc123:/app/logs ./logs` |
| `oc rsync local pod-name:remote` | Sync files to pod | `oc rsync ./config myapp-1-abc123:/app/config` |
| `oc get events --sort-by='.lastTimestamp'` | Show recent events | `oc get events --sort-by='.lastTimestamp'` |
| `oc get pods --field-selector status.phase=Pending` | Find pending pods | `oc get pods --field-selector status.phase=Pending` |
| `oc get pods --field-selector status.phase=Failed` | Find failed pods | `oc get pods --field-selector status.phase=Failed` |
| `oc describe pod pod-name \| grep -A 10 Events` | Show pod events | `oc describe pod myapp-1-abc123 \| grep -A 10 Events` |

### Administrative Commands

| Command                          | Description                   | Example Usage                                |
| -------------------------------- | ----------------------------- | -------------------------------------------- |
| `oc adm must-gather` | Collect cluster data for support | `oc adm must-gather` |
| `oc adm inspect` | Inspect cluster resources | `oc adm inspect ns/myproject` |
| `oc adm policy` | Manage authorization policies | `oc adm policy add-cluster-role-to-user cluster-admin user` |
| `oc adm groups` | Manage user groups | `oc adm groups new developers` |
| `oc adm prune` | Clean up resources | `oc adm prune images --keep-tag-revisions=3` |
| `oc adm cordon node` | Mark node as unschedulable | `oc adm cordon worker-1` |
| `oc adm uncordon node` | Mark node as schedulable | `oc adm uncordon worker-1` |
| `oc adm drain node` | Drain node for maintenance | `oc adm drain worker-1 --ignore-daemonsets` |

### Certificate Management

| Command                          | Description                   | Example Usage                                |
| -------------------------------- | ----------------------------- | -------------------------------------------- |
| `oc get csr` | List certificate signing requests | `oc get csr` |
| `oc describe csr` | Describe certificate signing request | `oc describe csr csr-abc123` |
| `oc adm certificate approve` | Approve certificate signing request | `oc adm certificate approve csr-abc123` |
| `oc adm certificate deny` | Deny certificate signing request | `oc adm certificate deny csr-abc123` |
| `oc delete csr` | Delete certificate signing request | `oc delete csr csr-abc123` |
| `oc get csr --field-selector spec.signerName=kubernetes.io/kubelet-serving` | Filter CSRs by signer | `oc get csr --field-selector spec.signerName=kubernetes.io/kubelet-serving` |
| `oc get csr -o jsonpath='{.items[?(@.status.conditions[0].type=="Pending")].metadata.name}'` | List pending CSRs | `oc get csr -o jsonpath='{.items[?(@.status.conditions[0].type=="Pending")].metadata.name}'` |

### Output Formatting

| Command                          | Description                   | Example Usage                                |
| -------------------------------- | ----------------------------- | -------------------------------------------- |
| `oc get pods -o wide` | Wide output format | `oc get pods -o wide` |
| `oc get pods -o yaml` | YAML output format | `oc get pods -o yaml` |
| `oc get pods -o json` | JSON output format | `oc get pods -o json` |
| `oc get pods -o jsonpath='{.items[*].metadata.name}'` | JSONPath output | `oc get pods -o jsonpath='{.items[*].metadata.name}'` |
| `oc get pods -o custom-columns=NAME:.metadata.name,STATUS:.status.phase` | Custom columns | `oc get pods -o custom-columns=NAME:.metadata.name,STATUS:.status.phase` |
| `oc get pods --show-labels` | Show labels | `oc get pods --show-labels` |
| `oc get pods --no-headers` | Suppress headers | `oc get pods --no-headers` |

### Resource Management

| Command                          | Description                   | Example Usage                                |
| -------------------------------- | ----------------------------- | -------------------------------------------- |
| `oc apply -f file.yaml` | Apply configuration from file | `oc apply -f deployment.yaml` |
| `oc create -f file.yaml` | Create resource from file | `oc create -f service.yaml` |
| `oc replace -f file.yaml` | Replace resource from file | `oc replace -f configmap.yaml` |
| `oc delete -f file.yaml` | Delete resource from file | `oc delete -f deployment.yaml` |
| `oc edit` | Edit resource | `oc edit deployment myapp` |
| `oc explain` | Show resource documentation | `oc explain pod.spec.containers` |
| `oc wait` | Wait for condition | `oc wait --for=condition=available deployment/myapp` |
| `oc wait --for=delete` | Wait for resource deletion | `oc wait --for=delete pod/myapp-1-abc123` |

### Miscellaneous Commands

| Command                          | Description                   | Example Usage                                |
| -------------------------------- | ----------------------------- | -------------------------------------------- |
| `oc patch` | Update resource using patch | `oc patch deployment myapp -p '{"spec":{"replicas":3}}'` |
| `oc label` | Add/update labels | `oc label pod myapp-1-abc123 env=production` |
| `oc annotate` | Add/update annotations | `oc annotate pod myapp-1-abc123 description="Main application pod"` |
