# OR 操作符（|）

管道符（|）用于指定可能出现在位置上的两个整体中的任意一个，“子表达式1|子表达式2”匹配其中的子表达式1或者子表达式2

__打印包含101或者102的行__

```
$ sed -n '/101\|102/ p' employee.txt
101,John Doe,CEO
102,Jason Smith,IT Manager
```

请注意，“|”符号用“\\”来转译。

__打印包含字符2-3中的任意一个或者包含字符串105的行__

```
$ sed -n '/[2-3]\|105/ p' employee.txt
102,Jason Smith,IT Manager
103,Raj Reddy,Sysadmin
105,Jane Miller,Sales Manager
```

# 确切出现的次数M（{m}）

正则表达式后跟{m}，匹配前面的表达式m次。

请创建如下numbers.txt文件用于例子演示。

```
$ vi numbers.txt
1
12
123
1234
12345
123456
```

__打印包含任意个连续数字字符的行（将会打印所有行）__

```
$ sed -n '/[0-9]/ p' numbers.txt
1
12
123
1234
12345
123456
```

__打印只由连续5位数字字符组成的行__

```
$ sed -n '/^[0-9]\{5\}$/ p' numbers.txt
12345
```

# M ~ N 次出现（{m,n}）

正则表达式后跟{m,n}表示匹配前面的表达式至少m次，最多不超过n次（包含n），该m和n的值必须是非负值，并且要小于255。

__打印包含连续数字字符至少3个，但是不超过5个的行__

```
$ sed -n '/^[0-9]\{3,5\}$/ p' numbers.txt
123
1234
12345
```

正则表达式后面跟{m,}是一种特殊情况，表示匹配前面的表达式至少连续出现m次，没有最高限制，同理{,n}表示匹配前面的表达式连续出现次数不超过n次（包含n次）

# 单词边界（\b）

\b被用来匹配单词边界。\b匹配单词以（\bxx）开头或以（xx\b）结尾的任何字符，因此，“\bthe\b”将只会匹配单词the而不是其他，"\bthe"将会匹配the或者the开头的单词。

创建如下测试例子：

```
$ cat words.txt
word matching using: the
word matching using: thethe
word matching using: they
```

__匹配包含单词“the”的行__

```
$ sed -n '/\bthe\b/ p' words.txt
word matching using: the
```
请注意，如果没有在末尾指定\b，则会匹配所有行。

__匹配包含“the”开头单词的行__

```
$ sed -n '/\bthe/ p' words.txt
word matching using: the
word matching using: thethe
word matching using: they
```


# 反向引用（\n）

反向引用可以将表达式分组以供进一步使用

__匹配包含单词“the”且重复出现2次的行__

```
sed -n '/\(the\)\1/ p' words.txt
word matching using: thethe
```

使用相同的逻辑，正则表达式“\([0-9]\)\1”匹配连续两位数字字符都是相同数字的行，例如:11, 22, 33
