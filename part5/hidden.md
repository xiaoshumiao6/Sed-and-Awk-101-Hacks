# 打印隐藏字符

Sed的 l 命令可以打印隐藏的字符，例如 \t 制表符 和 $ 行尾结束符。

请创建如下的文本用于测试，请确保字段之间使用了tab符号隔开。

```
$ cat tabfile.txt
fname First Name
lname Last Name
mname Middle Name
```

__执行l命令将会打印出\t  和 $__

```
$ sed -n l tabfile.txt
fname\tFirst Name$
lname\tLast Name$
mname\tMiddle Name$
```

当你在l命令之后指定数字，输出行将使用不可打印字符包装在第n个字符处，如下例所示，这只适用于GNU sed。

```
$ sed -n 'l 20' employee.txt
101,John Doe,CEO$
102,Jason Smith,IT \
Manager$
103,Raj Reddy,Sysad\
min$
104,Anand Ram,Devel\
oper$
105,Jane Miller,Sal\
es Manager$
```
