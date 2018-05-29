# sed替换定界符

在上面所有的sed例子中，我们使用sed默认的分割符'/'，即
{s/original-string/replacement-string/} 当原始字符串或替换字符串中包含'/'字符，我们需要使用
'\'进行转义，在本例中，我们创建一个包含目录路径的path.txt文件，如下所示。

```
$ vi path.txt
reading /usr/local/bin directory
```

现在，让我们替换/usr/local/bin 为 /usr/bin ,在这个替换例子中，{original-string} 和
{replacement-string}中的路径定界符'/'需要使用反斜杠'\'进行转义。

```
$ sed 's/\/usr\/local\/bin/\/usr\/bin/' path.txt
reading /usr/bin directory
```

很丑陋不是吗？当你试图替换一个长路径名时，使用'\'转义字符可能会非常混乱。幸运的是，你可以使用任何字符作为分隔符。
例如 | 或者 ^ 或者 @ 或者 ！ 。<br/>

以下示例均有效且易于阅读。我在这里没有展示结果，因为输出和上面的例子是一样的，在替换路径的时候，我更喜欢使用
@（或者!）符号，但这取决于您的个人选择。

```
sed 's|/usr/local/bin|/usr/bin|' path.txt
sed 's^/usr/local/bin^/usr/bin^' path.txt
sed 's@/usr/local/bin@/usr/bin@' path.txt
sed 's!/usr/local/bin!/usr/bin!' path.txt
```
