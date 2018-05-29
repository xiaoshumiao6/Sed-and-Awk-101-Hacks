#Sed语法和基本命令
所有的sed例子, 我们都将使用下面employee.txt这个文件。
请创建此文本文件以尝试本书中给出的命令。

```
$ vi employee.txt
101,John Doe,CEO
102,Jason Smith,IT Manager
103,Raj Reddy,Sysadmin
104,Anand Ram,Developer
105,Jane Miller,Sales Manager
```
以上数据库记录包含以下字段：

```
• Employee Id
• Employee Name
• Title
```

Sed是一个流编辑器。是一个非常强大的操作、过滤和转换文本的工具。Sed可以从文件或者管道获取输入
，你甚至可以在Bash命令行就开始处理文件，而不必通过脚本，总之您可以在各种情况下使用。
对于初学者来说，sed脚本可能看起来很神秘。一旦你掌握了sed命令，你将能够通过快速编写一个
sed脚本来解决很多的复杂文本。
在本书中，我将解释所有的sed命令，提供易于理解的例子。

