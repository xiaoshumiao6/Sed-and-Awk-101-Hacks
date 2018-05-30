# 多组Sed命令的执行

正如我们在第一章中所讲的那样，有好几种方法来执行来自命令行的多个sed命令

## 在命令行使用-e参数

使用sed命令的-e参数，使用方法如下：

```
sed -e 'command1' -e 'command2' -e 'command3'
```

__在/etc/passwd文件中搜索"root"或者"nobody"或者"mail"__

```
sed -n -e '/^root/ p' -e '/^nobody/ p' -e '/^mail/ p' /etc/passwd
```

## 使用"\\"分解sed的命令

当你的命令很长，例如在一行命令中使用-e参数指定好几个sed命令，你可以使用"\\"进行分解。

```
sed -n -e '/^root/ p' \
-e '/^nobody/ p' \
-e '/^mail/ p' \
/etc/passwd
```

## 使用{}对命令分组

当你有很少的sed命令组需要被执行，你可以通过"{}"统一分组，例如：

```
sed -n '{
    /^root/ p
    /^nobody/ p
    /^mail/ p
}' /etc/passwd
```
