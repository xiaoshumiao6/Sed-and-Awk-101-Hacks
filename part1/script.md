#Sed 脚本流程

Sed脚本遵循易于记忆的序列，依次为读取，执行，打印，重复。。。<br/>
我们看看这个序列中的步骤：
  * 在模式空间中读取一行（一个内部临时的sed缓冲区，缓存从文件中读取的行）
  * 在模式空间中的行上执行sed命令，如果有多个sed命令无论是来自脚本，-e选项
或者{}，都将按顺序依次执行所有的sed命令
  * 打印模式空间中的行（处理后的结果），打印完这一行后，sed模式空间将被清空
  * 再次重复上述操作，直到到达文件的末尾
<br/>

执行流程如图所示：
![sed-execution-flow](https://res.cloudinary.com/devops007/image/upload/v1523950266/Awk-Sed-101-Hacks/sed_execution_flow.jpg)



