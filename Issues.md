# Linux Command Reference for Manjaro

**Date**: October 21, 2025  
**Distribution**: Manjaro Linux (Arch-based)

This guide organizes essential Linux commands by functionality, providing syntax, descriptions, and examples for quick reference.

---

## System Administration
1. **sudo**: Execute a command with superuser privileges.
   - Syntax: `sudo <command>`
   - Example: `sudo whoami`  
     *Output*: `root`

2. **su**: Switch to another user (default: root).
   - Syntax: `su`
   - Example: `su`

3. **su -**: Switch to root with root’s environment.
   - Syntax: `su -`
   - Example: `su -`

4. **Change Ownership**: Modify ownership of a directory (e.g., root folder).
   - Syntax: `sudo chown -R $USER:$USER <directory>`
   - Example: `sudo chown -R $USER:$USER /`  
     *Warning*: Use cautiously; changing `/` ownership can break system permissions.

5. **Update System**: Update all packages on Manjaro.
   - Syntax: `sudo pacman -Syu`
   - Example: `sudo pacman -Syu`

6. **Reboot**: Restart the system.
   - Syntax: `reboot`
   - Example: `reboot`

7. **Power Off**: Shut down the system.
   - Syntax: `poweroff`
   - Example: `poweroff`

8. **Sync**: Flush file system buffers to disk.
   - Syntax: `sync`
   - Example: `sync`

---

## File and Directory Management
9. **ls**: List files and directories.
   - Syntax: `ls [options]`
   - Options:
     - `-a`: Show hidden files.
     - `-l`: Show detailed listing (permissions, owner, etc.).
     - `-hs`: Show sizes in human-readable format.
     - `-hsl`: Combine detailed listing with human-readable sizes.
   - Examples:
     - `ls`
     - `ls -a`
     - `ls -hsl`

10. **pwd**: Display the current working directory.
    - Syntax: `pwd`
    - Example: `pwd`  
      *Output*: `/home/user`

11. **cd**: Change directory.
    - Syntax: `cd <directory>`
    - Examples:
      - `cd Desktop`: Move to Desktop.
      - `cd ..`: Move up one directory.
      - `cd ~`: Move to home directory.

12. **cp**: Copy files or directories.
    - Syntax: `sudo cp -r <source> <destination>`
    - Example: `sudo cp -r LOGIN/ /opt/lampp/htdocs/`

13. **rm**: Remove files or directories.
    - Syntax: `rm [options] <file1> <file2>`
    - Options:
      - `-i`: Prompt before deletion (safer).
      - `-r`: Recursive deletion (for directories).
      - `-f`: Force deletion without prompts.
    - Example: `rm -i file.txt`  
      *Warning*: Avoid `rm -rf` unless necessary to prevent data loss.

---

## File Content Operations
14. **echo**: Display text or write to a file.
    - Syntax: `echo "<text>" [> or >>] <file>`
    - Examples:
      - `echo "Manjaro Linux"`: Print to terminal.
      - `echo "Basic commands" > file.txt`: Create/overwrite file.
      - `echo "Add this line" >> file.txt`: Append to file.
      - `echo "Overwritten content" > file.txt`: Overwrite file.

15. **cat**: Display entire file content.
    - Syntax: `cat <file>`
    - Example: `cat test.txt`

16. **head**: Display the first 10 lines (or specified number).
    - Syntax: `head [-n <number>] <file>`
    - Example: `head -n 2 test.txt`  
      *Output*: First 2 lines.

17. **tail**: Display the last 10 lines (or specified number).
    - Syntax: `tail [-n <number>] <file>`
    - Example: `tail -n 2 test.txt`  
      *Output*: Last 2 lines.

18. **tac**: Display file content in reverse order.
    - Syntax: `tac <file>`
    - Example: `tac test.txt`

19. **base64**: Encode or decode file content.
    - Syntax: `base64 <file> | base64 --decode`
    - Example: `base64 test.txt | base64 --decode`

---

## Package Management
20. **Install Package**: Install software on Manjaro.
    - Syntax: `sudo pacman -S <package_name>`
    - Example: `sudo pacman -S name_soft`

21. **Search Package**: Search for a package in repositories.
    - Syntax: `pacman -Ss <package_name>`
    - Example: `pacman -Ss package_name`

22. **Other Package Managers**:
    - **apt-get**: Package manager for Debian/Ubuntu.
    - **yum**: Package manager for CentOS/RHEL.

---

## Permissions
23. **chmod**: Change file or directory permissions.
    - Syntax: `chmod <permissions> <file>`
    - Examples:
      - `chmod +x file3.txt`: Make file executable for all.
      - `chmod -x file3.txt`: Remove executable permission.
      - `chmod u=rw,g=r,o=r file3.txt`: Set specific permissions (user: read/write, group/others: read).
      - `chmod 755 script.sh`: Owner: rwx, group/others: rx.

