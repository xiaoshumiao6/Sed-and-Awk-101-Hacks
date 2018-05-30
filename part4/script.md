# Sed脚本

如果你想重用一组sed命令，请创建一个sed脚本文件里面包含所有的sed命令，使用-f参数指定该脚本。

首先，创建一个包含所有命令的sed脚本，如下所示，你已经知道这些sed命令在做什么了，正如我们在前面的章节所解释的那样。

```
$ vi mycommands.sed
s/\([^,]*\),\([^,]*\),\(.*\).*/\2,\1,\3/g
s/^.*/<&>/
s/Developer/IT Manager/
s/Manager/Director/
```

然后，执行该脚本。

```
$ sed -f mycommands.sed employee.txt
<John Doe,101,CEO>
<Jason Smith,102,IT Director>
<Raj Reddy,103,Sysadmin>
<Anand Ram,104,IT Director>
<Jane Miller,105,Sales Director>
```
