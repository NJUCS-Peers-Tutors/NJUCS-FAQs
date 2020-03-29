# 获取帮助的方法

作为一名计科学生，或是作为一名大学生，最需要掌握的能力不是某个工具的熟练使用，而应该是自学能力。自学中的关键一点在于遇到问题时如何找到答案，需求帮助。

> [!Note|style:flat|label:本项目不是在帮你偷懒]
> 我们首先鼓励的是自己解决问题，在自己 STFW 和 RTFM 时，收获是最大的。在这里，我们希望的是
>
> - 让你知道某些工具的存在；至于如何使用甚至如何下载安装，Google 一下就有了
> - 帮助你对某些工具入门：帮助入门，实际上是帮助克服对工具的恐惧心理；上手后，继续学习*可能*就简单了
> - NJU 特色的回答：直系学长学姐帮助回答，结合了 NJU 实情

授人以鱼不如授人以渔，[jyy 如何获取帮助](https://nju-projectn.github.io/ics-pa-gitbook/ics2019#如何获得帮助) 中已经列举了常用的方法。鉴于其重要性，在这里重新整理给大家。

## Search by English First

很多英语资料的质量优于中文资料，且翻译中容易出现让人读不懂的情况。在中文资料没有保障，官方手册不存在中文版的时候，英语资料是我们的首选。

当然有很多同学难以适应查阅英语资料，jyy 老师给出了解决方法

> 尝试并坚持查阅英文资料

## STFW

Search The Fxxking Web.

|        | 搜索引擎                              | 百科                         | 问答网站                   |
| ------ | ------------------------------------- | ---------------------------- | -------------------------- |
| 推荐   | google([镜像](https://ac.scmor.com/)) | <http://en.wikipedia.org>    | <http://stackoverflow.com> |
| 不推荐 | ~~<http://www.baidu.com>~~            | ~~<http://baike.baidu.com>~~ | ~~<http://bbs.csdn.net>~~  |

具体理由见[此处](https://nju-projectn.github.io/ics-pa-gitbook/ics2019/#%E6%90%9C%E7%B4%A2%E5%BC%95%E6%93%8E-%E7%99%BE%E7%A7%91%E5%92%8C%E9%97%AE%E7%AD%94%E7%BD%91%E7%AB%99)

对于开源工具的问题，记得在项目主页的 Issue 处进行搜索

## RTFM

Read The Fxxking Manual

官方手册包含了查找对象的所有信息, 关于查找对象的一切问题都可以在官方手册中找到答案。

首先，可以通过搜索引擎定位你需要的手册。如果手册是网站形式出现的，你可以使用搜索引擎搜索该网站以快速定位需要的内容。如搜索：`nonlocal site:docs.python.org`

一般来说，手册中包含这样几个常用的章节

- Installation: 如何安装
- Get Started: 快速上手，帮助入门
- FAQs: 使用中常出现的问题

对于终端工具，可以直接使用 `man` 命令查询，其文档遵循一定格式。读的次数越多，就越能适应这种格式了

```bash
$ man ls
```

工具 `tldr` 基于社区维护（需要下载），对常用的方法进行解释。

```bash
$ tldr pip
```

同样，终端命令常常还可以使用参数获得帮助

```bash
$ pip --version
# 确认是否安装和确认版本，常见的此类参数还有 -v,-V
$ pip -h
# same to: pip --help
```

## 提问

推荐大家阅读[提问的智慧](http://www.catb.org/~esr/faqs/smart-questions.html)或[中文版](https://github.com/ryanhanwu/How-To-Ask-Questions-The-Smart-Way)

本站的问题来源于朋辈导师与大家交流中的普遍问题。你也可以在本项目的 [Issue](https://github.com/NJUCS-Peers-Tutors/NJUCS-FAQs/issues) 处提问。

或者你可以直接联系你的朋辈导师，让南大直系学长学姐为你解决问题。如果你的问题也是大家的问题，将被收录在这里。
