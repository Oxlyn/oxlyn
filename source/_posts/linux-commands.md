---
title: Linux 常用命令
date: 2016-06-10 00:30:18
tags: Linux
---
  
### ls 查看目录及子目录的内容
  ```
   # ls -lhRa /cpf/
   /cpf/:
   total 4.0K
   drwxr-xr-x.  4 root   root     33 Mar  1 07:17 .
   dr-xr-xr-x. 18 root   root   4.0K Nov 10 02:35 ..
   drwx------.  3 apache apache   16 Mar  1 07:17 var

   /cpf/var:
   total 0
   drwx------. 3 apache apache 16 Mar  1 07:17 .
   drwxr-xr-x. 4 root   root   33 Mar  1 07:17 ..
   drwx------. 4 apache apache 33 Mar  1 07:17 log

   /cpf/var/log:
   total 0
   drwx------. 4 apache apache 33 Mar  1 07:17 .
   drwx------. 3 apache apache 16 Mar  1 07:17 ..
   drwx------. 2 apache apache  6 Mar  1 07:17 httpd
   drwx------. 2 apache apache  6 Mar  1 07:17 keystone
   ```

### 查看命令所在位置
  [Linux]
  `# whereis ruby`
  [Windows]
  `> where ipconfig`

### 查看 zip 压缩文档的内容
  `# zcat file_name.zip`

### 压缩解压
  `# tar -cvf jpg.tar *.jpg`       # 压缩 tar
  `# tar -czf jpg.tar.gz *.jpg`    # 压缩 tar.gz
  `# tar -xvf file.tar`            # 解压 tar
  `# tar -xzvf file.tar.gz`        # 解压 tar.gz

### 清空文件内容
  `# echo |> /var/log/cinder/api.log`

<!--more-->

### VIM/VI 常用命令
  `:%d`                                  # 删除所有内容
  `:%s/10.12.10.151/10.11.0.179/g`       # 全局替换
  `:set num`                             # 显示行号
  `:set ff?`                             # 显示文件格式
  `:set ff=unix / :set fileformat=unix`  # 更改文件格式
  `:set ff=dos / :set fileformat=dos`    # 更改文件格式
  `:set paste`                           # 防止粘贴时候缩进混乱
  `:set nopaste`                         # 退出 paste 模式
  `/search_str`                          # 查找：n -> next; N -> previous

### 挂载 NFS
  `# mount -t nfs 192.168.1.1:/data/sdb2/nfs_share /mnt`

### CentOS7 设置 hostname
  `# hostnamectl set-hostname kilo-ror-keystone1`

### Chrome 发送 HTTP 请求的插件
  [Postman](http://chromecj.com/web-development/2014-09/60.html)：`http://chromecj.com/web-development/2014-09/60.html`

### Grep 文本搜索
  `# findstr /s /i /n /c:"search_str" *.*`                   # Window 全文搜索
  `# grep 'search_str' -r /`                                 # 全局搜索
  `# egrep 'search_str' -r /`                                # 全局搜索
  `# grep -E 'abc|def'`                                      # 正则搜索
  `# egrep 'abc|def'`                                        # 正则搜索
  `# cat /etc/nova/nova.conf | grep -v '#' | grep -v ^$`     # 去除空行和注释
  `# grep -A 10 'search_str'`                                # 显示结果及之后 10 行
  `# grep -B 10 'search_str'`                                # 显示结果及之前 10 行
  `# grep -C 10 'search_str'`                                # 显示结果及前后各 10 行
  参考：http://www.cnblogs.com/end/archive/2012/02/21/2360965.html

### Scp 文件拷贝
  `# scp /home/a.tar.tz root@192.168.0.2:/home/tmp/`         # 本地文件拷贝到远程服务器上
  `# scp root@192.168.0.2:/home/a.tar.tz ./`                 # 从远程机器拷贝到本机
  `# scp -r root@192.168.0.2：/home/* ./`                    # 拷贝目录中的所有文件
  `# sshpass -p 'password' scp -rp username@host:/var/lib/libvirt/images/dir/ /var`

### SSH 无密码登陆
  `# ssh-copy-id user@host`
  `# ssh -vvv user@host`                                     # 显示详细信息
  `# sshpass -p 'password' ssh username@193.168.1.1 sudo ls -lhR /var/ice_vm_backup_*`

### 数字证书原理 
  参考：http://blog.sina.com.cn/s/blog_44ee37cd01016r1h.html

### 文件查找
  `# find / -name live_migrate.py`                          # 文件查找
  `# find / -name live_migrate*`                            # 模糊查找

### CentOS7/RHEL7 Service
  `# pwd` -> usr/lib/systemd/
  `# systemctl {start|stop|status|restart..} <httpd.service>`
  `# systemctl stop firewalld`                               # 禁用防火墙

### SELinux
  `# sestatus -v`                   # 查看状态
  `# getenforce`                    # 查看状态
  `# setenforce 0`                  # 设置SELinux 成为permissive模式
  `# setenforce 1`                  # 设置SELinux 成为enforcing模式
  `# vi /etc/selinux/config`        # 修改配置文件并reboot, 关闭SELinux

### Windows CMD 显示时间
  `> prompt $P$G$T$G`

### 统计目录下文件的大小
  `# du -sh *`

### 统计 CPU 的核心数目
  `# grep 'model name' /proc/cpuinfo | wc -l`

### 查看负载状态
  `# cat /proc/loadavg`
  `# top`
  `# netstat -n | awk '/^tcp/ {++S[$NF]} END {for(a in S) print a, S[a]}'`  # 网络负载
  `# netstat -anp | grep -E "23|24" | grep -vE 'LISTEN|<IP>' | wc -l`

### Yum 常用命令
  `# yum provides libnetsnmp* --showduplicates | grep -w libnetsnmp`

### 监视文件变化
  `# tail -f /var/log/nova-api.log`
  `# tail -F /var/log/nova-api.log`         # 文件重新建立后,可以继续跟踪
  `# tail -n 20 filename`                   # 显示文件末尾 20 行的内容
  `# cat -n filename`                       # 显示行号

### Virsh 常用命令
  `# virsh list --all`
  `# virsh define`
  `# virsh console`
  `# virsh start|shutdown|reboot|destroy`
  `# virsh dumpxml`