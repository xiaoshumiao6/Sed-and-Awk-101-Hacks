# 模拟Unix命令（cat、grep、head）

我们已经看到了与其他标准UNIX命令非常相似的例子。 使用sed你可以模拟许多命令, 这样做只是为了了解sed是如何工作的。

## Cat

```
cat employee.txt
```

以下每个sed命令都会产生与上述cat命令相同的输出。

```
sed 's/JUNK/&/p' employee.txt
sed -n 'p' employee.txt
sed 'n' employee.txt
sed 'N' employee.txt
```

## Grep


```
grep Jane employee.txt
```

以下每个sed命令都会产生与上述grep命令相同的输出。

```
sed -n 's/Jane/&/p' employee.txt
sed -n '/Jane/ p' employee.txt
```

__grep -v (打印非匹配行)__

```
grep -v Jane employee.txt
```

下面的命令等价于上面的 "grep -v" 命令

```
sed -n '/Jane/ !p' employee.txt
```

## Head

```
head -10 /etc/passwd
```

以下每个sed命令都会产生与上述head命令相同的输出。

```
sed '11,$ d' /etc/passwd
sed -n '1,10 p' /etc/passwd
sed '10 q' /etc/passwd
```
