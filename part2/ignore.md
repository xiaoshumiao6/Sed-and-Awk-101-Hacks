# 忽略大小写标志（i falg）

Sed替换标志i表示忽略大小写。你可以使用i的标志以不区分大小写
的方式匹配{origin-string}，但是这仅在GNU Sed中可用。<br/>

在下面的例子中，Sed将不会用"Johnny"替换"John"，因为{origin-string}
以小写"john"给出

__替换"john"为Johnny__:

```
$ sed 's/john/Johnny/' employee.txt
101,John Doe,CEO
102,Jason Smith,IT Manager
103,Raj Reddy,Sysadmin
104,Anand Ram,Developer
105,Jane Miller,Sales Manager
```

----

__替换"john"或者"John"为"Johnny"__:

```
$ sed 's/john/Johnny/i' employee.txt
101,Johnny Doe,CEO
102,Jason Smith,IT Manager
103,Raj Reddy,Sysadmin
104,Anand Ram,Developer
105,Jane Miller,Sales Manager
```
