<!--
 * @Author: ldx
 * @Date: 2021-03-12 17:05:41
 * @LastEditTime: 2021-03-12 17:29:41
 * @LastEditors: ldx
 * @Description: 
 * @FilePath: \my-docs\docs\nginx\liunx安装.md
-->
# 下载地址

  nginx下载地址：https://nginx.org/download/
  
  下载tar.gz 后缀的文件

# 安装nginx 前提要安装的工具
```bash
yum -y install gcc pcre-devel zlib-devel openssl openssl-devel
```

# 解压

  一般解压到/usr/local目录
  ``` bash
  tar -zxvf nginx-1.9.9.tar.gz
  ```

# 进入nginx目录
```bash
  cd /usr/local/nginx-1.9.9
```

# 配置
``` bash
  ./configure --prefix=/usr/local/nginx
```

# make
``` bash
make
make install
```

# 检测安装
  1. cd到刚才配置的安装目录/usr/loca/nginx/
  2. ./sbin/nginx -t

## 错误
错误信息：

nginx: [alert] could not open error log file: open() "/usr/local/nginx/logs/error.log" failed (2: No such file or directory)
2016/09/13 19:08:56 [emerg] 6996#0: open() "/usr/local/nginx/logs/access.log" failed (2: No such file or directory)

原因分析：nginx/目录下没有logs文件夹

解决方法：

```bash
mkdir logs
chmod 700 logs
```

## 正常

nginx: the configuration file /usr/local/nginx/conf/nginx.conf syntax is ok
nginx: configuration file /usr/local/nginx/conf/nginx.conf test is successful

# 启动

```bash
cd /usr/local/nginx/sbin
./nginx //启动nginx
```

# 配置nginx开机自启动

```bash
vim /etc/rc.d/rc.local
```
添加/usr/local/nginx/sbin/nginx (nginx的启动文件的路径)

> 参考：https://www.cnblogs.com/xxoome/p/5866475.html