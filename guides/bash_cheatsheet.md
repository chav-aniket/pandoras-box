# Bash Cheat Sheet
Tags: #cheatsheet, #bash, #linux <br>
Related: [[]] <br>
## Theory

The `shell` is the environment in which you can interact with your computer using command lines. `Bash` is one such environment. Other examples of shells are Zsh and Fish. A terminal is an application which allows you to use a shell.

`.` is the symbolic link for the current directory which you are in.

`..` is the symbolic link for the "previous" or "upper" directory which your current directory is within.

## Commands

> cd [NAME]

This stands for 'change directory' and allows you to move to the directory specified. Changing to the previous directory can be done by entering `cd ..` while changing between multiple directories can look like `cd Desktop/photos/2018`. 

> ls

This stands for list. This is used to see all files within the current directory. `ls -a` can be used to list all files within the current directory, including hidden files and links such as `.`, `..` and `.git`.

> mkdir [FILE NAME]

This stands for make directory with the name specified.

> rm [FILE NAME]

This stands for remove, where the specified file will be removed. `rm -R [FOLDER NAME]` can be used to delete a directory. This file/folder cannot be recovered from recycle bin so use this command very safely.