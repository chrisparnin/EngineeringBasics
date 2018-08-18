[Setup](Setup.md#setup) | [Shells](Shells.md#shells) |  [Git](Git.md#git) | [Markdown and IDEs](MarkdownEditors.md#markdown) |  [Virtural Environments](Environments.md#environments) | [Task Management](OnlineTools.md#online-tools)

# Shells

A shell is a computing environment where commands can be interpreted, evaluated, and its output displayed (i.e., an instance of a read–eval–print loop (REPL)). A good shell provides access to a rich set of commands and allows simple programming of commands, which can be used to create powerful scripts and tools.

But with great power comes great [bullshittery](http://www.pgbovine.net/command-line-bullshittery.htm). Commands and their options can be terse, inconsistent, and difficult to learn. A steep learning curve often prevents novices from enjoying the eventual payoff.

If you've hardly used a command line environment before, you might want to go review this more thorough tutorial:
http://swcarpentry.github.io/shell-novice/index.html ---this page is more of a collection of pointers, discussion of common tasks and mistakes, and resources.

## Resources

### Command Line Fu

A list of command line examples for interesting tasks:  
http://www.commandlinefu.com/commands/browse

Create a graphical directory tree from your current directory.
```
ls -R | grep ":$" | sed -e 's/:$//' -e 's/[^-][^\/]*\//--/g' -e 's/^/ /' -e 's/-/|/'
```

### Explain shell

What does `tar -zxvf ph.tar.gz` do?

http://explainshell.com/explain?cmd=tar+-zxvf

![image](https://cloud.githubusercontent.com/assets/742934/15635713/8fc9cf7e-25b4-11e6-957e-0bb03756b9fb.png)


## Shell Basics

Depending on your operating system and desktop manager, you have many ways to open up a shell. There may even be several different choices for shell programs.

### Accessing and Using Shells

Mac: you can run the Terminal in Applications. 

Windows: *Shell options*. In windows, you can use Cmd, Powershell, or emulated shells (Bash for Git, Bash with Linux Subsystem). A downside to using an emulated shell is that you may be limited in accessing other executables/environments on windows.

Windows: *Opening*. You access a shell in several ways. You can right click on the Windows Icon in the Task Bar and open a terminal window. You can type in the name of the shell program in the search bar (e.g., Cmd/Powershell). 

Windows: *Admin shell*. Some commands require adminstration privileges. If you need to run a command with admin, you must start a shell with admin privilege. There is typically an admin command shell available in the menu when right clicking the Windows Icon on the Task Bar. You can also get one from right clicking the Cmd executable in the search bar.

Tip: If opening up a cmd shell in admin mode, make sure you do not perform operations, such as `git clone` in your current directory (`C:\WINDOWS\system32`). Otherwise, you will be writing to a location that only admin will have access to which will make it difficult to run the commands/tasks you are intending on doing.

Tip: IDES, such as VS Code provide easy access to a terminal (View => Terminal).

### Commands

99% of the reason you use shells is to run useful commands.

##### Essential commands.

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

##### Combining commands

Command can run sequentially or conditionally:

```bash
command1 ; command2
(command1 ; command2) # in a sub-shell
command1 || command2  # do command2 only if command1 fails
command1 && command2  # do command2 only if command1 succeeds
```

Note: In Windows, `;` does not work in Cmd, but does in Powershell. Use `&&` for the most portable commands.

##### Command I/O

The UNIX shell commands push data from sources through filters along pipes. In a shell there are three sources of I/O: standard input (stdin), standard output (stout), and standard error (sterr). Standard error is a specialized version of standard out, so we'll focus on standard in and standard out.  The default for standard in is the keyboard and the default for standard out is to print to the shell (or console).

Pipes and redirects change standard in and standard out from defaults.

```bash
command              # default standard in and standard out
command < inputFile  # redirect of inputFile contents to command as standard in
command > outputFile # redirect command output to outputFile as standard out
command1 | command2  # pipes output of command1 as standard in to command2
command &            # run in background, typically used for applications
```

A neat trick: Command the value of a file into your clipboard!

Windows: `clip < file.txt` Mac: `pbcopy < file.txt` 

## Practice: Working with a CSV File

* Create a `product-hunt-dataset` folder in your class folder.
* Download the Product Hunt Data `wget https://s3-us-west-2.amazonaws.com/producthunt-downloads/ph-export--2016-04-01.tar.gz`
* Extract dataset: `tar -zxvf ph-export--2016-04-01.tar.gz`
* Change into `product-hunt` folder.
* Inspect the file contents: `head posts--2016-04-01_14-36-24-UTC.csv`
* Estimate number of contents: `cat posts--2016-04-01_14-36-24-UTC.csv | wc -l`

Missing wget? https://chocolatey.org/packages/Wget

## Environment Variables

Environment variables are dynamically configurable elements that are available to processes on your system.

Mac/Linux: `echo $PATH`
Windows: `echo %PATH%`

A common problem with shells is that changing your `PATH` or other environment variables after an installation/OS GUI change will not affect any currently open shells. You either have to manually refresh the shell or open a new one. 

##### Setting Environment Variables (Windows)

In addition to editing environment variables in your desktop manager GUI, you can also set environment variables in your shell.

In Windows, you can use `set` and `setx` to update environment variables. `set` will update environment variables in your current shell instance, but that will be lost after the shell closes. Using `setx`, you can permanently, set an environment variable for the user or system (use `setx /m`). See the [documentation](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/setx) for more information.

```
C:\Users\chris>set DEBUG_MODE=true
C:\Users\chris>echo %DEBUG_MODE%
true
```

Tip: One limitation of using setx is that it cannot store values longer than 1024 characters.

##### Setting Environment Variables (Mac/Linux)

In bash/*sh environments, you can set temporary environment variables in two ways:

Like `set`, you can define a variable just for your shell session:
```
$ DEBUG_MODE=true
$ echo $DEBUG_MODE
true
```

##### Scoping

You can also define a variable that will only exist inside a subprocess  spawned from the shell. This may not behave the way you expect!
```
$ BUG_TEST=true echo $BUG_TEST

```
A blank is printed out because `$BUG_TEST` is expanded before the process executing the echo command is started. On the other hand, if you had code that checked for `BUG_TEST` while running, it would contain `true`.

Finally, you can enable access to an environment variable for all processes and subprocesses started in the shell by using `export VAR=VALUE`

> *Permenant environment variables are actually more tricky in Mac/Linux shells!*

When a shell is initialized, several startup scripts are run for customization and initialization. If you want to make a variable always available, a common strategy is to locate one of these initialization scripts (typically in your home directory, and editing them to run your commands on startup). Common locations include: `~/.profile`, or `~/.bashrc`. The symbol `~`, is a shortcut for your home directory: `/home/<user>`.

To summarize (Mac/Linux):

* Use `export VAR=VALUE` to enable a variable to be seen by all executed commands.
* Use `VAR=VALUE` for a variable only available in the shell.
* Use `VAR=VALUE <command>` for a variable only available to that command.
* Set permenant variables inside a start script such as `~/.bashrc`.

## Advanced: Shell Programming

The shell is a general programming language that can be parameterized.  You may find it useful to create a bash script to automate frequent commands as part of data collection and analysis.  There are many online resources (like [Ryans Tutorials - Bash Scripting Tutorial](https://ryanstutorials.net/bash-scripting-tutorial/) to help with the creation of a bash script.

```bash
e=expansion
$e
$(command)
'literal string'
"string with \$ $e"
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

## Optional practice

* Write a simple shell script to find the largest file  
Hint: (loop through each file in directory and run `wc -l`
