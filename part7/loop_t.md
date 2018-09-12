# 循环使用t命令

仅当先前的替换命令成功时，sed命令`t label`才将执行流分支到标签。
也就是说，当前一次替换成功时，sed跳转到标签标记的行并继续从那里执行其余命令，否则它继续正常执行流程。

以下示例将员工姓名和职位（来自empnametitle.txt文件）组合到一个单独的行，
字段之间用：分割，并在员工姓名前面添加三个“\*”，此时该员工的职位包含关键字“Manager”。

注意：我们只需将前一个示例中的替换命令更改为“s/^/\*\*\*/”（而不是s/^/\*/）即可获得相同的结果。此示例仅用于解释sed t命令的工作原理。

```
$ vi label-t.sed
#!/bin/sed -nf

h;n;H;x
s/\n/:/
:repeat
/Manager/s/^/*/
/\*\*\*/!t repeat
p
$ chmod u+x label-t.sed
$ ./label-t.sed empnametitle.txt
John Doe:CEO
***Jason Smith:IT Manager
Raj Reddy:Sysadmin
Anand Ram:Developer
***Jane Miller:Sales Manager
```

在上面的例子中:
 -  以下代码片段执行循环

 ```
 :repeat
 /Manager/s/^/*/
 /\*\*\*/!t repeat
 ```

 - __`/Manager/s/^/*/`__ - 如果是Manager，它会在行前面添加一个\*。

 - __`/\*\*\*/!t repeat`__ - 如果该行不包含三个\*s（由/\\\*\\\*\\\*/！表示），并且如果前一个替换命令通过在该行前面添加一个\*成功，
 则sed会跳转到名为`repeat`的标签 （用t重复表示）

 - __`:repeat`__ - 这只是标签
