# 模式空间写入文件（w命令）

使用w命令，可以将当前模式空间写入文件。
根据sed默认的标准流程，模式空间将会被打印到标准输出，因此
如果你想输出到文件而不是屏幕上，你还应该使用-n选项。<br/>

接下来是一些例子:

__将employee.txt文件的内容写入到output.txt文件（并在屏幕上显示）__:

```
$ sed 'w output.txt' employee.txt
101,John Doe,CEO
102,Jason Smith,IT Manager
102,Jason Smith,IT Manager
103,Raj Reddy,Sysadmin
104,Anand Ram,Developer
```
----

__写入从第2行开始之后所有的行__:

```
$ sed -n '2,$ w output.txt' employee.txt
$ cat output.txt
102,Jason Smith,IT Manager
103,Raj Reddy,Sysadmin
104,Anand Ram,Developer
105,Jane Miller,Sales Manager
```

----

__写入奇数行__:

```
$ sed -n '1~2 w output.txt' employee.txt
$ cat output.txt
101,John Doe,CEO
103,Raj Reddy,Sysadmin
105,Jane Miller,Sales Manager
```

----

__写入匹配到"Jane"的行__:

```
$ sed -n '/Jane/ w output.txt' employee.txt
$ cat output.txt
105,Jane Miller,Sales Manager
```

----

__写入从开始行匹配到"Jason"后，一直到第4行__:

```
$ sed -n '/Jason/,4 w output.txt' employee.txt
$ cat output.txt
102,Jason Smith,IT Manager
```
