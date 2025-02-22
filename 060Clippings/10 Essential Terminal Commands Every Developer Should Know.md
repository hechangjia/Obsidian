---
title: "10 Essential Terminal Commands Every Developer Should Know"
source: "https://www.trevorlasn.com/blog/10-essential-terminal-commands-every-developer-should-know"
author:
  - "[[Trevor I. Lasn]]"
published: 2024-08-21
created: 2025-02-21
description: "List of useful Unix terminal commands to boost your productivity. Here are some of my favorites."
tags:
  - "clippings"
---
## List of useful Unix terminal commands to boost your productivity. Here are some of my favorites.

Sometimes, tasks that might take hours to code can be accomplished in minutes with the terminal.

This article assumes you’re already comfortable with basic commands like **rm**, **pwd**, and **cd**.

### **grep**

Need to find where a function or variable is used in your codebase, or sift through logs to locate specific entries? grep can help you with that.

The **grep** command searches for specific patterns in files. It’s like having a supercharged search function that digs into file contents.

The basic syntax for the grep command goes as the following;

```expressive
➜ grep "let's find something" file.[txt,json,js,md,etc]
```

**Case-insensitive search:** Add the *\-i* flag to ignore case differences.

```expressive
➜ grep -i "REact" compiler/apps/playground/app/index.tsx? '[DEV] React Compiler Playground': 'React Compiler Playground'
```

**Count occurrences:** Use the *\-c* flag to count the number of matching lines.

```expressive
➜ grep -c "React" compiler/apps/playground/app/index.tsx2
```

**Analyzing logs:** If you’re troubleshooting an issue, you can use grep to find specific error messages in logs.

```expressive
➜ grep -i "Operation not supported on socket" system.log09/24 08:51:01 INFO   :..settcpimage: Get TCP images rc - EDC8112I Operation not supported on socket.
```

**Search for Multiple Patterns:** You can search for multiple patterns by using the **\-e** flag multiple times.

Match either *“error”* or *“404”* in *system.log*.

```expressive
➜ grep -e "error" -e "404" system.lognpm error code E404npm error 404  'trevorlasn.com@*' is not in this registry.npm error A complete log of this run can be found in: /Users/trevorindreklasn/.npm/_logs/2024-08-20T16_41_32_846Z-debug-0.log
```

**Recursive Search:** To search for a pattern in all files within a directory and its subdirectories, use the *\-r* (or —recursive) flag.

```expressive
➜ grep -o -r "fs" node_modules | wc -l22491
```

This will search through all files in the specified directory and its subdirectories. The **\-o** option tells grep to print only the matched parts of the line.

The pipe **|** takes the output from the command on the left (grep) and uses it as input for the command on the right (*wc -l*). **wc -l** counts and displays the number of lines in its input.

### **man**

The man command stands for “manual.” It helps you find detailed information about other commands and programs.

```expressive
➜ man grepNAME     grep, egrep, fgrep, rgrep, bzgrep, bzegrep, bzfgrep, zgrep,     zegrep, zfgrep – file pattern searcherSYNOPSIS     grep [-abcdDEFGHhIiJLlMmnOopqRSsUVvwXxZz] [-A num] [-B num]          [-C num] [-e pattern] [-f file] [--binary-files=value]          [--color[=when]] [--colour[=when]] [--context=num]          [--label] [--line-buffered] [--null] [pattern] [file ...]DESCRIPTION     The grep utility searches any given input files, selecting     lines that match one or more patterns.  By default, a pattern     matches an input line if the regular expression (RE) in the     pattern matches the input line without its trailing newline.     An empty expression matches every line.  Each input line that     matches at least one of the patterns is written to the standard     output.     grep is used for simple patterns and basic regular expressions     (BREs); egrep can handle extended regular expressions (EREs).     See re_format(7) for more information on regular expressions.     fgrep is quicker than both grep and egrep, but can only handle     fixed patterns (i.e., it does not interpret regular     expressions).  Patterns may consist of one or more lines,     allowing any of the pattern lines to match a portion of the     input.     zgrep, zegrep, and zfgrep act like grep, egrep, and fgrep,     respectively, but accept input files compressed with the     compress(1) or gzip(1) compression utilities.  bzgrep, bzegrep,     and bzfgrep act like grep, egrep, and fgrep, respectively, but     accept input files compressed with the bzip2(1) compression     utility.     The following options are available:     -A num, --after-context=num             Print num lines of trailing context after each match.             See also the -B and -C options.             ...
```

  

### **cat**

