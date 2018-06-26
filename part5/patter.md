# 打印模式空间（n）

sed n命令打印当前模式空间并从输入文件中提取下一行。这发生在命令执行的中间，所以如果它发生在其他命令之间，它可以改变正常流程。

__打印每行的模式空间__

```
$ sed n employee.txt
101,John Doe,CEO
102,Jason Smith,IT Manager
103,Raj Reddy,Sysadmin
104,Anand Ram,Developer
105,Jane Miller,Sales Manager
```

如果你使用n命令的同时使用了-n标志，sed将不会打印任何东西。

```
$ sed -n n employee.txt
```

正如我们前面所讨论的，普通的sed执行流程是Read，Execute（所有可用的sed命令），Print，Repeat。<br>
sed n命令可让您更改该流程。 sed n命令将打印当前模式空间，清除当前模式空间，从输入文件读取下一行，并继续执行命令流程。<br>

让我们假设你有2个sed命令，之前和之后有2个sed命令,如下所示。

```
sed-command-1
sed-command-2
n
sed-command-3
sed-command-4
```

在这种情况下，sed-command-1和sed-command-2将应用于模式空间中的当前行; 当sed遇到n命令时，它将从模式空间中清除当前行，从输入文件读取下一行，
并将sed-command-3和sed-command-4应用于sed模式中的新读取行空间。<br>

{% em type="yello" %}注意{% endem %}: 正如你在上面的例子中看到的那样，sed n命令本身相对没有用处。但是，它与以下黑客中讨论的sed保留模式命令结合使用时功能非常强大。
