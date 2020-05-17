# Linux常用命令

# 目录操作

### 基本操作

* mv
* rm

* cp

* mkdir

  ```shell
  # 创建目录和父目录a,b,c,d
  # -p 表示确保目录名称存在，不存在的就建一个
  mkdir -p a/b/c/d
  
  # 拷贝文件夹a到/tmp目录
  # -r表示递归，-v表示显示进度，-f表示强制(覆盖已经存在的目标文件而不给出提示)
  cp -rvf a/ /tmp/
  
  # 移动文件a到/tmp目录，并重命名为b
  mv -vf a /tmp/b
  
  # 删除机器上的所有文件
  rm -rvf /
  ```
  
  

### 	漫游

 * find

 * ls

 * pwd

 * cd

   

### 文本处理

 * cat

 * less

 * tail

 * head

 * grep

   

   ```shell
   # 查看文件大小
   #-h 表示human-readable 以K，M，G为单位，提高信息的可读性。
   du -h file
   
   # 查看文件内容(全部)
   cat file
   
   # 查看文件内容(滚动)
   less file
   
   # 实时滚动
   tail -f access.log
   
   # 静态查看
   tail -n100 access.log
   head -n100 access.log
   
   # 正则关键词搜索
   # A  after  内容后n行
   # B  before  内容前n行
   # C  count?  内容前后n行
   # -r 表示递归，-n表示显示行数，--color表示高亮
   grep -rn --color POST access.log
   grep -rn --color Exception -A10 -B2 error.log
   
   ```
   
   
   
   
   
   

## 压缩与解压

 * tar

 * zip

   ```shell
   # 压缩
   tar cvfz archive.tar.gz dir/
   # 解压
   tar xvfz. archive.tar.gz
   
   # 压缩
   zip -r myfile.zip ./*
   
   # 解压到当前目录
   unzip filename.zip
   # 解压到-d指定的目录。-o表示不提示的情况下覆盖文件
   unzip -o -d /home/sunny myfile.zip
   
   ```
   
   
   
   



# 日常运维

* mount
* 管理用户组和用户
* passwd
* chown
* chmod
* yum
* systemctl
* su

```shell
# 挂在一些外部设备到(挂载Linux系统外的文件)到某一目录之下
mount /dev/sdb1 /mnt

# 不加任何参数，仅创建用户,此时用户的家目录是/home/myuser。创建用户的时候会默认创建一个和用户名相同的用户组
useradd myuser

# -d 目录 指定用户主目录，如果此目录不存在，则同时使用-m选项，可以创建主目录
useradd -d /opt/myuser -m myuser

# -g 用户组 指定用户所属的用户组。前提条件是指定的用户组已存在
useradd -g mygroup myuser

# 修改用户信息，用法同useradd
usermod xxx

# 删除用户
userdel myuser

# 删除用户，同时删除用户的主目录
userdel -r myuser

# 创建用户组
groupadd mygroup

# 删除用户组
groupdel mygroup

# 设置密码
passwd myuser

# 修改自己的密码(普通用户或root用户)
输入passwd命令后按回车键

# 锁定账号
passwd -l myuser

# 解锁账号
passwd -u myuser

# 删除用户的密码，用户以后可以无密码登录
passwd -d myuser

# 修改a目录的用户和组为 xjj。-R表示递归，第一个xjj表示用户，第二个xjj表示用户组。用户组可以省略。
chown -R xjj:xjj a

# 给a.sh文件增加执行权限
chmod +x a.sh

# -y表示安装过程提示选择全部为"yes"
yum -y install wget 

# centos管理后台服务
systemctl restart mysqld

# 切换用户
su xjj

```





# 系统状态概览

 * uname

 * ps

 * top

 * free

 * ifconfig

 * ip addr

 * ping

 * netstat

   
   
   ```shell
   # 显示操作系统信息
   uname -a
   
   # 查看进程/线程状态
   ps -ef|grep java
   
   # 实时显示 process 的动态，-H表示线程模式，-p表示后面要接进程id
   top -H -p pid
   
   # free是专门用来查看内存的。包括物理内存和虚拟内存swap
   free
   
   # 查看ip地址
   ifconfig
   ip addr
   
   # 查看网络连通状态
   ping
   
   # 查看当前的所有tcp连接
   netstat -ant
   
   ```
   
   
   
   

# 工作常用

 * export

 * env

 * date

 * hwclock

 * ssh

 * scp

 * wget

   
   
   ```shell
   # export key=value  export用来设定环境变量
   export PATH=$PATH:/home/xjj/jdk/bin
   
   # 查看当前系统中所有的环境变量
   env
   
   # 输出当前的系统时间
   date
   
   # 输出当前的系统时间(硬件时间)
   hwclock
   
   # ssh隧道
   ssh 192.168.48.131
   
   # scp用来进行文件传输。也可以用来传输目录
   scp -r a_dir 192.168.0.12:/tmp/
   
   # 直接使用命令行下载文件，并支持断点续传。 -c表示continue
   wget -c http://oracle.fuck/jdk2019.bin
   
   ```
   
   
   
   



