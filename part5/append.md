# 指定位置的后面追加新行
你可以使用追加命令（a）在指定位置后面插入新行

__语法：__

```
$ sed '[address] a the-line-to-append' input-file
```

__在employee.txt文件指定的行号2之后插入新的记录__

```
$ sed '2 a 203,Jack Johnson,Engineer' employee.txt
101,John Doe,CEO
102,Jason Smith,IT Manager
203,Jack Johnson,Engineer
103,Raj Reddy,Sysadmin
104,Anand Ram,Developer
105,Jane Miller,Sales Manager
```

__在employee.txt文件末尾插入新的记录__

```
$ sed '$ a 106,Jack Johnson,Engineer' employee.txt
101,John Doe,CEO
102,Jason Smith,IT Manager
103,Raj Reddy,Sysadmin
104,Anand Ram,Developer
105,Jane Miller,Sales Manager
106,Jack Johnson,Engineer
```

你也可以使用a命令同时插入多行

__在匹配到‘Jason’的所在行之后插入两行新记录__

```
$ sed '/Jason/a\
203,Jack Johnson,Engineer\
204,Mark Smith,Sales Engineer' employee.txt
101,John Doe,CEO
102,Jason Smith,IT Manager
203,Jack Johnson,Engineer
204,Mark Smith,Sales Engineer
103,Raj Reddy,Sysadmin
104,Anand Ram,Developer
105,Jane Miller,Sales Manager
```
