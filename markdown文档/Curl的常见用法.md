# Curl常见用法

## 1. 	获取页面内容

```shell
# 默认会发送 GET 请求来获取链接内容到标准输出
curl http://www.codebelief.com

```



## 2. 显示http头

```shell
# -I表示只显示 HTTP 头，而不显示文件内容
curl -I http://www.codebelief.com

# -i表示同时显示 HTTP 头和文件内容
curl -i http://www.codebelief.com

```



##  3.将链接保存到文件

```shell
# 使用 > 符号将输出重定向到本地文件中
curl http://www.codebelief.com > index.html

# -o（小写的 o）：结果会被保存到命令行中提供的文件名
# -O（大写的 O）：URL 中的文件名会被用作保存输出的文件名。使用 -O 选项时，必须确保链接末尾包含文件名，否则 	curl 无法正确保存文件。
curl -o index.html http://www.codebelief.com
curl -O http://www.codebelief.com/page/2/

```



## 4.   使用 -L 跟随链接重定向   

```shell
# 跟随链接重定向。像浏览器一样跟随链接的跳转，获取最终的网页内容。
curl -L http://codebelief.com
```



## 5.   使用 -A 自定义 User-Agent   

```shell
# 使用 -A 来自定义用户代理，例如下面的命令将伪装成安卓火狐浏览器对网页进行请求
curl -A "Mozilla/5.0 (Android; Mobile; rv:35.0) Gecko/35.0 Firefox/35.0" http://www.baidu.com

```





## 6.   使用 -H 自定义 header   

```shell

curl -H "Referer: www.example.com" -H "User-Agent: Custom-User-Agent" http://www.baidu.com
curl -H "Cookie: JSESSIONID=D0112A5063D938586B659EF8F939BE24" http://www.example.com

```



## 7.   使用 -c 保存 Cookie   

```shell

# 当我们使用 curl 访问页面的时候，默认是不会保存 Cookie 的。此处将cookie保存到cookie-example这个文件中
curl -c "cookie-example" http://www.example.com

```



## 8.   使用 -b 读取 Cookie   

```shell
# 将cookie字符串写在命令中
curl -b "JSESSIONID=D0112A5063D938586B659EF8F939BE24" http://www.example.com

# 从cookie-example文件中读取cookie
curl -b "cookie-example" http://www.example.com
```



## 9.   使用 -d 发送 POST 请求   

```shell
# -d 用于指定发送的数据，-X 用于指定发送数据的方式
curl -d "userName=tom&passwd=123456" -X POST http://www.example.com/login

# 在使用 -d 的情况下，如果省略 -X，则默认为 POST 方式
curl -d "userName=tom&passwd=123456" http://www.example.com/login

# 使用GET方式
curl -d "somedata" -X GET http://www.example.com/api
# 使用GET方式
curl -d "somedata" -G http://www.example.com/api

# 从文件data.txt中读取数据
curl -d "@data.txt" http://www.example.com/login

# 带Cookie登录
# 如果我们再次访问该网站，仍然会变成未登录的状态。我们可以用之前提到的方法保存 Cookie，在每次访问网站时都带上该 Cookie 以保持登录状态。
# -c 指定含Cookie信息的文件
curl -c "cookie-login" -d "userName=tom&passwd=123456" http://www.example.com/login
# 再次访问的时候，读取该cookie文件
curl -b "cookie-login" http://www.example.com/login




```

