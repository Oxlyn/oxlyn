---
title: Linux 常用命令
date: 2016-06-10 00:30:18
tags: ["Windows"]
---

### 压缩解压
```Plain
$ tar -cvf jpg.tar *.jpg          # 压缩 tar
$ tar -czf jpg.tar.gz *.jpg       # 压缩 tar.gz
$ tar -xvf file.tar               # 解压 tar
$ tar -xzvf file.tar.gz -C /abc   # 解压 tar.gz

$ gzip -v file1.txt               # 压缩
$ gzip -d run.log.gz              # 解压 gzip

$ unzip abc.zip -d /dir           # 解压 zip
```
- c create 创建新的压缩文件
- v verbose 显示详细信息
- f 使用档案名字，最后一个参数，后面只能接档案名
- x extract 解压缩
- z gzip

### 清空文件内容
`$ echo |> /var/log/cinder/api.log`

<!--more-->

### 查看命令所在位置
```Plain
$ whereis ruby                    # Linux
$ which ruby`                     # Linux
```

### 查看 zip 压缩文档的内容
`$ zcat file_name.zip`

### 目录操作 
```Plain
$ ls -lhRa /cpf/                  # 查看目录及子目录的内容
$ du -sh *                        # 统计目录及文件大小
 ```

### VIM/VI 常用命令
```Plain
:%d                              # 删除所有内容
:%s/1.1.1.1/2.2.2.2/g            # 全局替换
:set num                         # 显示行号
:set ff?                         # 显示文件格式
:set ff=unix                     # 更改文件格式
:set ff=dos                      # 更改文件格式
:set paste                       # 防止粘贴时候缩进混乱
:set nopaste                     # 退出 paste 模式
/search_str                      # 查找：n -> next; N -> previous
```

### 挂载 NFS
`$ mount -t nfs 192.168.1.1:/data/sdb2/nfs_share /mnt`

### Chrome 插件
[Postman](http://chromecj.com/web-development/2014-09/60.html)：`http://chromecj.com/web-development/2014-09/60.html`

### Grep 文本搜索
```Plain

$ grep 'search_str' -r /                                 # 全局搜索
$ egrep 'search_str' -r /                                # 全局搜索
$ grep -E 'abc|def'                                      # 正则搜索
$ egrep 'abc|def'                                        # 正则搜索
$ cat /etc/nova/nova.conf | grep -v '#' | grep -v ^$     # 去除空行和注释
$ grep -A 10 'search_str'                                # 显示结果及之后 10 行
$ grep -B 10 'search_str'                                # 显示结果及之前 10 行
$ grep -C 10 'search_str'                                # 显示结果及前后各 10 行
$ grep -v grep                                           # 忽略 grep 本身
$ grep -i Abc                                            # 不区分大小写
```
### Scp 文件拷贝
```Plain
$ scp /home/a.tar.tz root@192.168.0.1:/home/tmp/         # 本地文件拷贝到远程服务器上
$ scp root@192.168.0.1:/home/a.tar.tz ./                 # 从远程机器拷贝到本机
$ scp -r root@192.168.0.2：/home/* ./                    # 拷贝目录中的所有文件
$ sshpass -p 'password' scp -rp username@host:/var/aaa/ /dstdir
```

### SSH 无密码登陆
```Plain
$ ssh-copy-id user@host
$ ssh -vvv user@host   # 显示详细信息
$ sshpass -p 'password' ssh username@192.168.1.1 sudo ls -lhR /var
```

### 数字证书原理
参考：http://blog.sina.com.cn/s/blog_44ee37cd01016r1h.html

### 文件查找
```Plain
$ find / -name live_migrate.py          # 文件查找
$ find / -name live_migrate*            # 模糊查找
```

### SELinux
```Plain
$ sestatus -v                           # 查看状态
$ getenforce                            # 查看状态
$ setenforce 0                          # 设置SELinux 成为permissive模式
$ setenforce 1                          # 设置SELinux 成为enforcing模式
$ vi /etc/selinux/config                # 修改配置文件并reboot, 关闭SELinux
```

### 统计 CPU 的核心数目
`$ grep 'model name' /proc/cpuinfo | wc -l`

### 查看负载状态
`$ cat /proc/loadavg`  
`$ top`  
`$ netstat -n | awk '/^tcp/ {++S[$NF]} END {for(a in S) print a, S[a]}'`  # 网络负载  
`$ netstat -anp | grep -E "23|24" | grep -vE 'LISTEN|<IP>' | wc -l`

### Yum 常用命令
`$ yum provides libnetsnmp* --showduplicates | grep -w libnetsnmp`

### 监视文件变化
```Plain
$ tail -f /var/log/nova-api.log  
$ tail -F /var/log/nova-api.log         # 文件重新建立后,可以继续跟踪  
$ tail -n 20 filename                   # 显示文件末尾 20 行的内容  
$ cat -n filename                       # 显示行号
```

### Virsh 常用命令
`$ virsh list --all`  
`$ virsh define`  
`$ virsh console`  
`$ virsh start|shutdown|reboot|destroy`  
`$ virsh dumpxml`