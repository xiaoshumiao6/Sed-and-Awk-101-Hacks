# Sed替换命令语法

```
sed '[address-range|pattern-range] s/original-string/replacement-string/[substitute-flags]' inputfile
```

在上面的替换命令语法中:
  * address-range|pattern-range -- 地址范围或者模式范围是可选的，如果你没有指定任何一个，sed将在所有行上执行替换命令。
  * s -- 告诉sed执行替换。
  * original-string -- 这是待搜索的原始字符串， 原始字符串也可以是正则表达式。
  * replacement-string -- 这是用来替换原始字符串的字符串。
  * substitute-flags --替换标志，可选的，下一节将介绍这点。

请记住，原始文件不会被修改。替换发生在模式空间缓冲区，随后会被打印到标准输出。<br/>

以下是几个简单的sed替换示例（更改以{% em color="#ff0000" %}红色{% endem %}显示）。<br/>

__替换所有出现的Manager为Director__:

```
**[terminal]
$ sed 's/Manager/Director/' employee.txt
101,John Doe,CEO
102,Jason Smith,IT **[error Director]
103,Raj Reddy,Sysadmin
104,Anand Ram,Developer
105,Jane Miller,Sales **[error Director]
```
----

__在只包含关键字Sales的行将出现的Manager替换为Director__:

```
**[terminal]
$ sed '/Sales/s/Manager/Director/' employee.txt
101,John Doe,CEO
102,Jason Smith,IT Manager
103,Raj Reddy,Sysadmin
104,Anand Ram,Developer
105,Jane Miller,Sales **[error Director]
```

{% em style="yellow" %}注意{% endem %}: 地址范围的使用只会导致一个更改，不像前面的例子有两处更改。
