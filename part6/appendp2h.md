# 追加模式空间到保持空间（H 命令）

大写的H是追加模式空间的行到保持空间，以前保持空间的内容不会被覆盖;
相反会在末尾增加新行，将模式空间的内容追加到保留空间的现有内容。

假设模式空间包含“第1行”并且保持空间包含“第2行”; 执行H命令后，模式空间不会改变，、
仍然会有“第1行”，但保持空间将有“第1行\n第2行”。

__打印managers的姓名和职务（分开排列）__

```
$ sed -n -e '/Manager/!h' -e '/Manager/{H;x;p}' empnametitle.txt
Jason Smith
IT Manager
Jane Miller
Sales Manager
```

在上面的例子中：
 - `__/Manager/!h__` - 如果模式空间的内容不包含Manager（模式后面的！“不等于” 模式），则将模式空间的内容复制到保持空间。 （在这种情况下，
 这可能是员工姓名（或）不是“经理”的标题。）这与我们在h命令示例中使用的命令相同。

 - `__/Manager/{H;x;p}__` - 如果模式空间的内容包含关键字“Manager”，则H命令会追加模式空间（即Manager）以使用新行保留空间。
 因此，此阶段的保留空间将具有“Employee Name \ nTitle”（其中包含关键字manager）。 x命令交换保持空间到模式空间，并且p打印图案空间。


 你也可以将命令保存到脚本中执行，像下面这样：

```
$ vi H-upper.sed
#!/bin/sed -nf

/Manager/!h
/Manager/{H;x;p}

$ chmod u+x H-upper.sed
$ ./H-upper.sed empnametitle.txt
Jason Smith
IT Manager
Jane Miller
Sales Manager
```

如果您希望员工的姓名与职务打印在同一行，可以稍微修改上面的示例，以“：”作为分隔符

```
$ sed -n -e '/Manager/!h' -e '/Manager/{H;x;s/\n/:/;p}' empnametitle.txt
Jason Smith:IT Manager
Jane Miller:Sales Manager
```

在第二个示例中，除了添加到第二个-e选项的替换命令之外，所有内容都与前一个示例相同。 
H，x和p命令与以前一样; s命令用：替换\n， 替换后打印。 因此，姓名和职务打印在一行上，用冒号分隔。

你可以将命令用脚本执行，像下面这样：

```
$ vi H1-upper.sed
#!/bin/sed -nf

/Manager/!h
/Manager/{H;x;s/\n/:/;p}

$ chmod u+x H1-upper.sed
$ ./H1-upper.sed empnametitle.txt
Jason Smith:IT Manager
Jane Miller:Sales Manager
```
