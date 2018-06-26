# 打印行号

Sed = 命令会打印输入文本的的行号

__打印所有行号__

```
$ sed = employee.txt
1
101,John Doe,CEO
2
102,Jason Smith,IT Manager
3
103,Raj Reddy,Sysadmin
4
104,Anand Ram,Developer
5
105,Jane Miller,Sales Manager
```

{% em style="yellow" %}注意{% endem %}：你可以结合=和数字来限制打印行号的范围

__只打印1-3行的行号__

```
$ sed '1,3 =' employee.txt
1
101,John Doe,CEO
2
102,Jason Smith,IT Manager
3
103,Raj Reddy,Sysadmin
104,Anand Ram,Developer
105,Jane Miller,Sales Manager
```

只打印匹配到关键字所在行的行号。

```
$ sed '/Jane/ =' employee.txt
101,John Doe,CEO
102,Jason Smith,IT Manager
103,Raj Reddy,Sysadmin
104,Anand Ram,Developer
5
105,Jane Miller,Sales Manager
```

如果你只想知道匹配到关键字所在行的行号，而不关心内容，可以使用-n参数

```
$ sed -n '/Raj/ =' employee.txt
3
```

__打印输入文件的总行数__

```
$ sed -n '$ =' employee.txt
5
```
