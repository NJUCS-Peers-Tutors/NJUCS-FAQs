# Linux基本操作熟悉

南京大学 欧阳鸿荣

[TOC]

## 0.前言

听说你们即将进行程设实验的第二次大实验——**Linux相关实验**。听到这里，我脑海里不禁浮现起了当时学这个时遇到了一大堆神奇的错误（~~如果不是天选之子的话，你们肯定也会遇到各种报错的~~）。刚好看到阿里云给我的短信，说我的服务器快到期了，于是我想想干脆把我的服务器给大家当个playground，也可以在Vmware和ubuntu镜像安装的时候，熟悉熟悉linux的命令操作。（由于服务器可以无限重装，所以可以尽请尝试~~不必担心会搞出什么大新闻~~）

### 更新日志

> 2020.3.29
>
> - 感谢17级郑奘巍提供的gitbook框架，并发起了[NJUCS-Peers-Tutors](https://github.com/NJUCS-Peers-Tutors)/**NJUCS-FAQs**项目
>
> 2020.3.28 
>
> - 感谢17级陈善梁分享了 
>   - 2.6 更舒服的写代码方式
>   - 2.7在windows运行Linux系统
>
> - 感谢16级吴德亚分享了自己Debug经验
>   - 3.31 面对BUG时，怎么办呢？
>
> 2020.3.27 
>
> - 完成初稿

## 1.配置

本服务器使用的是阿里云的Ubuntu18.04镜像，即将于2020-04-04 00:00到期。

| IP Address   | user  | password   |
| ------------ | ----- | ---------- |
| 120.78.76.94 | root  | njucs@2019 |
| 120.78.76.94 | njucs | njucs      |



## 2.入门

### 2.1 连接方式

Windows下可以使用cmd，winscp（你们教程里的）、MobaXterm等工具ssh连接服务器。以下以cmd为例子。

首先，`win+R`,键入`cmd`，即可看到一个黑框框。输入下列命令：

```bash
ssh njucs@120.78.76.94
```

若成功登陆，你会看到这样一个画面：

<div>
    <img src="https://tsunaou.github.io/linux_guide/images/login.png">
</div>

然后你就可以开始愉快的Linux探索之旅了（温馨提示，用用`tab`键可以自动补全，在我配置的这个服务器上，尝试方向键`↑`说不定也有奇效哟）

### 2.2 目录操作

我没有创建太多用户，大家都是在njucs用户下进行操作，所以为了分开不同用户的操作，我们需要新建一个工作目录，以免产生冲突。

#### 查看当前目录

使用`pwd`命令查看当前目录(Print Working Directory)

```bash
pwd
```

可以看到结果是`/home/njuics`

#### 创建目录

使用 `mkdir` 命令创建目录（Make Directory，实际操作的时候可以把guide换成你的学号）

```bash
mkdir guide
```

#### 切换目录

使用 `cd` 命令切换目录(Change Directory)

```bash
cd guide
```

此时继续运行`pwd`，可以看到结果是`/home/njucs/guide`

这个时候你可能会注意到shell里有一个`~/guide`

<div>
    <img src="https://tsunaou.github.io/linux_guide/images/2.png">
</div>

实际上，在linux中对于目录有一些特别的记号：

- `~`：表示用户的home目录，对于njucs用户来说，`~`就是`/home/njucs`
- `/`：表示系统根目录
- `..`：表示上级目录
- `.`：表示当前目录
- `-`：表示前一个工作目录

同学们可以用`cd`命令进行尝试

#### 查看目录下的文件

使用 `ls` 命令查看目录下所有文件和文件夹(List)

```bash
ls /tmp
```

在linux中，以`.`开头的文件属于隐藏文件，如果想要显示这些文件，可以考虑使用`ls -a`命令。

``` bash
ls -a /tmp
```

可以看到与没有`-a`的结果相比，多了一些内容。

如果有兴趣的同学，可以试一下`ll`命令，会得到文件系统中更多有用的信息。

### 2.3 文件操作

假设我们都在`~/guide`目录下进行

#### 创建文件

使用 `touch` 命令创建文件

```bash
touch helloword.cpp
```

执行 `ls` 命令, 可以看到刚才新建的文件

```bash
ls
```

#### 复制文件

使用 `cp` 命令复制文件(copy)

```bash
cp helloworld.cpp hiworld.cpp
```

#### 移动文件

使用 `mv` 命令移动文件(move)

```bash
mkdir folder
mv hiworld folder/
```

这时候，你可以下面的命令

```bash
tree
```

<div>
    <img src="https://tsunaou.github.io/linux_guide/images/3.png">
</div>

可以注意到，`hiworld.cpp`被移动到目录`folder`中了。`tree`命令的结果其实也给我们展示了Linux下的文件目录实际上也是一种树结构（相信学过计构（~~被计构折磨过~~）的小伙伴们都知道）。

实际上，`mv`命令的功能不只是移动，它还可以重命名。按照某些命名规范，`helloworld.cpp`这个文件其实是不规范的，因为把单词连起来不利于阅读，我们可以使用`mv`命令对其重命名

```bash
mv helloworld.cpp hello_world.cpp
```

再次运行，会发现`helloworld.cpp`不见了，取而代之的是`hello_world.cpp`。

那么有小伙伴们可能会问了，Linux下命令那么多，我哪里知道`mv`还有这种用法啊（等到大二上的PA会告诉你STFM(~~Search The Fucking Manual~~)）。其实linux下还有个很有用的功能，叫做`man`（manual）

```bash
man mv
```

可以看到如下结果。只要能看到英文，很多时候一些命令的用法就会无师自通，是一个很强的工具。键入`q`即可退出。

<div>
    <img src="https://tsunaou.github.io/linux_guide/images/4.png">
</div>

#### 删除文件

实际上，`mv`和`cp`以及接下来要提到的`rm`命令，不止可以针对文件，也可以针对目录。

删除之前，我们首先复制一下`folder`文件夹

```bash
cp folder folder_bak
```

然后就会发现系统报错QAQ(~~不报点错还真的对不起秃掉的头~~)

```log
cp: -r not specified; omitting directory 'folder'
```

这个报错的意思其实是说，要加上`-r`参数(Recursive)。什么意思呢？查阅手册

```bash
man cp
```

可以看到其实就是递归（~~递归可不止应用在汉诺塔和斐波那契~~）复制的意思。

<div>
    <img src="https://tsunaou.github.io/linux_guide/images/5.png">
</div>

于是输入如下命令，即可成功复制，然后就可以愉快地删除了。

```bash
cp -r folder folder_bak
```

使用 `rm` 命令删除文件, 输入 `y` 后回车确认删除

```bash
rm folder/hiworld.cpp
```

使用`tree`或者`ls`命令，可以看到`rm folder/hiworld.cpp`的确已经被删了。接下来我们大胆些，删除`fold_bak`目录，你可以自己尝试尝试。

#### 编辑文件内容

在这里要介绍一个强大的编辑器，叫*vim*，传说中的**编辑器之神**，与 Emacs, **其他编辑器**三分天下。很多人都经历了『从入门到放弃』的痛苦过程（~~俺也一样~~）。不过这个编辑器之后是会伴随我们的生涯的，网上有很多资料（你们有的那个word Linux相关资料里的[ICS课程的讲义](<https://nju-projectn.github.io/ics-pa-gitbook/ics2019/>)很有用，推荐去看）。这里我只介绍下一些简单的操作（~~毕竟很多人第一次用甚至都不会退出~~）

##### 打开并编辑

```bash
vim hello_world.cpp
```

你会发现什么都做不了，甚至都退出不了，可以摸索下。

按下`i`键，发现窗口左下角出现了`-- INSERT --`，表示进入了插入模式，这时候也就可以编辑了。我们可以写一个C++的hello world。

```c++
#include <iostream>
using namespace std;

int main(){
    cout << "Hello World" << endl;
    return 0;
}
```

如果你是`Tab`键缩进选手，你会发现此时的Tab缩进不是4个空格，这个细节日后可能会让你在windows下移植到linux的代码变得你不认识的样子。同时，如果你试图用Visual Studio编辑，然后放到linux下，可能还会遇到GBK和utf-8编码的问题。所以同学们还是老老实实学习吧（~~或者想办法解决这些问题~~）。

##### 保存并退出

言归正传，写完程序后怎么保存呢？同样是按下`q`，退出插入模式，键入`:x`即可保存并退出。如果没有进行编辑，可以用`:q`退出。若要放弃编辑的内容，可以用`:q!`。

#### 查看文件内容

保存完后，可以使用 cat 命令查看`hello_world.cpp` 文件内容(catenate)

```bash
cat hello_world.cpp
```

<div>
    <img src="https://tsunaou.github.io/linux_guide/images/6.png">
</div>

可以看到hello world的程序编写完毕。

### 2.4 编译并运行

以下内容参考你们的那个word文件的[Linux常用工具及命令](https://blog.csdn.net/sillyxue/article/details/83382909)

当没有了宇宙第一IDE Visual Studio后，没有万能的`ctrl + F5`，可能你甚至不会编译运行你的程序？甚至什么是编译都不知道。首先让我们来走进编译，走进编译器。

#### Gcc：编译器       

linux下程序的执行就是告诉操作系统程序文件在哪个路径下。gcc是一个编译工具，将我们所写的C语言程序编程成为机器可识别的语言程序。

windows下和Linux下的二进制接口不同，程序不能互相运行，因为ABI不同。ABI应用程序二进制接口是一个所有处理二进制的程序（包括编译器、汇编器、链接器和语言运行库支持）都会使用的接口。

#### G++：编译器       

以下内容参考自[g++的基本使用](https://blog.csdn.net/chengqiuming/article/details/88410794)。g++是GNU组织推出的C++编译器。它不但可以用来编译传统的C++程序，也可以用来编译现代C++，比如C++11/14等。

g++的用法和gcc类似，编译C++的时候比gcc更简单，因为它会自动链接到C++标准库，而不像gcc需要手工指定。

g++编译程序的内部过程和gcc一样，也要经过4个阶段：预处理、编译、汇编和链接。

##### 基本语法格式

```bash
g++ [选项] 准备编译的文件 [选项] [目标文件]
```

##### 编译

```bash
g++ hello_world.cpp -o hello
```

可以看到当前目录下有一个`hello`文件，而且颜色是绿色，表示可执行文件。

##### 运行

```bash
 ./hello
```

即可看到屏幕打印出了Hello World

<div>
    <img src="https://tsunaou.github.io/linux_guide/images/7.png">
</div>

实际gcc/g++的使用有更多细节，由于本教程只是一个入门教程，这里不多赘述。

### 2.5 Makefile

有了上面的知识，其实你已经可以在linux下运行你大一写的绝大多数程序了（单文件）。但是这学期的程设实验怎么可能只写一个文件呢（~~也许大佬可以Orz~~）。如果要编译一个复杂的项目，输入太多命令显然很麻烦，因此就有了makefile的诞生。

在makefile 中定义很多程序编译规则，在终端命令行下敲击一个make命令，这时make程序，会跑到当前目录下找寻makefile文件，按照makefile中已经规划好的编译顺序和规则，完成整个项目的编译。

##### 编写makefile

```makefile
目标对象名称：依赖对象名称
【Tab键】 为了生成对象所执行的命令
```

比如我们可以对刚刚的hello world编写一个makefile。

```makefile
main: hello_world.cpp
        g++ hello_world.cpp -o hello
```

##### 运行makefile

保存后，在命令行运行

```bash
make
```

可以看到makefile实际上将刚刚手动的命令又执行了一遍，生成了可执行文件`hello`。

学会使用makefile对于你项目的编译和构建是很有帮助的。

### 2.6 更舒服的写代码方式

Linux下写代码确实是一键让人头秃的事情。在Windows下面有devc++、visual studio这些IDE，写完代码就可以F5直接运行了。但是在Linux中，用无插件的vim直接写代码，然后敲出gcc编译无疑一件是痛苦的事(没有代码补全、必须手动输入空格和回车以维持良好的代码风格、手动写makefile编译等)。但是，微软的vscode横空出现解决了这一难题。

#### 什么是vscode?

vscode是一款跨平台的代码编辑器，windows、linux、macos下都可以安装，并且使用方法类似。vscode提供了丰富的插件，你可以用vscode写几乎所有类型的代码:c/c++、Java、python、markdown、latex等。

#### linux下安装vscode

从微软官网下载对应的Linux系统vscode安装包，在ubuntu中 ，下载完后，就可以用dpkg命令来安装了。(貌似vscode现在不提供32位linux系统的版本了，或许可以从网上下载之前的32位版本安装?)

#### 安装vscode插件

Vscode应用商店中有很多插件。对于写C++代码，首先需要安装C/C++插件。可以安装C/C++ Project Generator或者Easy C++ Project这种类型的插件，它能够帮你自动编写makefile、建立含有src、bin和include文件夹的项目目录，你就可以写完代码后愉快地按下run或者debug就开始运行了。具体的插件安装和配置网上都有很多教程，大家可以主动搜索资料(~~其实是我太懒~~)。

### 2.7 在windows运行Linux系统

如果你的电脑是轻薄本甚至是surface的话，要运行虚拟机也许有点费力，体验也不是很好。这时候，微软又出现了，你可以安装WSL(windows subsystem linux)。WSL提供了在Windows下模拟Linux系统的方式，就写c++代码来说，是基本可以替代虚拟机的。

#### 安装WSL

从Microsoft Store安装需要的ubuntu版本，具体安装步骤可以去知乎或者简书搜索，并不难。

#### vscode连接wsl

vscode提供了Remote-wsl插件，安装了以后，可以连接到wsl,就能进入wsl的文件系统，在和Linux几乎相同的环境中愉快地编写代码了(windows和wsl的插件不是互相通用的，要在wsl中重新安装需要的插件，也不是很麻烦)。



## 3.彩蛋

### 3.1 oh-my-zsh

如果你用了我的服务器的话，你可能会发现我的服务器命令行好像比较好用一些，也比较好看（~~自恋一下~~）。其实是因为我不是用默认的bash，而是用了zsh，同时用了oh-my-zsh进行配置，增加了一些插件和主题。如果你对于ubuntu默认的bash不满意的话，也许可以试试哟。安装的教程如下[oh-my-zsh的安装](https://www.jianshu.com/p/2f1ba0e9dc6b)

### 3.2 我的程设实验Lab2

16级老年人当初的程设实验二是实现一个MUD游戏（~~我知道你们不知道是啥~~）

我放在`/home/njucs/mud_game/161220096`下，你们无聊的话可以把它复制到你们的文件夹里，然后用makefie编译运行下，可以体会一下多个文件的情况下makefile是怎么用的（~~当然不要嘲笑我的代码写得丑QAQ~~）。

不过当初我没有设置退出键，不想玩了可以`ctrl+c`强制退出。

### 3.3 Tips

会想写这个的原因是我在表白墙看到有计科的学弟问转专业的事情，也看到有学弟抱怨作业太多太难了（~~有一说一，确实~~），还有同学在后悔没有去商院的。其实大一下这个阶段遇上疫情，真的是一个艰难的时期，也希望大家有困难可以大胆找老师或者朋辈导师们解决吧，都是过来人。我也打算开一个专题，分享一些学长学姐当初这个时期的感受，以及现在回顾时又是怎么样的心情。不过今天也晚了，有空更新吧。

#### 面对BUG时，怎么办呢？

面对编程中出现的BUG，有一些调试经验的学长建议你不妨这样做。

- 首先你要做的事情不是喊别人来帮你看，而是自己先认真琢磨一下，是不是之前遇到过这个BUG，自己的代码中可能哪边有问题，尝试着打印信息出来看看，缩小BUG范围，尽自己所能调试一下。有很多错误都是自己不小心写错或者情况没有考虑周全导致的问题（段错误，结果不符合预期，死循环，assert中断等）。

- 然后，你发现调了一会没有结果，那就“百度”或“谷歌”，去CSDN，博客园，segmentfault逛逛，将错误信息拿到网上看看是否有人也出现过类似的BUG（90%以上都有的），可能会找到类似的或一模一样的，你看看是不是解决办法。

- 接着，你看了个把小时仍然没有头绪，那就让同学们帮帮忙吧（别不好意思，你的室友和你一样处在编程实验阶段，他可能会给你一些灵感）。

- 最后，以上方案都无效，那么去大胆地请教实验老师或者助教吧~（PA和程设实验都有请教过老师的经历），他们应该会给你最终的解决方案！
  相信你们能让BUG无所遁形，祝学弟学妹们调BUG愉快！

  

  —— By 16级吴德亚

  ​					                                                                                                            

## To Be Continue

