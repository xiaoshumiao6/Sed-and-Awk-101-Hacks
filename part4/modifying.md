# 直接修改文件

正如你早就知道的，sed默认不会修改输入文件，sed将输出写到了标准输出上，当你想将它存储在文件中时，你将它重定向到一个文件（或者使用w命令。）在继续此例之前，请先备份employee.txt:

```
cp employee.txt employee.txt.orig
```

要直接在输入文件上进行修改，通常会将输出重定向到临时文件，然后将临时文件重名为新文件。

```
sed 's/John/Johnny/' employee.txt > new-employee.txt
mv new-employee.txt employee.txt
```

除此之外，你可以使用sed命令行参数__-i__，这将直接修改输入文件。

__用原始的employee.txt文件本身将John替换为Johnny__:

```
$ sed -i 's/John/Johnny/' employee.txt

$ cat employee.txt
101,Johnny Doe,CEO
102,Jason Smith,IT Manager
103,Raj Reddy,Sysadmin
104,Anand Ram,Developer
105,Jane Miller,Sales Manager
```

请再次注意，__-i__修改了输入文件，有时你可能想要这样做，但是要非常小心。你可以通过在使用-i时添加一个文件扩展名来做保护。在编写新内容之前，Sed会对原始文件进行备份。

__在原始employee.txt文件中将John替换为Johnny，但保存备份副本。__

```
$ sed -ibak 's/John/Johnny/' employee.txt
```

原始文件的备份如下所示：

```
$ cat employee.txtbak
101,John Doe,CEO
102,Jason Smith,IT Manager
103,Raj Reddy,Sysadmin
104,Anand Ram,Developer
105,Jane Miller,Sales Manager
```

原始文件已经被上面的sed命令修改。

```
$ cat employee.txt
101,Johnny Doe,CEO
102,Jason Smith,IT Manager
103,Raj Reddy,Sysadmin
104,Anand Ram,Developer
105,Jane Miller,Sales Manager
```

除了-i，你还可以使用长选项__--in-place__，已下两个命令都是相同的。

```
sed -ibak 's/John/Johnny/' employee.txt
sed --in-place=bak 's/John/Johnny/' employee.txt
```

最后，恢复原始的employee.txt文件，因为我们需要对其余的示例继续使用它。

```
cp employee.txt.orig employee.txt
```
