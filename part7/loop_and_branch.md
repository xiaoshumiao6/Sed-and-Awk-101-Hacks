# 循环和分支（b 命令和 ：label）

您可以使用label和branch（b命令）更改sed命令的执行流程。

 - __:label__ 定义标签
 - __b label__ 将执行流分支到标签。Sed跳转到标签标记的行，并从那里继续执行其余命令。
 - 注意：你也可以只执行b命令（没有任何标签名称）。 在这种情况下，sed会跳转到sed脚本文件的末尾。

以下示例将员工姓名和职位（来自empnametitle.txt文件）组合到一个单独的行，字段之间用：分隔，
并在员工姓名前面添加“\*”，此时该员工的职位包含关键字“Manager”。

```
$ vi label.sed
#!/bin/sed -nf
h;n;H;x
s/\n/:/
/Manager/!b end
s/^/*/
:end
p
```

在上面的例子中，你已经知道了什么是“h; n; H; x”和“s/\n/:/”，正如我们在前面的例子中所讨论的那样。
以下是此文件中的分支相关行。

 - __`/Manager/!b end`__ - 如果这些行不包含关键字“Manager”，则会转到名为“end”的标签。 
 请注意，标签的名称可以是您想要的任何名称。 因此，这将执行“s/^/\*/”（在前面添加\*），仅适用于Managers。
 - __`:end`__ - 这是标签


__执行label.sed脚本：__

```
$ chmod u+x label.sed
$ ./label.sed empnametitle.txt
John Doe:CEO
*Jason Smith:IT Manager
Raj Reddy:Sysadmin
Anand Ram:Developer
*Jane Miller:Sales Manager
```

