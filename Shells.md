The UNIX shell tools push data from sources through filters along pipes:

```bash
command
command < inputFile
command > outputFile
command1 | command2 # pipes
command &           # run in background
```

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



### Resources

##### Explain shell

What does `tar -zxvf ph.tar.gz` do?

http://explainshell.com/explain?cmd=tar+-zxvf

![image](https://cloud.githubusercontent.com/assets/742934/15635713/8fc9cf7e-25b4-11e6-957e-0bb03756b9fb.png)

http://www.commandlinefu.com/commands/browse
