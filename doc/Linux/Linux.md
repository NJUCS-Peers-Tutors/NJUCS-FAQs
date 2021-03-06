# Linux 基本操作

## 前言

16级 欧阳鸿荣：
> 听说你们即将进行程设实验的第二次大实验——**Linux 相关实验**。听到这里，我脑海里不禁浮现起了当时学这个时遇到了一大堆神奇的错误（~~如果不是天选之子的话，你们肯定也会遇到各种报错的~~）。
>
> 刚好看到阿里云给我的短信，说我的服务器快到期了，于是我想想干脆把我的服务器给大家当个 playground，也可以在 Vmware 和 ubuntu 镜像安装的时候，熟悉熟悉 linux 的命令操作。（由于服务器可以无限重装，所以可以尽请尝试~~不必担心会搞出什么大新闻~~）

## 实验平台

目前可以使用的平台

| IP Address   | user  | password   | 到期时间         | 镜像         |
| ------------ | ----- | ---------- | ---------------- | ------------ |
| 120.78.76.94 | root  | njucs@2019 | 2020-04-04 00:00 | Ubuntu 18.04 |
| 120.78.76.94 | njucs | njucs      | 2020-04-04 00:00 | Ubuntu 18.04 |

## 连接方式

Windows 系统下可以使用 cmd、winscp（你们教程里的）、MobaXterm 等工具 ssh 连接服务器。以 cmd 为例，首先按键 `win+R`,键入`cmd`，即可看到一个黑框框，再键入下方指令。

Macos, Linux 系统下可以直接打开终端（Terminal），键入下方指令。

```bash
$ ssh njucs@120.78.76.94
```

如果有弹出提示消息，键入 yes 并回车。若成功登陆，你会看到这样一个画面：

![登录成功](https://tsunaou.github.io/linux_guide/images/login.png)

然后你就可以开始愉快的 Linux 探索之旅了（温馨提示，用用`tab`键可以自动补全，在我配置的这个服务器上，尝试方向键`↑`说不定也有奇效哟）

## 相关教程

- [jyy 的贴心教程](https://nju-projectn.github.io/ics-pa-gitbook/ics2019/linux.html)
