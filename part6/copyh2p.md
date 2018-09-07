# 拷贝保持空间到模式空间（g 命令）

Sed get（g）命令将保持空间的内容复制到模式空间。

可以这样想：h命令在保持空间中“保持”它，g命令从保持空间“获取”它。

假设模式空间包含“第1行”并且保持空间包含“第2行”; 执行g命令后，模式空间改变，现在包含“第2行”，而保持空间不变，仍然包含“第2行”。

__打印managers的姓名__

```
$ sed -n -e '/Manager/!h' -e '/Manager/{g;p}' empnametitle.txt
Jason Smith
Jane Miller
```

在上面的例子中：

 - `__/Manager/!h__` - 我们在最后几个例子中一直使用这个。 如果模式空间的内容不包含Manager，则复制模式空间的内容到保持空间

 - `__/Manager/{g;p}__` - g 从保持空间获取该行并将其放入模式空间，然后打印它。

你也可以将其保存到脚本文件中，像下面这样：

```
$ vi g.sed
#!/bin/sed -nf

/Manager/!h
/Manager/{g;p}

$ chmod u+x g.sed
$ ./g.sed empnametitle.txt
Jason Smith
Jane Miller
```
