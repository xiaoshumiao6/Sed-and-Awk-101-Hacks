# 改变某行

Sed命令（c）允许你用新内容替换已存在的行

__语法:__

```
$ sed '[address] c the-line-to-insert' input-file
```

__替换第2行为新内容__

```
$ sed '2 c 202,Jack Johnson,Engineer' employee.txt
101,John Doe,CEO
202,Jack Johnson,Engineer
103,Raj Reddy,Sysadmin
104,Anand Ram,Developer
105,Jane Miller,Sales Manager
```

你也可以用多行替换单行

__将匹配到的‘Raj’所在行用两行新内容替换__

```shell
$ sed '/Raj/c\
203,Jack Johnson,Engineer\
204,Mark Smith,Sales Engineer' employee.txt
101,John Doe,CEO
102,Jason Smith,IT Manager
203,Jack Johnson,Engineer
204,Mark Smith,Sales Engineer
104,Anand Ram,Developer
105,Jane Miller,Sales Manager
```
