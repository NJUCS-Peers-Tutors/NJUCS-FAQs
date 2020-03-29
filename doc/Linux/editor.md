# 文本编辑器

## Vim

在这里要介绍一个强大的编辑器，叫*vim*，传说中的**编辑器之神**，与 Emacs, **其他编辑器**三分天下。很多人都经历了『从入门到放弃』的痛苦过程（~~俺也一样~~）。不过这个编辑器之后是会伴随我们的生涯的，网上有很多资料（你们有的那个 word Linux 相关资料里的[ICS 课程的讲义](https://nju-projectn.github.io/ics-pa-gitbook/ics2019/)很有用，推荐去看）。这里我只介绍下一些简单的操作（~~毕竟很多人第一次用甚至都不会退出~~）

### 打开并编辑

```bash
vim hello_world.cpp
```

你会发现什么都做不了，甚至都退出不了，可以摸索下。

按下`i`键，发现窗口左下角出现了`-- INSERT --`，表示进入了插入模式，这时候也就可以编辑了。我们可以写一个 C++的 hello world。

```c++
#include <iostream>
using namespace std;

int main(){
    cout << "Hello World" << endl;
    return 0;
}
```

如果你是`Tab`键缩进选手，你会发现此时的 Tab 缩进不是 4 个空格，这个细节日后可能会让你在 windows 下移植到 linux 的代码变得你不认识的样子。同时，如果你试图用 Visual Studio 编辑，然后放到 linux 下，可能还会遇到 GBK 和 utf-8 编码的问题。所以同学们还是老老实实学习吧（~~或者想办法解决这些问题~~）。

### 保存并退出

言归正传，写完程序后怎么保存呢？同样是按下`q`，退出插入模式，键入`:x`即可保存并退出。如果没有进行编辑，可以用`:q`退出。若要放弃编辑的内容，可以用`:q!`。

### 查看文件内容

保存完后，可以使用 cat 命令查看`hello_world.cpp` 文件内容(catenate)

```bash
cat hello_world.cpp
```

![查看文件内容]("https://tsunaou.github.io/linux_guide/images/6.png")

可以看到 hello world 的程序编写完毕。

## 更舒服的写代码方式

Linux 下写代码确实是一键让人头秃的事情。在 Windows 下面有 devc++、visual studio 这些 IDE，写完代码就可以 F5 直接运行了。但是在 Linux 中，用无插件的 vim 直接写代码，然后敲出 gcc 编译无疑一件是痛苦的事(没有代码补全、必须手动输入空格和回车以维持良好的代码风格、手动写 makefile 编译等)。但是，微软的 vscode 横空出现解决了这一难题。

### 什么是 vscode?

vscode 是一款跨平台的代码编辑器，windows、linux、macos 下都可以安装，并且使用方法类似。vscode 提供了丰富的插件，你可以用 vscode 写几乎所有类型的代码:c/c++、Java、python、markdown、latex 等。

### linux 下安装 vscode

从微软官网下载对应的 Linux 系统 vscode 安装包，在 ubuntu 中 ，下载完后，就可以用 dpkg 命令来安装了。(貌似 vscode 现在不提供 32 位 linux 系统的版本了，或许可以从网上下载之前的 32 位版本安装?)

### 安装 vscode 插件

Vscode 应用商店中有很多插件。对于写 C++代码，首先需要安装 C/C++插件。可以安装 C/C++ Project Generator 或者 Easy C++ Project 这种类型的插件，它能够帮你自动编写 makefile、建立含有 src、bin 和 include 文件夹的项目目录，你就可以写完代码后愉快地按下 run 或者 debug 就开始运行了。具体的插件安装和配置网上都有很多教程，大家可以主动搜索资料(~~其实是我太懒~~)。
