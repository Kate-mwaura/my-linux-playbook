# Linux Command Reference for DevOps Engineers

A personal Linux command reference built throughout my DevOps journey.

Every command in this repository has been studied, tested, and practiced in real Linux environments as I continue developing my skills in DevOps and cloud infrastructure.

This serves as both a learning archive and a long-term reference I will continue building throughout my career..

---

## 📚 Table of Contents

1. [File System Navigation](#1-file-system-navigation)
2. [File Viewing & Inspection](#2-file-viewing--inspection)
3. [Search & Discovery](#3-search--discovery)
4. [Text Processing Power](#4-text-processing-power)
5. [Pipes & Redirection](#5-pipes--redirection)
6. [Permissions & Ownership](#6-permissions--ownership)
7. [Users & Groups](#7-users--groups)
8. [Password & Authentication](#8-password--authentication)
9. [Disk & System Monitoring](#9-disk--system-monitoring)
10. [Process Management](#10-process-management)
11. [Networking](#11-networking)
12. [Archiving & Compression](#12-archiving--compression)
13. [System Information](#13-system-information)
14. [System & Service Management](#14-system--service-management)
15. [Package Management](#15-package-management)

---

## 1. File System Navigation 

| Command | My Definition / Logic | Flag / Example | Flag Definition |
|---|---|---|---|
| `pwd` | print the present working directory where i am right now. | -- | -- |
| `man` | opens the manual documentation for any command. | `man mkdir` | [man mkdir] |
| `ls` | listing the files and directories in a directory. | `ls /path/to/` | |
|  |  | `ls -l` | viewing the list in a (l)long listed format i.e [file size, file ownership, permissions e.t.c] |
|  |  | `ls -a` | viewing (a) all files inclusive of hidden files in the directory. |
|  |  | `ls -la` | viewing the list inclusive of hidden files in a long listed format. |
|  |  | `ls -lh` | viewing the list with the size in a (h) human readable format. |
|  |  | `ls -t` | sort files by time from the newest to the oldest. |
|  |  | `ls -R` | list directories recursively. |
|  |  | `ls -d/f` | list only files or directories. |
| `cd` | change directory from where I am to a new directory. | | |
|  |  | `cd ..` | move one directory up |
|  |  | `cd ~` | go to home directory |
|  |  | `cd -` | go to previous directory |
|  |  | `cd /` | go to root directory |
| `mkdir` | make a new directory. | `mkdir -p` | creating a directory from a parent dir. [ mkdir -p /home/script/{dir1,dir2,dir3} ] |
| `touch` | creating a new file. | `touch log{1..10}.log` | creating multiple files |
| `cp` | copying files from one location to another. | `cp -r` | copying all files from a directory to another recursively. |
|  |  | `cp -v` | verbose output (shows what is being copied). |
|  |  | `cp dir1/* dir2` | copying only files from one directory to another. |
| `mv` | moving a file or directory from one dir to another | `mv file.txt path/to/move.` | |
| `mv` | renaming a file or a directory | `mv old.name new.name.` | |
|  |  | `mv -v` | shows files being moved. |
| `rm` | removing a file or directory. | | |
|  |  | `rm -r` | removing a directory and all the files in it (r)recursively. |
|  |  | `rm -f` | removing a file by (f) forcefully. |
|  |  | `rm -rf` | force delete directories recursively without confirmation. [⚠⚠Cautious with this one] |
<p align="right"><a href="#kathys-linux-command-reference-for-devops">⬆ Back to Top</a></p>
---

## 2. File Viewing & Inspection

| Command | My Definition / Logic | Flag / Example | Flag Definition |
|---|---|---|---|
| `cat` | cat [concatenate]→ show the content of a file. | `cat filex.txt` | |
|  |  | `cat -n` | print the content of a file and (n)numbering the lines in the file. |
|  |  | `cat file1 file2` | display multiple files. |
| `less` | print the context of a large file one page at a time. | `less -N` | print the file content on a single screen and number the lines. |
|  |  | `n/enter` | next line |
|  |  | `:b` | back to previous page |
|  |  | `space/pgUp/pgDn` | navigate the file pages |
|  |  | `q` | quit. |
| `more` | print file content in a page at a time unlike less no chance to move back just next. | `more +10 file.txt` | start at line 10. |
| `head` | print the first 10 lines of a file. | `head -n 20` | '-n' allows you to specify the number of lines you want to display from the top. |
|  |  | `head -c 50 file.txt` | first 50 characters. |
|  |  | `head -q file1 file2` | print content for both files. |
| `tail` | print the last 10 lines of a file. | `tail -n 20` | '-n' allows you to specify the number of lines you want to display from the bottom. |
|  |  | `tail -c 100 file.txt` | last 100 characters. |
|  |  | `tail -f server.log` | follow live log. |
| `nl` | print the content of a file and (n)number (l)lines in the file as output. | `nl -b a` | number all lines in a file. |
|  |  | `nl -b t` | number non-empty lines in a file. |
| `wc` | print the number of lines, number of words and number of characters in a file. | `wc -l` | print the number of (l)lines only in a file. |
|  |  | `wc -w` | print the number of (w) in the file. |
|  |  | `wc -c` | print the number of (c) characters/letters in a file. |
<p align="right"><a href="#kathys-linux-command-reference-for-devops">⬆ Back to Top</a></p>
---

## 3. Search & Discovery

| Command | My Definition / Logic | Flag / Example | Flag Definition |
|---|---|---|---|
| `grep` | search for a specific pattern in a file. |  |  |
|  |  | `grep -v` | search a pattern in a file and exclude it in the output. |
|  |  | `grep -i` | search for a pattern and ignore the case. |
|  |  | `grep -n` | search a pattern and print the output with numbered lines. |
|  |  | `grep -r` | search a pattern in the entire directory and all directories and files in it (r) recursively. |
|  |  | `grep -c` | count the matches. |
|  |  | `grep -l` | show files containing matches. |
|  |  | `grep -E "word1\|word2\|word3" file_name` | search either of the words. |
|  |  | `grep "word1" \| grep "word2"` | Only shows lines that have BOTH keywords. |
|  |  | `grep -e "word1" -e "word 2" file_name` | finds lines containing "word1" OR "word2" |
|  |  | `grep -f file_input.txt search_file` | using a file with all the list of words to search |
| `find` | search for a pattern in the system |  |  |
|  |  | `find /path/ -name (name)` | search by name |
|  |  | `find /path/ -type (f/d)` | search by type file or directory |
|  |  | `find /path -size` | search by size |
|  |  | `find /path -iname` | search by name and ignore the case. |
|  |  | `find /path/ -mtime` | search by modification time |
|  |  | `find /path/ -type (f/d) -name  …. '-exec' command {}+` | finding a file or directory and executing commands to the output. |
|  |  | `-size unit & suffix` | c=bytes M=megabytes k=kilobytes G=gigabytes b=blocks |
| `locate` | search the location of a file in the system | `locate file.sh` |  |
|  |  | `locate -i` | search file location and ignore case. |
| `which` | search the executable path of a command. |  |  |
| `whereis` | search for a path of a command and returns all relevant paths. |  |  |
| `who -b` | view when the system was started. |  |  |
<p align="right"><a href="#kathys-linux-command-reference-for-devops">⬆ Back to Top</a></p>
---

## 4. Text Processing Power

| Command | My Definition / Logic | Flag / Example | Flag Definition |
|---|---|---|---|
| `sort` | arranging an output in a certain order. |  |  |
|  |  | `sort -n` | sort a file in a (n)numeric order. |
|  |  | `sort -u` | sort a file outputting only the unique lines. |
|  |  | `sort -r` | sort a file in (r)reverse/descending order |
|  |  | `sort -f` | sort a file and ignore the case. |
|  |  | `sort -b` | ignore preceding spaces. |
|  |  | `sort -o [new_output_file] [input_file]` | sort a file and store the output in a specified file. |
| `uniq` | filters identical lines in a file. The uniq command is more powerful combined with the sort command. |  |  |
|  |  | `uniq -c` | count how many times a line has been repeated in a file. |
|  |  | `uniq -d` | show lines that have been repeated. |
|  |  | `uniq -u` | show uniq lines that have appeared only once i.e. have not been repeated. |
|  |  | `uniq -i` | show identical lines and ignore the case. |
| `cut` | cut out specific fields from files. |  |  |
|  |  | `cut -d` | specify a diameter separator [cut -d “:”] |
|  |  | `cut -f` | specify the field to output from a file [cut -f 1,3 or cut -f 1-3] |
|  |  | `cut -c` | outputs specific characters from a file [cut -c 1-5 or cut -c 2,4,7] |
| `tr` | translate characters: run replacements based on single characters and character sets. |  |  |
|  |  | `tr [:lower:] [:upper:]` | changing characters from lowercase to uppercase. |
|  |  | `tr -d` | delete characters [tr -d ‘,’ or for multiple characters tr -d ‘>{};?’ ] |
|  |  | `tr -s` | squeeze characters i.e remove duplicate characters. |
|  |  | `tr “char1” “char2”` | replace characters with different characters. |
| `diff` | highlight the differences between  files. |  |  |
|  |  | `a` | added:: content was added. |
|  |  | `d` | deleted:: content was removed. |
|  |  | `c` | changed:: content was modified. |
|  |  | `<` | less than:: shows lines from the first file. |
|  |  | `>` | greater than:: shows lines from the second file. |
|  |  | `diff [file1] [file2]` | check the difference between the two files. |
|  |  | `diff -s` | check if files are same/identical. |
|  |  | `diff -y` | show the difference side by side. |
|  |  | `diff -i` | ignore case. |
|  |  | `diff -u` | output the difference using the + and - symbols. |
|  |  | `diff -q` | only check if the files differ, not how. |
|  |  | `diff -w` | ignore extra spaces and tabs. |
|  |  | `diff -B` | ignore blank lines. |
| `awk` | awk is a command used to filter and extract a certain column of data from a file | `awk ‘{print $column_no}’ file/path` | This will print words in the third column in a file extracted from every line. |
| `sed` | sed is used to replace a certain word in a file with a new one or remove it completely. Essential for words repeated multiple times in a file. | `sed  -i ‘s/pineapple/mango/’ file/path` | [-i →ensures changes are saved in the file, g(global) |
<p align="right"><a href="#kathys-linux-command-reference-for-devops">⬆ Back to Top</a></p>
---

## 5. Pipes & Redirection

| Command | My Definition / Logic | Flag / Example | Flag Definition |
|---|---|---|---|
| `>` | overwrite everything in the file and add new content | | |
| `>>` | append the file and adds new content below the existing content | | |
| `|` | pass the output of a command to the next command for execution. | | |
| `tee` | redirect the output to a file and print the results on the screen. | | |
|  |  | `tee -a` | append with the file and don't overwrite an existing file |
<p align="right"><a href="#kathys-linux-command-reference-for-devops">⬆ Back to Top</a></p>
---

## 6. Permissions & Ownership

| Command | My Definition / Logic | Flag / Example | Flag Definition |
|---|---|---|---|
| `sudo chown username:groupname filename` | changing the user and group owners of a file. | `sudo chown deploy:devops app.log` | change both user and group owner of a log file used by a deployment process |
| `sudo chown username file_name` | Changing the own user owner of a file. | `sudo chown kathy script.sh` | transfer ownership of a deployment script to a specific user |
| `sudo chgrp groupname file_name` | Changing the group owning a file. | `sudo chgrp developers project.conf` | assign a shared configuration file to the developers group |
| `sudo chmod u+-[r/w/x] filename` | Giving read or write or execute permission to a user for a file. | `sudo chmod u+x deploy.sh` | allow the file owner to execute a deployment script |
| `sudo chmod g+-[r/w/x] filename` | Giving read or write or execute permission to a group for a file. | `sudo chmod g+w shared.log` | allow a team group to write to a shared log file |
| `sudo chmod o+-[r/w/x] filename` | Giving read or write or execute permission to Other Users for a file. | `sudo chmod o-r secrets.env` | prevent other users from reading sensitive environment variables |
| `sudo chmod a+-[r/w/x] filename` | Giving read or write or execute permission to all Users; owner, groups and others for a file. | `sudo chmod a+r public.conf` | allow all users to read a system configuration file |
| `sudo chmod u=,g=rwx,o=x filename` | universally changing all permissions of a file in one command. | `sudo chmod u=,g=rwx,o=x shared_script.sh` | restrict owner permissions while allowing group execution in a shared environment |
| `sudo chmod +t filename` | working in a shared directory (like a folder for a group project) and want users to be able to add files but not delete or change each other's files. | `sudo chmod +t /shared/team_directory` | enable sticky bit so users cannot delete files created by others |
| `umask` | checking the default permission settings of new files and directory. | `umask` | display the default permission mask |
| `umask -S` | checking the default permission settings in human-readable format. | `umask -S` | display the symbolic representation of the default permissions |
<p align="right"><a href="#kathys-linux-command-reference-for-devops">⬆ Back to Top</a></p>
---

## 7. Users & Groups

| Command | My Definition / Logic | Flag / Example | Flag Definition |
|---|---|---|---|
| `cat /etc/passwd` | Viewing all users | `cat /etc/passwd` | display all system users |
| `cat /etc/group` | Viewing all groups | `cat /etc/group` | display all system groups |
| `su - username` | Switching users | `su - deploy` | switch to the deploy user account |
| `sudo adduser/(useradd -m)` | Adding a new user | `sudo adduser devops` | create a new DevOps user account |
| `sudo addgroup/groupadd` | Adding a new group | `sudo groupadd developers` | create a developers group |
| `sudo deluser/userdel` | Deleting a user | `sudo userdel olduser` | remove a user account from the system |
| `sudo delgroup/groupdel` | Deleting a group. | `sudo groupdel oldteam` | remove an unused system group |
| `sudo usermod -u username` | changing the UID of a user. | `sudo usermod -u 1050 deploy` | modify the UID of a deployment user |
| `sudo usermod -d directory/path username` | changing the home location of a user. | `sudo usermod -d /srv/deploy deploy` | change the home directory of a user |
| `sudo usermod -l oldname newname` | changing the username of a user. | `sudo usermod -l devops_engineer devops` | rename a system user |
| `sudo usermod -g groupname username` | Adding user to a new group. | `sudo usermod -g developers kathy` | set the primary group of a user |
| `sudo usermod -G groupname username` | Overwriting users group with current group. | `sudo usermod -G docker deploy` | replace user group memberships |
| `sudo usermod -aG groupname username` | Adding user to an additional group without overwriting the previous group. | `sudo usermod -aG docker kathy` | add a user to the docker group |
| `sudo gpasswd -d username groupname` | Deleting user from a group. | `sudo gpasswd -d deploy docker` | remove user from docker group |
| `sudo setfacl -m u:username:r/w/x /file/path` | set file access control list on files. | `sudo setfacl -m u:nginx:r /var/log/nginx/access.log` | allow nginx user read access to log file |
| `sudo usermod username --shell /bin/bash` | changing user from shell to bash. | `sudo usermod deploy --shell /bin/bash` | assign bash shell to a user |
| `sudo useradd -r accname` | creating a system user. | `sudo useradd -r prometheus` | create system account for a monitoring service |
| `sudo useradd -M username` | creating a user without a home directory. | `sudo useradd -M ci-runner` | create service user without login environment |
| `sudo useradd -s path/nologin username` | creating a non-interactive user. | `sudo useradd -s /usr/sbin/nologin backupsvc` | create non-interactive backup user |
| `sudo useradd -r -M -s /usr/sbin/nologin servicename` | creating a service account. | `sudo useradd -r -M -s /usr/sbin/nologin node_exporter` | create secure service account for monitoring |
<p align="right"><a href="#kathys-linux-command-reference-for-devops">⬆ Back to Top</a></p>
---

## 8. Password & Authentication

| Command | My Definition / Logic | Flag / Example | Flag Definition |
|---|---|---|---|
| `sudo chage -l username` | viewing account passwd aging details list. | `sudo chage -l deploy` | display password aging information for the deploy user |
| `sudo chage -M days username` | setting when a Password expires. | `sudo chage -M 90 deploy` | set password to expire after 90 days |
| `sudo chage -M -1 username` | setting password expiry to never. | `sudo chage -M -1 serviceuser` | disable password expiration for a service account |
| `sudo chage -W days username` | setting number of days of warning before password expires. | `sudo chage -W 7 deploy` | warn the user 7 days before password expiration |
| `sudo chage -m days username` | setting the number of days a user has to wait to change the password again. | `sudo chage -m 2 deploy` | enforce minimum 2 days between password changes |
| `passwd -l username` | Locking a user’s account. | `sudo passwd -l olduser` | lock an inactive user account |
| `passwd -u username` | unlocking a user’s password. | `sudo passwd -u deploy` | unlock a user account |
| `passwd -S username` | viewing passwd status of a  user. | `passwd -S deploy` | show password status information |
| `passwd -x days username` | adding an expiration day to a passwd. | `sudo passwd -x 120 deploy` | set password expiration after 120 days |
| `passwd -d username` | deleting a user's passwd. | `sudo passwd -d tempuser` | remove password requirement from a temporary user |
<p align="right"><a href="#kathys-linux-command-reference-for-devops">⬆ Back to Top</a></p>
---

## 9. Disk & System Monitoring

| Command | My Definition / Logic | Flag / Example | Flag Definition |
|---|---|---|---|
| `du` | estimate and summarize file and directory space usage. | `du /var/log` | estimate disk usage of the /var/log directory |
|  |  | `du -h` | show disk usage in human readable format. |
|  |  | `du -s` | show the total (s)summary disk space in use. |
|  |  | `du -ah` | show (a)all files and directories disk space including hidden files in human readable format. |
|  |  | `du -hs /path/dir1 /path/dir2` | show the disk size of multiple path directories and total size summary. |
|  |  | `du -hsc /path1/ /path2/` | show the disk size of multiple path directories and (c)count the total. |
|  |  | `du -h --max-depth n /path/` | show the disk usage of a directory and its subdirectories to n'th depth. |
|  |  | `du -sh *` | show which directories are consuming most space. |
| `df` | shows the overview of the file system disk space usage. | `df` | show overall disk usage summary |
|  |  | `df -h` | show the file system disk usage report in human-readable format. |
|  |  | `df -T` | show the disk usage report and type of filesystems. |
|  |  | `df -x filesystem` | show disk usage report but exclude this filesystem in the command. |
| `free` | show the memory and swap report in human-readable format. | `free -h` | show memory and swap report |
| `top` | show real-time running processes, their cpu and memory usage. | `top` | display active processes in real time |
|  |  | `M` | Sort processes by Memory usage (useful for finding "memory leaks"). |
|  |  | `P` | Sort processes by CPU usage (the default). |
|  |  | `k` | Kill a process (it will ask you for the Process ID or PID). |
|  |  | `q` | Quit top and return to the terminal. |
| `htop` | show real-time running processes, and their cpu and memory usage in a more advanced way compared to top. In htop you can modify your data appearance, monitor and also manage processes. | `htop` | interactive process viewer |
| `uptime` | show how long the system has been running and load average. | `uptime` | display system running time and load |
|  |  | `uptime -s` | show what time the system was started. |
| `lsblk` | list block devices (disks and partitions) | `lsblk` | display disks and partitions layout |
| `blkid` | list the block devices identity numbers. [UUID] | `blkid` | show UUID of connected block devices |
| `mount` | list mounted devices on the system | `mount` | show mounted file systems |
|  |  | `mount disk_name directory/path` | attaching a device to a directory to be able to input data, view or retrieve data. |
| `umount` | detaching a device from a directory; closing the access loop. | `umount device_name` | unmount a disk device |
| `mkfs` | making a file system for a device e.g. xfs, ext4. | `mkfs -t ext4 /dev/sdb1` | create an ext4 filesystem on a device |
<p align="right"><a href="#kathys-linux-command-reference-for-devops">⬆ Back to Top</a></p>
---

## 10. Process Management

| Command | My Definition / Logic | Flag / Example | Flag Definition |
|---|---|---|---|
| `ps` | show processes in the current shell session. | `ps` | show processes running in the current shell session |
| `pgrep processname` | getting PID of a process. | `pgrep nginx` | get PID of nginx process |
| `pidof (processname)` | getting PID of a process. | `pidof nginx` | get PID of nginx service |
| `ps -l` | view a process list in detail including the PPID and Priority. | `ps -l` | display detailed process information including parent process ID |
| `ps aux` |  | `ps aux` | show all running processes on the system |
|  |  | `a` | Shows processes for all users, not just your current session. |
|  |  | `u` | Displays the output in a user-oriented format, providing detailed info like CPU and Memory usage. |
|  |  | `x` | Includes processes not attached to a terminal (TTY), such as background system daemons like snapfuse or systemd |
|  |  | `ps aux --sort=-%cpu` | show processes in their cpu usage order. |
|  |  | `ps aux --sort=-%mem` | show processes in their memory usage order. |
| `kill` |  | `kill -l` | List of kill commands. |
|  |  | `kill -2 PID [ctrl+z]` | Interrupt process. |
|  |  | `kill -9 PID [ctrl+c]` | force kill process. |
|  |  | `kill -19 PID` | stop/pause process. |
|  |  | `kill -18 PID` | resume stopped process. |
| `pkill` |  | `pkill -9 processname [ctrl+c]` | killing processes by name. |
|  |  | `pkill -9 -u username` | killing all processes being run by a user. |
| `killall` |  | `killall -u username` | killing all processes being run by a user |
| `jobs` | viewing running jobs and the PID. | `jobs` | list background jobs in the shell |
| `bg` | running a process in the background | `bg` | resume a stopped process in the background |
| `fg` | running a process in the foreground. | `fg` | bring background job to foreground |
|  |  | `fg %2` | bringing a background process to the foreground. |
| `nice` | setting the priority number of a new process. | `nice -n 10 command` | start a command with lower CPU priority |
| `nice -n` | setting the (n)nice number of a new process. | `nice -n 5 tar -czf backup.tar.gz /var/www` | run backup with controlled CPU priority |
| `renice` | setting the priority value of an existing process. | `renice 5 1234` | change priority of running process |
|  |  | `sudo renice -n 0 -p PID` | setting the priority and nice value of an existing process referencing the PID of the process. |
<p align="right"><a href="#kathys-linux-command-reference-for-devops">⬆ Back to Top</a></p>
---

## 11. Networking

| Command | My Definition / Logic | Flag / Example | Flag Definition |
|---|---|---|---|
| `ping` | checking the connectivity, reachability & response rate(latency) of a host e.g. server. | `ping -c` | specify the number of ICMP(Internet Control Message protocol) to send to the host. |
|  |  | `ping -i` | sets the wait time between packets sent to the host. |
|  |  | `ping -t` | sets how long to wait for a response before giving up. |
| `curl` | communicating with servers. | `curl -o` | downloading files from the internet. [curl -o filename url] |
|  |  | `curl -I` | requests only for the header of a webpage. |
|  |  | `curl -v` | verbose the output and show the request and response. |
| `wget` | downloads files from a server. | `wget -O` | setting the custom name for a download file. [wget -O customname url] |
|  |  | `wget -P` | setting a (p)path to where you want to store the download file |
|  |  | `wget -c` | (c)continue a download that is incomplete |
|  |  | `wget -i` | download urls contained in a file [wget -i file1.txt] |
|  |  | `wget -b` | set a download to run in the (b) background. |
| `ss` | show socket statistics. | `ss -t` | show all sockets on TCP connection. |
|  |  | `ss -u` | show all sockets on UDP connection. |
|  |  | `ss -s` | show overall statistics of the socket connection. |
|  |  | `ss -l` | show all sockets that are actively listening. |
|  |  | `ss -4` | show all ipv4 sockets. |
|  |  | `ss -6` | show all ipv6 sockets. |
|  |  | `ss --listening src :portno` | check which services are listening to a specific port. |
|  |  | `ss -tulpn` | show listening ports with associated processes. |
| `ip` | show information about the ip addresses connected. | `ip a` | display all network interfaces and IP addresses. |
|  |  | `ip addr show dev [interface_name]` | show info about a specific device. |
|  |  | `sudo ip link set [interface_name] down` | setting a specific interface down. |
|  |  | `sudo ip link set [interface_name] up` | setting a specific interface up. |
|  |  | `sudo ip addr add [ip_no] dev [interface_name]` | adding an ip address to the server. |
|  |  | `sudo ip addr del [ip_no] dev [interface_name]` | removing an ip address from the server. |
|  |  | `ip route show` | print routing table. |
<p align="right"><a href="#kathys-linux-command-reference-for-devops">⬆ Back to Top</a></p>
---

## 12. Archiving & Compression

| Command | My Definition / Logic | Flag / Example | Flag Definition |
|---|---|---|---|
| `tar` | archiving/bundling directories & files together into one single file. | `tar -c` | (c)Create a new archive. |
|  |  | `tar -v` | (v)Verbose :: shows you the list of files being packed. |
|  |  | `tar -x` | Extract the contents :: unarchive a file. |
|  |  | `tar -z` | compress :: create a g[z]ipped archive to make the file smaller. |
|  |  | `tar -f` | (f)File :: tells tar the next word is the name of the file to create. |
|  |  | `tar -t` | view what's inside the archive without having to unarchive it. |
|  |  | `tar -r` | archive a directory recursively including all the subdirectories. |
|  |  | `tar -czvf [new_file_name.tar] [file_to_compress]` | create a compressed tar archive. |
| `gzip` | compressing/uncompressing files N:B Not Folders. | `gzip [file_name]` | compress a file. |
|  |  | `gzip -k [file_name]` | create a compressed file of the file and also (k)keep the original. |
|  |  | `gzip -r [directory_name]` | compress each file in a directory. |
|  |  | `zcat [filename.gz]` | view the content of a zipped file without having to unzip it. |
| `gunzip` | uncompress a file to its original format. | `gunzip [compressed_file_name]` | uncompress a file. |
| `zip` | compress and bundle files or folders into a zip archiver. | `zip [name_of_new_file] [files_to_put_inside]` | compress files into a zip archive. |
|  |  | `zip [path/to/compressed.zip] [path/to/file_or_directory1] [path/to/file_or_directory2 …]` | compress files or directories into a zip archive. |
|  |  | `zip -r [compressed.zip] [folder name]` | zip everything inside the folder. |
|  |  | `zip -e` | prompts you for a password to protect the file |
|  |  | `zip -d [compressed.zip] [file_to_delete]` | Removes a specific file from inside the zip. |
|  |  | `zip -u` | updates by adding new files to an existing zip without recreating it. |
| `unzip` | unzip a zipped archive. | `unzip` | unzip a zipped archive. |
|  |  | `unzip -l` | to list what's inside a file without having to unzip |
<p align="right"><a href="#kathys-linux-command-reference-for-devops">⬆ Back to Top</a></p>
