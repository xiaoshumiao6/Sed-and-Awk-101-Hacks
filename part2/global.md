# 全局标志（g falg）

Sed替换标志g代表全局，默认的sed替换命令只会替换每行{original-string}第一次出现的地方，
如果你想替换一行中所有出现的{original-string}为{replacement-string}，你需要使用全局标志g。<br/>

__替换每行中第一次出现小写字母a为大写字母+中括号[A]__:

```
$ sed 's/a/[A]/' employee.txt
101,John Doe,CEO
102,J[A]son Smith,IT Manager
103,R[A]j Reddy,Sysadmin
104,An[A]nd Ram,Developer
105,J[A]ne Miller,Sales Manager
```

__替换每行中所有出现的小写字母a为大写字母+中括号[A]__:

```
$ sed 's/a/[A]/g' employee.txt
101,John Doe,CEO
102,J[A]son Smith,IT M[A]n[A]ger
103,R[A]j Reddy,Sys[A]dmin
104,An[A]nd R[A]m,Developer
105,J[A]ne Miller,S[A]les M[A]n[A]ger
```

{% em type="yellow" %}注意{% endem %}: 这些例子适用于整个文件，因为没有地址范围被指定。
