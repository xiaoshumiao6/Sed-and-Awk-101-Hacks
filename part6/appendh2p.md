# 追加保持空间到模式空间（G 命令）

大写字母G将保持空间的内容以新行的方式追加到模式空间，模式空间先前的内容不会被覆盖，
相反在末尾添加来自保持空间的内容附加为新行。

G和g以与H和h相同的方式相关; 小写版本替换内容，而大写版本附加到内容。

假设模式空间包含“第1行”并且保持空间包含“第2行”; 执行G命令后，模式空间将更改为包含“第1行\n第2行”，而保持空间不会更改且仍包含“第2行”。

__打印以冒号分割的Manager的姓名和职位__

```
$ sed -n -e '/Manager/!h' -e '/Manager/{x;G;s/\n/:/;p}' empnametitle.txt
Jason Smith:IT Manager
Jane Miller:Sales Manager
```

 - __`/Manager/!h`__ -与前面的示例一样，如果模式空间的内容不包含Manager，则复制模式空间到保持空间。

 - __`/Manager/{x;G;s/\n/:/;p}`__ -如果模式空间中包含Manager，则做以下事情：

   - __x__ -交换模式空间和保持空间的内容，存储在保持空间的员工姓名（name）现在将位于模式空间，而职称（title）将位于保持空间中

   - __G__ -将保持空间（title）内容附加到模式空间（name），因此，现阶段的模式空间中存储着“name\ntitle”

   - __s/\n/:/__ -这会将“name\ntitle”中的`\n`替换成`:`（冒号）

   - __p__ -打印结果（就是模式空间中的内容）

   - __注意__ -如果我们省略了x命令，即如果我们使用 `/Manager/{G;s/\n/:/;p}` 我们将打印每个员工的title：name 而不是name：title


你也可以将此内容写如脚本中执行：

```
$ vi G-upper.sed
#!/bin/sed -nf

/Manager/!h
/Manager/{x;G;s/\n/:/;p}

$ chmod u+x G-upper.sed
$ ./G-upper.sed empnametitle.txt
Jason Smith:IT Manager
Jane Miller:Sales Manager
```

