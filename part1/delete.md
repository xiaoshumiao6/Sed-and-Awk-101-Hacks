# 删除行（p命令）

使用d命令，你可以删除行，请注意该行只是从输出流中删除，类似于其他的
sed命令，d命令不会修改输入文件的原始内容。<br/>

默认情况下，如果不在sed命令前指定地址范围，它会匹配所有行。所以下面的
例子不会打印任何内容，因为它匹配到employee.txt中所有行然后删除它们。

```
$ sed 'd' employee.txt
```
----
最好的方式是指定地址范围去删除，接下来是一些例子：

__只删除第2行__:

```
$ sed '2 d' employee.txt
101,John Doe,CEO
103,Raj Reddy,Sysadmin
104,Anand Ram,Developer
105,Jane Miller,Sales Manager
```
----

__删除1~4行__:

```
$ sed '1,4 d' employee.txt
105,Jane Miller,Sales Manager
```
----

__删除从第2行开始以后所有行__:

```
$ sed '2,$ d' employee.txt
101,John Doe,CEO
```
----

__删除奇数行__:

```
$ sed '1~2 d' employee.txt
102,Jason Smith,IT Manager
104,Anand Ram,Developer
```
----

__删除匹配到"Manager"的行__:

```
$ sed '/Manager/ d' employee.txt
101,John Doe,CEO
103,Raj Reddy,Sysadmin
104,Anand Ram,Developer
```

----

__删除从第1行开始匹配到"Jason"后，一直删到第4行__:

```
$ sed '/Jason/,4 d' employee.txt
101,John Doe,CEO
105,Jane Miller,Sales Manager
```

{%em color="#ff0000" %}注意{% endem %}: 如果前4行没有匹配到，则后面只删除匹配到的行。

___

__删除从匹配到"Raj"开始后面所有的行__:

```
$ sed '/Raj/,$ d' employee.txt
101,John Doe,CEO
102,Jason Smith,IT Manager
```
----

__删除从匹配到"Raj"开始，直到匹配到"Jane"的中间所有行（包括匹配行）__:

```
$ sed '/Raj/,/Jane/ d' employee.txt
101,John Doe,CEO
102,Jason Smith,IT Manager
```
----

__删除从匹配到"Jason"开始，延伸到后面2行__:

```
$ sed '/Jason/,+2 d' employee.txt
101,John Doe,CEO
105,Jane Miller,Sales Manager
```

----

## 有用的删除示例

以下示例在实际的日常工作中非常有用。<br/>



__删除文件所有的空行__:

```
$ sed '/^$/ d' employee.txt
```

----

__删除所有的注释行（假设注释以#开头）__:

```
$ sed '/^#/ d' employee.txt
```
<br/>
{% em color="#ff0000" %}注意{% endem %}:当你有多个sed命令时，在遇到d命令时，整个匹配行将会被删除，并且不会进一步在删除行执行后续命令。
