# Creating and Exploring a Git Repository and Managing Content

In this lab, we'll create an empty Git repository on your local disk and stage and commit content into it.

**Prerequisites**  

To complete this and all future labs in the course, you must have a working version of Git installed. We assume 2.0 or higher for the version. (To see which version you have, you can run git --version) If you don't have a working version of Git installed, then you should install it now.

**Steps**  

1. On your local disk, create a new directory and change (cd) into it. (This will be the directory we work in unless otherwise specified).
```
mkdir <name of directory>
cd <name of directory>
```

2. In the new directory, initialize a new repo by running the command: 
```
git init
```

> Note: This command created a new git repository skeleton in a subdirectory named ".git" under the current directory - as indicated by the output message from the command. This means that you're now able to start using other Git commands in the current directory.

3. Tell Git who you are by setting your basic identification configuration settings with the following commands (Note the double dashes before "global" since we are spelling out the option. Also, values only require quotes if there is a space in the value.)
```
git config --global user.name "first-name last-name" 
git config --global user.email your-email-address
```

4. Now let's create some content to put through the Git workflow. Note that for purposes of these initial labs, we just need files to work with - we don't really care what's in them. We can "cheat" and just echo something into a file via the ">" operator. In fact, the output of any command could be used to put content into a file via the ">" operator. Of course, if you prefer, you can certainly create files via your favorite editor instead. Create two files - contents and names don't matter.
```
date > date-file1 
cat /etc/hosts > host-file2
```

5. Stage the files with the add command. (If you prefer you can add each separate file explicitly rather than use the ".")
```
git add .
```

> Note: If you see any messages about end of line conversions, you can ignore them.

6) Now commit the files. You can use whatever commit message (comment) you want. Note the single hyphen/dash before the short form of the option.
```
git commit -m "This is my first commit"
```

> Notice the output you get. There is the branch name - the default branch - main, followed by an indicator that this was the first (root) commit and then the first few characters of the SHA1 for the commit.

7. Edit one of the files. (We can just use the ">>" to append something to the file's content.)
```
echo "01.01.2024" >> date-file1
```

8. Stage and commit the file with the shortcut. Note the combined short options "-am" for "-a" + " -m".
```
git commit -am "Lines added to date-file1"
```