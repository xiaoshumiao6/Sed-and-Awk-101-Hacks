# Summary

* [序言](README.md)

### 第一章 Sed语法和基本命令
* [说明](part1/README.md)
* [1. Sed命令语法](part1/syntax.md)
* [2. Sed脚本流程](part1/script.md)
* [3. 打印模式空间(p 命令)](part1/pattern.md)
* [4. 删除行(d 命令)](part1/delete.md)
* [5. 模式空间写入文件(w 命令)](part1/write.md)

### 第二章 Sed替换命令
* [说明](part2/README.md)
* [6. Sed替换命令语法](part2/syntax.md)
* [7. 全局标志（g flag）](part2/global.md)
* [8. 数字标志（1,2,3...flag）](part2/number.md)
* [9. 打印标志（p falg）](part2/print.md)
* [10. 写标志（w falg）](part2/write.md)
* [11. 忽略大小写标志（i falg）](part2/ignore.md)
* [12. 执行标志（e falg）](part2/exec.md)
* [13. sed替换标志组合使用](part2/combine.md)
* [14. sed替换定界符](part2/delimiter.md)
* [15. 多个替换命令作用到同一行上](part2/multiple.md)
* [16. &魅力 - 引用匹配模式](part2/pattern.md)
* [17. 分组替换（单一组）](part2/single_group.md)
* [18. 分组替换（多组）](part2/multiple_group.md)
* [19.  Gnu Sed {replacement-string}标志](part2/string.md)

### 第三章 Sed正则表达式
* [说明](part3/README.md)
* [20. 正则表达式基本原理](part3/syntax.md)
* [21. 扩展正则表达式](part3/additional.md)
* [22. Sed基于正则表达式的替换](part3/substitution.md)

### 第四章 Sed的执行
* [说明](part4/README.md)
* [23. 命令行中的多个Sed命令](part4/multiplecmd.md)
* [24. Sed脚本](part4/script.md)
* [25. Sed注释](part4/comment.md)
* [26. Sed解释执行](part4/interpreter.md)
* [27. 直接将修改应用到输入文件](part4/modifying.md)

### 第五章 Sed扩展命令
* [说明](part5/README.md)
* [28. 行后追加（a 命令）](part5/append.md)
* [29. 行前追加（i 命令）](part5/insert.md)
* [30. 改变行（c 命令）](part5/change.md)
* [31. a、i、c 命令结合](part5/combine.md)
* [32. 打印隐藏字符（l 命令）](part5/hidden.md)
* [33. 打印行号（= 命令）](part5/linenumber.md)
* [34. 改变大小写（y 命令）](part5/case.md)
* [35. 指定多个输入文件](part5/multiple.md)
* [36. 退出（q 命令）](part5/quit.md)
* [37. 读取额外文件（r 命令）](part5/read.md)
* [38. 模拟Unix命令（cat、grep、head）](part5/unix.md)
* [39. sed命令行参数](part5/option.md)
* [40. 打印模式空间（n 命令）](part5/patter.md)
