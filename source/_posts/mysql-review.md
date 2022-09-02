---
title: Mysql复习
date: 2021-12-03 11:22:54
tags:
  - 复习
  - Mysql
categories:
  - 复习
keywords:
description: Mysql 复习记录
top_img:
cover: https://cdn.jsdelivr.net/gh/changrisheng/cdn@master/img/article/mysql_review.png
---

# Mysql相关知识

## 数据表引擎
{% folding cyan, 点击查看 %}
{% tabs %}
<!-- tab innodb引擎 -->
{% note simple %}
  1. 默认事务型引擎，最重要最广泛的存储引擎，性能非常优秀
  2. 数据存储在共享表空间，可通过配置分开
  3. 对主键查询的性能高于其他类型的存储引擎
  4. 内部做了很多优化，从磁盘读取数据时自动在内存构建hash索引，插入数据时自动构建插入缓冲区
  5. 通过一些机制和工具支持真正的热备份
  6. 支持崩溃后的安全恢复
  7. 支持行级锁
  8. 支持外键
{% endnote %}
<!-- endtab -->
<!-- tab MyISAM引擎 -->
{% note simple %}
  1. 5.1版本前是默认引擎
  2. 拥有全文索引、压缩、空间函数
  3. 不支持事务和行级锁，不支持奔溃后安全恢复
  4. 表存储在两个文件，MYD和MYI
  5. 设计简单，某些场景下性能很好
{% endnote %}
<!-- endtab -->
<!-- tab 其他引擎 -->
{% note simple %}
  1. Archive
  2. Blackhole
  3. CSV、Memory
{% endnote %}
<!-- endtab -->
{% endtabs%}
{% endfolding %}

{% note blue 'fas fa-bullhorn' modern %}待更新{% endnote %}
