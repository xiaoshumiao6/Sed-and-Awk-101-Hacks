# &魅力 - 引用匹配模式

当在{replacement-string}中使用'&'的时候，它会引用任何与{original-string}或者正则表达式匹配的字符串，
这是非常强大的一个功能。

一下是几个例子。

__使用[]包含员工id（前三个数字）,即101变成[101]，102变成[102]等等__:

```
$ sed 's/^[0-9][0-9][0-9]/[&]/g' employee.txt
[101],John Doe,CEO
[102],Jason Smith,IT Manager
[103],Raj Reddy,Sysadmin
[104],Anand Ram,Developer
[105],Jane Miller,Sales Manager
```

__使用<>包含整个行__:

```
$ sed 's/^.*/<&>/' employee.txt
<101,John Doe,CEO>
<102,Jason Smith,IT Manager>
<103,Raj Reddy,Sysadmin>
<104,Anand Ram,Developer>
<105,Jane Miller,Sales Manager>
```
