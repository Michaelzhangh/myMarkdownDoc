

# shell编程

## 1. shell是什么

 Shell是指一种应用程序，这个应用程序提供了一个界面，用户通过这个界面访问操作系统内核的服务, Shell脚本（shell script），是一种为Shell编写的脚本程序。我们经常说的shell通常都是指shell脚本。 



## 2. 环境和工具

 Shell跟java、php、Python编程一样，只要有一个能编写代码的文本编辑器和一个能解释执行的脚本解释器就可以了。  Linux 自带了shell解释器 



## 3. sh与bash

sh: Bourne shell，POSIX（Portable Operating System Interface）标准的shell解释器，它的二进制文件路径通常是/bin/sh

bash: Bash是Bourne shell的替代品，属GNU Project，二进制文件路径通常是/bin/bash



## 快速学习编写shell脚本

	### 编写shell

 新建一个文件，扩展名为sh（sh代表shell） 

```shell
# 第一行一般是这样。#!是一个约定的标记，它告诉系统这个脚本需要什么解释器来执行。 /env 表示在系统的PATH目录中查找
#!/usr/bin/env bash
#!/bin/bash
```

### 运行shell脚本的两种方法

  * 方法一：作为可执行程序

    ```shell
    chmod +x op_base.sh
    ./op_base.sh
    ```

  * 方法二：作为参数

    ```shell
    /bin/sh op_base.sh
    ```

    

### 变量

  定义变量时，变量名前不需要加符号 。

  变量名和等号之间不能有空格,变量后面不能有分号; 

  字符串可以用单引号，也可以用双引号 。

单引号字符串的限制：

- 单引号里的任何字符都会原样输出，单引号字符串中的变量是无效的
- 单引号字串中不能出现单引号（对单引号使用转义符后也不行）

双引号字符串的限制：

- 双引号里可以有变量
- 双引号里可以出现转义字符



```shell
# 定义变量
my_name="jack"

# 使用变量，在前面添加$
# 变量名外面的花括号是可选的，加不加都行,建议使用第二种形式
echo $my_name
echo ${my_name}

```



### 注释

 以“#”开头的行就是注释，会被解释器忽略。 

 sh里没有多行注释，只能每一行开头加一个#号。 

```shell
#--------------------------------------------
# Author:  jack 
#
# Notes: 10分钟入门Shell脚本编程
#
# Project home page:
#       https://github.com/hi-dhl/fast_guides
#--------------------------------------------
```



### 字符串

 字符串可以用单引号，也可以用双引号，也可以不用引号。 

 在Shell中常用的数据类型数字和字符串 。

```shell
# 拼接字符串
my_name="jack";
my_age="20岁"
echo $my_name $my_age
echo $my_name$my_age

# 获取字符串长度
echo ${#my_name}

# 截取字符串
echo ${my_name:0:2}

```



### shell数组

```shell
# 定义数组
# 用括号来表示数组，数组元素用"空格"符号分割开。定义数组的一般形式为：
name=(name1 name2 name3)

# 还可以单独定义数组的各个分量。可以不使用连续的下标，而且下标的范围没有限制
ary[0]=name1
ary[1]=name2
ary[3]=name3

# 读取数组元素值的一般格式是：${数组名[下标]}
echo ${name[0]}

# 使用@符号可以获取数组中的所有元素
echo ${name[@]}

# 获取数组长度的方法与获取字符串长度的方法相同
# 取得数组元素的个数
length=${#name[@]}
echo $length

# 或者
length=${#name[*]}
echo $length

# 取得数组单个元素的长度
length=${#name[n]}
echo $length

```



### shell流程控制

 * if

    如果else分支没有语句执行，就不要写这个else 

   ```shell
   # 语法格式
   if condition1
   then
       command1
   elif condition2 
   then 
       command2
   else
       commandN
   fi
   
   
   # 举例如下
   #!/usr/bin/env bash
   
   a=1
   b=2
   if [ $a == $b ]
       then
           echo "a 等于 b"
    elif [ $a -gt $b ]
       then
           echo "a 大于 b"
    elif [ $a -lt $b ]
       then
           echo "a 小于 b"
    else
       echo "没有符合的条件"
   
    fi
   ```

   

 * for

   ```shell
   # 第一种写法
   for index in 1 2 3 4 5; do
       echo "index="$index
   done
   
   
   # 第二种写法
   for ((i=0; i<5; i++)); do
       echo "i="$i
   done
   
   ```

   

	* while

 while循环用于不断执行一系列命令，也用于从输入文件中读取数据； 

```shell
int=1
while(( $int<=5 ))
do
    echo $int
    let "int++"
done
```



### Shell结合Linux系统命令































