# Wildcards

You can use wildcards in the Shell-type of task. When a wildcard is used in the parameter, the SHELL script would take it as path or file name and search accross the 在“参数”中遇到了通配符时，Shell会将其当作路径或文件名在磁盘上搜寻可能的匹配：

* 若符合要求的匹配存在，则进行替换(路径扩展)；
* 若无符合要求的匹配存在，则将该通配符作为一个普通字符传递给“命令”，然后再由命令进行处理。

Shell常见通配符如下：
