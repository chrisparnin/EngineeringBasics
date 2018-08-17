[Shells](Shells.md#shells) | [Development Environments](PackageManagers.md#development-environments) |  [Git](Git.md#git) | [Virtural Environments](Environments.md#environments) | [Markdown and Editors](MarkdownEditors.md#markdown) | [Programming Languages](Programming.md#programming) | [Task Management](OnlineTools.md#online-tools) | [Specialized Tools](SpecializedTools.md#specialized-tools) 

# Shells

A shell is a computing environment where commands can be interpreted, evaluated, and its output displayed (i.e., an instance of a read–eval–print loop (REPL)). A good shell provides access to a rich set of commands and allows simple programming of commands, which can be used to create powerful scripts and tools.

But with great power comes great [bullshittery](http://www.pgbovine.net/command-line-bullshittery.htm). Commands and their options can be terse, inconsistent, and difficult to learn. A steep learning curve often prevents novices from enjoying the eventual payoff.

If you've hardly used a command line environment before, you might want to go review this more thorough tutorial:
http://swcarpentry.github.io/shell-novice/index.html ---this page is more of a collection of pointers and resources.

## Shell Basics

### Opening a shell

Depending on your operating system and desktop manager, you have many ways to open up a shell. There may even been several different choices for shell programs.

Windows: In windows, you can use Cmd, Powershell, or emulated shells (Bash for Git, Bash with Linux Subsystem). A downside to using an emulated shell is that you may be limited in accessing other executables/environments on windows.

Windows: You access a shell in several ways. You can right click on the Windows Icon in the Task Bar and open a terminal window. You can type in the name of the shell program in the search bar (e.g., Cmd/Powershell).

Mac: you can run the Terminal in Applications.

IDES, such as VS Code provide easy access to a terminal (View => Terminal).

### Environment Variables

Environment variables are dynamically configurable elements that are available to processes on your system.

Mac/Linux: `echo $PATH`
Windows: `echo %PATH%`

A common problem with shells is that changing your `PATH` or other environment variables after an installation/OS GUI change will not affect any currently open shells. You either have to manually refresh the shell or open a new one. 

##### Setting Environment Variables

In addition to editing environment variables in your desktop manager GUI, you can also set environment variables in your shell.

In Windows, you can use `set` and `setx` to update environment variables. `set` will update environment variables in your current shell instance, but that will be lost after the shell closes. Using `setx`, you can permanently, set an environment variable for the user or system (use `setx /m`). See the [documentation](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/setx) for more information.

```
C:\Users\chris>set DEBUG_MODE=true
C:\Users\chris>echo %DEBUG_MODE%
true
```

In bash/*sh environments, you have set variables also set temporary environment variables in two ways:

```
$ DEBUG_MODE=true
$ echo $DEBUG_MODE
true
```

```
$ BUG_TEST=true echo $BUG_TEST

```

### 


### Shell Commands

The UNIX shell tools push data from sources through filters along pipes. In a shell there are three sources of I/O: standard in, standard out, and standard error. Standard error is a specialized version of standard out, so we'll focus on standard in and standard out.  The default for standard in is the keyboard and the default for standard out is to print to the shell (or console).

Pipes and redirects change standard in and standard out from defaults.

```bash
command              # default standard in and standard out
command < inputFile  # redirect of inputFile contents to command as standard in
command > outputFile # redirect command output to outputFile as standard out
command1 | command2  # pipes output of command1 as standard in to command2
command &            # run in background, typically used for applications
```

## Resources

### Explain shell

What does `tar -zxvf ph.tar.gz` do?

http://explainshell.com/explain?cmd=tar+-zxvf

![image](https://cloud.githubusercontent.com/assets/742934/15635713/8fc9cf7e-25b4-11e6-957e-0bb03756b9fb.png)

### Command Line Fu

A list of command line examples for interesting tasks:  
http://www.commandlinefu.com/commands/browse

Essential commands:

* **`ls`**: list content of a directory.
* **`cd`**: change directories to a new path.
* **`mkdir`**: make a new directory.
* **`pwd`**: output current directory
* **`cp`**: copy files
* **`rm`**: rm files
* **`touch`**: make a new file/update status**
* **`cat`**: output the contents of a file.
* **`head`**: output the first lines of a file.
* **`tail`**: output the last lines of a file.
* **`grep`**: search files for a key phrase.
* **`wget`**: retrieve file from the web.
* **`cut`**: extract output of a file (columns)
* **`awk`** and **`sed`**: Magic commands for extracting, searching, and transforming content.

## Practice: Set Up a Research Workspace

You want to keep your research files organized on your local system.  We suggest creating a `Research` folder with subfolders for specific projects.  Set up a research environment using the command line.

Note that if you're using Linux on Windows, the Linux system is a virtual machine.  That means that the files that make up the Linux system are not easy to find and if you do find them, you consider them read-only when accessing them outside of Linux.

## Practice: Working with a CSV File

* Create a `product-hunt-dataset` folder in your research environment.
* Download the Product Hunt Data `wget https://s3-us-west-2.amazonaws.com/producthunt-downloads/ph-export--2016-04-01.tar.gz`
* Extract dataset: `tar -zxvf ph-export--2016-04-01.tar.gz`
* Change into `product-hunt` folder.
* Inspect the file contents: `head posts--2016-04-01_14-36-24-UTC.csv`
* Estimate number of contents: `cat posts--2016-04-01_14-36-24-UTC.csv | wc -l`

Missing wget? https://chocolatey.org/packages/Wget

## More practice

* Write a simple shell script to find the largest file  
Hint: (loop through each file in directory and run `wc -l`

## Advanced: Shell Programming

The shell is a general programming language that can be parameterized.  You may find it useful to create a bash script to automate frequent commands as part of data collection and analysis.  There are many online resources (like [Ryans Tutorials - Bash Scripting Tutorial](https://ryanstutorials.net/bash-scripting-tutorial/) to help with the creation of a bash script.

```bash
e=expansion
$e
$(command)
'literal string'
"string with \$ $e"
```

Command can run sequentially or conditionally:

```bash
command1 ; command2
(command1 ; command2) # in a sub-shell
command1 || command2  # do command2 only if command1 fails
command1 && command2  # do command2 only if command1 succeeds
```

Usual conditionals and loops:

```bash
if command; then
   commands
fi

while command; do
  commands
done

while read var; do
   commands
done

# looping over lists
for var in a b c; do
   commands # that can access $var
done

# looping over numerics
for((x=1;x<=10;x++); do
   commands # that can access $x
done

case word in
pattern1) commands1;;
pattern2) commands2;;
esac
```

