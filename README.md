- 👋 Hi, I’m @Hsiao-YangWu
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
Hsiao-YangWu/Hsiao-YangWu is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
安装brew：

git clone git://mirrors.ustc.edu.cn/homebrew-core.git//usr/local/Homebrew/Library/Taps/homebrew/homebrew-core --depth=1
（注意：如果有/usr/local/Homebrew/Library/Taps/homebrew/homebrew-core目录，可以不执行，也可以，直接把这个目录删掉，再执行）

安装brew cask：

git clone git://mirrors.ustc.edu.cn/homebrew-cask.git//usr/local/Homebrew/Library/Taps/homebrew/homebrew-cask --depth=1
（注意：如果有/usr/local/Homebrew/Library/Taps/homebrew/homebrew-cask目录，可以不执行，也可以，直接把这个目录删掉，再执行）

替换成国内源：

cd "$(brew --repo)"
git remote set-url origin https://mirrors.ustc.edu.cn/brew.git
cd "$(brew --repo)/Library/Taps/homebrew/homebrew-core"
git remote set-url origin https://mirrors.ustc.edu.cn/homebrew-core.git
cd "$(brew --repo)/Library/Taps/homebrew/homebrew-cask"
git remote set-url origin https://mirrors.ustc.edu.cn/homebrew-cask.git
1、Homebrew是什么？

引用官方的一句话：Homebrew是Mac OS 不可或缺的套件管理器。

Homebrew是一款Mac OS平台下的软件包管理工具，拥有安装、卸载、更新、查看、搜索等很多实用的功能。简单的一条指令，就可以实现包管理，而不用你关心各种依赖和文件路径的情况，十分方便快捷。

2、Homebrew的安装方法

官网给出的安装方法：将以下命令粘贴到终端

/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
但这种方法并不适用国内的Mac用户，因为网络资源的原因，电脑下载是龟速，实在是无法忍受，不信你自己试试就知道了。

解决下载慢有两个办法：

一是替换镜像源，将下载资源改为国内镜像资源即可（推荐）

二是科学上网，通过全局代理来进行安装，也是解决网络问题的一种方法（不推荐，不爱喝茶）

下面来说一下，怎样替换镜像源：

步骤一： 获取install文件：将以下命令粘贴到终端 + 回车

curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install >> brew_install


步骤二：更改文件中的链接资源，将原有的链接资源替换成清华大学的镜像资源

把这两句用#注释掉

BREW_REPO = “https://github.com/Homebrew/brew“.freeze
CORE_TAP_REPO = “https://github.com/Homebrew/homebrew-core“.freeze

修改为这两句

BREW_REPO = "git://mirrors.ustc.edu.cn/brew.git".freeze
CORE_TAP_REPO = "git://mirrors.ustc.edu.cn/homebrew-core.git".freeze

步骤三：安装，运行修改了的brew_install，然后是漫长的等待

/usr/bin/ruby ~/brew_install
执行之后你会看到如下界面：


出现这个因为源不通，代码无法下载到本地，解决方法是更换成国内镜像源，执行如下命令，更换到中科院的镜像：

git clone git://mirrors.ustc.edu.cn/homebrew-core.git//usr/local/Homebrew/Library/Taps/homebrew/homebrew-core --depth=1

然后把Homebrew-core的镜像地址也设置为中科院的国内镜像

cd "$(brew --repo)"
git remote set-url origin https://mirrors.ustc.edu.cn/brew.git
cd "$(brew --repo)/Library/Taps/homebrew/homebrew-core"
git remote set-url origin https://mirrors.ustc.edu.cn/homebrew-core.git

执行更新brew命令：

brew update

接着执行brew检测命令：

brew doctor


如上图出现警告是正常情况，因为我们更改了镜像源。到目前为止，海外用户或者已经设置系统全局代理的用户就可以使用brew安装你所需要的软件了。国内用户咱们继续操作，不然龟速下载搞得我想摔电脑！

让我们把默认源替换为国内USTC源：

(1) 替换核心软件仓库：

cd "$(brew --repo)/Library/Taps/homebrew/homebrew-core"
git remote set-url origin https://mirrors.ustc.edu.cn/homebrew-core.git
(2) 替换cask软件仓库：

cd "$(brew --repo)"/Library/Taps/caskroom/homebrew-cask
git remote set-url origin https://mirrors.ustc.edu.cn/homebrew-cask.git
(3) 替换Bottle源：

bash用户（shell用户）：

echo 'export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.ustc.edu.cn/homebrew-bottles' >> ~/.bash_profile
source ~/.bash_profile
zsh用户：

echo 'export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.ustc.edu.cn/homebrew-bottles' >> ~/.zshrc
source ~/.zshrc
Homebrew基本用法：

假设需要安装的软件是 wget


操作命令更新 Homebrewbrew update更新所有安装过的软件包brew upgrade更新指定的软件包brew upgrade wget查找软件包brew search wget安装软件包brew install wget卸载软件包brew remove wget列出已安装的软件包brew list查看软件包信息brew info wget列出软件包的依赖关系brew deps wget列出可以更新的软件包brew outdated

卸载方法：

/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/uninstall)"

参考：

Homebrew 中文主页

https://brew.sh/index_zh-cn.html


Homebrew Bottles 源使用帮助

http://mirrors.ustc.edu.cn/help/homebrew-bottles.html


Homebrew Cask 源使用帮助

http://mirrors.ustc.edu.cn/help/homebrew-cask.git.html


Homebrew Core 源使用帮助

http://mirrors.ustc.edu.cn/help/homebrew-core.git.html

