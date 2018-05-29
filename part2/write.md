# 写标志（w falg）

Sed替换标志w代表写入，当替换成功后，将发生更改的行写入文件。但是大多数人使用
p标志，并将输出重定向到一个文件中去。接下看完整的例子。

__将发生替换的行写入到output.txt文件中去__:

```
$ sed -n 's/John/Johnny/w output.txt' employee.txt
$ cat output.txt
101,Johnny Doe,CEO
```
----

就像我们p命令显示的一样，将w标志添加到我们substitute-locate.txt文件的示例中，
将会把发生更改的两行写入output文件中去

__将第2次出现的"locate"替换为"find"，将结果写入文件的同时，打印所有行__:

```
$ sed 's/locate/find/2w output.txt' substitute-locate.txt
locate command is used to find files
locate command uses database to find files
locate command can also use regex for searching
$ cat output.txt
locate command is used to find files
locate command uses database to find files
```
