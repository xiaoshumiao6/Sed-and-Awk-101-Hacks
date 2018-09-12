# 追加下一行到模式空间（N 命令）

正如大写字母`H`和`G`附加而不是替换一样，N命令将输入文件中的下一行附加到模式缓冲区，而不是替换当前行。

正如我们之前讨论过的，小写命令`n`打印当前模式空间，清除模式空间，从输入文件中读取下一行到模式空间，
并从中断处继续执行剩余的sed命令

大写`N`命令不打印当前模式空间，也不清除模式空间。 相反，它在当前模式空间的末尾添加换行符（\n），
将输入文件中的下一行追加到当前模式空间，并通过执行其余的sed命令继续sed标准流。

__打印员工的姓名和职务,通过：分割__

```
$ sed -e '{N;s/\n/:/}' empnametitle.txt
John Doe:CEO
Jason Smith:IT Manager
Raj Reddy:Sysadmin
Anand Ram:Developer
Jane Miller:Sales Manager
```

在上面的例子中：

 - __`N`__ 附加新行到当前模式空间（本身包含了雇员姓名）并且从输入文件中读取下一行附加到当前模式空间中。
因此，模式空间最后总包含了（employee name\ntitle）

 - __`s/\n/:/`__ 替换 "Employee Name\nTitle"中的`\n`为`:`

![sed-execution-flow2](https://res.cloudinary.com/devops007/image/upload/v1536565524/Awk-Sed-101-Hacks/sed-follow-2.jpg)

以下示例演示如何使用N命令在与文本相同的行上打印行号，同时从employee.txt打印每一行。

__打印行号__

```
$ sed -e '=' employee.txt | sed -e '{N;s/\n/ /}'
1 101,John Doe,CEO
2 102,Jason Smith,IT Manager
3 103,Raj Reddy,Sysadmin
4 104,Anand Ram,Developer
5 105,Jane Miller,Sales Manager
```

正如我们在前面的例子中看到的那样，sed`=`命令首先打印行号，然后打印原始行。

在此示例中，N命令将\n添加到当前模式空间（包括行号），然后读取下一行并附加它。
因此，模式空间将包含“行号\n原始行内容”。然后我们执行`s/\n/ /`将换行符（\n）改为空格。
