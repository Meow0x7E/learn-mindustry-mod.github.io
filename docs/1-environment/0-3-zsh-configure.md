# Z Shell 配置

使用终端一个好用的 Shell 同样是不可或缺的，一个配置完好的 Shell 可以帮你更加方便的使用终端

## Z Shell 和命令增强工具介绍

> [!NOTE]
> 你只需安装并配置 **Z Shell** 即可。
> 其他的命令增强工具会在配置后被自动处理。
> 如果你不想安装命令增强工具可以选择不安装，配置会自动检查工具是否被安装

::::: tabs
:::: tab zsh

[Zsh](https://www.zsh.org/) 是一款功能强大的 [shell](https://wiki.archlinux.org/title/Command-line_shell)，既可用作交互式 shell，也可用作脚本语言解释器。
它与 POSIX sh 兼容（默认情况下不兼容，只有在发出 `emulate sh` 命令时才兼容），
同时还具有改进的[Tab 补全](https://zsh.sourceforge.io/Guide/zshguide06.html)和[通配符](https://zsh.sourceforge.io/Doc/Release/Expansion.html)等优势。

[Zsh FAQ](https://zsh.sourceforge.io/FAQ/zshfaq01.html#l4) 提供了更多使用 Zsh 的理由。

::: details 原文（来自[ArchLinux Wiki](https://wiki.archlinux.org/title/Zsh)）

[Zsh](https://www.zsh.org/) is a powerful [shell](https://wiki.archlinux.org/title/Command-line_shell) that operates as both an interactive shell and as a scripting language interpreter.
While being compatible with the POSIX sh (not by default, only if issuing emulate sh),
it offers advantages such as improved [tab completion](https://zsh.sourceforge.io/Guide/zshguide06.html) and [globbing](https://zsh.sourceforge.io/Doc/Release/Expansion.html).

The [Zsh FAQ](https://zsh.sourceforge.io/FAQ/zshfaq01.html#l4) offers more reasons to use Zsh.

:::
::::

:::: tab eza

<GitHubCard repo="eza-community/eza"/>

[eza](https://github.com/eza-community/eza) 是 Unix 和 Linux 操作系统自带的著名文件列表命令行程序 **ls** 的现代替代程序，它赋予了 ls 更多的功能和更好的默认设置。
它使用颜色来区分文件类型和元数据。
它了解符号链接、扩展属性和 Git。
而且它**小巧**、**快速**，只有**一个二进制文件**。

通过故意做出一些不同的决定，eza 试图成为一个功能更强大、更友好的 ls 版本。

::: details 原文

**eza** is a modern alternative for the venerable file-listing command-line program `ls` that ships with Unix and Linux operating systems, giving it more features and better defaults.
It uses colours to distinguish file types and metadata.
It knows about symlinks, extended attributes, and Git.
And it’s **small**, **fast**, and just **one single binary**.

By deliberately making some decisions differently, eza attempts to be a more featureful, more user-friendly version of `ls`.

:::
::::

:::: tab zoxide

<GitHubCard repo="ajeetdsouza/zoxide"/>

zoxide 是一个**更智能的 cd 命令**，其灵感来自 z 和 autojump。

它能记住你最常用的目录，因此你只需敲几下键盘就能“跳转”到它们。

zoxide 适用于所有主流 shell。

::: details 原文

zoxide is a **smarter cd command**, inspired by z and autojump.

It remembers which directories you use most frequently, so you can "jump" to
them in just a few keystrokes.<br />
zoxide works on all major shells.

:::
::::

:::: tab fzf

<GitHubCard repo="junegunn/fzf"/>

fzf 是一款通用的命令行模糊查找器。

它是一个交互式过滤程序，可过滤文件、命令历史、进程、主机名、书签、git 提交等任何类型的列表。
它采用 “fuzzy” 匹配算法，因此你可以快速输入带有省略字符的模式，但仍能得到你想要的结果

::: details 原文

fzf is a general-purpose command-line fuzzy finder.

It's an interactive filter program for any kind of list; files, command
history, processes, hostnames, bookmarks, git commits, etc. It implements
a "fuzzy" matching algorithm, so you can quickly type in patterns with omitted
characters and still get the results you want.

:::
::::
:::::

## zinit 插件加载器与插件介绍

:::::: details 介绍
::::: tabs
:::: tab zinit

<GitHubCard repo="zdharma-continuum/zinit"/>

Zinit 是一款灵活快速的 Zshell 插件管理器，能让你从 GitHub 和其他网站安装各种插件。它的特性包括：

1. 目前，Zinit 是唯一提供 Turbo 模式的一个插件管理系统。
   Turbo模式可让 Shell 的启动速度提升 **50-80%**（也就是说，Shell 可以快到 **5 倍** ！）。
   你可以在[这里](https://github.com/zdharma-continuum/pm-perf-test)查看它与其他受欢迎的插件管理系统相比的速度对比。

2. 插件管理器会报告插件加载时的状态，描述出每个插件设置了哪些别名、函数、绑定键（bindkeys）、Zle 组件（如 Zle 键盘扩展程序 widgets）、zstyles、补全项、变量、`PATH` 和 `FPATH` 的内容。
   这让用户能够迅速熟悉一个新插件，并且提供了丰富易于理解的信息，这些信息在各种场合下都可能有用。

3. 支持卸载插件，可以列出、安装、卸载和选择性启用或禁用插件的补全项的功能。

4. 插件管理器支持从 Oh My Zsh 或 Prezto 加载插件和库。尽管实现方式不基于特定框架，并且不会在插件管理系统中增加这样的代码（更多内容可参阅 Wiki，见[简介](https://zdharma-continuum.github.io/zinit/wiki/INTRODUCTION/#oh_my_zsh_prezto)）

5. 系统并不使用 `$FPATH` 来加载插件。多重插件的加载不会使 `$FPATH` 中充斥相同的条目（例如，10个、15个或更多）。代码免疫 `KSH_ARRAYS` 和其他通常会引起兼容性问题的功能选项。

6. Zinit 支持一种特殊类型的插件“包”，能够把用户从编写长而复杂的命令中解放出来。
   你可以在这里找到 [Zinit 包管理器](https://github.com/zdharma-continuum/zinit-packages) 里不断扩展且完整的包列表，以及在[Wiki 页面](https://zdharma-continuum.github.io/zinit/wiki/Zinit-Packages/) 找到关于这一功能的文章。

7. 此外，Zinit 还提供了一种特殊类型的功能插件称为“附录”或“annexes”，它们具有扩展插件管理器的能力。
   这些附加组件可以添加新命令、URL 预处理器（例如 [zinit-annex-readurl](https://github.com/zdharma-continuum/zinit-annex-readurl) 附件）、安装后和更新后的钩子等。
   更多关于 Zinit 扩展功能的信息可参考 [zdharma-continuum](https://github.com/zdharma-continuum) 组织里的完整列表，以及在 [Wiki 文章](https://zdharma-continuum.github.io/zinit/wiki/Annexes/) 中了解如何创建你的附件。

::: details 原文

Zinit is a flexible and fast Zshell plugin manager that will allow you to install everything from GitHub and other
sites. Its characteristics are:

1. Zinit is currently the only plugin manager that provides Turbo mode, which yields **50-80% faster Zsh startup**
   (i.e., the shell will start up to **5** times faster!). Check out a speed comparison with other popular plugin
   managers [here](https://github.com/zdharma-continuum/pm-perf-test).

2. The plugin manager gives **reports** from plugin loadings describing what **aliases**, functions, **bindkeys**, Zle
   widgets, zstyles, **completions**, variables, `PATH` and `FPATH` elements a plugin has set up. This allows one to
   quickly familiarize oneself with a new plugin and provides rich and easy-to-digest information which might be helpful
   on various occasions.

3. Supported is the unloading of plugin and ability to list, (un)install and **selectively disable**, **enable**
   plugin's completions.

4. The plugin manager supports loading plugins and libraries from Oh My Zsh or Prezto. However, the implementation isn't
   framework-specific and doesn't bloat the plugin manager with such code (more on this topic can be found on the Wiki,
   in the [Introduction](https://zdharma-continuum.github.io/zinit/wiki/INTRODUCTION/#oh_my_zsh_prezto)).

5. The system does not use `$FPATH`, loading multiple plugins doesn't clutter `$FPATH` with the same number of entries
   (e.g. `10`, `15` or more). Code is immune to `KSH_ARRAYS` and other options typically causing compatibility problems.

6. Zinit supports special, dedicated **packages** that offload the user from providing long and complex commands. See
   the [zinit-packages repository](https://github.com/zdharma-continuum/zinit-packages) for a growing, complete list of
   Zinit packages and the [Wiki page](https://zdharma-continuum.github.io/zinit/wiki/Zinit-Packages/) for an article
   about the feature.

7. Also, specialized Zinit extensions — called **annexes** — have the ability to extend the plugin manager with new
   commands, URL-preprocessors (used by e.g.:[zinit-annex-readurl](https://github.com/zdharma-continuum/zinit-annex-readurl) annex), post-install and post-update
   hooks, and much more. See the [zdharma-continuum](https://github.com/zdharma-continuum) organization for a growing,
   complete list of available Zinit extensions and refer to the
   [Wiki article](https://zdharma-continuum.github.io/zinit/wiki/Annexes/) for an introduction on creating your annex.

:::
::::

:::: tab powerlevel10k

<GitHubCard repo="romkatv/powerlevel10k"/>

Powerlevel10k 是 Zsh 的主题。它强调[速度](https://github.com/romkatv/powerlevel10k?tab=readme-ov-file#uncompromising-performance)，
[灵活性](https://github.com/romkatv/powerlevel10k?tab=readme-ov-file#extremely-customizable)和[开箱即用的体验](https://github.com/romkatv/powerlevel10k?tab=readme-ov-file#configuration-wizard)。

::: details 原文

Powerlevel10k is a theme for Zsh. It emphasizes [speed](https://github.com/romkatv/powerlevel10k?tab=readme-ov-file#uncompromising-performance),
[flexibility](https://github.com/romkatv/powerlevel10k?tab=readme-ov-file#extremely-customizable) and [out-of-the-box experience](https://github.com/romkatv/powerlevel10k?tab=readme-ov-file#configuration-wizard).

:::
::::

:::: tab zsh-syntax-highlighting

<GitHubCard repo="zsh-users/zsh-syntax-highlighting"/>

[Zsh](https://www.zsh.org/) 的类似 [Fish shell](https://fishshell.com/) 的语法高亮

该软件包为 zsh shell 提供语法高亮功能。
它能高亮显示在 zsh 提示符下输入到交互式终端的命令。
交互式终端中键入命令时突出显示这些命令。
这有助于在运行命令前对其进行审查，尤其是在捕捉语法错误时。

一些例子：

高亮前: [![Screenshot #1.1](https://raw.githubusercontent.com/zsh-users/zsh-syntax-highlighting/master/images/before1-smaller.png)](https://raw.githubusercontent.com/zsh-users/zsh-syntax-highlighting/master/images/before1.png)
<br/>
高亮后:&nbsp; [![Screenshot #1.2](https://raw.githubusercontent.com/zsh-users/zsh-syntax-highlighting/master/images/after1-smaller.png)](https://raw.githubusercontent.com/zsh-users/zsh-syntax-highlighting/master/images/after1.png)

高亮前: [![Screenshot #2.1](https://raw.githubusercontent.com/zsh-users/zsh-syntax-highlighting/master/images/before2-smaller.png)](https://raw.githubusercontent.com/zsh-users/zsh-syntax-highlighting/master/images/before2.png)
<br/>
高亮后:&nbsp; [![Screenshot #2.2](https://raw.githubusercontent.com/zsh-users/zsh-syntax-highlighting/master/images/after2-smaller.png)](https://raw.githubusercontent.com/zsh-users/zsh-syntax-highlighting/master/images/after2.png)

高亮前: [![Screenshot #3.1](https://raw.githubusercontent.com/zsh-users/zsh-syntax-highlighting/master/images/before3-smaller.png)](https://raw.githubusercontent.com/zsh-users/zsh-syntax-highlighting/master/images/before3.png)
<br/>
高亮后:&nbsp; [![Screenshot #3.2](https://raw.githubusercontent.com/zsh-users/zsh-syntax-highlighting/master/images/after3-smaller.png)](https://raw.githubusercontent.com/zsh-users/zsh-syntax-highlighting/master/images/after3.png)

高亮前: [![Screenshot #4.1](https://raw.githubusercontent.com/zsh-users/zsh-syntax-highlighting/master/images/before4-smaller.png)](https://raw.githubusercontent.com/zsh-users/zsh-syntax-highlighting/master/images/before4-smaller.png)
<br/>
高亮后:&nbsp; [![Screenshot #4.2](https://raw.githubusercontent.com/zsh-users/zsh-syntax-highlighting/master/images/after4-smaller.png)](https://raw.githubusercontent.com/zsh-users/zsh-syntax-highlighting/master/images/after4-smaller.png)

::: details 原文

**[Fish shell](https://fishshell.com/)-like syntax highlighting for [Zsh](https://www.zsh.org/).**

This package provides syntax highlighting for the shell zsh. It enables
highlighting of commands whilst they are typed at a zsh prompt into an
interactive terminal. This helps in reviewing commands before running
them, particularly in catching syntax errors.

Some examples:

Before: [![Screenshot #1.1](https://raw.githubusercontent.com/zsh-users/zsh-syntax-highlighting/master/images/before1-smaller.png)](https://raw.githubusercontent.com/zsh-users/zsh-syntax-highlighting/master/images/before1.png)
<br/>
After:&nbsp; [![Screenshot #1.2](https://raw.githubusercontent.com/zsh-users/zsh-syntax-highlighting/master/images/after1-smaller.png)](https://raw.githubusercontent.com/zsh-users/zsh-syntax-highlighting/master/images/after1.png)

Before: [![Screenshot #2.1](https://raw.githubusercontent.com/zsh-users/zsh-syntax-highlighting/master/images/before2-smaller.png)](https://raw.githubusercontent.com/zsh-users/zsh-syntax-highlighting/master/images/before2.png)
<br/>
After:&nbsp; [![Screenshot #2.2](https://raw.githubusercontent.com/zsh-users/zsh-syntax-highlighting/master/images/after2-smaller.png)](https://raw.githubusercontent.com/zsh-users/zsh-syntax-highlighting/master/images/after2.png)

Before: [![Screenshot #3.1](https://raw.githubusercontent.com/zsh-users/zsh-syntax-highlighting/master/images/before3-smaller.png)](https://raw.githubusercontent.com/zsh-users/zsh-syntax-highlighting/master/images/before3.png)
<br/>
After:&nbsp; [![Screenshot #3.2](https://raw.githubusercontent.com/zsh-users/zsh-syntax-highlighting/master/images/after3-smaller.png)](https://raw.githubusercontent.com/zsh-users/zsh-syntax-highlighting/master/images/after3.png)

Before: [![Screenshot #4.1](https://raw.githubusercontent.com/zsh-users/zsh-syntax-highlighting/master/images/before4-smaller.png)](https://raw.githubusercontent.com/zsh-users/zsh-syntax-highlighting/master/images/before4-smaller.png)
<br/>
After:&nbsp; [![Screenshot #4.2](https://raw.githubusercontent.com/zsh-users/zsh-syntax-highlighting/master/images/after4-smaller.png)](https://raw.githubusercontent.com/zsh-users/zsh-syntax-highlighting/master/images/after4-smaller.png)

:::
::::

:::: tab fzf-tab
<GitHubCard repo="Aloxaf/fzf-tab"/>

用 fzf 代替 zsh 的默认补全选择菜单！

::: details 原文

Replace zsh's default completion selection menu with fzf!

:::
::::

:::: tab zsh-autosuggestions

<GitHubCard repo="zsh-users/zsh-autosuggestions"/>

_用于 zsh 的类似 [Fish](http://fishshell.com/) 的快速/不起眼自动建议_

它可以根据历史记录和补全情况，在你输入命令时提出建议。

::: details 原文

_[Fish](http://fishshell.com/)-like fast/unobtrusive autosuggestions for zsh._

It suggests commands as you type based on history and completions.

:::
::::

:::: tab zsh-completions

<GitHubCard repo="zsh-completions"/>

**[Zsh](https://www.zsh.org/) 的附加补全定义。**

_本项目旨在收集/开发 Zsh 中尚未提供的新补全脚本。当脚本足够稳定时，可以将其贡献给 Zsh 项目。_

::: details 原文

**Additional completion definitions for [Zsh](https://www.zsh.org/).**

_This projects aims at gathering/developing new completion scripts that are not available in Zsh yet. The scripts may be contributed to the Zsh project when stable enough._

:::

::::
:::::
::::::

## 开始安装 Z Shell 和命令增强工具

### 安装Z Shell、配置所需的前置依赖和命令增强工具

```shell
pkg install -y zsh eza zoxide fzf git
```

### 配置 Z Shell 和 zinit 插件，以及命令增强工具

#### 克隆配置仓库并创建 `zshrc.sh` 的软链接到 `home` 目录

```shell
git clone --branch=basic-configure https://github.com/Meow0x7E/config-zsh.git "${HOME}/.config/zsh"
ln -sv "${HOME}/.config/zsh/zshrc.sh" "${HOME}/.zshrc"
```

你可以在 `${HOME}/.config/zsh` 查看里面的 `sh` 文件，根据注释自行添加或修改配置

#### 更改默认 Shell

::: code-group

```shell [Termux 或 ZeroTermux]
chsh -s zsh
```

```shell [Linux]
chsh -s "$(which -p zsh)"
```

:::

#### 最后步骤

重启终端，并等待 zinit 配置完成。然后根据需要自定义 powerlevel10k 的主题即可
