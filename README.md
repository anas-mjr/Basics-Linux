### Linux Commands Questions and Answers:

1. **What does the `grep` command do, and how would you use it to find a specific string in multiple files?**

   `grep` is used to search for a specific pattern of text within files. To find a specific string in multiple files, you can use:

   ```
   grep "pattern" *.txt
   ```

2. **Explain how to find the 10 largest files in a directory.**

   You can use the `du` command combined with `sort` to find the 10 largest files:

   ```
   du -ah /directory_path | sort -rh | head -n 10
   ```

3. **How do you check the current disk space usage on a Linux system?**

   Use the `df` command:

   ```
   df -h
   ```

4. **What command would you use to check active network connections on your system?**

   The `netstat` or `ss` commands can be used to check active connections:

   ```
   netstat -tuln
   ```
   or
   ```
   ss -tuln
   ```

5. **How do you list all currently running processes, and how would you filter them for a specific process name?**

   Use the `ps` command:

   ```
   ps aux | grep process_name
   ```

6. **What is the difference between `cp` and `rsync`? When would you use each?**

   `cp` is used for copying files or directories locally. `rsync` is more powerful and can synchronize files between locations, even remotely, while maintaining attributes and providing incremental copy.

7. **How would you find and kill a process by its name or by a specific port?**

   To find a process by name:

   ```
   pgrep process_name
   ```
   To kill it:

   ```
   pkill process_name
   ```
   To find a process by port:

   ```
   lsof -i :port_number
   ```
   To kill it:

   ```
   kill -9 PID
   ```

8. **How do you change file permissions, and what do `chmod 755` and `chmod 644` mean?**

   `chmod` changes file permissions.

   ```
   chmod 755 filename
   ```
   means the owner can read, write, and execute; others can read and execute.

   ```
   chmod 644 filename
   ```
   means the owner can read and write; others can only read.

9. **What is the difference between `hard link` and `soft link`? How do you create them?**

   A hard link points directly to the file's data on disk, whereas a soft link (symbolic link) points to the filename.

   To create a hard link:

   ```
   ln file link_name
   ```
   To create a soft link:

   ```
   ln -s file link_name
   ```

10. **Explain the difference between `/etc/hosts` and DNS.**

    `/etc/hosts` is a local file that maps hostnames to IP addresses manually. DNS is a distributed system that resolves hostnames to IP addresses over the network.

### Bash Scripting Questions and Answers:

1. **What is the difference between `$*` and `"$@"` in a Bash script?**

   `$*` treats all arguments as a single word, whereas `"$@"` treats each argument as a separate word, preserving spaces.

2. **How would you write a script to check if a directory exists and create it if it does not?**

   ```bash
   #!/bin/bash
   if [ ! -d "/path/to/directory" ]; then
     mkdir -p "/path/to/directory"
   fi
   ```

3. **Explain how you would schedule a script to run every day at midnight using `cron`.**

   Edit the cron jobs using `crontab -e` and add:

   ```
   0 0 * * * /path/to/script.sh
   ```

4. **How do you pass arguments to a Bash script, and how can you access them within the script?**

   Arguments are passed as:

   ```
   ./script.sh arg1 arg2
   ```
   Inside the script, `$1` refers to `arg1`, `$2` to `arg2`, and so on.

5. **How can you use a `for` loop to iterate over all files in a directory?**

   ```bash
   for file in /path/to/directory/*; do
     echo "Processing $file"
   done
   ```

6. **How do you redirect both standard output and standard error to the same file in Bash?**

   Use:

   ```
   command > output.log 2>&1
   ```

7. **What is a shebang (`#!`) and why is it used in Bash scripts?**

   A shebang (`#!`) indicates the interpreter to use for the script. For Bash, it is:

   ```
   #!/bin/bash
   ```

8. **Explain the use of conditional statements (`if-else`) in a Bash script, with an example.**

   ```bash
   #!/bin/bash
   if [ "$1" -gt 10 ]; then
     echo "Argument is greater than 10"
   else
     echo "Argument is 10 or less"
   fi
   ```

9. **How would you extract the filename from a given file path in Bash?**

   Use `basename`:

   ```
   basename /path/to/file.txt
   ```
   will output:

   ```
   file.txt
   ```

10. **What is the difference between `export` and setting a variable without `export` in a script?**

    `export` makes the variable available to child processes, whereas without `export`, the variable is only available in the current shell.

### Additional Topics to Consider:

- **Pipelines:** How do you use `|` to chain multiple commands together?

  You can use `|` to send the output of one command as input to another.

  Example:

  ```
  cat file.txt | grep "pattern"
  ```

- **Awk and Sed:** Basic usage for processing text in files.

  `awk` is used for pattern scanning and processing:

  ```
  awk '{print $1}' file.txt
  ```
  prints the first column.

  `sed` is a stream editor:

  ```
  sed 's/old/new/g' file.txt
  ```
  replaces all occurrences of `old` with `new` in the file.

- **Environment Variables:** How to set and export them, and their significance in Bash.

  Set a variable:

  ```
  VAR=value
  ```
  Export it:

  ```
  export VAR=value
  ```

- **SSH and SCP:** How to securely connect to remote servers and transfer files.

  Use:

  ```
  ssh user@remote_host
  ```
  to connect to a remote server.

  Use:

  ```
  scp file user@remote_host:/path/to/destination
  ```
  to copy a file securely.
