# 数字标志（1,2,3... flag）

使用数字标志来指定{origin-string}在该行出现的第几次，只有{origin-string}出现的第n
次位置会发生替换。计数从没哦一行开始，n可以是从1-512的任何一个数字。<br/>

__将第2次出现的小写字母a替换为[A]__：

```
$ sed 's/a/[A]/2' employee.txt
101,John Doe,CEO
102,Jason Smith,IT M[A]nager
103,Raj Reddy,Sys[A]dmin
104,Anand R[A]m,Developer
105,Jane Miller,S[A]les Manager
```
----

__对于这个例子，我们使用如下3行创建这个文件__:

```
$ vi substitute-locate.txt
locate command is used to locate files
locate command uses database to locate files
locate command can also use regex for searching
```

__在刚刚创建的文件中，只有第2次出现的locate被替换成find__:

```
$ sed 's/locate/find/2' substitute-locate.txt
locate command is used to find files
locate command uses database to find files
locate command can also use regex for searching
```

{% em type="yellow" %}注意{% endem %}: 在上面例子中，substitute-locate.txt文件的第3行只有一个locate出现，
所以未发生替换。
