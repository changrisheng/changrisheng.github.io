---
title: Laravel8 & Vue.Js
date: 2021-12-09 14:16:48
tags:
  - Composer
  - Laravel
categories:
  - 学习
keywords:
description: 为Laravel8安装 `laravel-ui` 拓展
top_img:
cover: https://cdn.jsdelivr.net/gh/changrisheng/cdn@master/img/article/laravel-ui.png
---

# 环境版本

| 名称        | 介绍     |
| ----------- | -------- |
| 本地环境    | Laradock |
| Laravel版本 | 8.68.1   |
| Node.js     | v16.8.0  |
| npm         | 7.21.0   |

# 创建Laravel 8 项目


    # 通过composer 安装项目并取名为laravel-ui
    composer create-project --prefer-dist laravel/laravel laravel-ui

    # 安装框架自带的composer依赖
    composer install

    # 应用密钥（一般都会生成好的，如果没有可以自己生成）
    php artisan key:generate

{% span red small right logo, <a href='https://learnku.com/docs/laravel/8.x/installation/9354#e655a4'>Laravel8 中文文档（详细安装步骤）</a> %}

# 安装拓展`laravel/ui`

### 支持的版本
| Version | Laravel Version |
|---- |----|
| [1.x](https://github.com/laravel/ui/tree/1.x) | 5.8, 6.x |
| [2.x](https://github.com/laravel/ui/tree/2.x) | 7.x |
| [3.x](https://github.com/laravel/ui/tree/3.x) | 8.x |

### 安装
> Laravel 提供的 Bootstrap 和 Vue 脚手架位于laravel/uiComposer 包中，可以使用 Composer 安装：

```bash
composer require laravel/ui
```

> 安装完 laravel/ui 包后，可以使用 ui artisan 命令安装前端脚手架:

```bash
// Generate basic scaffolding...
php artisan ui bootstrap
php artisan ui vue
php artisan ui react

// Generate login / registration scaffolding...
php artisan ui bootstrap --auth
php artisan ui vue --auth
php artisan ui react --auth
```

### CSS

[Laravel Mix](https://laravel.com/docs/mix) 提供了干净的、富有表现力的 API，用于编译 SASS 和 Less，它们能够拓展原始的 CSS，拥有向 CSS 中添加变量、mixins 和其它使 CSS 更好用的强大特性。在这篇文档中，我们将简要说明 CSS 的大体编译过程；不过，你最好翻阅完整的 [Laravel Mix 文档](https://laravel.com/docs/mix) 以获取编译 SASS 和 Less 的详细信息。

### JavaScript

Laravel 不要求你使用特定的 JavaScript 框架或库来构建应用。事实上，你完全可以不使用 JavaScript。但是 Laravel 包括了几个基本的脚手架，它们可以使创建基于[Vue](https://vuejs.org)库的现代 JavaScript 变得更容易。Vue 提供了一个极富表现力的 API，使用组件来构建健壮的 JavaScript。像 CSS 一样，可以使用 Laravel Mix 轻松将 JavaScript 组件编译到单个的、基于浏览器的 JavaScript 文件中。

### Writing CSS

在安装 laravel/ui 编写器包并[生成前端脚手架 ](#introduction),之后，Laravel 的 `package.json` 文件将包含 `bootstrap` 包，以帮助你开始使用 `bootstrap` 对应用程序的前端进行原型设计。但是你可以根据自己应用的需要，在 `package.json` 文件中，随意添加或删除依赖包。不是一定要使用 Bootstrap 框架来构建您的 Laravel 应用程序，它只是为想使用它的人提供了一个易用的起点。

编译 CSS 之前，请使用[Node 包管理器 (NPM)](https://www.npmjs.org)安装项目前端依赖:

```bash
npm install
```