24. **ls -l**: View file permissions.
    - Syntax: `ls -l`
    - Example: `ls -l`

---

## Networking
25. **ping**: Test network connectivity.
    - Syntax: `ping <host>`
    - Example: `ping 8.8.8.8`

26. **nmcli**: Display network configuration and status.
    - Syntax: `nmcli`
    - Example: `nmcli`

27. **netstat**: Display network connections (if installed).
    - Syntax: `netstat`
    - Example: `netstat`

28. **wget**: Download files from the internet.
    - Syntax: `wget <url>`
    - Example: `wget https://example.com/file.txt`

---

## Search and Find
29. **find**: Search for files by name or pattern.
    - Syntax: `find . -name "<pattern>"`
    - Examples:
      - `find . -name "*.txt"`: Find all `.txt` files.
      - `find . -name "*example*"`: Find files containing "example".
      - `find . -name "example*"`: Find files starting with "example".

30. **grep**: Search for text patterns in files.
    - Syntax: `grep "<pattern>" <file(s)>`
    - Examples:
      - `grep "text" the_example.txt`: Search for "text" in a file.
      - `grep "text" *.txt`: Search in all `.txt` files.
      - `grep "Text" *.txt`: Case-sensitive search.

---

## Text Processing
31. **gawk (awk)**: Process and manipulate text based on patterns.
    - Syntax: `awk '/regex pattern/{action}' <file>`
    - Example: `awk '/pattern/{print}' input_file.txt`

32. **tee**: Output to terminal and file simultaneously.
    - Syntax: `<command> | tee [options] <file>`
    - Example: `ping 8.8.8.8 | tee -a test_network.txt`

---

## System Information
33. **df**: Display disk space usage.
    - Syntax: `df [-h]`
    - Example: `df -h` (human-readable format)

34. **free**: Show memory usage.
    - Syntax: `free [-h]`
    - Example: `free -h` (human-readable format)

35. **uname**: Display system information.
    - Syntax: `uname [-a]`
    - Example: `uname -a`

36. **whoami**: Show current user’s name.
    - Syntax: `whoami`
    - Example: `whoami`

37. **cal**: Display a calendar.
    - Syntax: `cal`
    - Example: `cal`

---

## Help and Documentation
38. **man**: Display manual pages for a command.
    - Syntax: `man <command>`
    - Example: `man ls`  
      *Note*: Press `q` to exit.

39. **help**: Show help for built-in commands.
    - Syntax: `help`
    - Example: `help`

---

## Archiving
40. **tar**: Create or extract archives.
    - Syntax:
      - Create: `tar -cvf <archive.tar> <file1> <file2>`
      - Extract: `tar -xvf <archive.tar>`
    - Examples:
      - `tar -cvf archive.tar file1 file2`
      - `tar -xvf archive.tar`

---

## Web Server
41. **python3 -m http.server**: Start a simple HTTP server.
    - Syntax: `python3 -m http.server <port>`
    - Example: `python3 -m http.server 8000`  
      *Access*: `http://localhost:8000`

---

## History and Aliases
42. **history**: Display previously executed commands.
    - Syntax: `history`
    - Example: `history`

43. **alias**: Create shortcuts for commands.
    - Syntax: `alias <name>="<command>"`
    - Example: `alias ll="ls -l"`

---

## File Comparison
44. **diff**: Compare two files and show differences.
    - Syntax: `diff <file1> <file2>`
    - Example: `diff file1.txt file2.txt`

45. **cmp**: Check if two files are identical.
    - Syntax: `cmp <file1> <file2>`
    - Example: `cmp file1.txt file2.txt`

---

## Additional Commands
46. **clear**: Clear the terminal screen.
    - Syntax: `clear`
    - Example: `clear`

47. **mv**: Move or rename files/directories.
    - Syntax: `mv <source> <target>`
    - Example: `mv file.txt /path/to/destination/`

---

## Notes
- **Warnings**:
  - Use `rm -rf` and `chown -R` cautiously to avoid data loss or system issues.
  - Prefer `rm -i` for safer file deletion.
- **Manjaro-Specific**: Commands like `pacman` are for Arch-based systems. Use `apt-get` (Debian/Ubuntu) or `yum` (CentOS/RHEL) for other distributions.
- **Resources**: Visit [https://manjaro.org/](https://manjaro.org/) for Manjaro-specific documentation.
- **SuperGrok**: For advanced queries, explore the SuperGrok subscription at [https://x.ai/grok](https://x.ai/grok).

---

This structured list covers all provided commands in a clear, concise format. Let me know if you need further details or additional commands!
