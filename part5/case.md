# 改变字符

Sed的 y 命令按位置转换字符。一个方便的用途是将大写字母转换为小写字母，反之亦然。

__在下面这个例子中，字符“a”将被转换为“A”， “b”变为“B”， “c”变为“C” 等等...__

```
$ sed 'y/abcde/ABCDE/' employee.txt
101,John DoE,CEO
102,JAson Smith,IT MAnAgEr
103,RAj REDDy,SysADmin
104,AnAnD RAm,DEvElopEr
105,JAnE MillEr,SAlEs MAnAgEr
```

__转换所有的小写为大写__

```
$ sed 'y/abcdefghijklmnopqrstuvwxyz/ABCDEFGHIJKLMNOPQRSTUVWXYZ/' employee.txt
101,JOHN DOE,CEO
102,JASON SMITH,IT MANAGER
103,RAJ REDDY,SYSADMIN
104,ANAND RAM,DEVELOPER
105,JANE MILLER,SALES MANAGER
```

以上整个命令将被在每一行上执行应用。
