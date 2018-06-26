# 命令作用于多个文件之上

在我们之前所有的例子中，我们都是使用了单个输入文件，你可以指定多个输入文件。

下面的例子在/etc/passwd文件中搜寻“root”关键字，并打印出来.

```
$ sed -n '/root/ p' /etc/passwd
root:x:0:0:root:/root:/bin/bash
```

同上，在另一个文件/etc/group中做同样的操作

```
$ sed -n '/root/ p' /etc/group
root:x:0:
```

结合上面两个例子，在两个文件中搜寻“root”关键字并打印

```
$ sed -n '/root/ p' /etc/passwd /etc/group
root:x:0:0:root:/root:/bin/bash
root:x:0:
```

