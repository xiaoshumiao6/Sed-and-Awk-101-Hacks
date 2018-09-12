# 在MultiLine中删除第一行（D 命令）

如前所述，小写d命令删除当前模式空间，从输入文件读取下一行到模式空间，
终止其余的sed命令并再次启动循环。

大写D命令在删除后不会读取模式空间的下一行，也不会完全清除模式缓冲区（除非它只有一行）。
相反，它执行以下操作：

 - 删除部分模式空间，直到遇到新行（\n）。
 - 终止其余的sed命令，并从模式缓冲区中的剩余内容开始执行命令。

考虑以下文件，其中包含@和@之间的注释，用于每个职位。请注意，在某些情况下，此注释也会跨越多行。 例如@Information Technology officer@跨越两行。

请创建以下示例文件。

```
$ vi empnametitle-with-comment.txt
John Doe
CEO @Chief Executive Officer@
Jason Smith
IT Manager @Information Technology
Officer@
Raj Reddy
Sysadmin @System Administrator@
Anand Ram
Developer @Senior
Programmer@
Jane Miller
Sales Manager @Sales
Manager@
```

我们的目标是从此文件中删除这些注释。这可以使用如下的命令完成：

```
$ sed -e '/@/{N;/@.*@/{s/@.*@//;P;D}}' empnametitle-with-comment.txt
John Doe
CEO
Jason Smith
IT Manager
Raj Reddy
Sysadmin
Anand Ram
Developer
Jane Miller
Sales Manager
```

你也可以将其保存到脚本中执行:

```
$ vi D-upper.sed
#!/bin/sed -f

/@/ {
N
/@.*@/ {s/@.*@//;P;D }
}
$ chmod u+x D-upper.sed
$ ./D-upper.sed empnametitle-with-comment.txt
```

在上面的例子中：

 - __`/@/ {`__ - 这是外循环。Sed查找包含@的任何行。如果它找到一个，它将执行逻辑的其余部分。如果没有，
 它会读取下一行。例如，让我们采用第4行，即“@Information Technology”（注释跨越多列并转到第5行）。 第4行有一个@符号，因此执行其余命令。

 - __`N`__ - 从输入文件中读取下一行，然后附加到模式空间。例如：这将读取第5行“Officer@”，并将其附加到模式空间。
 因此，模式空间将包含“@Information Technology \nOfficer @”。

 - __`/@.*@/`__ - 搜索模式空间是否具有“@.\*@”模式，这意味着@和@之间包含的任何内容。 对于当前模式空间，表达式为true，因此，它将进入下一步。

 - __`s/@.*@//;P;D`__ - 这样就无需替换整个文本“@Information Technology \nOfficer@”（基本上它会删除文本）。
 P打印行的第1部分。 D删除模式空间的其余内容。 并且逻辑再次从顶部继续。
