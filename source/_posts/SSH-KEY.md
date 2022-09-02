---
title: 如何生成SSH key
date: 2021-12-07 16:39:28
tags:
  - SSH
categories:
  - 工具
keywords:
description: 生成SSH key步骤
top_img:
cover: https://cdn.jsdelivr.net/gh/changrisheng/cdn@master/img/article/ssh-key.jpg
---

{% tip cogs %}SSH key提供了一种与GitHub通信的方式，通过这种方式，能够在不输入密码的情况下，将GitHub作为自己的remote端服务器，进行版本控制{% endtip %}

1. 检查SSH keys是否存在
2. 生成新的ssh key
3. 将ssh key添加到GitHub中

![](https://cdn.jsdelivr.net/gh/changrisheng/cdn@master/img/article/ssh-key/gevin-essay-how-to-generate-SSH-key.png)

# 检查SSH keys是否存在

{% note info simple %}输入下面的命令，如果有文件`id_rsa.pub` 或 `id_dsa.pub`，则直接进入步骤3将SSH key添加到GitHub中，否则进入第二步生成SSH key{% endnote %}


    ls -al ~/.ssh
    # Lists the files in your .ssh directory, if they exist


# 生成新的ssh key

> 生成public/private rsa key pair 在命令行中输入`ssh-keygen -t rsa -C "your_email@example.com"`
  默认会在相应路径下（/your_home_path）生成id_rsa和id_rsa.pub两个文件，如下面代码所示


    ssh-keygen -t rsa -C "your_email@example.com"
    # Creates a new ssh key using the provided email
    Generating public/private rsa key pair.
    Enter file in which to save the key (/your_home_path/.ssh/id_rsa):

> 输入passphrase（本步骤可以跳过）


    设置passphrase后，进行版本控制时，每次与GitHub通信都会要求输入passphrase，以避免某些“失误”
    Enter passphrase (empty for no passphrase): [Type a passphrase]
    Enter same passphrase again: [Type passphrase again]

> 将新生成的key添加到ssh-agent中:

    # start the ssh-agent in the background
    eval "$(ssh-agent -s)"
    Agent pid 59566
    ssh-add ~/.ssh/id_rsa

# 将ssh key添加到GitHub中
{% note info simple %}用自己喜欢的文本编辑器打开`id_rsa.pub`文件，里面的信息即为SSH key，将这些信息复制到GitHub的Add SSH key页面即可{% endnote %}

{% tip sync %}不同的操作系统，均有一些命令，直接将SSH key从文件拷贝到粘贴板中，如下：{% endtip %}

> mac

    pbcopy < ~/.ssh/id_rsa.pub

    # Copies the contents of the id_rsa.pub file to your clipboard

> windows

    clip < ~/.ssh/id_rsa.pub

    # Copies the contents of the id_rsa.pub file to your clipboard

> linux

    sudo apt-get install xclip
    # Downloads and installs xclip. If you don't have `apt-get`,
      you might need to use another installer (like `yum`)

    xclip -sel clip < ~/.ssh/id_rsa.pub
    # Copies the contents of the id_rsa.pub file to your clipboard
