---
title: Composer 国内加速，修改镜像源
date: 2021-12-22 19:38:55
tags:
  - Composer
  - Laravel
categories:
  - 学习
keywords:
description: 修改Composer镜像源方法
top_img:
cover: https://cdn.jsdelivr.net/gh/changrisheng/cdn@master/img/article/composer.jpg
---

# 为什么慢

> 由于默认情况下执行 composer 各种命令是去国外的 composer 官方镜像源获取需要安装的具体软件信息，所以在不使用代理、不翻墙的情况下，从国内访问国外服务器的速度相对比较慢

# 如何修改镜像源
> 可以使用阿里巴巴提供的 Composer 全量镜像 [点击前往](https://developer.aliyun.com/composer)

## 配置只在当前项目生效
    composer config repo.packagist composer https://mirrors.aliyun.com/composer/

    # 取消当前项目配置
    composer config --unset repos.packagist

## 配置全局生效
    composer config -g repo.packagist composer https://mirrors.aliyun.com/composer/

    # 取消全局配置
    composer config -g --unset repos.packagist

## 使用第三方软件快速修改源
> [点击前往Github](https://github.com/slince/composer-registry-manager)

### 安装crm
    composer global require slince/composer-registry-manager

### 列出可用的所有镜像源，前面带 * 代表当前使用的镜像
    composer repo:ls

    -- --------------- ------------------------------------------------
       composer        https://packagist.org
       phpcomposer     https://packagist.phpcomposer.com
       aliyun          https://mirrors.aliyun.com/composer
       tencent         https://mirrors.cloud.tencent.com/composer
       huawei          https://mirrors.huaweicloud.com/repository/php
       laravel-china   https://packagist.laravel-china.org
       cnpkg           https://php.cnpkg.org
       sjtug           https://packagist.mirrors.sjtug.sjtu.edu.cn
    -- --------------- ------------------------------------------------
### 使用 aliyun 镜像源

    composer repo:use aliyun

    # 执行成功之后会输出类似以下信息
    [OK] Use the repository [aliyun] success

### 再次执行 composer repo:ls 命令，看到前面带 * 的就是当前使用的镜像

    composer repo:ls

    # 可以看到 aliyun 前面有一个 * 号，代表当前使用的是 aliyun 的源
    --- --------------- ------------------------------------------------
          composer        https://packagist.org
          phpcomposer     https://packagist.phpcomposer.com
      *   aliyun          https://mirrors.aliyun.com/composer
          tencent         https://mirrors.cloud.tencent.com/composer
          huawei          https://mirrors.huaweicloud.com/repository/php
          laravel-china   https://packagist.laravel-china.org
          cnpkg           https://php.cnpkg.org
          sjtug           https://packagist.mirrors.sjtug.sjtu.edu.cn
    --- --------------- ------------------------------------------------

# 文章来源
> 原文作者：z__r
> 转自链接: [点击前往](https://learnku.com/articles/15977/composer-accelerate-and-modify-mirror-source-in-china)
