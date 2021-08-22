# How to Contribute

任何朋辈导师，或想要为学弟学妹答疑解惑的同学，都可以加入 Github Organization [NJU 计科朋辈导师](https://github.com/NJUCS-Peers-Tutors)。您可以通过[邮件](mailto:zzw@smail.nju.edu.cn)请求加入。

您可以在编辑 [NJUCS-FAQs](https://github.com/NJUCS-Peers-Tutors/NJUCS-FAQs) 后，提交 Pull Request 请求修改。

## 直接参与

您可以在 [Issue](https://github.com/NJUCS-Peers-Tutors/NJUCS-FAQs/issues) 区直接回答同学提出的问题，本项目维护者会为您整理并通知您。

如果您就某一问题/话题有经验、分享、想说的话，可以直接在 Issue 区新建问题，我们会为您整合。

## Gitbook 安装

为了安装 gitbook，首先需要 npm 包管理器。在 [node 官网](https://nodejs.org/en/download/) 可以获取 Node.js 和 npm 的安装包。

全局安装 gitbook-cli

```bash
$ npm install -g gitbook-cli
$ gitbook -V
```

更多操作可以参考这里我写的一份gitbook从开箱到使用[教程](https://lawrshen.github.io/post/wsl-gitbook/)。

## Github 操作流程

NJUCS-FAQs 通过 Gitbook 发布，每次向 master 分支提交 pull 后，Github Actions 将自动构建到 gh-pages 分支并发布，等待时间约一分半。

在项目 NJU 计科朋辈导师中的同学，首先将项目下载到本地

```bash
$ git clone https://github.com/NJUCS-Peers-Tutors/NJUCS-FAQs.git
```

切到dev分支开发

```bash
$ git switch dev
```

安装插件

```bash
$ gitbook install
```

修改后本地预览

```bash
$ gitbook serve
# 访问 http://localhost:4000
```

本地提交（可以选择在 [更新日志](/README.md#更新日志) 中简要列举贡献）

```bash
$ git add -A && git commit -m "解答了问题：如何在 Windows 上使用 Linux"
```

提交前先拉取最新版本

```bash
$ git pull -r dev
```

将修改提交到远端

```bash
$ git push -u origin dev
```

提交 Pull Requests并需要reviewer通过

## Gitbook 语法

Gitbook 采用 Markdown 语法，通过学习 [Markdown 教程](https://www.runoob.com/markdown/md-tutorial.html) 可以轻松掌握。

需要新增目录，则在 `SUMMARY.md` 中修改，并运行以下命令获得新文件，详见 [Gitbook 文档（中文版）](https://chrisniael.gitbooks.io/gitbook-documentation/content/format/chapters.html)。

```bash
$ gitbook init
```

本页面使用了 flexible alerts 插件，关于其语法可见 [Gitbook plugin: Flexible Alerts](https://www.npmjs.com/package/gitbook-plugin-flexible-alerts)
