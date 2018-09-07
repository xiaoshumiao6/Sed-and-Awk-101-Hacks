# 交换模式空间与保持空间

Sed的交换命令（x）交换保持空间与模式空间，除非将他和其他的sed命令结合使用，
否则此命令本身没有什么用处;但是，结合其他命令，它非常强大。

假设模式空间包含“第1行”，并且保持空间包含“第2行”，执行x命令后，模式空间将具有
“第2行”，保持空间将具有“第1行”。

以下命令将打印管理者的name，它寻找关键字“Manager”，并打印上一行

__从empnametitle.txt文件打印管理者名称__

```
$ sed -n -e 'x;n' -e '/Manager/{x;p}' empnametitle.txt
Jason Smith
Jane Miller
```

在上面这个例子中：
 - __`{x;n}`__ - x交换模式空间到保持空间; n将下一行读入模式空间。因此，此命令将当前行
 保存在保持空间中，并将下一行读入模式空间。对于示例文件，保存员工姓名到保持空间
 并将员工标题提取到模式空间中。

 - __`/Manager/{x;p}`__ - 如果模式空间的内容包含关键字“Manager”，此命令将模式空间与保留
 空间交换，然后打印模式空间。这意味着如果员工职称包含“Manager”，则将打印员工姓名

您也可以将其保存在sed脚本文件中并执行它，如下所示：

```
$ vi x.sed

#!/bin/sed -nf
x;n
/Manager/{x;p}

$ chmod u+x empnametitle.txt

$ ./x.sed empnametitle.txt
Jason Smith
Jane Miller
```
