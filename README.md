# Linux
 Linux学习笔记

## 一、安装Linux

官网下载链接：[http://isoredirect.centos.org/centos/7/isos/x86_64/](http://isoredirect.centos.org/centos/7.4.1708/isos/x86_64/)

阿里云站点：http://mirrors.aliyun.com/centos/7/isos/x86_64/

- `init 3` 由图形界面切换为命令行界面

- `init 0` 关机

- 在图形界面使用 `ctrl+alt+F2`切换到dos界面  

  dos界面 `ctrl+alt+F2`切换回图形界面

  在命令上 输入 `init 3` 命令 切换到dos界面 

  输入` init 5`命令 切换到图形界面
  
- CentOS下使用命令行Web浏览器Links

  - ```bash
    yum install links
    ```

  - ```bash
    links www.baidu.com
    ```

    

## 二、登录

- `$`为普通用户
- `#`为超级用户

## 三、终端的使用

#### **终端**

- 图形终端
- 命令行终端
- 远程终端（SSH、VNC）

## 四、常见目录

```c
/根目录
/root root用户的家目录
/home/username 普通用户的家目录
/etc 配置文件目录
/bin 命令目录
/sbin 管理命令目录
/usr/bin/usr/sbin系统预装的其他命令
```

## 五、万能帮助命令

#### 1、man帮助

- man 是manual的缩写
- man 帮助用法：`man ls`  、`man -a "命令"`
- man 也是一条命令，分为9章，可以使用man 命令获得 man 的帮助
- - `man 7 man`

#### 2、help帮助

- shell（命令解释器）自带的命令称为内部命令，其他的是外部命令
- - `type "命令" `查看（区分）内外部命令
- 内部命令使用 help 帮助
- - `help cd`
- 外部命令使用 help 帮助
- - `ls --help`

#### 3、info帮助(英文)

- info帮助比help更详细，作为help的补充
- - `info ls`

## 六、文件管理

### ==**一切皆文件**==

#### 1、文件查看

- `pwd`显示当前的目录名称
- `cd`  更改当前的操作目录
- - `cd /path/to/...绝对路径`
  - `cd ./path/to/...相对路径`
  - `cd ../path/to/...`相对路径
- `ls`查看当前目录下的文件
  - `ls` [选项，选项... ] 参数 ...
  - 常用参数：
  - `-l` 长格式显示文件
  - `-a` 显示隐藏文件
  - `-r` 逆序显示
  - `-t` 按照时间顺序显示
  - `-R` 递归显示

###### 

#### 2、目录文件的创建与删除

- `mkdir`建立目录
  - `-p` 建立多级目录 `mkdir -p /a/a/b/c/d/e`
- `rmdir`删除空目录

- `rm -r ` 删除非空目录
- `rm -rf ` 删除非空目录并且不提示删除信息

#### 3、通配符

- 定义:shell ⽤用途:操作多个相似(有简单规律律)的⽂文件 常⽤用通配符

`*` 匹配任何字符串

`? `匹配1个字符串
 `[xyz]` 匹配xyz任意⼀一个字符

` [a-z]` 匹配⼀一个范围
` [!xyz]` 或 `[xyz]`不不匹配

`*`匹配当前目录所有文件夹和文件

```shell
[root@localhost copy]# cp -v file* /mnt/hgfs//copy/a
"filea" -> "/mnt/hgfs//copy/a/filea"
"fileb" -> "/mnt/hgfs//copy/a/fileb"
"filec" -> "/mnt/hgfs//copy/a/filec"
[root@localhost copy]# 
```



#### 4、文件操作

##### 复制和移动目录

###### 复制目录：

```shell
cp -r /home/chuzhi/a /mnt/hgfs/copy/
# 把/home/chuzhi的a文件，复制到/mnt/hgfs/copy/
```

###### 显示复制内容：

```shell
cp -v /home/chuzhi/a /mnt/hgfs/copy/
```

```shell

```

###### 移动文件

mv [选项] 源文件 目标⽂文件 

mv [选项] 源文件 目录

#### 6、文本内容查看

- `cat` 文本内容显示到终端

- `head`查看文件开头

- `tail`查看文件结尾
  - 常用参数`-f`文件内容更新后，显示信息同步更新

- `wc` 统计⽂文件内容信息

#### 7、打包&压缩（常用备份🔧）

##### 7.1 打包命令

​		最早的 Linux 备份介质是磁带，使⽤用的命令是` tar` 可以打包后的磁带⽂文件进⾏行行压缩储存，压缩的命令是 `gzip` 和 `bzip2` 经常使⽤用的扩展名是` .tar.gz .tar.bz2 .tgz`

- `tar` 打包命令 常⽤用参数

- 常用参数
  - `c` 打包
  - `x` 解包
  - `f` 指定操作类型为文件

##### 7.2 压缩和解压缩

- 可以使⽤用 `gzip` 和 `bzip2` 命令单独操作 
- 通常和 `tar` 命令配合操作
- 常⽤用参数
  - `-z gzip` 格式压缩和解压缩
  - `-j bzip2` 格式压缩和解压缩
  - `zxf` `jxf`解压缩命令

```shell
tar cf /home/chuzhi/study/etc_back_up.tar /etc
#   打包   打包存放的目录                       目标文件

tar czf /home/chuzhi/study/etc_backup.tar.gz /etc
#   打包压缩

tar xf /home/chuzhi/study/etc_back_up.tar -C /home/chuzhi/a
#   解包


```



## 七、Vim编辑器



#### vim的基本配置

  编辑VIM配置文件

```bash
vim /etc/vimrc
```

```bash
#在最后添加以下内容

set nu          // 设置显示行号
set showmode    // 设置在命令行界面最下面显示当前模式等
set ruler       // 在右下角显示光标所在的行数等信息
set autoindent  // 设置每次单击Enter键后，光标移动到下一行时与上一行的起始字符对齐
syntax on       // 即设置语法检测，当编辑C或者Shell脚本时，关键字会用特殊颜色显示
```



### 1、vim的四种模式

#### 1.1四种模式:

i插入模式
v可视模式
n正常模式
c命令模式

#### 1.2插入模式 `i a o I A O`

`i`进入插入模式
`I`进去插入模式并且光标到当前行开头
`a`进去插入模式并且光标到当前光标的下一位
`A`进去插入模式并且光标到当前行的末尾
`o`进去插入模式并且光标到当前光标的下一行产生空行
`O`进入插入模式并且光标到当前行的上一行产生空行

#### 1.3`:`表示末行模式

### **2.正常模式下，四个方向hjkl**

h 左
l 右
j 下
k 上

正常模式下，复制，粘贴

`yy` 复制单行 `p` 粘贴单行 `3p` 粘贴3行
`3yy` 复制3行（当前行往下三行，包括当前行）

单行无提示，多行有提示

`y$` 复制当前光标位置到这一行的结尾字符
`dd` 剪切一整行

`d$(D)` 剪切当前位置到这一行的结尾
`u` 普通模式下，撤销 ，多次u多次撤销
`u` `ctrl +r` 重做，返回上一次撤销，相当于win的ctrl+y
`x` 删除指定字符，光标选中，按`x`
`r+新字符` 字符替换，光标选中按`r`在输入新字符



`G` 移动到指定行
`:set nu` 查看当前行
`11G` 移动到第11行
`g` 移动到第一行
`G`移动到最后一行
`^` 表示到这一行字符的开头
`$` 表示到这一行的结尾（用于一行太长的情景）

### 3.命令模式

`w + 文件名`保存到指定文件名中，不接文件名表示保存到原始文件当中

`:q`退出

`:q！`强制退出

`:wq!` 强制写入退出

`:! + 功能命令 如：ipconfig`表示临时查看命令

`/ + 字符`表示查找某个字符  `n`向下移动查找 `shift n `向上移动查找



`:s/old/new`替换字符，默认表示所在行范围进行替换

`:s/old/new/g`整个文件范围替换（ g 表示全局）

`:起始行，结束行s/old/new/g `(多次替换加`/g`，单次则不需要)

`例：:3,4s/l/L`即替换3-4行的 l 变为 L 

`:set nu（命令） `表示单次修改设置生效，如 `nu` `nonu`

设置永久生效需设置配置文件`/etc /vimrc`中最后一行添加`set nu`

### 3.可视模式

- 进入方式

  - `v` 字符可视模式

  - `V` 行可视模式

  - `ctrl + v` 块可视模式

    - 配合 `d ` 和`I(插入)`（大写 i ）命令可以进行块的便捷操作 连续按两次`esc`

    

## 八、用户管理

- `useradd` 新建用户  （`root`用户模式下）
- `userdel` 删除用户
- `passwd` 修改用户密码
- `usermod` 修改用户属性
- `chage` 修改用户属性
- `/root` 为`root` 用户的家目录
- `/home/用户名` 为普通用户的家目录



### 1、创建用户`useradd` （`root`用户模式下）

![](https://tva1.sinaimg.cn/large/00831rSTgy1gcbbce5ynsj311e06gmy2.jpg)



### 2、 修改用户密码`passwd`

- `passwd + 用户名` 修改用户密码
- `passwd` 修改`root`用户密码



### 3、删除用户`userdel` 

- `userdel -r 用户名` 删除用户➕用户目录



### 4、组管理命令

- `groupadd` 新建用户组
- `groupdel` 删除用户组
- `useradd -g group1 user1` 
  - 新建用户 user1 并添加到 group1 中



### 5、用户和用户组的配置文件

```shell
#超级用户模式下
vim /ect/passwd

 root:x:0:0:root:/root:/bin/bash
 chuzhi:x:1000:1000:chuzhi:/home/chuzhi:/bin/bash
 wilson:x:1001:1001::/home/wilson:/bin/bash
```

```shell
#存储用户加密的密码文件
vim /etc/shadow
```

```shell
#用户组
vim /etc/group
```



### 6、查看文件权限

<img src="https://tva1.sinaimg.cn/large/00831rSTgy1gcbbyhxt9uj313o0ae75h.jpg" alt="查看文件权限" style="zoom:80%;" />

```shell
# 文件类型
- 普通⽂文件
d ⽬目录⽂文件
b 块特殊⽂文件
c 字符特殊⽂文件 
l 符号链接
f 命名管道
s 套接字⽂文件
```

#### 文件权限表示方法

- 字符权限表示法
  - r  读
  - w 写
  - x  执行
- 数字权限表示法
  - r = 4
  - w = 2
  - x = 1 



- -==rw-==<u>r-x</u>r-- 1 ==userame== <u>groupname</u> mtime filename
  - ==rw-== ⽂文件属主的权限
  - <u>r-x</u> ⽂文件属组的权限
  - r-- 其他⽤用户的权限

创建新⽂文件有默认权限，根据 umask 值计算，属主和属组根据当前进程的⽤用户来设定



#### 目录权限表示方法

- x    进入目录
- rx  显示目录内的文件名
- wx 修改目录内的文件名



### 7、权限管理



#### 修改权限

- chmod 修改⽂文件、⽬目录权限
  - chmod u+x /tmp/testfile
  - chmod 755 /tmp/testfile
- chown
- chgrp

```bash
[root@localhost test]# ls -l /usr/bin/passwd 
-rwsr-xr-x. 1 root root 27856 Aug  9  2019 /usr/bin/passwd
[root@localhost test]# ls -l /etc/shadow
----------. 1 root root 1321 Mar  1 13:12 /etc/shadow
```



#### 特殊权限

- SUID ⽤用于⼆二进制可执⾏行行⽂文件，执⾏行行命令时取得⽂文件属主权限
  - 如 /usr/bin/passwd
- SGID ⽤用于⽬目录，在该⽬目录下创建新的⽂文件和⽬目录，权限⾃自动更更改为该⽬目录的属组（==一般用于文件共享==）
- SBIT ⽤用于⽬目录，该⽬目录下新建的⽂文件和⽬目录，仅 root 和⾃自⼰己可以删除
  - 如 /tmp

例子：

```bash
[root@localhost test]# ls -l /usr/bin/passwd 
-rwsr-xr-x. 1 root root 27856 Aug  9  2019 /usr/bin/passwd
[root@localhost test]# chmod 4755 bfile 
[root@localhost test]# ls -l
-rwsr-xr-x. 1 chuzhi chuzhi 0 Mar  1 13:05 bfile

drwxrwxrwt. 20 root root 4096 Mar  1 13:25 /tmp
[root@localhost test]# chmod 1777 test
[root@localhost test]# ls -l
drwsrwxrwt. 2 root   root   6 Mar  1 12:01 test

```





```bash
[chuzhi@localhost test]$ ls -l
total 0
-rw-r--r--. 1 root root 0 Mar  1 12:01 afile
drwxr-xr-x. 2 root root 6 Mar  1 12:01 test
[root@localhost test]# chmod 400 afile 
[root@localhost test]# ls -l
total 0
-r--------. 1 root root 0 Mar  1 12:01 afile
drwxr-xr-x. 2 root root 6 Mar  1 12:01 test
[root@localhost test]# echo 123
123
[root@localhost test]# echo 123 > afile 
[root@localhost test]# cat afile 
123

```



```bash
[chuzhi@localhost test]$ touch bfile
[chuzhi@localhost test]$ ls -l
总用量 4
-r--------. 1 root   root   4 3月   1 12:05 afile
-rw-rw-r--. 1 chuzhi chuzhi 0 3月   1 13:05 bfile
drwxr-xr-x. 2 root   root   6 3月   1 12:01 test
[chuzhi@localhost test]$ chmod 020 bfile 
[chuzhi@localhost test]$ ls -l
总用量 4
-r--------. 1 root   root   4 3月   1 12:05 afile
-----w----. 1 chuzhi chuzhi 0 3月   1 13:05 bfile
drwxr-xr-x. 2 root   root   6 3月   1 12:01 test
[chuzhi@localhost test]$ id chuzhi
uid=1000(chuzhi) gid=1000(chuzhi) 组=1000(chuzhi)
[chuzhi@localhost test]$ echo 123 > bfile 
-bash: bfile: 权限不够
[chuzhi@localhost test]$ 

```



## 九、网络管理



### 1、网络状态查看

#### 工具包

##### net-tools  & iproute

```bash
#1.net-tools
ifconfig
route
netstat

#2.iproute2 (centos7主推命令)
ip
ss

```



##### ifconfig

- eth0第一块网卡（网络接口）
- 第一个网络接口可能叫下面的名字
  - eno1 板载网卡
  - ens33PCI-E网卡
  - en0s3无法获取物理信息的PCI-E网卡
  - centos 7 使用了一致性网络设备命名，以上都不匹配则使用eth0



#### 网络接口命名修改

- 网卡命名规则受 biosdevname 和 net。ifnames两个参数影响
- 编辑 /etc/default/grub 文件。增加 biosdevname = 0 net.ifnames = 0
- 更新grub
  - 命令#：grub2-mkconfig -o /boot/grub2/grub.cfg
- 重启
  - reboot

|       | biosdevname | net.names | 网卡名 |
| ----- | ----------- | --------- | ------ |
| 默认  | 0           | 1         | ens33  |
| 组合1 | 1           | 0         | em1    |
| 组合2 | 0           | 0         | eth0   |



#### 查看网络情况

- 查看网卡物理链接情况

  ```bash
  mii-tool eth0
  ```



#### 查看网关

- 查看网关

  ```bash
  route -n
  ```

- 使用 -n 参数不解析主机名



### 2、网络配置

#### 常用命令

```bash
ifconfig<接口> <IP地址> [netmask 子网掩码]

#启动
ifup <接口>
#关闭
ifdown <接口>
```



#### 添加网关

```bash
route add defaut gw <网关>

route add -host <指定IP> gw <网关>

route add -net <指定网段> netmask <子网掩码> gw <网关IP>
```



- 添加网关(10.211.55.2)需要先删除原来的网关（10.211.55.1）

  ```bash
  route del default gw 10.211.55.
  #查看网关
  route -n
  route add default gw 10.211.55.2
  ```

- 添加明细路由

  ```bash
  #设定为如果访问的主机为10.0.0.1时，把数据包发给10.211.55.1
  route add -host 10.0.0.1 gw 10.211.55.1
  ```

- 指定访问网段

  ```bash
  #访问192.168.0.1时，通过10.211.55.3出去访问
  route add -net 192.168.0.1 netmask 255.255.255.0 gw 10.211.55.3
  ```

  



#### 网络命令合集：ip命令

- ip addr ls

  ```bash
  ifconfig
  ```

-  ip link set dev eth0 up

  ```bash
  #启动eth0网卡
  ifup eth0
  ```

- ip adds add 10.0.0.1/24 dev eth1

  ```bash
  #修改ip并同时修改子网掩码
  ifconfig eth1 10.0.0.1 netmask 255.255.255.0
  ```

- ip route add 10.0.0/24 via 192.168.0.1

  ```bash
  route add -net 10.0.0.0 netmask 255.255.255.0 gw 192.168.0.1
  ```

例子：

```bash
#修改本季ip地址10.211.55.3为10.211.55.4
ifconfig eth0 10.211.55.4
```

> 注意：如果是使用云主机，该条命令会立即生效。



### 3、路由命令

### 4、网络故障排除

### 5、网络服务管理

### 6、常用网络配置文件

