# 多个替换命令作用到同一行上

如前所述，sed执行流程是Read，Excute，Print，Repeat。正如我们所提到的，执行部分可能包含
多个sed命令，sed将会逐个执行。<br/>

例如，你有2个sed命令，sed将会在模式空间上执行命令1，然后执行命令2。如果命令1更改了模式
空间的某些内容，命令2将接着在当前模式空间的内容上做执行（而不是读取原始行）。<br/>

以下示例演示在模式空间上2个sed替换命令的执行。


__替换"Developer"为"IT Manager", 然后替换"Manager"为"Director"__:

```
$ sed '{
    s/Developer/IT Manager/
    s/Manager/Director/
}' employee.txt
101,John Doe,CEO
102,Jason Smith,IT Director
103,Raj Reddy,Sysadmin
104,Anand Ram,IT Director
105,Jane Miller,Sales Director
```

让我们分析一下第4行sed的执行流程：

__1. Read:__在这个阶段，Sed读出该行并将其放入模式空间。所以以下模式空间的内容。

```
104,Anand Ram,Developer
```

__2. Execute:__Sed在模式空间执行第一个命令 s/Developer/IT Manager/。因此，在这个命令
之后，以下是模式空间的内容。

```
104,Anand Ram,IT Manager
```

现在，sed开始在模式空间上执行第2个命s/Manager/Director/。在执行完之后，模式空间的内容像下面
这样。

```
104,Anand Ram,IT Director
```

{% em type="yellow" %}记住{% endem %}:Sed在执行第2个命令的时候，模式空间是第一个命令执行过后的内容。

__3. Print:__打印当前模式空间中的内容，像下面这样。

```
104,Anand Ram,IT Director
```

__4. Repeat:__跳到下一行，重复从第1步开始执行。
