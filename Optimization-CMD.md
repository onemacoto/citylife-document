# 1. 常用Linux命令

## 1.1 网络TCP阻塞原因调查

``` shell
netstat -n | awk '/^tcp/ {++S[$NF]} END {for(a in S) print a, S[a]}'
```

## 1.2  显示了当前 shell 环境中已启动的作业状态

``` shell
jobs -l
```

## 1.3  列出系统中左右的Java应用程序

``` shell
jps -l
```

## 1.4  查看某个端口的连接数

``` shell
netstat -nat|grep -i "80"|wc -l
```

## 1.5  统计httpd协议连接数

``` shell
ps -ef|grep httpd|wc -l
```

##  1.6 统计已连接上的连接数

``` shell
netstat -na|grep ESTABLISHED|wc -l
```

## 1.7 查看进程占用的端口

``` shell
netstat -nap | grep 32176
```

## 1.8 查看占用端口的进程

```shell
netstat -tunlp | grep 9001
```

## 1.9 查出哪个IP地址连接数最多

``` shell
netstat -na|grep ESTABLISHED|awk "{print $5}"|awk -F: "{print $1}"|sort|uniq -c|sort -r
```

## 1.11 列出打开的文件

 ```shell
# 列出所有打开的文件
lof
# 找出谁在使用某个文件
lsof /path/to/file
# 递归查找某个目录中所有打开的文件
lsof +D /usr/lib
lsof | grep ‘/usr/lib’
# 列出某个用户打开的所有文件
lsof -u appdeploy
 ```

## 1.12  查看硬盘使用状况

``` bash
df -lh
```

## 1.13 查询档案或目录的磁盘使用空间

``` shell
du -ah
```



## 1.14  按照文件名查找文件

```shell
find ./* -name "*.log"
```



## 1.15  Grep查找文件

``` shell
grep -i pattern files ：不区分大小写地搜索。默认情况区分大小写
grep -l pattern files ：只列出匹配的文件名,不列出路径
grep -L pattern files ：列出不匹配的文件名
grep -w pattern files ：只匹配整个单词，而不是字符串的一部分（如匹配‘magic’，而不是‘magical’）grep -C number pattern files ：匹配的上下文分别显示[number]行
grep pattern1 | pattern2 files ：显示匹配 pattern1 或 pattern2 的行
grep pattern1 files | grep pattern2 ：显示既匹配 pattern1 又匹配 pattern2 的行
```



##  1.16  针对活着的进程做本地的或远程的线程dump

``` shell
jstack [-l] pid
```



