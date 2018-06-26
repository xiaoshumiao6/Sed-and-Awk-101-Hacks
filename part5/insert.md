# 指定位置的前面追加新行
Sed的insert命令（i）类似于append命令，只不过它是在指定位置之前插入一行而不是指定位置之后

__语法：__

```
$ sed '[address] i the-line-to-insert' input-file
```

__在employee.txt文件指定的行号2之前插入新的记录__

```
$ sed '2 i 203,Jack Johnson,Engineer' employee.txt
101,John Doe,CEO
203,Jack Johnson,Engineer
102,Jason Smith,IT Manager
103,Raj Reddy,Sysadmin
104,Anand Ram,Developer
105,Jane Miller,Sales Manager
```

__在employee.txt文件尾行前插入新的记录__

```
$ sed '$ i 108,Jack Johnson,Engineer' employee.txt
101,John Doe,CEO
102,Jason Smith,IT Manager
103,Raj Reddy,Sysadmin
104,Anand Ram,Developer
108,Jack Johnson,Engineer
105,Jane Miller,Sales Manager
```

你也可以使用i命令同时插入多行。

__在匹配到‘Jason’的所在行之前插入两行新记录__

```
$ sed '/Jason/i\
203,Jack Johnson,Engineer\
204,Mark Smith,Sales Engineer' employee.txt
101,John Doe,CEO
203,Jack Johnson,Engineer
204,Mark Smith,Sales Engineer
102,Jason Smith,IT Manager
103,Raj Reddy,Sysadmin
104,Anand Ram,Developer
105,Jane Miller,Sales Manager
```
