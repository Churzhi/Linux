## 一、安装Linux

官网下载链接：[http://isoredirect.centos.org/centos/7/isos/x86_64/](http://isoredirect.centos.org/centos/7.4.1708/isos/x86_64/)

阿里云站点：http://mirrors.aliyun.com/centos/7/isos/x86_64/

- `init 3` 由图形界面切换为命令行界面

- `init 0` 关机

- 在图形界面使用 `ctrl+alt+F2`切换到dos界面  

  dos界面 `ctrl+alt+F2`切换回图形界面

  在命令上 输入 `init 3` 命令 切换到dos界面 

  输入` init 5`命令 切换到图形界面

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

![](https://tva1.sinaimg.cn/large/0082zybpgy1gbslv2kba0j311e06gjs8.jpg)

### 2、 修改用户密码`passwd`

- `passwd + 用户名` 修改用户密码
- `passwd` 修改`root`用户密码

### 3、删除用户`userdel` 

- `userdel -r 用户名` 删除用户➕用户目录



## 九、组管理命令

- `groupadd` 新建用户组
- `groupdel` 删除用户组
- `useradd -g group1 user1` 
  - 新建用户 user1 并添加到 group1 中

