# 1. Sed 命令语法
本节的目的是让你熟悉sed语法和命令格式，这不意味着会解释sed的单个命令
，后面会详细介绍。

__基本的sed语法：__

```
sed [options] {sed-commands} {input-file}
```

sed一次从{input-file}中读取一行，然后在该行上执行{sed-commands}。<br/><br/>
它从{input-file}读取第一行并在该行执行{sed-commands}。接着读取
第二行并执行{sed-commands}，sed不断重复这个过程，直到到达文件
{input-file}的末尾。<br/><br/>
sed还有一些可选的命令行选项可以通过[options]传递给sed。<br/><br/>

以下示例演示基本的sed语法，这个简单的sed示例打印/etc/passwd文件中的所有行。

```
sed -n 'p' /etc/passwd
```

这里主要关注{sed-commands}，它可以是一个sed命令或者多个sed命令，你也可以将
多个sed命令组合写入sed脚本文件中并通过-f选项指定该脚本，如下所示：

__基本的sed语法通过使用sed脚本文件：__

```
sed [options] -f {sed-commands-in-a-file} {input-file}
```

以下示例演示了基本语法，这个例子打印以root和nobody开头的行。

```
$ vi test-script.sed
/^root/ p
/^nobody/ p
$ sed -n -f test-script.sed /etc/passwd
```

在执行多个sed命令时，您也可以直接在命令行指定-e参数，如下所示：

__基本的sed语法使用-e参数：__

```
sed [options] -e {sed-command-1} -e {sed-command-2} {input-file}
```

以下示例演示了基本语法,它将打印/etc/passwd文件中以root和nobody开头的所有行

```
sed -n -e '/^root/ p' -e '/^nobody/ p' /etc/passwd
```

如果你使用-e参数在单行上执行多条sed命令，你可以用 '\' 将他们分成多行，如下所示。

```
sed -n \
-e '/^root/ p' \
-e '/^nobody/ p' \
/etc/passwd
```

你也可以通过命令行指定多个sed命令，通过{}将他们分组：

__基本的sed语法{}：__

```
sed [options] '{
    sed-command-1
    sed-command-2
}' input-file
```

以下示例演示了此版本的基本语法，同样是打印/etc/passwd文件中以root和nobody开头的所有行：

```
sed -n '{
    /^root/ p
    /^nobody/ p
}'  /etc/passwd
```

__注意__：sed从不修改原始文件，它总是打印到标准输出，如果你想保存更改，
可以通过显示指定 >filename.txt 重定向到文件中去。