The cat command is short for “concatenate.” It’s used to display the contents of a file, combine files, or create new ones.

```expressive
➜  trevorlasn.com git:(master) ✗ cat astro.config.mjsimport { defineConfig } from "astro/config";import mdx from "@astrojs/mdx";import sitemap from "@astrojs/sitemap";import tailwind from "@astrojs/tailwind";import vercel from "@astrojs/vercel/static";import partytown from "@astrojs/partytown";// https://astro.build/configexport default defineConfig({  site: "https://www.trevorlasn.com",  integrations: [ mdx(), sitemap(), tailwind(), partytown({    config: {      forward: ["dataLayer.push"]    }  }), ],  output: "static",  adapter: vercel(),});
```

**Combining Files:** One of the key features of cat is its ability to combine multiple files into one. For instance, if you want to merge file1.txt and file2.txt into file3.txt, you can do this:

```expressive
➜ cat file1.txt file2.txt > file3.txt
```

This command above takes the content of *file1.txt* and *file2.txt* and merges them into *file3.txt*. The **\>** operator is used to direct the combined output into a new file.

**Creating New Files:** You can also use *cat* to create new files. Type your text, and when you’re done, press *Ctrl+D* to save and exit.

```expressive
➜ cat > newfile.txthey➜ lsnewfile.txt➜ cat newfile.txthey
```

**cat** is helpful for viewing smaller files, but for very large files, it can be overwhelming as it dumps everything at once. In such cases, it’s better to use commands like **less** or **head** to view files in a more controlled way.

### **head**

You often don’t need to see all the content when working with large files. Instead of using cat to display everything, the head command lets you preview just the first few lines of a file.

This is especially useful for checking the structure of CSV files, logs, or any other large text files.

By default, **head** shows the first 10 lines of a file:

```expressive
➜  trevorlasn.com git:(master) ✗ head package-lock.json{  "name": "trevorlasn.com",  "version": "1.0.0",  "lockfileVersion": 3,  "requires": true,  "packages": {    "": {      "name": "trevorlasn.com",      "version": "1.0.0",      "dependencies": {
```

If you need more or fewer lines, you can specify the exact number using the **\-n** option:

```expressive
➜  trevorlasn.com git:(master) ✗ head -n 5 package-lock.json{  "name": "trevorlasn.com",  "version": "1.0.0",  "lockfileVersion": 3,  "requires": true,
```

**Previewing CSV Headers:** For CSV files, head is perfect for quickly checking the header or structure:

```expressive
➜ head -n 1 username-password-recovery-code.csvUsername; Identifier;One-time password;Recovery code;First name;Last name;Department;Location
```

  

### **awk**

**awk** is a powerful tool for pattern scanning and processing. It’s particularly useful for manipulating and analyzing text files and data streams.

With awk, you can filter, extract, and transform data in a file or from command output.

awk efficiently extracts and combines data from various sources using its associative arrays. Suppose you have two CSV files:

List of employees.

```expressive
➜ cat employees.csvID,Name,Department101,John Doe,Sales102,Jane Smith,Engineering103,Jim Brown,Sales
```

List of salaries.

```expressive
➜ cat salaries.csvID,Salary101,50000102,60000103,55000
```

Use **awk** to merge these files and display each employee’s name with their salary.

```expressive
➜ awk -F',' '    NR==FNR {salaries[$1]=$2; next}    FNR==1 {next}    {print $2, salaries[$1]}' salaries.csv employees.csvJohn Doe 50000Jane Smith 60000Jim Brown 55000
```

- **NR==FNR {salaries\[$1\]=$2; next}**: While processing the first file (**salaries.csv**), store salaries in an associative array. The employee ID (**$1**) is the key, and the salary (**$2**) is the value. This runs only for the first file.
- **FNR==1 {next}**: Skip the header line of the second file (**employees.csv**).
- **{print $2, salaries\[$1\]}**: For each line in the second file (**employees.csv**), print the employee’s name (**$2**) and their salary from the array (**salaries\[$1\]**).

You can also save the results to a new file.

```expressive
➜ awk -F',' '    NR==FNR {salaries[$1]=$2; next}    FNR==1 {next}    {print $2, salaries[$1]}' salaries.csv employees.csv > combined.csv➜ cat combined.csvJohn Doe 50000Jane Smith 60000Jim Brown 55000
```

  

### **sed**

**sed**, short for Stream Editor, is a powerful tool for text processing in the terminal. It allows you to find, replace, insert, or delete text within files or streams of data.

