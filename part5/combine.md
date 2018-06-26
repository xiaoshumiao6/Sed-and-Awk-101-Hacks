# 结合 a、i、c 命令

你可以结合a、i、c命令，以下sed例子做了三件事:

- a - 在‘Jason’之后追加‘Jack Johnson’
- i - 在‘Jason’之前插入‘Mark Smith’
- c - 替换‘Jason’所在行为‘Joe Mason’新行

```
$ sed '/Jason/ {
     a\
     204,Jack Johnson,Engineer
     i\
     202,Mark Smith,Sales Engineer
     c\
     203,Joe Mason,Sysadmin
}' employee.txt
101,John Doe,CEO
202,Mark Smith,Sales Engineer
203,Joe Mason,Sysadmin
204,Jack Johnson,Engineer
103,Raj Reddy,Sysadmin
104,Anand Ram,Developer
105,Jane Miller,Sales Manager
```
