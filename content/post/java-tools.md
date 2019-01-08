---
title: "Java 常用工具"
description: "Java Tool Usage"
date: "2019-01-02"
tags: [ "java", "jstat", "jmap"]
---

### Jps
```Plain
$ jps                   # 查看 Java 进程
```

### Jmap
```Plain
$ jmap -histo <pid>     # 查看 JVM 堆中对象数量及空间使用情况
```

### Jstat
```Plain
$ jstat -gcutil <pid>   # 查看 GC 执行情况
```

<!--more-->
