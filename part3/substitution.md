# 正则替换

下面是几个使用正则表达式替换的例子。

__将employee.txt中每行中最后两个字符替换为“,Not Defined”__:

```
$ sed 's/..$/,Not Defined/' employee.txt
101,John Doe,C,Not Defined
102,Jason Smith,IT Manag,Not Defined
103,Raj Reddy,Sysadm,Not Defined
104,Anand Ram,Develop,Not Defined
105,Jane Miller,Sales Manag,Not Defined
```

__删除每行从“Manager”开始的后面的内容__

```
$ sed 's/Manager.*//' employee.txt
101,John Doe,CEO
102,Jason Smith,IT
103,Raj Reddy,Sysadmin
104,Anand Ram,Developer
105,Jane Miller,Sales
```

__删除所有行中“#”后面的注释内容并且删除空行__

```
sed -e 's/#.*// ; /^$/ d' employee.txt
```

创建如下test.html文件用于接下来的例子。

```
$ vi test.html
<html><body><h1>Hello World!</h1></body></html>
```

__从test.html中去掉所有的html标签__

```
$ sed -e 's/<[^>]*>//g' test.html
Hello World!
```

{% em type="yellow" %}注意{% endem %}:__\[^>\]__表示过滤（排除）掉"<"后面紧接着是">"的情况。

__删除所有注释和空行__

```
sed -e 's/#.*//' -e '/^$/ d' /etc/profile
```

__只删除所有出现注释的行，保留空行__

```
sed -e '/^#.*/ d' /etc/profile
```

您可以使用sed将DOS换行符（CR/LF）转换为Unix格式。 将DOS文件复制到Unix时，可以在每行的末尾找到\r\n。
 
__转换DOS文件格式为Unix文件格式使用如下命令__

```
sed 's/.$//' filename
```
