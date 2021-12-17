# LINUX命令行大全



# 学习shell

## 基本的

`date`	显示日期

`cal`	显示日历

`df`	查看磁盘驱动器当前的可用空间

`free`	显示可用内存

`exit`	结束终端会话

`pwd`	打印当前工作目录

`ls`	列出目录的内容，`ls /usr`可以显示/usr的目录内容，`ls -l`会显示更加详细的内容·

`cd /usr/bin`	cd表示更改工作目录

`.`	符号`.`表示工作目录，`..`表示父目录，以`.`开头的文件名是隐藏的，除非输入`ls-a`才能显示

`cd ..`	将工作目录改为当前目录的父目录

`-`	-命令表示选项，有很多种选项：

> -a	列出所有文件
>
> -d	作为d和l的组合，即可查看当前目录的详细信息
>
> -F	在名字之后加上一个类型指示符
>
> -l	长格式显示
>
> -r	以相反的顺序显示（字母逆序）
>
> -S	按文件大小对结果进行排序
>
> -t	按修改时间排序

`file`	打印文件内容的简短说明

 `less filename`	查看文本文件

> G	跳转到文本结尾
>
> g	跳转到文本开头
>
> /*character*	查找character字符串
>
> n	查找下一个出现的字符
>
> q	退出less



## 操作文件与目录

通配符

> `*`	匹配任意多个字符
>
> `?`	匹配任意一个单字符
>
> `[character]`	匹配任意一个属于character中的字符
>
> `[!character]`	匹配任意一个不属于character中的字符
>
> `[[:class:]]`	匹配任意一个属于指定字符类的字符（alnum, alpha, digit, lower, upper)\

`mkdir`	创建目录

`cp` 	复制文件和目录 例: `cp file1 file2 dir1`		`-i`提示用户确认	`-u`表示仅仅复制目标文件中不存在的文件

`mv`	移除和重命名文件，`mv item1 item2` 将item1移到item2

`rm`	删除文件和目录

> -i	删除前提示用户确认
>
> -r	删除一个目录的时候使用，递归的删除
>
> -f	忽略不存在的文件且无需提醒

`ln file link`	创建硬连接		不能引用自身文件系统之外的文件，无法引用目录

`ln -s item link`	创建符号连接		连接指向的文件不会随着连接删除而删除



## 命令

命令包含四种：可执行程序，shell内置命令，shell函数，alias命令（可以在其基础上定义的自己的命令）

`type`	显示命令的类型

`which`	显示可执行程序的位置

`help`	获取帮助文档，显示命令的使用信息；两种使用方法`help ls`和`ls --help`

`man`	显示程序的手册页

`whatis`	显示命令的简要描述

`info`	显示程序的info目录，在这样的页面中一般按q退出

> 创建一个alias命令：
>
> 1. 首先查看命令名称是否存在 type foo
>
> 2. alias foo='cd /usr; ls; cd -' foo命令就创建好了
> 3. unalias foo 命令就删除了



## 重定向

`>`	重定向操作符>可以用于后接文件名，把标准输出重定向到另一个文件中去；举例来说`ls -l /usr/bin > ls-output.txt`，在我的电脑中就会出现ls-output.txt文件。如果重定向符之前的操作是一个错误信息，产生的文件就是一个空文件;

`>>`	使输出内容添加到文件的最后面

`2>`	标准错误等同于文件描述符2，使用2>实现将标准重定向到后面的文件中，举例来说：`ls -l /bin/usr 2> ls-error.txt`

`&>`	将标准输出和标准错误都重定向到同一个文件，举例来说：`ls -l /bin/usr &> ls-output.txt`

`/dev/null`	这个文件位置可以接受输入但是不对输入进行任何处理，举例来说：`ls -l /bin/usr 2> /dev/null`

`cat`	cat有很多种用途，首先cat可以显示短的文本文件，并且cat可以将多个文件作为参数，将他们合并起来。

显示操作：`cat ls-output.txt` 合并操作：`cat movie.mpeg.0* > movie.mpeg`	

除此之外，cat还可以创建短文本文件：`cat > lazy_dog.txt`	`i am a lazy dog!`，这样的结果就是创建好了一个内容为i am a lazy dog!的lazy_dog.txt文件

`|`	管道操作符，把一个命令的标准输出传送到另一个命令的标准输入中，举例来说：`ls -l /usr/bin | less`	，这可以方便的检查任意一条生成标准输出的命令的运行结果；`ls /bin /usr/bin | sort | less`，把两个目录下的所有可执行程序合并成一个列表，并按照顺序排序，最后再查看

`uniq`	可以忽略文件中重复的行，后面加上-d表示查看重复的行，举例来说：`ls /bin /usr/bin | sort | uniq-d | less`

`wc`	打印行数，字数，字节数`wc ls-output.txt`，用`wc -l`可以只打印行数，同理，可以把wc加在管道里：`ls /bin /usr/bin | sort | uniq | wc -l`

`grep`	用管道的方式打印含有zip的匹配的行：`ls /bin /usr/bin | sort | uniq | grep zip`，-i表示搜索时忽略大小写，- v表示输出和模式不匹配的行

`head/tail`	打印文件的开头，结尾部分，-n表示显示多少行。可以使用管道的方式：`ls /bin | head -n 5  `	和直接输出的方式：`tail -n 5 ls-output.txt`	

`tee`	获取，输出：`ls /usr/bin |tee ls.txt|grep zip`将内容输出到ls.txt中，然后再用grep进行过滤



## echo

echo命令本身只是将文本参数内容打印到屏幕

`echo hello world`

`echo *` 	这会打印*的扩展结果



扩展包括很多：

*就是一种任意字符的拓展，～会拓展为用户的主目录名，$(())表示算术拓展，

{}表示花括号拓展，举例：`echo {2009..2011}--{1..9}-  `，$USER称之为参数拓展，



引用的方式也很多

""双引号中引用的特殊字符都将被看作是普通字符，$，\，'除外，参数拓展，算术拓展，命令替换在双引号中仍然成立。

''单引号中所有拓展都被抑制

\转义字符可以实现引用单个字符，\\\实现引用反斜杠



## 高级键盘技巧

Ctrl+A：移动光标到行首

Ctrl+E：移动光标到行尾



Ctrl+K：复制光标到行尾的内容

Ctrl+U：复制光标到行首的内容

Ctrl+Y：粘贴到光标位置



`tab`	在输入字符之后按tab可以实现自动补齐，

`history`	可以实现搜索历史命令，例如我想寻找输入的包含ls的历史命令行：`history | grep ls`	会得到结果` 173 ls Desktop`	输入`！173`可以输出173行的命令；按Ctrl+R可以实现逆向递增式搜索，按Ctrl+J实现将内容复制到当前行。

`!!`	重复最后一个执行的命令



## 权限

创建用户时，用户将被分配一个称为用户id （uid）的号码，用户还被分配为一个有效组id（gid），超级用户一般uid为0

关于读取，写入和执行：一般会用10个字符来表示文件属性，第一个字符表示文件属性，后面每三个字符分别表示文件所有者，文件所属群组，其他所有用户对该文件的读写执行操作权限。

第一个字符：- 表示普通文件，d 表示目录文件，l 表示符号连接，c 表示字符设备文件，b 表示块设备文件

后面的字符：r表示可以打开和读取文件，w表示可以写入或者截短文件，x表示允许把文件当作程序一样来执行

举例：drwxr-xr-x，d表示这是一个目录文件，所有者拥有读，写，执行的权限，组成员拥有读和执行的权限，其他用户也拥有读和执行的权限。

`chmod`	可以实现更改文件模式，有两种方法，第一种是用八进制数字表示，第二种是符号表示法，八进制对应的如下： 

<img src="/Users/lizhihan/Library/Application Support/typora-user-images/image-20210405202531431.png" alt="image-20210405202531431" style="zoom:50%;" />

举例来说：

`chmod 600 foo.txt`	可以实现对foo.txt的权限更改

符号表示法中，u,g,o分别表示用户，群组和其他用户

`chmod u+x foo.txt`

`chmod o-rw foo.txt`

`chmod u+x,go=rx foo.txt`	# 为文件所有者添加可执行权限，同时设置群组和其他用户具有读权限和可执行权限

`umask`	一般可以用来设置默认权限，默认掩码值一般为0022

除了常用的rwx权限之外，还存在setuid，setgid，sticky位；setuid可以将一个实际用户id设置为程序所有者id，setgid可以把有效组id从该用户的实际组id更改为该文件所有者的组id，sticky可以阻止用户删除或者重命名文件（除非用户为程序所有者或root）

`su -l`	-l表示指定用户，后面输入user即可以其他用户和组id的身份来运行shell，不输入名称默认为root

`su -c 'command'`	这种格式下单个命令行command会被传递到一个新的shell环境下执行

`sudo`	sudo可以实现让一个用户拥有不同的用户身份执行命令，但是被限制为智能执行一条或者几条特定的命令；除此之外，sudo不用输入密码。

`chown`	更改文件所有者和所属群组；把文件的所有者更改为tony `sudo chown tony: ~tony/myfile.txt`	chown的参数可以设置为

> Bob 	将文件所有者改为bob
>
> Bob:users	所有者改为bob，所属群组改为users
>
> :adnin	将所属群组改为adnin
>
> bob:	将所有者改为bob，把文件所属群组改为bob登录时的群组

`chgrp`	可以更改文件所在的组，功能和chown类似

`passwd`	可以更改当前用户的密码	



## 进程

`ps`	查看进程信息

`ps x`	显示所有进程，STAT列表示进程的状态

`ps aux`	输出更详细的信息，包括虚拟耗用内存大小，CPU使用百分比等等

`top`	动态查看进程信息，按q退出



`Ctrl+c`	中断一个程序

`Ctrl+z`	暂停一个程序

`xlogo &`	在后台运行xlogo程序

`jobs`	查看从该终端启动的所有任务

`fg %1`	fg命令后面加上%符号和作业编号，可以使进程回到前台运行；当程序被ctrl+z暂停的时候，也可以通过这个命令来恢复运行，作业编号可以从jobs命令中查看



`kill [signal] PID`	该命令为通过kill来发送信号，其中PID信息可以通过ps命令来查看而signal包含很多

> [signal]: 	`HUP`	挂起信号，进程接收到之后将重启并重新读取它的配置文件	
>
> ​					`INT`	中断信号，等同于“Ctrl+c”
>
> ​					`STOP`	暂停信号
>
> ​					`CONT`	继续运行信号



# 配置与环境

## 环境

在bash中，存在两种数据类型：环境变量，shell变量。

shell变量是由bash存在的少量数据，而环境变量就是其他变量。

除去变量，shell还存储了一些编程数据（别名和shell函数）



`printenv|less`	printenv命令可以打印所有的环境变量，通过less管道打印可以实现；举例来说，我想查看名为USER的环境变量，输入`printenv USER`就可以查看了

`set|less`	使用set命令可以打印shell变量，环境变量，任何已定义的shell函数；使用`echo $HOME`可以实现打印查看某单个变量的值



用户登录系统后，bash会读取启动文件的配置脚本，这些脚本定义了所有用户共享的默认环境

shell会话包含两种：login shell 和non-login shell；启动文件来自于：login shell中的启动文件，non-login shell中的启动文件。



修改环境：

>  我们想要修改环境，加入一条命令`l.`实现显示所有以.开头的文件
>
> `cp .bashrc .bashrc.bak`	备份文件，防止出现错误
>
> `nano .bashrc`	启动文本编译器
>
> `alias l.='ls -d .* --color=auto'`	在文件中写入这句话
>
> `ctrl+o`	保存	`ctrl+x`	退出编辑
>
> `source  .bashrc`	激活修改，强制重新读取.bashrc文件，一般来说，重启shell才可以修改生效



## vi

为了不被其他linux和unix用户鄙视，我们开始学习vi

进入vi之后，`:q`	表示退出vi，`:q!`	表示强制退出vi，`:w`	表示保存

`vi doc_name`	进入vi编辑模式，进入编辑模式之后，使用A命令可以快速到达行尾

`dd`	可与复制当前行，`dG`	复制当前行到结尾，`yy`	可以剪切当前行，`yG`	裁剪当前行到结尾	`p`	可以粘贴我们复制的内容，`u`	可以取消我们的操作

`/o`	可以实现整个文件中o的位置，按n显示下一个n的位置



`vi file1 file2 file3`	可以实现编辑多个文件

`:n`切换到下一个文件

`:N`切换到上一个文件

`buffers`	查看正在编辑的文件列表

`buffer 1`	切换到1文件中



保存工作时的：w操作并不是保存当前文件，而是另存为，下次打开当前文件，仍然是之前的版本



## 定制提示符

提示符的设计：

`PS1="\A \h \$"`	可以实现重新设置输入的提示符，A表示当前的时间，h表示当前机器的主机名，不包括域名，还有很多转义字符可以设置，这里不展开细说



文本的颜色，光标，保存提示符都可以进行设置，详细可以参考官方文档



# 常见任务和主要工具

## 软件包管理

多数linux发行版都使用了两种软件包技术阵容debian和red hat；ubuntu属于debian，centOS属于red hat

因为学习过程中我使用的是centOS7，所以下面仅记录red hat系统的操作方式，ubuntu的操作方式可以参考网上的其他教程

`yum search package_name`	在库中查找软件包

`yum install package_name`	安装库中的软件包

`yum erase package_name`	删除软件包

`yum update `	更新库中的软件包



`rpm -qa`	列出所有已经安装的软件

`rpm -q package_name`	判断软件包是否安装

`yum info package_name`	显示已经安装的软件包的信息

`rpm -qf file_name`	查看某个文件是由哪个软件包安装得到的

​     

## 存储介质

（这章的内容貌似有些过时和小众，我仅仅作为了解略读了一遍，毕竟这个年代，谁还会想着自己刻录一张光盘呢？😔）

挂载：管理存储设备首先要做的就是将该设备添加到文件系统树中，从而允许操作系统可以操作该设备，这个过程称之为挂载；卸载设备可以保证缓存中的所有剩余数据全部写入设备，从而设备可以安全移除

`mount`	查看已挂载的文件系统列表

`umount /file_path`	可以卸载设备，这个命令必须在挂载目录以外的地方执行才可以，否则会出现设备繁忙的错误警告



创建新的文件系统：1）创建一个新的分区布局 	2）在驱动器上创建一个新的空文件系统 

`sudo fdisk /dev/sdb`	用fdisk命令进行磁盘分区

`sudo mkfs -t ext3 /dev/sdb1`	 创建新的文件系统

 `sudo fsck /dev/sdb1`	检查，测试修复文件系统，类unix系统中，fsck修复的文件会存放在系统根目录下的lost+found文件中

格式化软盘：

`sudo fdformat /dev/fd0`	首先执行格式化操作

`sudo mkfs -t msdos /dev/fd0`	用mkfs命令为软盘创建一个FAT文件系统



## 网络

***warning：*** 学习一些大数据组件过程中总是会遇到网络相关的命令行，这一章需要仔细看！

### 检查和检测网络

***在centOS7系统中，需要通过`yum install net-tools`安装netstat***



`ping slashdot.org` 	向网络主机发送IMCP命令，网络收到该数据包后会回应，以此验证网络连接是否正常

`tracerout slashdot.org`	显示文件通过网络从本地系统传输到指定主机过程中所有停靠点的列表

`netstat -ie`	检查系统中网络接口信息，这个命令结果的第二行显示有效的ip字段

![image-20210512210224196](/Users/lizhihan/Downloads/1.png)

`netstat -r`	显示内核的网络路由表，显示网络之间传送数据包时网络的配置情况；ip以0结尾表示接收方是网络而不是个人主机，getaway表示建立当前主机与目标网络之间联系的网关的名称或ip地址，此参数值是星号表示无需网关

![image-20210512210235802](/Users/lizhihan/Downloads/2.png)

​																																																																																																																																																																																												

### 通过网络传输文件

FTP（文件传输协议），用这种方式传输并不安全，因为他用的是明文传输，但是我使用的centos版本好像不支持书上的例子了，就跳过吧，在编译程序章节中我写了例子可以参考。

lftp是ftp的一种改进版，增加了很多功能。

wget是一种用于文件下载的命令行程序，举例`wget http://linuxcommand.org/index.php`	可以下载这个网页第一页的内容



### 与远程主机的安全通信

ssh（secure shell）：它解决了两个问题 1. 验证主机的身分是否真实 	2. 协议本身将本机和远程主机之间的通信内容全部加密

scp和sftp都可以实现安全的传输文件，简单示例：`scp remote-sys:document.txt`	`sftp remote-sys`



## 文件搜索

***warning：*** locate命令需要使用`yum install mlocate`方式进行安装

​					locate命令无法使用的时候，尝试使用`updatedb`进行数据库手动更新，默认每天更新一次



 `locate bin/zip`	简单的文件查找方式

`locate zip | grep bin`	管道方式过滤含有bin的文件



`find ~`	列出系统主目录的文件列表清单

`find ~ | wc -l`	使用管道方法计算，主目录文件列表清单中文件的总量



`find ~ -type f | wc -l` 只对普通文件进行搜索

`find ~ -type d | wc -l` 只对目录文件进行搜索

`find ~ -type f -name "*.jpg" -size +1M | wc -l`  查找大于1m的jpg普通文件，+表示大于，-表示小于

其他更多的test 项参数，可以通过`man find ` 查看 



在find找到文件之后，可以直接执行动作：

`find ~ -type f -name '*.BAK' -delete`	找到bak结尾的文件，找到就删除

`find -type f -name '*.BAK' -print`	按照顺寻运行，只有符合前两项的文件才会被print，如果print放在最前面，限定条件就无效了，因为print总是可以被满足的；可以直接理解为每个判定之间是一个`-and`连接符



除去上述option命令外，还可以加入其他option选项实现find程序陷入目录数的最大级别数，最小级别数等等



## 归档和备份

### 压缩

`gzip foo.txt`	压缩文件，加上-c表示将输出内容写到标准输出端口

`gunzip foo.txt`	解压缩

`gunzip -c foo.txt | less`	只查看某个压缩文本文件的内容

`bzip2 foo.txt`	bzip2也是一种压缩的方式，牺牲速度换取高质量，用法和gzip相似



### 文件归档

tar命令用于归档文件，tap archive的缩写

> `c`	创建文件
>
> `x`	从归档文件中提取文件
>
> `t`	在归档文件末尾追加指定路径名
>
> `r`	列出归档文件的内容



`tar cf playground.tar playground`	为playground文件创建一个归档文件playground.tar

`tar tf playground.tar`	列出归档文件的内容，查看已经备份了哪些文件

 

`zip -r playground.zip playground`	创建一个playground的zip归档文件，如果不加r进行递归的话，只会保留playground目录而不包括目录中的内容

`unzip ../playground.zip`	提取zip文件夹中的内容



### 同步文件和目录

`rsync options source destination`	options表示-a这种命令，source和destination一般是一个本地文件或目录，一个远程文件或目录，或者一个远程rsync服务器

`rsync -av playground foo`	同步playground目录和它在foo目录中的副本，-a表示递归归档并保留文件属性，-v表示详细输出

  

## 正则表达式

`ls /usr/bin | grep zip`	利用grep搜索固定的字符串，列出/usr/bin目录下文件名包含zip字符串的所有文件

> 常用选项：
>
> `-i`	忽略大小写
>
> `-v`	输出不匹配的
>
> `-c`	输出匹配的数目
>
> `-l`	输出匹配项文件名而不是匹配项本身
>
> `-h`	多文件搜索时，抑制文件名输出

`grep bzip dirlist*.txt`	搜索所有文件，查找字符串bzip，且名称要匹配dirlist*.txt（当然，dirlist\*.txt文件要存在）

`grep -h '.zip' dirlist.txt`	.可以代表任何字符

`grep -i '^..j.r$' /usr/share/dict/words`	^表示只与行开头进行比较，$表示只与行末尾进行比较

`grep -h '[bg]zip' dirlist*.txt`	匹配包含bzip和pzip的文件；中括号的第一个字符为^表示不包含中括号中的内容的匹配项

`grep -h '^[A-Za-z0-9]' dirlist*.txt`	匹配开头为数字或字母的文件名

`grep -Eh '^(bz|gz|zip)' dirlist*.zip`	引入|，表示或者，注意这里加不加（）影响很大

限定符包含？ * + {}，分别有不同的作用



`locate --regx 'bin/(bz|gz|zip)'`	加入--regx才可以支持正则表达式

可以利用less展示文件，并使用vi按下/，输入正则表达式





>  ***文本化处理，格式化输出，打印三个章节暂时跳过，对目前的后续学习没有帮助***
>
> 其中包含了命令：
>
> `cat`	链接文件并打印到标准输出
>
> `sort`	对文本排序
>
> `uniq`	报告并省略重复行
>
> `cut`	从每一行中移除目标文本
>
> `paste`	合并文件文本行
>
> `join`	基于某个共享字段来联合两个文件的文本行
>
> `comm`	逐行比较两个已经排序好的文件
>
> `diff`	逐行比较文件
>
> `patch`	对原文件打补丁
>
> `tr`	转换或删除字符
>
> `sed`	用于过滤和转换文本的流编辑器
>
> `aspel`	交互式拼写检查器
>
> ---
>
> `nl`	对行进行标号
>
> `fold`	设定文本行长度
>
> `fmt`	文本格式化工具
>
> `pr`	格式化打印文本
>
> `printf`	格式化并打印输出数据
>
> `grof`	文档格式化系统
>
> ---
>
> `lpr`	打印文件
>
> `lp`	打印文件
>
> `a2ps`	格式化文件，以在postScript上打印
>
> `lpstat`	显示打印状态信息
>
> `lpq`	显示打印机队列状态
>
> `lprm`	取消打印任务
>
> `cancel`	取消打印任务



## 编译程序

为了进行练习，从一个叫做diction的GNU项目中选择一个程序进行练习

> `mkdir src`	新建存储文件的文件夹
>
> `cd src`	进入文件夹
>
> `ftp ftp.gnu.org`	使用ftp文本传输协议
>
> `anonymous`	匿名登录，无需输入密码
>
> `cd gnu/diction`	找所需要的文件位置
>
> `get diction-xxxxxx`	在ftp中使用get命令，将文件从ftp服务器复制到本地主机
>
> `bye`	退出ftp



`./configure`	configure程序是个源代码树下的一个shell脚本，任务在于分析生成环境。

`make` 	生成程序，运行make时，会使用Makefile文件中的内容指导其操作。make有一个原则：目标文件比依赖文件新，make能够确保所有需要基于刚更新的代码而生成的程序都会生成。

`sudo make install`	在系统目录下安装最后生成的可执行程序，安装完成之后就可以使用该程序了



# 编写shell脚本

可以使用将命令行组合成程序的方式，编写shell脚本，使shell可以独立完成一系列复杂任务。

shell脚本就是包含一系列命令的文件，shell读取这个文件，然后执行这些命令，就好像把这些命令直接输入到命令行一样。

## 编写一个shell脚本

首先创建一个程序并使用vi编辑它

```shell
#!/bin/bash

# this is my first script

echo 'HELLO WORLD'
```

第一行称之为shebang，用来告知操作系统，执行后面的脚本应该使用的解释器的名字



`chmod 755 xxxx`	使xxxx脚本可执行，权限755表示所有人可执行，700表示仅脚本所有人可执行。

`./xxxx`	需要指明脚本的路径才可以运行，因为我们的path变量中没有当前文件的路径，所以需要指明。通过`echo $PATH `	可以显示目录列表。

如果想像其他命令一样直接使用，可以将文件移动到path目录中：

```shell
mkdir bin
mv xxxx bin
xxxx
```

除此之外，还可以直接更改PATH环境变量：

```shell
exprt PATH=~/bin:"$PATH"
```

更改完成后重新读取.bashrc文件，`. .bashrc` 命令



建议：系统管理员使用的脚本放置在`/usr/local/sbin` 中，普通脚本放置在`/usr/local/bin` ；大多数情况下，本地支持的软件，脚本或编译好的程序，都应该放在`/usr/local` 目录下。



更改virc文件可以为编写脚本提供方便，一般来说进入etc/ 目录，使用vi命令修改virc文件，输入：

```
syntax on	开启语法高亮
set health		将搜索的结果高亮显示
set tabstop = 4		设置tab键造成的空格长度
set autoindent		开启自动缩进特征
```



## 启动一个项目

编写一个简单的shell脚本方式就像上一节提到的方式一样，下面举一个shell的实例，目的是制作一个HTML文件：

```shell
#!/bin/bash

# output a information page

TITLE="System information report"
CURRENT_TIME=$(date+"%x %r %z")
TIME_STAMP="Generated $CURRENT_TIME,by $USER"

echo "<HTML>
			<HEAD>
					<TITLE>$TITLE</TITLE>
			</HEAD>
			<BODY>
					<H1>$TITLE</H1>
					<P>$TIME_STAMP</P>
			</BODY>
	</HTML>
"
```

说明：HTML中，`<H1>` 表示的是标题文本，H1到H6可以理解为Markdown格式中的一个#到6个#；`<P>` 表示的是一个段落。`<BODY>`  元素的内容会显示在浏览器中。`<TITLE>`  元素的内容会显示在浏览器的标题栏中。`<HEAD>` 是一个必备属性。



除去上述使用echo的方法，我们还可以使用cat和here文档。

```shell

#!/bin/bash

# output a information page

TITLE="System information report"
CURRENT_TIME=$(date+"%x %r %z")
TIME_STAMP="Generated $CURRENT_TIME,by $USER"

cat << _EOF_
<HTML>
			<HEAD>
					<TITLE>$TITLE</TITLE>
			</HEAD>
			<BODY>
					<H1>$TITLE</H1>
					<P>$TIME_STAMP</P>
			</BODY>
</HTML>
_EOF_
```

here文档会使shell将引号当作普通字符，这样就可以在here文档中随意嵌入引号了。

除此之外，如果不写HTML文件，输入普通的shell命令的话需要将所有的语句放在没一句的开头，将`<<` 改为`<<-` ，shell就会忽略tab字符，这样就可以不同把语句顶头写了，增加了可读性。



## 自顶向下的设计

先确定上层的步骤，然后逐步细化这些操作步骤的过程，成为自顶向下的设计。

函数的两种写法

```shell
function name{
	commands
	return
}
```

```shell
name(){
	commands
	return
}
```



## 流控制：IF分支语句

if的使用方法

```shell
x=5 

if [$x=5];then
	echo "x equals 5"
else
	echo "x does not equals 5"
fi
```

或者直接在命令行中输入这两行

```shell
x=5
if [$x=5];then echo "equals";else echo "does not equal";fi
```





shell有检测退出状态的参数，

举例来说：

> 输入ls
>
> 输入echo $?
>
> 这时候输出结果就是0,0表示成功

> 输入ls，后面跟一个不存在的路径
>
> 输入echo $?
>
> 这时候输出结果就是2，命令使用不同的返回值来诊断错误





shell中拥有test命令，其中包含了文件表达式，字符串表达式，整数表达式。每种表达式都包含了很多不同的测试语句。

test命令的一般形式为`[expression]`，其中expression是一个表达式

分别进行举例

文件表达式：

```shell
#!/bin/bash

# test status of file
# -e file 成为true的条件为file存在

FILE=-/.bashrc
if [-e "$FILE"];then 
	echo "exist"
else
	echo "does not exist"
fi
```

字符串表达式

```shell
#!/bin/bash

# test value of string
# -z STRING 成为true的条件为string长度等于0

ANSWER=maybe

if [-z "$ANSWER"];then 
	echo "there is no answer"
else
	echo "the answer is $ANSWER"
fi
```

整数表达式

```shell
#!/bin/bash

# test value of integer
# -z INT 成为true的条件为int长度等于0

INT=5

if [-z "$INT"];then 
	echo "INT is empty" >&2
	exit 1
fi
```





使用&&和||同样可以进行分支控制

举例：`command1&&command2`		`command1||command2`

对于&&，先执行1,1执行成功之后才会执行2；对于||，先执行1，只有1执行成功了，2才会开始执行。

实例

```shell
mkdir temp&&cd temp
# 先创建temp目录，创建成功后才会更改目录到temp

[-d temp] || exit 1
# temp存在且是一个目录，如果目录不存在，这个脚本将会终止，且退出状态为1
```



## 读取键盘输入

read作用为读取一行标准输入，直接上例子

```shell
#!/bin/bash

# test read function

echo -n "please input int"
read var1 var2

echo "var1 = '$var1'"
echo "var2 = '$var2'"
```

除去标准的输入方法，read也有很多选项，例如`-s` 保密模式，`-n num` 从输入中读取n个字符，不是一整行。

利用这种方法，可以实现判断输入内容是否正确，构建菜单等等功能，这些内容和其他编程语言一致，不再赘述。



## while和until循环

上例子

```shell
#!/bin/bash

# test while function

count=1

while [$count -le 5]; do
	echo $count
	count=$((count+1))
done
echo "finished"
```

while的使用规则和很多其他的语言是一样的这里不多说了，要提一句，在do和done之间加入`continue` 语句，可以跳出当前循环；加入`break` 语句，跳出循环。



until命令和while命令相反，while退出状态不为0时终止循环，until命令退出状态为0时终止循环。



## 故障诊断方法

书里全是一些没用的，写过其他语言根本就可以跳过。

唯一需要记录的就是在shell脚本开头加上`-x` 或者在过程中加入`set -x`可以实现脚本执行追踪。

举例

```shell
#!/bin/bash
#shell语句······
```

```shell
set -x

#shell语句······

set +x
```



## case分支

上实例

```shell
#!/bin/bash

read -p "Enter selection[A,B,C or D]"

case $REPLY in
	q|Q)	echo "program error!";;
	
	a|A)	echo "input is a";;
esac
```



## 位置参数

就是在讲一个shell脚本的调用时会需要传入参数，这参数的格式设置

上实例

```shell
#!/bin/bash

echo "
	\$0=$0
"
```

这个例子就会需要输入一个值作为`$0`的替代，否则就会输出`$0=`，很多个参数的时候也是同样的道理。



## for循环

好无聊，看到这里我都懒的继续看了

写两个例子吧

```shell
#!/bin/bash

for((i=0; i<5; i+=1)); do
	echo $i
done
```

```shell
#!/bin/bash

for i in A B C D; do echo $1;done
```



> 后面两章内容跳过了，之后工作不可能在shell里写数组啊，字符串处理啊之类的东西的······

# 总结
学linux主要是去实习的公司平时会用到常用的linux语句，而且会有一些数据需求会要求写shell脚本，所以系统地学习了一下。
除此之外就是我觉得如果想真的把编程的很多东西学明白，计算机的基础课还是十分重要的，所以我准备过一遍操作系统，学操作系统绝对少不了linux的作用，所以就先学linux了，下一步就是在啃一本操作系统的书，冲踏🐎的！

