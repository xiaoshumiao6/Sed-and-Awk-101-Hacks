# sed命令行参数

## -n

我们早就讨论过这个参数并且在很多例子中用到了它。sed的-n参数禁止sed流程中的默认打印。<br>
你也可以使用--quiet 或者 --silent 而不是-n，他们在功能上是相同的。

__以下写法结果是一样的__

```
sed -n 'p' employee.txt
sed --quiet 'p' employee.txt
sed --silent 'p' employee.txt
```

## -f

你可以将多个sed命令组合到一个文件中，并且使用-f选项调用sed脚本，我们之前已经证明了这一点，你也可以使用--file


__以下写法结果一致__

```
sed -n -f test-script.sed /etc/passwd
sed -n --file=test-script.sed /etc/passwd
```

## -e

使用-e从命令行执行sed命令脚本。 您可以从命令行使用多个-e选项。 你也可以使用--expression。

__以下写法结果一致__

```
sed -n -e '/root/ p' /etc/passwd
sed -n --expression '/root/ p' /etc/passwd
```

## -i

正如我们已经讨论过的，sed不会修改输入文件。它总是打印到标准输出，或者您可以使用w命令将输出写入到不同的文件。 我们还展示了sed如何使用-i选项直接修改输入文件。


__替换John为Johnny并应用修改到原文件中__

```
sed -i 's/John/Johnny/' employee.txt
```

__执行相同的命令，但通过将扩展名bak传递给-i来进行原文件的备份__

```
sed -ibak 's/John/Johnny/' employee.txt
```

也可以使用--in-place来替代-i

__以下写法结果一致__

```
sed -ibak 's/John/Johnny/' employee.txt
sed --in-place=bak 's/John/Johnny/' employee.txt
```

## -c

这应该与sed的-i选项一起使用，sed的-i通常使用临时文件创建更改，并在其操作完成时将其更名为原始输入文件。这可能会导致文件所有权发生变化。与-i一起使用时，输入文件的
所有权不会更改。你也可以使用--copy.

__以下写法结果一致__

```
sed -ibak -c 's/John/Johnny/' employee.txt
sed --in-place=bak --copy 's/John/Johnny/' employee.txt
```

## -l

指定行长，需要与sed的l命令一起使用。在-l选项中指定的值将用作行大小。你也可以使用--line-length

__以下写法结果一致__

```
sed -n -l 20 'l' employee.txt
sed -n --line-length=20 employee.txt
```

请注意，您也可以在不指定-n选项的情况下获得相同的输出，如下所示。

```
sed -n 'l 20' employee.txt --posix option
```
