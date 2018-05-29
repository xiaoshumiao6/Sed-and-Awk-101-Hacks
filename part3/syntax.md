# 行首（^）
符号__^__匹配一行的开始

__打印103开头的行:__

```
$ sed -n '/^103/ p' employee.txt
103,Raj Reddy,Sysadmin
```
{% em type="yellow" %}注意{% endem %}:__^__匹配表达式的行首，当且仅当它是正则表达式中的第一个字符。在这个例子中，^N匹配所有以N开头的行。

# 行尾（$）
符号__$__匹配一行的结尾

__打印以字母r结尾的行:__

```
$ sed -n '/r$/ p' employee.txt
102,Jason Smith,IT Manager
104,Anand Ram,Developer
105,Jane Miller,Sales Manager
```

# 单个字符（.）
特殊的元字符__"."__匹配除了换行符以外的所有字符。
  * __.__   匹配单个字符
  * __..__  匹配两个字符
  * __...__ 匹配三个字符
  * 以此类推...

在下面的这个例子中，模式J后面跟了三个点"__.__"和一个空格,它将被Jason后面跟一个空格取代。
因此， "__J...__"从employee.txt中匹配了"John"和"Jane"，这两行都将被替换，如下所示：

```
$ sed -n 's/J... /Jason /p' employee.txt
101,Jason Doe,CEO
105,Jason Miller,Sales Manager
```

# 0次或多次匹配（\*）
特殊字符"__\*__"（星号）0次或多次匹配前一个字符，例如'__a\*__'表示匹配a 0次或者多次

__创建如下log.txt文件：__

```
$ vi log.txt
log: Input Validated
log:
log:  testing resumed
log:
log:output created
```

假设只想查看包含"log:"的消息，在"log:"后面可能是一条消息也可能是一些空格，你不想要那些没有包含任何消息的"log:"行。

__打印包含"log:"后面紧接着是一个或多个空格，然后是其他字符的所有行__

```
$ sed -n '/log: *./ p' log.txt
log: Input Validated
log:  testing resume
log:output created
```

{% em type="yellow" %}注意{% endem %}：在正则的最后的"__.__"是必要的，如果没有，它将只打印所有包含"log:"的行。

# 匹配至少一次（\\+）
特殊字符"__\\+__"匹配前一个字符至少1次，例如如果"__\\+__"前面是一个空格，表示匹配1个或多个空格，至少出现一次。
让我们再次使用log.txt举例

__打印所有包含"log:"后面紧接着至少超过1个空格的所有行__

```
$ sed -n '/log: \+/ p' log.txt
log: Input Validated
log:  testing resumed
```

{% em type="yellow" %}注意{% endem %}：不是匹配"log:",需要后面有超过1个空格的行，"log:output created"这行无法匹配，因为后面没有出现至少1个空格

# 匹配0次或1次（\\?）
特殊字符"__?__"匹配前一个字符0次或1次，例如：

```
$ sed -n '/log: \?/ p' log.txt
log: Input Validated
log:
log:  testing resumed
log:
log:output created
```

# 转译字符（\\）
当你需要匹配特殊的正则字符（例如：\*，__.__）你需要在正则表达式使用转译字符。

```
$ sed -n '/127\.0\.0\.1/ p' /etc/hosts
127.0.0.1       localhost.localdomain localhost
```

# 字符类（[0-9]）
字符类是只不过是[]方括号里字符列表，这只用于匹配几个中的一个字符

__匹配每行中包括2或者3或者4的行：__

```
$ sed -n '/[234]/ p' employee.txt
102,Jason Smith,IT Manager
103,Raj Reddy,Sysadmin
104,Anand Ram,Developer
```

方括号中的字符，可以使用连字符"__-__"来指定一个范围，例如[0123456789]可以通过[0-9]表示，还可以指定字母范围，如[a-z]，[A-Z]等等。。。

__匹配每行中包括2或者3或者4的行（替代形式）：__

```
$ sed -n '/[2-4]/ p' employee.txt
102,Jason Smith,IT Manager
103,Raj Reddy,Sysadmin
104,Anand Ram,Developer
```
