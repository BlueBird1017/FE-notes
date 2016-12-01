# Learn the Command Line
--------------------------------
# Manipulation
## pwd
```$ pwd``` stands for ***"print working directory"***.Outputs the name of the current working directory.
##ls
```$ ls``` stands for ***"list"***.Lists all files and directories in the working directory.
#### －a
lists all contents,including hidden files and directories
#### -l
list all contents of a directories in long format
#### -t
order files and directories by the time they were last modified.

(multiple options can be used together,like ```$ ls-alt```.)
## cd
```$ cd``` stands for ***"change directory"***.Switches you into the directory you specify.
##mkdir
```$ mkdir``` stands for ***"make directory"***.Creates a new directory in the working directory.
## touch
```$ touch``` creates a new file inside the working directory.
## CP
**$ cp** command copies files or directories.
#### *
use ```*``` to select group of files.These special characters are called wildcards.The ```*``` selects all files in the working directory.

	$ cp m*.txt scifi/
	
Here,```m*.txt``` selects all files in the working directory starting with ```m``` and ending with ```.txt```,and copies them to ```scifi/```.
## mv
The ```$ mv``` command moves and renames files.It's similar to cp in its usage.
## rm
The ```$ rm``` command deletes files and directories.It deletes files and directories permanently.
#### -r
The ```-r``` stands for ***"recursive"***,and it's used to delete a directory and all of its child directories.
# Redirection
## echo
```$ echo``` accepts the string as standard input,and echoes the string back to the terminal as standard output.
#### stdin
standard input,abbreviated as stdin,is information inputted into the terminal through the keyboard or input device.
#### stdout
standard output,abbreviated as stdout,is the information outputted after a process is run.
#### stderr
standaed output,abbreviated as stdout,is the message outputted by a failed process.
## cat
```$ cat``` outputs the contents of a file to the terminal.
## >
```$ >``` redirects standard output of a command to a file,overwriting previous content.
##>>
```$ >>``` redirects standard output of a command to a file,appending new content to old content.
## <
```$ <``` redirects standard input to a command.
##|
| is a "pipe".**$ |** redirects standard output of a command to another command.
## sort
```$ sort``` sorts lines of text alphabetically.
##uniq
```$ uniq``` filters duplicate,adjacent lines of text.
## grep
```$ grep``` searches for a text pattern and outputs it.
#### -i
```$ grep -i``` enables the command to be case insensitive.```$ grep``` searches for capital or lowercase strings.
#### -R
```$ grep -R``` searches all files in a directory and outputs filenames and lines containing matched results.

```$ grep -Rl``` searches all files in a directory and outputs only filenames with matched results.

```-R``` stands for ***"recursive"***.

```l``` stands for ***"files with matches"***.
## sed
```$ sed``` searches for a text pattern,modifies it,and output it.

Its expression is:
	
	$ sed 's/[the search string,the text to find]/[the replacement string,the text to add in place]

# Environment

The environment refers to the preferences and settings of the current user.

## nano
The nano is a command line text editor.It works just like a desktop text editor

	$ nano hello.txt
	
It opens a new text file named hello.txt in the nano text editor.

```Ctrl+O``` saves a file.```O``` stands for ***output***.

```Ctrl+X``` exits the nano program.```X``` stands for ***exit***.

```Ctrl+G``` opens a help menu.

```Clear``` clears the ternimal window,moving the command prompt to the top of the screen.

	$ nano ~/.bash_profile

```~/.bash_profile``` is the name of file used to store environment settings.It is commonly called the "bash profile".

The ```~``` represents the user's home directory.

The ```.``` indicates a hidden file.

The name ```~/.bash_profile``` is important,since this is how the command line recognizes the bash profile.

## source
The command ```source ~/.bash_profile``` activates the changes in ```~/.bash_profile``` for the current session. Instead of closing the terminal and needing to start a new session, ```$ source``` makes the changes available right away in the session we are in.

## alias
```$ alias``` command allows you to create keyboard shortcuts,or aliases,for commonly used commands.

## export
```$ export``` makes the variable to be available to all child sessions initiated from the session you are in.This is a way to make the variable persist across programs.

```export VARIABLE="Value"``` sets and exports an environment variable.


## PS1

	export PS1=">> "

**PS1** is a variable that defines the makeup and style of the command prompt.

## HOME
The ```HOME``` variable is an environment variable that displays the path of the home directory.

## PATH
```PATH``` is an environment variable that stores a list of directories separated by a colon.

Each directory contains scripts for the command line to execute.The ```PATH``` variable simply lists which directories contain scripts.

In advanced cases,you can customize the PATH variable when adding scripts of your own.

## env
The ```env``` command stands for ***environment***,and returns a list of the environment variables for the currnt user.