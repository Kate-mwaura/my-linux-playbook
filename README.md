# Linux Command Reference for DevOps Engineers

A personal Linux command reference built throughout my DevOps journey.

Every command in this repository has been studied, tested, and practiced in real Linux environments as I continue developing my skills in DevOps, system administration, and cloud infrastructure.

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
| `sudo chown username` | Changing the own user owner of a file. | `sudo chown kathy script.sh` | transfer ownership of a deployment script to a specific user |
| `sudo chgrp groupname` | Changing the group owning a file. | `sudo chgrp developers project.conf` | assign a shared configuration file to the developers group |
| `sudo chmod u+-[r/w/x] filename` | Giving read or write or execute permission to a user for a file. | `sudo chmod u+x deploy.sh` | allow the file owner to execute a deployment script |
| `sudo chmod g+-[r/w/x] filename` | Giving read or write or execute permission to a group for a file. | `sudo chmod g+w shared.log` | allow a team group to write to a shared log file |
| `sudo chmod o+-[r/w/x] filename` | Giving read or write or execute permission to Other Users for a file. | `sudo chmod o-r secrets.env` | prevent other users from reading sensitive environment variables |
| `sudo chmod a+-[r/w/x] filename` | Giving read or write or execute permission to all Users, groups and others for a file. | `sudo chmod a+r public.conf` | allow all users to read a system configuration file |
| `sudo chmod u=,g=rwx,o=x filename` | universally changing all permissions of a file in one command. | `sudo chmod u=,g=rwx,o=x shared_script.sh` | restrict owner permissions while allowing group execution in a shared environment |
| `sudo chmod +t filename` | working in a shared directory (like a folder for a group project) and want users to be able to add files but not delete or change each other's files. | `sudo chmod +t /shared/team_directory` | enable sticky bit so users cannot delete files created by others |
| `umask` | checking the default permission settings of new files and directory. | `umask` | display the default permission mask |
| `umask -S` | checking the default permission settings in human-readable format. | `umask -S` | display the symbolic representation of the default permissions |

<p align="right"><a href="#kathys-linux-command-reference-for-devops">⬆ Back to Top</a></p>
