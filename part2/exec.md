# 执行标志（e falg）

Sed替换标志e表示执行，使用sed的e标志，你可以在模式空间中执行任何可用的
shell命令，输出将重新返回到模式空间。这个仅在GNU Sed中可用，以下是几个例子。

__如下例，请创建以下file.txt，其中包含具有完整路径的文件名列表__:

```
$ cat files.txt
/etc/passwd
/etc/group
```

__在file.txt的每行前面增加文本 "ls -l" ，并输出__:

```
$ sed 's/^/ls -l /' files.txt
ls -l /etc/passwd
ls -l /etc/group
```

__在file.txt的每行前面增加文本 "ls -l" ，并执行输出__:

```
$ sed 's/^/ls -l /e' files.txt
-rw-r--r-- 1 root root 1547 Oct 27 08:11 /etc/passwd
-rw-r--r-- 1 root root 651 Oct 27 08:11 /etc/group
```