You can use it for quick edits without opening a text editor, making it great for scripting and automation.

**Replace a word or pattern in a file:** Replacing “Trevor” with “John”.

```expressive
➜ cat hello.mdMy name is Trevor➜ sed -i '' 's/Trevor/John/' hello.md➜ cat hello.mdMy name is John
```

If you want save the changes, use the **\-i** option.

**Print Specific Lines:** Print only specific lines from a file.

```expressive
➜  trevorlasn.com git:(master) ✗ sed -n '2,4p' package-lock.json  "name": "trevorlasn.com",  "version": "1.0.0",  "lockfileVersion": 3,
```

This prints lines 2 through 4.

**Regular Expressions:** *sed* supports regular expressions, allowing for complex search-and-replace operations. For example, replace all digits with “*X*”:

```expressive
➜ cat combined.csvJohn Doe 50000Jane Smith 60000Jim Brown 55000➜ sed 's/[0-9]/X/g' combined.csvJohn Doe XXXXXJane Smith XXXXXJim Brown XXXXX
```

**Renaming Files in Bulk:** Let’s say you have multiple files with the extension *.txt* and you want to rename them to *.md*.

```expressive
➜ ls1.txt 2.txt 3.txt➜ for file in *.txt; do    mv "$file" "$(echo "$file" | sed 's/.txt$/.md/')"  done➜ ls1.md 2.md 3.md
```

*sed* is highly versatile, and these examples just scratch the surface

### **tail**

**tail** is the counterpart to **head**. It allows you to view the last few lines of a file rather than the first. It’s commonly used to monitor log files or check the end of a document. By default, tail shows the last 10 lines of a file.

```expressive
➜  trevorlasn.com git:(master) ✗ tail package.json  },  "devDependencies": {    "@typescript-eslint/eslint-plugin": "^7.3.1",    "@typescript-eslint/parser": "^7.3.1",    "eslint": "^8.57.0",    "eslint-plugin-astro": "^0.32.0",    "eslint-plugin-jsx-a11y": "^6.8.0",    "typescript": "^5.4.2"  }}
```

**Viewing More or Fewer Lines:** You can adjust the number of lines shown using the *\-n* option.

```expressive
➜  trevorlasn.com git:(master) ✗ tail -n 15 package.json    "astro": "^4.13.3",    "clsx": "^2.1.0",    "sharp": "^0.33.3",    "tailwind-merge": "^2.2.2",    "tailwindcss": "^3.4.1"  },  "devDependencies": {    "@typescript-eslint/eslint-plugin": "^7.3.1",    "@typescript-eslint/parser": "^7.3.1",    "eslint": "^8.57.0",    "eslint-plugin-astro": "^0.32.0",    "eslint-plugin-jsx-a11y": "^6.8.0",    "typescript": "^5.4.2"  }}
```

**Real-Time File Monitoring:** One of the most powerful features of tail is the *\-f* option, which allows you to follow a file as it grows. This is especially useful for watching log files in real-time.

```expressive
➜ tail -f 1.md11Changing file
```

As new lines are added to **1.md**, tail will automatically display them.

### **chmod**

Each file has three sets of permissions: **owner**, **group**, and **others**. These are typically represented in a format like **rwxr-xr—**

- **r:** Read permission
- **w:** Write permission
- **x:** Execute permission

```expressive
➜ ls -l sensitive.md-rw-r--r--@ 1 trevorindreklasn  staff  0 Aug 21 15:22 sensitive.md
```

The file permissions -rw-r—r— indicate that:

- **Owner (trevorindreklasn):** Has read (r) and write (w) permissions.
- **Group (staff):** Has read (r) permissions.
- **Others:** Have read (r) permissions.

The **@** symbol indicates that the file has extended attributes, which are additional metadata beyond standard file permissions.

File permissions control who can read, write, or execute a file, ensuring security and proper access management by preventing unauthorized users from modifying or viewing sensitive data.

To restrict access to ***sensitive.md*** so that only the root user or superadmins can view and write to it, you can use the chmod command to modify the file’s permissions.

First, ensure the file is owned by the root user or a superadmin. You might need sudo for changing ownership:

```expressive
➜ ls -l sensitive.md-rw-r--r--@ 1 root  staff  0 Aug 21 15:22 sensitive.md➜ sudo chown root:admin sensitive.md➜ ls -l sensitive.md-rw-r-----@ 1 root  admin  0 Aug 21 15:22 sensitive.md➜ sudo chmod 600 sensitive.md➜  textfiles ls -l sensitive.md-rw-------  1 root  admin  0 Aug 21 15:22 sensitive.md
```

