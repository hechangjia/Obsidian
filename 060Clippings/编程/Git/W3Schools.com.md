---
title: W3Schools.com
date: 2025-02-24T21:09:59+08:00
author:
  - https://www.w3schools.com/git/git_ignore.asp?remote=github
tags:
  - clippings
category: 
  - git 
  - gitignore 
  - 教程
rating: "7"
published: 
description: Well organized and easy to understand Web building tutorials with lots of examples of how to use HTML, CSS, JavaScript, SQL, Python, PHP, Bootstrap, Java, XML and more.
source: https://www.w3schools.com/git/git_ignore.asp?remote=github
---
## Git Ignore and .gitignore

---

## Git Ignore

When sharing your code with others, there are often files or parts of your project, you do not want to share.

Examples

- log files
- temporary files
- hidden files
- personal files
- etc.

Git can specify which files or parts of your project should be ignored by Git using a `.gitignore` file.

Git will not track files and folders specified in `.gitignore`. However, the `.gitignore` file itself **IS** tracked by Git.

---

## Create .gitignore

To create a `.gitignore` file, go to the root of your local Git, and create it:

Now open the file using a text editor.

We are just going to add two simple rules:

- Ignore any files with the `.log` extension
- Ignore everything in any directory named `temp`

### Example

\# ignore ALL .log files  
\*.log

\# ignore ALL files in ANY directory named temp  
temp/

Now all `.log` files and anything in `temp` folders will be ignored by Git.

**Note:** In this case, we use a single `.gitignore` which applies to the entire repository.

It is also possible to have additional `.gitignore` files in subdirectories. These only apply to files or folders within that directory.

---

---

## Rules for .gitignore

Here are the general rules for matching patterns in `.gitignore` files: 

| Pattern | Explanation/Matches | Examples |
| --- | --- | --- |
|  | Blank lines are ignored |  |
| \# *text comment* | Lines starting with # are ignored |  |
| *name* | All *name* files, *name* folders, and files and folders in any *name* folder | /name.log   /name/file.txt   /lib/name.log |
| *name*/ | Ending with / specifies the pattern is for a folder. Matches all files and folders in any *name* folder | /name/file.txt   /name/log/name.log  **no match:**   /name.log |
| *name*.*file* | All files with the *name.file* | /name.file   /lib/name.file |
| */name*.*file* | Starting with / specifies the pattern matches only files in the root folder | /name.file  **no match:**   /lib/name.file |
| *lib/name*.*file* | Patterns specifiing files in specific folders are always realative to root (even if you do not start with / ) | /lib/name.file  **no match:**   name.file   /test/lib/name.file |
| \*\**/lib/name.file* | Starting with \*\* before / specifies that it matches any folder in the repository. Not just on root. | /lib/name.file   /test/lib/name.file |
| \*\**/name* | All *name* folders, and files and folders in any *name* folder | /name/log.file   /lib/name/log.file   /name/lib/log.file |
| /lib/\*\**/name* | All *name* folders, and files and folders in any *name* folder within the lib folder. | /lib/name/log.file   /lib/test/name/log.file   /lib/test/ver1/name/log.file  **no match:**   /name/log.file |
| \*.*file* | All files withe *.file* extention | /name.file   /lib/name.file |
| \**name*/ | All folders ending with *name* | /lastname/log.file   /firstname/log.file |
| *name*?.*file* | ? matches a **single** non-specific character | /names.file   /name1.file  **no match:**   /names1.file |
| *name*\[a-z\].*file* | \[*range*\] matches a **single** character in the specified range (in this case a character in the range of a-z, and also be numberic.) | /names.file   /nameb.file  **no match:**   /name1.file |
| *name*\[abc\].*file* | \[*set*\] matches a **single** character in the specified set of characters (in this case either a, b, or c) | /namea.file   /nameb.file  **no match:**   /names.file |
| *name*\[!abc\].*file* | \[!*set*\] matches a **single** character, **except** the ones spesified in the set of characters (in this case a, b, or c) | /names.file   /namex.file  **no match:**   /namesb.file |
| \*.*file* | All files withe *.file* extention | /name.file   /lib/name.file |
| *name*/   !*name*/secret.log | ! specifies a negation or exception. Matches all files and folders in any *name* folder, except name/secret.log | /name/file.txt   /name/log/name.log  **no match:**   /name/secret.log |
| \*.*file   *!*name*.file | ! specifies a negation or exception. All files withe *.file* extention, except name.file | /log.file   /lastname.file  **no match:**   /name.file |
| \*.*file   *!*name*/\**.file*   junk.\* | Adding new patterns after a negation will re-ignore a previous negated file   All files withe *.file* extention, except the ones in *name* folder. Unless the file name is junk | /log.file   /name/log.file  **no match:**   /name/junk.file |

---

## Local and Personal Git Ignore Rules

It is also possible to ignore files or folders but not show it in the distributed `.gitignore` file.

These kinds of ignores are specified in the ` .git/info/exclude` file. It works the same way as `.gitignore` but are not shown to anyone else.
