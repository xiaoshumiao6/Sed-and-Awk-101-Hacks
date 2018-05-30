# 注释

注释以"#"开头，我们都明白，sed使用非常神秘的语言。如果您在隔了很长一段时间再去查看它们，您可能看着并不熟悉。因此，建议在sed脚本文件中使用注释来表明您的意思。

```
$ vi mycommands.sed
# Swap field 1 (employee id) with field 2 (employee name)
s/\([^,]*\),\([^,]*\),\(.*\).*/\2,\1,\3/g
# Enclose the whole line within < and >
s/^.*/<&>/
# Replace Developer with IT Manager
s/Developer/IT Manager/
# Replace Manager with Director
s/Manager/Director/
```
{% em type="yellow" %}注意{% endem %}:如果sed脚本中第一行的前两个字符是#n，sed将自动使用-n（不打印模式缓冲区）选项。

