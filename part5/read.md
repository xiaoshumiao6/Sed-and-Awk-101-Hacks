# 读取额外文件

Sed的 r 命令从额外的文件中读内容，然后打印到输入文件的指定位置。下面的例子将从log.txt中读取内容，打印到employee.txt文件的末尾。这是一个经典的使用方法，
结合2个文件的内容将其打印出来。

```
$ sed '$ r log.txt' employee.txt
```

你也可以对 r 命令使用模式空间。下面的例子将会从log.txt中读取内容，然后打印到employee.txt中匹配到“Raj”所在行之后。

```
$ sed '/Raj/ r log.txt' employee.txt
```
