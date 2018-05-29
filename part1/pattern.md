# 打印模式空间（p命令）

使用sed的p命令，你可以打印当前的模式空间。<br/>

你可能想知道为什么要使用p命令，因为sed默认在执行完命令后
会打印模式空间的缓冲区。<br/>

如你所见，有一些原因。该命令允许你
控制打印到标准输出的内容，p是标准sed流程的默认行为，你可以通过-n选项来
禁止默认打印。否则的话，当你显示指定p（打印）作为你的一个参数，该行将被
打印两次。

__以下是一个两次打印的例子:__

```
$ sed 'p' employee.txt
101,John Doe,CEO
101,John Doe,CEO
102,Jason Smith,IT Manager
102,Jason Smith,IT Manager
103,Raj Reddy,Sysadmin
103,Raj Reddy,Sysadmin
104,Anand Ram,Developer
104,Anand Ram,Developer
105,Jane Miller,Sales Manager
105,Jane Miller,Sales Manager
```

__以下只打印一次（功能等同于 'cat employee.txt'）:__

```
$ sed -n 'p' employee.txt
101,John Doe,CEO
102,Jason Smith,IT Manager
103,Raj Reddy,Sysadmin
104,Anand Ram,Developer
105,Jane Miller,Sales Manager
```

## 指定地址的范围

如果你在sed命令之前没有指定地址的范围，则按默认它会打印所有的匹配行，
以下是指定打印地址的例子：

__只打印匹配到的第2行__:

```
$ sed -n '2 p' employee.txt
102,Jason Smith,IT Manager
```

__指定打印匹配到的1-4行__:

```
$ sed -n '1,4 p' employee.txt
101,John Doe,CEO
102,Jason Smith,IT Manager
103,Raj Reddy,Sysadmin
104,Anand Ram,Developer
```

__打印从匹配到的第2行及其以后的所有行（包括第2行）__:

```
$ sed -n '2,$ p' employee.txt
102,Jason Smith,IT Manager
103,Raj Reddy,Sysadmin
104,Anand Ram,Developer
105,Jane Miller,Sales Manager
```

## 修改地址范围

你可以使用逗号(,)、加号(+)、波浪号(~)来修改范围<br/>

在上面的例子中，我们使用逗号(,)作为地址范围的一部分，意思很明确:
n, m表示n至m<br/>

加号(+)可以与逗号一起使用来指定一个行数而不是绝对行号。例如，
n, +m 表示以n开头的m行<br/>

波浪号(~)也可用于地址范围。它的意思是跳过命令之间的行。例如，
地址范围n~m表示sed应从第n行开始，以后每跳过m行取该行。

  * 1~2 匹配1, 3, 5, 7, ...
  * 2~2 匹配2, 4, 6, 8, ...
  * 1~3 匹配1, 4, 7, 10, ...
  * 2~3 匹配2, 5, 8, 11, ...

__只打印奇数行__:

```
$ sed -n '1~2 p' employee.txt
101,John Doe,CEO
103,Raj Reddy,Sysadmin
105,Jane Miller,Sales Manager
```

## 模式匹配

就像你可以指定地址编号（或地址范围）一样
也可以指定一个模式（或模式范围）来匹配，看看接下来的几个例子。

__打印匹配到"Jane"的行__:

```
$ sed -n '/Jane/ p' employee.txt
105,Jane Miller,Sales Manager
```

__打印从开始匹配到"Jason",及其第4行之前的所有行__:

```
$ sed -n '/Jason/,4 p' employee.txt
102,Jason Smith,IT Manager
103,Raj Reddy,Sysadmin
104,Anand Ram,Developer
```
{% em color="#ff0000" %}注意{% endem %}:如果前4行没有匹配到"Jason"，超过的部分命令将只会打印匹配到的行，因为此时已经超过了编号4

__打印从开始匹配到"Raj"，及其后面的所有行（一直到末尾）__:

```
$ sed -n '/Raj/,$ p' employee.txt
103,Raj Reddy,Sysadmin
104,Anand Ram,Developer
105,Jane Miller,Sales Manager
```

__打印从匹配到"Raj"开始，一直到匹配到"Jane"停止打印__:

```
$ sed -n '/Raj/,/Jane/ p' employee.txt
103,Raj Reddy,Sysadmin
104,Anand Ram,Developer
105,Jane Miller,Sales Manager
```

__打印从匹配到"Jason"开始及其后面2行__:

```
$ sed -n '/Jason/,+2 p' employee.txt
102,Jason Smith,IT Manager
103,Raj Reddy,Sysadmin
104,Anand Ram,Developer
```
