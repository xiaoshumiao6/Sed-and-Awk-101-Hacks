# 退出命令 q

sed的q命令会使sed的执行终止。<br>
正如我们之前介绍的，正常的sed执行流是Read、Execute、Print、Repeat. <br>
当sed遇到q命令，只是退出而不执行其余的sed命令，并且不必重复输入文件的其他行

__打印第一行后退出__

```
$ sed 'q' employee.txt
101,John Doe,CEO
```

__打印5行后退出__

```
$ sed '5 q' employee.txt
101,John Doe,CEO
102,Jason Smith,IT Manager
103,Raj Reddy,Sysadmin
104,Anand Ram,Developer
105,Jane Miller,Sales Manage
```

__打印所有行，直到遇到‘Manager’关键字停下来__

```
$ sed '/Manager/q' employee.txt
101,John Doe,CEO
102,Jason Smith,IT Manager
```

{% em type="yello" %}注意{% endem %}:q命令不用于地址空间（范围内），它仅适用于单一地址。（或单一模式）
