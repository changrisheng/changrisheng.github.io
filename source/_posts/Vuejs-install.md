---
title: Vue.js安装步骤
date: 2021-12-29 13:06:03
tags:
  - Vue.js
categories:
  - 学习
keywords:
description: 记录Vue.js安装步骤
top_img:
cover: https://cdn.jsdelivr.net/gh/changrisheng/cdn@master/img/article/vuejs.jpg
---

## 版本介绍

| 名称   | 版本    |
| ------ | ------- |
| node   | v17.3.0 |
| npm    | 8.3.0   |

## 起飞

> 安装`Vue 3.0`版本 使用脚手架安装
> 安装 `Vue 3`，你应该使用 npm 上可用的 `Vue CLI v4.5` 作为 `@vue/cli`。
> 要升级，你应该需要全局重新

```sh
# 首先全局进行安装
yarn global add @vue/cli
# 或
npm install -g @vue/cli

# 之后在Vue项目中使用
vue upgrade --next

# 创建项目
vue create [项目名称]

Vue CLI v4.5.15
? Please pick a preset:
❯ Default ([Vue 2] babel, eslint)
  Default (Vue 3) ([Vue 3] babel, eslint)
  Manually select features

? Pick the package manager to use when installing dependencies:
  Use Yarn
❯ Use NPM

# 运行完成后
✨  Creating project in /var/www/vue.
🗃  Initializing git repository...
⚙️  Installing CLI plugins. This might take a while...


added 1276 packages in 50s

17 packages are looking for funding
  run `npm fund` for details
🚀  Invoking generators...
📦  Installing additional dependencies...


added 55 packages in 4s

17 packages are looking for funding
  run `npm fund` for details
⚓  Running completion hooks...

📄  Generating README.md...

🎉  Successfully created project vue.
👉  Get started with the following commands:

 $ cd vue
 $ npm run serve

 WARN  Skipped git commit due to missing username and email in git config, or failed to sign commit.
You will need to perform the initial commit yourself.
```

### Vue 命令说明

```sh
root@b4ec61ffb8aa:/var/www# vue
Usage: vue <command> [options]

Options:
  -V, --version                              output the version number
  -h, --help                                 output usage information

Commands:
  create [options] <app-name>                create a new project powered by vue-cli-service
  add [options] <plugin> [pluginOptions]     install a plugin and invoke its generator in an already created project
  invoke [options] <plugin> [pluginOptions]  invoke the generator of a plugin in an already created project
  inspect [options] [paths...]               inspect the webpack config in a project with vue-cli-service
  serve [options] [entry]                    serve a .js or .vue file in development mode with zero config
  build [options] [entry]                    build a .js or .vue file in production mode with zero config
  ui [options]                               start and open the vue-cli ui
  init [options] <template> <app-name>       generate a project from a remote template (legacy API, requires @vue/cli-init)
  config [options] [value]                   inspect and modify the config
  outdated [options]                         (experimental) check for outdated vue cli service / plugins
  upgrade [options] [plugin-name]            (experimental) upgrade vue cli service / plugins
  migrate [options] [plugin-name]            (experimental) run migrator for an already-installed cli plugin
  info                                       print debugging information about your environment

  Run vue <command> --help for detailed usage of given command.
```

## 安装完成

![](https://cdn.jsdelivr.net/gh/changrisheng/cdn@master/img/article/vue/vue_install.png)
