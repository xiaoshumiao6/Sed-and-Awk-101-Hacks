# 打印标志（p falg）

Sed替换标志p代表打印，当替换成功后，它会打印发生替换的行，像
大多数sed打印命令一样，它与-n参数结合时非常有用，默认打印所有行。

__只打印发生替换的行__:

```
$ sed -n 's/John/Johnny/p' employee.txt
101,Johnny Doe,CEO
```

在我们的数字标志示例中，我们使用/2去指定第二次出现的"locate"被替换成"find",
在substitute-locate.txt文件中第3行没有出现第2次"locate"，因此未发生替换，
现在给我们之前使用的命令添加p标志，打印出发生更改的2行。


__将第2次出现的"locate"替换为"find"，并打印结果__:

```
$ sed -n 's/locate/find/2p' substitute-locate.txt
locate command is used to find files
locate command uses database to find files
```
