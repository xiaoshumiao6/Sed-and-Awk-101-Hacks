# 解释执行

就像编写shell脚本并通过调用文件名从命令行执行它们一样，你可以设置sed脚本以便从命令行执行，即Sed可以作为解释程序参与。为此，请将"#!/bin/sed -f"作为sed脚本的第一行，如下sed-script.sh文件那样：

```
$ vi myscript.sed
#!/bin/sed -f
# Swap field 1 (employee id) with field 2 (employee name)
s/\([^,]*\),\([^,]*\),\(.*\).*/\2,\1,\3/g
# Enclose the whole line within < and >
s/^.*/<&>/
# Replace Developer with IT Manager
s/Developer/IT Manager/
# Replace Manager with Director
s/Manager/Director/
```

现在，通过从命令行调用它直接执行sed脚本。

```
chmod u+x myscript.sed
./myscript.sed employee.txt
```

你也可以在sed脚本的第一行指定-n来禁止输出。

```
$ vi testscript.sed
#!/bin/sed -nf
/root/ p
/nobody/ p
```

现在，执行上面的测试脚本，如下所示：

```
chmod u+x testscript.sed
./testscript.sed /etc/passwd
```

仅用于测试目的，从testcript.sed的第一行中删除-n，然后再次执行以查看它的工作原理。

{% em style="yellow" %}__重要说明:__{% endem %}你必须使用-nf（而不是-fn）。如果您指定-fn，则在执行sed脚本时会收到如下错误消息。

```
$ ./testscript.sed /etc/passwd
/bin/sed: couldn't open file n: No such file or directory
```