Only the owner (root) has read and write access. While the group and others have no permissions. This restricts access to the file, making it readable and writable only by the owner.

### Improper file permissions can lead to security issues or system problems

- **Unauthorized Access:** File containing sensitive information, like passwords or financial data, has overly permissive settings (e.g., *chmod 777*), anyone on the system can read or modify it. This could lead to data breaches or unauthorized access to sensitive information.
- **Malware Installation:** A file or directory with write permissions for all users (e.g., *chmod 777*) could be exploited by attackers to place malicious scripts or software, potentially compromising the entire system.
- **Data Corruption:** If files that should be read-only (e.g., logs or system configurations) are accidentally given write permissions, users or applications might inadvertently corrupt or erase critical data, leading to system instability or loss of important information.

### **xargs**

The **xargs** command builds and runs commands using input from other commands. It’s used to pass a list of items as arguments to another command.

Suppose you have a list of files that you want to delete.

```expressive
➜ ls1.txt        2.txt       2.md         3.md         sensitive.md# Find all .txt files and delete them➜ find . -name "*.txt" | xargs rm➜  ls2.md         3.md         sensitive.md
```

Instead of deleting them one by one, you can use xargs to pass the list of files to *rm*.

```expressive
find . -name "*.tmp" | xargs rm
```

**Creating Multiple Directories:** If you have a list of directory names in a file and want to create all of them, you can use xargs with mkdir.

```expressive
➜ cat dirs.txtsrctemputilspublic➜ ls2.md         3.md         dirs.txt     sensitive.md# Creates each directory listed in the file.➜ cat dirs.txt | xargs mkdir➜ ls2.md         dirs.txt     sensitive.md temp3.md         public       src          utils
```

**Compressing Files:** If you have multiple files that you want to compress using gzip, you can use xargs to pass the filenames to gzip.

```expressive
# Compresses all .log files in the current directoryls *.log | xargs gzip
```

  

### **find**

Search and locate files and directories within your file system based on various criteria. It’s highly customizable and can be combined with other commands for complex tasks.

The find command searches for occurrences of “astro” within the *node\_modules* directory, returning paths to files and directories with that name, including executables and package files.

```expressive
➜ trevorlasn.com git:(master) ✗ find node_modules -name "astro"node_modules/.bin/astronode_modules/astronode_modules/astro/dist/runtime/server/render/astro
```

**Cleanup old log files:** Regularly delete log files older than a month to free up disk space.

```expressive
➜ find /var/log -type f -name "*.log" -mtime +30 -delete
```

**Backup important files:** Locate and copy all **.docx** files from home directory to a backup location.

```expressive
➜  find ~/Documents -name "*.docx" -exec cp {} /path/to/backup/ \;
```

The **find** command is incredibly versatile and can be tailored to suit a wide range of file management tasks.

### Honorable Mentions

- **[jq](https://jqlang.github.io/jq/)**: Slice, filter, map and transform structured data with the same ease that sed, awk, grep.
- **[cut](https://www.gnu.org/software/coreutils/manual/html_node/cut-invocation.html)**: A command used to remove sections from each line of files.
- **[netstat](https://man7.org/linux/man-pages/man8/netstat.8.html)**: A network utility to display network connections, routing tables, and interface statistics.
- **[ping](https://man7.org/linux/man-pages/man8/ping.8.html)**: A tool to test the reachability of a host on an IP network and measure round-trip time.
- **[ifconfig](https://man7.org/linux/man-pages/man8/ifconfig.8.html)**: A command to configure network interfaces (deprecated in favor of **ip**).
- **[telnet](https://linux.die.net/man/1/telnet)**: A program to interact with remote hosts over a network using the Telnet protocol.
- **[sftp](https://man.openbsd.org/sftp)**: An interactive file transfer program that uses the SSH protocol.
- **[wget](https://www.gnu.org/software/wget/manual/wget.html)**: Network utility to retrieve files from the World Wide Web using HTTP and FTP.
- **[ps](https://man7.org/linux/man-pages/man1/ps.1.html)**: Displays information about running processes.
- **[top](https://man7.org/linux/man-pages/man1/top.1.html)**: A task manager to view and manage running processes in real-time.
- **[kill](https://man7.org/linux/man-pages/man1/kill.1.html)**: A command used to send signals to processes, typically to terminate them.
- **[comm](https://www.gnu.org/software/coreutils/manual/html_node/comm-invocation.html)**: A command that compares two sorted files line by line.