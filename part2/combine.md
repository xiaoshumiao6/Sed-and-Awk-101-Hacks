# sed替换标志组合使用

你可以根据需要组合一个或多个替换标志。以下示例将替换所有出现的"Manager" 或
"manager" 为 "Director",同时打印发生替换的行，并将信息写入output.txt问价中。

__结合g、i、p和w标志__:

```
$ sed -n 's/Manager/Director/gipw output.txt' employee.txt
102,Jason Smith,IT Director
105,Jane Miller,Sales Director
$ cat output.txt
102,Jason Smith,IT Director
105,Jane Miller,Sales Director
```
