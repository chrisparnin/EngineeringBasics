[Shells](https://github.com/REU-SOS/EngineeringBasics/blob/master/Shells.md#shells) | [Package Managers](https://github.com/REU-SOS/EngineeringBasics/blob/master/PackageManagers.md#configuration-management) | [Markdown and Editors](https://github.com/REU-SOS/EngineeringBasics/blob/master/MarkdownEditors.md#markdown) | [Git](https://github.com/REU-SOS/EngineeringBasics/blob/master/Git.md#git) | [Programming with Python/Node](https://github.com/REU-SOS/EngineeringBasics/blob/master/Programming.md#programming) | [Online Tools](https://github.com/REU-SOS/EngineeringBasics/blob/master/OnlineTools.md#online-tools)

# Shells

A shell is a computing environment where commands can be interpreted, evaluated, and its output displayed (i.e., an instance of a read–eval–print loop (REPL)). A good shell provides access to a rich set of commands and allows simple programming of commands, which can be used to create powerful scripts and tools.

But with great power comes great [bullshittery](http://www.pgbovine.net/command-line-bullshittery.htm). Commands and their options can be terse, inconsistent, and difficult to learn. A steep learning curve often prevents novices from enjoying the eventual payoff.

If you've hardly used a command line environment before, you might want to go review this more thorough tutorial:
http://swcarpentry.github.io/shell-novice/index.html -- this page is more of a collection of pointers and resources.

### Tips for Windows Users

* Git for Windows provides a BASH emulation used to run Git from the command line. You can run "Git Bash" to get this slightly improved command prompt.
* Powershell is a new shell for windows.
* Windows 10 will soon support a native bash shell! Stay tuned.

### Shell Basics

The UNIX shell tools push data from sources through filters along pipes:

```bash
command
command < inputFile
command > outputFile
command1 | command2 # pipes
command &           # run in background
```

### Resources

##### Explain shell

What does `tar -zxvf ph.tar.gz` do?

http://explainshell.com/explain?cmd=tar+-zxvf

![image](https://cloud.githubusercontent.com/assets/742934/15635713/8fc9cf7e-25b4-11e6-957e-0bb03756b9fb.png)

##### Command Line Fu

A list of command line examples for interesting tasks:  
http://www.commandlinefu.com/commands/browse

### Advanced: Shell Programming

The shell is a general programming langauge:

```bash
e=expansion
$e
$(command)
'literal string'
"string with \$ $e"
```

Command can run sequetially or conditionally:

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

