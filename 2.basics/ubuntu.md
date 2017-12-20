## Ubuntu基本操作
#### 常用命令
##### cd: 改变路径(change directory)
常用路径：
* ~ 当前用户的根目录，对应路径为/home/[user_name]
* / 系统根目录，一般不会直接操作
* .. 上一级目录，cd .. 改变目录为上一级
* . 当前路径

##### ls: 显示路径下文件(list)
* ll 显示当前路径下详细信息(等效于ls -alF)
* la 显示当前路径下所有文件，包括隐藏文件(等效于ls -A)
* ls [directory] 显示指定路径下文件，ll, la同理

##### mv: 移动文件
* mv file1 [directory] 将文件移动至指定路径
* mv file1 file2 将文件重命名
* mv -r [folder]  [directory] 将整个文件夹移动至指定路径

##### cp: 复制文件
* cp file1 [directory] 将文件复制至指定路径
* mv file1 file2 以另一文件名复制文件
* mv -r [folder]  [directory] 将整个文件夹复制至指定路径

##### rm: 删除文件
* rm file1 删除文件
* rm -r [folder] 删除整个文件夹(慎用，无法恢复)

##### mkdir: 新建文件夹
* mkdir [folder] 在当前路径下新建一个文件夹
* mkdir -p [folder]/[folder] 在当前路径下新建一系列嵌套的文件夹

#### 常用技巧
##### tab键自动填充
输入指令时，通过tab键，可以利用系统的自动填充功能，方便指令输入

##### 文件名缺省查找
* mv *.py 移动所用.py结尾的文件(即移动所有python文件)