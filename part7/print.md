# 在MultiLine中打印第一行（P 命令）

到目前为止，我们已经看到三个大写命令，每个命令都附加到而不是替换缓冲区的内容。 
我们现在将看到大写P和D以类似于它们的小写等价的方式操作，但它们也做了与MultiLine缓冲区有关的特殊事情。

如前所述，小写p命令打印模式空间。 大写P命令也打印模式空间，但只有在遇到新行（\n）时才会打印。
以下示例打印empnametitle.txt文件中的所有managers的姓名

```
$ sed -n -e 'N' -e '/Manager/P' empnametitle.txt
Jason Smith
Jane Miller
```
