# 拷贝模式空间到保持空间（h 命令）

保持命令（h）拷贝模式空间到保持空间，与x命令不同，h命令不会更改模式空间的内容。
保持空间的先前内容被来自模式空间的内容覆盖。

假设模式空间包含“第1行”，并且保持空间包含“第2行”，执行h命令后，模式空间不会改变，
仍然会有“第1行”，但保持空间也会有“第1行”。

__打印管理员的名称__

```
$ sed -n -e '/Manager/!h' -e '/Manager/{x;p}' empnametitle.txt
Jason Smith
Jane Miller
```

在上面的例子中：
 - `__/Manager/!h__` - 如果模式空间的内容不包含Manager（模式后面的！ “不等于” 模式），则将模式空间的内容复制到
 保留空间。（在这种情况下，这可能是员工姓名（或）不是"Manager"的标题。）请注意，与前面的示例不同，这个不使用
 ‘n’命令来获取下一行；相反，下一行是通过正常的执行流程获取的。

 - `__/Manager/{x;p}__` - 如果模式空间的内容包含关键字“Manager”，则此命令将模式空间与保持空间交换并打印。 
 这与我们在x命令的示例中用于打印的命令相同。

你仍然可以使用脚本文件来执行，像下面这样：

```
$ vi h.sed
#!/bin/sed -nf

/Manager/!h
/Manager/{x;p}

$ chmod u+x empnametitle.txt
$ ./h.sed empnametitle.txt
Jason Smith
Jane Miller
```
