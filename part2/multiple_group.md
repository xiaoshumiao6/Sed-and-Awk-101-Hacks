# 分组替换（多组）

在多分组中，可以将多个组包含在多个"\\("和"\\)"中。 如果在替代正则表达式中有多个组，
则可以使用\n指定sed替换字符串中的第n个组。 一个例子如下所示。

__只获得第一列（employee id）和第三列（title）：__:

```
$ sed 's/\([^,]*\),\([^,]*\),\([^,]*\).*/\1,\3/g' employee.txt
101,CEO
102,IT Manager
103,Sysadmin
104,Developer
105,Sales Manager
```

在上面的例子中，你可以看到{original-string}（reg-ex）中提到的三个组。这三个组由逗号分隔。
  * (\[^,\]\*\)是employee id匹配的组1, 
  * ','是组1后面的字段分隔符
  * (\[^,\]\*\)是employee name匹配的组2 
  * ','是组2后面的字段分隔符
  * (\[^,\]\*\)是employee title匹配的组3
  * ','是组3后面的字段分隔符,上面的{replacement-string}示例指明了如何使用这些组
  * \1 打印组1（employee id）
  * ','是在组1打印之后，紧接着打印的部分
  * \3 打印组3（title）

{% em type="yellow" %}注意{% endem %}：Sed最多可以容纳9组的引用，\1 ~ \9

__交换字段1（employee id），字段2（employee title）; 打印employee.txt文件：__:

```
$ sed 's/\([^,]*\),\([^,]*\),\(.*\).*/\2,\1,\3/g' employee.txt
John Doe,101,CEO
Jason Smith,102,IT Manager
Raj Reddy,103,Sysadmin
Anand Ram,104,Developer
Jane Miller,105,Sales Manager
```
