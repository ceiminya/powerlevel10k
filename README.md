# Powerlevel10k(中文说明)
[![Gitter￼](https://badges.gitter.im/powerlevel10k/community.svg)](
  https://gitter.im/powerlevel10k/community?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge)

Powerlevel10k是一个为Zsh设计的主题。它强调 [速度](#极致性能),[灵活性](#高度可定制) 和 [开箱即用的体验](#配置向导)。

![Powerlevel10k](
  https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/prompt-styles-high-contrast.png)

- [开始使用](#开始使用)
- [特性](#特性)
- [安装](#安装)
- [配置](#配置)
- [字体](#字体)
- [在Docker中尝试](#在docker中尝试)
- [许可证](#许可证)
- [常见问题解答](#常见问题解答)
- [故障排除](#故障排除)

## 开始使用

1. [安装推荐字体](#为powerlevel10k定制的meslo-nerd-font)。 * 可选但强烈推荐。*
1. [安装 Powerlevel10k](#安装) 本身。
1. 使用 `exec zsh` 重新启动Zsh。
1. 如果配置向导没有自动启动，请输入 `p10k configure` 。

## 特性

- [配置向导](#配置向导)
- [极致性能](#极致性能)
- [对于Powerlevel9k的兼容性](#对于powerlevel9k的兼容性)
- [纯粹兼容性](#纯粹兼容性)
- [即时提示](#即时提示)
- [命令行显示信息优化](#命令行显示信息优化)
- [瞬态提示](#瞬态提示)
- [当前工作目录](#当前工作目录)
- [高度可定制](#高度可定制)
- [内置命令行提示段](#内置命令行提示段)
- [可扩展性](#可扩展性)

### 配置向导

输入 `p10k configure` 以从终端直接访问内置的配置向导.

<details>
  <summary>屏幕截图</summary>

  ![Powerlevel10k Configuration Wizard](
    https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/configuration-wizard.gif)
</details>

除 [Pure](#纯粹兼容性) 之外的所有样式都在功能上是一样的。 它们显示的是相同的信息，只是呈现方式不同。

配置向导会根据您的偏好在 `~/.p10k.zsh` 中创建配置文件。 可以通过编辑此文件来进行其他提示自定义。它有许多注释来帮助您浏览配置选项。

*提示*: 在运行 `p10k configure` 之前安装推荐的[字体](#为powerlevel10k定制的meslo-nerd-font)，以解锁所有提示样式。

*常见问题解答:*

- [在配置向导中哪种提示样式最好？](#在配置向导中哪种提示样式最好)
- [Git状态中不同符号的含义是什么？](#git状态中不同符号的含义是什么)
- [如何更改提示颜色？](#如何更改提示颜色)

*故障排除*:

- [配置向导中缺少一些提示样式](#配置向导中缺少一些提示样式)。
- [提示中标出的问号](#提示中标出的问号)。
- [ 图标、字符或powerline符号无法呈现](#图标字符或powerline符号无法呈现)。
- [powerline符号周围的Sub-pixel渲染不完美](#powerline符号周围的sub-pixel渲染不完美)。
- [使用Rainbow样式时，提示中的目录难以看清](#使用rainbow样式时提示中的目录难以看清)。

### 极致性能

当您按 *回车键*，下一个提示立即出现。使用Powerlevel10k时，没有提示延迟。
如果在Raspberry Pi上安装Cygwin， `cd` 到Linux Git存储库中并激活足够多的提示段来填满屏幕两侧的四行提示...
等等，这只是疯狂的，没有人会这样做。也许也是不可能的。但重点是，无论您做什么，Powerlevel10k提示都是迅速的！

<details>
  <summary>屏幕截图</summary>

  ![Powerlevel10k Performance](
    https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/performance.gif)
</details>

注意每个命令的效果是如何立即反映在下一个提示上的。

| 命令                       | 提示指示符 | 含义                                                               |
|-------------------------------|:----------------:|----------------------------------------------------------------------:|
| `timew start hack linux`      | `⌚ hack linux`  | 在 [timewarrior](https://timewarrior.net/)中启用时间跟踪      |
| `touch x y`                   | `?2`             | Git存储库中有2个未跟踪的文件                                     |
| `rm COPYING`                  | `!1`             | Git存储库中有1个未暂存的变更                                     |
| `echo 3.7.3 >.python-version` | `🐍 3.7.3`       | 当前[pyenv](https://github.com/pyenv/pyenv)中的python版本 |

其他能够显示相同信息的Zsh主题要么会产生提示延迟，要么会打印不反映当前系统状态的提示，然后稍后再刷新。使用Powerlevel10k，您可以获得快速提示 *和* 最新信息。

*常见问题解答*: [真的很快吗？](#真的很快吗)

### 对于Powerlevel9k的兼容性

Powerlevel10k兼容所有[Powerlevel9k](https://github.com/Powerlevel9k/powerlevel9k)配置参数。

<details>
  <summary>屏幕截图</summary>

  ![Powerlevel10k Compatibility with 9k](
    https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/9k-compatibility.gif)
</details>

从Powerlevel9k[迁移](#安装) 到Powerlevel10k是一个直截了当的过程。 所有 `POWERLEVEL9K` 配置参数仍然有效。 提示看起来和以前差不多
([几乎一样](#对于给定的相同配置powerlevel10k是否始终渲染与powerlevel9k完全相同的提示))但速度会 [快得多](#极致性能) ([肯定](#真的很快吗))。

*常见问题解答*:

- [如何迁移我正在Oh-My-Zsh上使用的Powerlevel9k](#如何迁移我正在oh-my-zsh上使用的powerlevel9k)
- [对于给定的相同配置，Powerlevel10k是否始终渲染与Powerlevel9k完全相同的提示？](#对于给定的相同配置powerlevel10k是否始终渲染与powerlevel9k完全相同的提示)
- [Powerlevel9k和Powerlevel10k之间的关系是什么？](#powerlevel9k和powerlevel10k之间的关系是什么)

### 纯粹兼容性

Powerlevel10k 可以生成与 [Pure](https://github.com/sindresorhus/pure)相同的提示。 输入
`p10k configure` 并选择 *Pure* 样式。

<details>
  <summary>屏幕截图</summary>

  ![Powerlevel10k Pure Style](
    https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/pure-style.gif)
</details>

使用Pure样式时，仍然可以使用Powerlevel10k的 [瞬态提示](#瞬态提示) 或[即时提示](#即时提示) 功能。

要自定义提示，请编辑 `~/.p10k.zsh`。Powerlevel10k不识别Pure配置参数，因此您需要使用 `POWERLEVEL9K_COMMAND_EXECUTION_TIME_THRESHOLD=3` 
代替`PURE_CMD_MAX_EXEC_TIME=3`等。所有相关参数都在 `~/.p10k.zsh`中。此文件有许多注释，可帮助您浏览它。

*常见问题解答:* [在配置向导中哪种提示样式最好？](
  #在配置向导中哪种提示样式最好)

### <a name='即时提示'></a>即时提示

如果您的 `~/.zshrc` 加载了许多插件，或者只加载了几个慢插件
(例如 [pyenv](https://github.com/pyenv/pyenv) 或 [nvm](https://github.com/nvm-sh/nvm))，您可能已经注意到Zsh启动较慢。

<details>
  <summary>屏幕截图</summary>

  ![Powerlevel10k No Instant Prompt](
    https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/no-instant-prompt.gif)
</details>

Powerlevel10k可以消除Zsh启动延迟， **即使它不是由主题造成的**。

<details>
  <summary>屏幕截图</summary>

  ![Powerlevel10k Instant Prompt](
    https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/instant-prompt.gif)
</details>

这个功能称为 *即时提示*。 您需要通过 `p10k configure` 或 [手动](#如何配置即时提示)去启用它。 它正如其名所示——在Zsh启动时立即打印提示，让您在插件仍在加载时开始输入。

其他主题会 *增加* Zsh启动延迟——有些很多，有些只是很少。Powerlevel10k会彻底*消除* 它。

如果您想了解 *即时提示* 的工作原理，请参阅[zsh-bench中的这一部分](https://github.com/romkatv/zsh-bench#instant-prompt)。

*常见问题解答:* [如何配置即时提示？](#如何配置即时提示)

### 命令行显示信息优化

某些命令的行为取决于全局环境。例如， `kubectl run ...` 在由当前kubernetes上下文定义的集群中运行镜像。 
如果您经常在“prod”和“testing”之间切换上下文，则可能希望在Zsh提示符中显示当前上下文。如果你对AWS，Azure和Google Cloud凭证也采用同样的方式，提示符将变得非常拥挤。

输入 *Show On Command*。此功能使提示符段仅在与您当前正在输入的命令相关时出现。

<details>
  <summary>屏幕截图</summary>

  ![Powerlevel10k Show On Command](
    https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/show-on-command.gif)
</details>

`p10k configure` 创建的配置默认为若干提示符段启用了命令行显示信息优化功能。
这是kubernetes上下文的相关参数：

```zsh
#仅在您输入的命令调用kubectl，helm，kubens，kubectx，oc，istioctl，kogito，k9s，helmfile，flux，fluxctl，stern，kubeseal或skaffold时显示提示符段“kubecontext”。
typeset -g POWERLEVEL9K_KUBECONTEXT_SHOW_ON_COMMAND='kubectl|helm|kubens|kubectx|oc|istioctl|kogito|k9s|helmfile|flux|fluxctl|stern|kubeseal|skaffold'
```

要自定义显示不同提示符段的时间，请打开 `~/.p10k.zsh`，搜索 `SHOW_ON_COMMAND` ，然后删除这些参数以无条件显示受影响的段，或者更改它们的值。

### 瞬态提示

通过 `p10k configure`启用了 *瞬态提示* 之后, 将在接受命令行时精简所有提示符。

<details>
  <summary>屏幕截图</summary>

  ![Powerlevel10k Transient Prompt](
    https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/transient-prompt.gif)
</details>

瞬态提示符使复制粘贴终端滚动回的命令系列变得更加容易。

*提示*: 如果启用瞬态提示符，请利用双行提示符。您将获得额外空间输入命令的好处，而不会有通常的减少滚动回密度的缺点。稀疏提示（在提示符之前有一个空行）也与瞬态提示符很好地配合使用。

### 当前工作目录

当前工作目录可能是最重要的提示符段。 Powerlevel10k花了很大的努力来突出其重要部分，并在水平空间紧张时尽可能减少其丢失的信息。

<details>
  <summary>屏幕截图</summary>

  ![Powerlevel10k Directory Truncation](
    https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/directory-truncation.gif)
</details>

当完整的目录不适合显示时，最左边的段将被截断到最短的唯一前缀。在屏幕录制中， `~/work` 变成了 `~/wo`。它不能被截断到 `~/w` ，因为它是有歧义的（当会话记录时有 `~/wireguard` ）。
接下来的一段 -- `projects` -- 变成了 `p` ，因为 `~/work/`中没有任何以 `p` 开头的东西。

目录段以三种颜色之一显示：

- 截断的段是暗淡的。
- 重要的段是明亮的，不会被截断。这些包括第一个和最后一个段，Git存储库的根目录等。
- 正常段（不会被截断但会）使用既不暗淡也不明亮的颜色。

*提示*: 如果复制粘贴截断的目录并按 *TAB*键，它将完成为原始目录。

*故障排除*: [使用Rainbow样式时，提示中的目录难以看清。](#使用rainbow样式时提示中的目录难以看清)

### 高度可定制

Powerlevel10k 可以配置得看起来像Zsh主题中的其他主题。

<details>
  <summary>屏幕截图</summary>

  ![Powerlevel10k Other Theme Emulation](
    https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/other-theme-emulation.gif)
</details>

[Pure](#纯粹兼容性), [Powerlevel9k](#对于powerlevel9k的兼容性) 和 [robbyrussell](
  #如何使-powerlevel10k-看起来像-robbyrussell-oh-my-zsh-主题) 的内置仿真方法。
要仿真其他主题的外观，则需要编写合适的配置文件。进行此操作的最佳方法是运行 `p10k configure`，选择与您的目标最接近的样式，然后编辑 `~/.p10k.zsh`。

Powerlevel10k的外观可以从简约：

![Powerlevel10k Spartan Style](
  https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/spartan-style.png)

变到 ~~荒谬的~~ 奢华:

![Powerlevel10k Extravagant Style](
  https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/extravagant-style.png)

### 内置命令行提示段

Powerlevel10k 附带数十个内置高质量段。运行 `p10k configure` 并选择除 [Pure](#纯粹兼容性)之外的任何样式时，其中许多提示段将默认启用，
而其他提示段可以通过打开 `~/.p10k.zsh` 并取消注释来手动启用。您可以启用任意数量的段。它不会使您的提示符或Zsh启动速度变慢。

| 提示段 | 意思 |
|--------:|---------|
| `anaconda` | [conda](https://conda.io/) 的虚拟环境 |
| `asdf` | [asdf](https://github.com/asdf-vm/asdf) asdf工具版本 |
| `aws` | [aws 配置文件](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-profiles.html) |
| `aws_eb_env` | [aws elastic beanstalk](https://aws.amazon.com/elasticbeanstalk/) 环境 |
| `azure` | [azure](https://docs.microsoft.com/en-us/cli/azure) 账户名称 |
| `background_jobs` | 存在后台作业 |
| `battery` | 内部电池状态和充电级别 (是的，电池 *确实* 是被包括的) |
| `command_execution_time` | 上一条命令的持续时间（真实时间） |
| `context` | 用户@主机名 |
| `cpu_arch` | CPU架构 |
| `dir` | 当前工作目录 |
| `direnv` | [direnv](https://direnv.net/) 状态 |
| `disk_usage` | 磁盘使用情况 |
| `dotnet_version` | [dotnet](https://dotnet.microsoft.com) 版本 |
| `fvm` | [fvm](https://github.com/leoafarias/fvm) 环境中的flutter |
| `gcloud` | [google cloud](https://cloud.google.com/) cli 账户和项目 |
| `goenv` | [goenv](https://github.com/syndbg/goenv) 环境中的go |
| `google_app_cred` | [google应用凭据](https://cloud.google.com/docs/authentication/production) |
| `go_version` | [go](https://golang.org) 版本 |
| `haskell_stack` | [stack](https://haskellstack.org/) 中的haskell版本 |
| `ip` | 指定网络接口的IP地址和带宽使用情况 |
| `java_version` | [java](https://www.java.com/) 版本 |
| `jenv` | [jenv](https://github.com/jenv/jenv) 环境中的java |
| `kubecontext` | 当前 [kubernetes](https://kubernetes.io/) 上下文 |
| `laravel_version` | [laravel php 框架](https://laravel.com/) 版本 |
| `load` | CPU 负载 |
| `luaenv` | [luaenv](https://github.com/cehoffman/luaenv) 环境中的lua |
| `midnight_commander` | [midnight commander](https://midnight-commander.org/) shell |
| `nix_shell` | [nix shell](https://nixos.org/nixos/nix-pills/developing-with-nix-shell.html) 指示器 |
| `nnn` | [nnn](https://github.com/jarun/nnn) shell |
| `lf` | [lf](https://github.com/gokcehan/lf) shell |
| `nodeenv` | node.js环境中的[nodeenv](https://github.com/ekalinin/nodeenv) |
| `nodenv` | node.js环境中的 [nodenv](https://github.com/nodenv/nodenv) |
| `node_version` | [node.js](https://nodejs.org/) 版本 |
| `nordvpn` | [nordvpn](https://nordvpn.com/) 连接状态 |
| `nvm` | [nvm](https://github.com/nvm-sh/nvm) 环境中的node.js |
| `os_icon` | 您的操作系统徽标（macOS的apple，debian的旋涡等） |
| `package` | [package.json](https://docs.npmjs.com/files/package.json) 中的`name@version` |
| `perlbrew` | [perlbrew](https://github.com/gugod/App-perlbrew) 中的perl版本 |
| `phpenv` | [phpenv](https://github.com/phpenv/phpenv) 环境中的php |
| `php_version` | [php](https://www.php.net/) 版本 |
| `plenv` | [plenv](https://github.com/tokuhirom/plenv) 环境中的perl |
| `prompt_char` | 多功能提示符号; 根据vi模式而改变：插入，命令，视觉和替换模式分别为: `❯`, `❮`, `V`, `▶` ; 在错误时变红 |
| `proxy` | 系统范围内的http / https / ftp代理 |
| `public_ip` | 公共IP地址 |
| `pyenv` | [pyenv](https://github.com/pyenv/pyenv) 环境中的python |
| `ram` | 可用 RAM |
| `ranger` | [ranger](https://github.com/ranger/ranger) shell |
| `rbenv` | [rbenv](https://github.com/rbenv/rbenv) 环境中的ruby |
| `rust_version` | [rustc](https://www.rust-lang.org) 版本 |
| `rvm` | [rvm](https://rvm.io) 环境中的ruby |
| `scalaenv` | [scalaenv](https://github.com/scalaenv/scalaenv) 中的scala版本 |
| `status` | 上一条命令的退出代码 |
| `swap` | 已使用交换空间 |
| `taskwarrior` | [taskwarrior](https://taskwarrior.org/) 任务数 |
| `terraform` | [terraform](https://www.terraform.io) 工作区 |
| `terraform_version` | [terraform](https://www.terraform.io) 版本 |
| `time` | 当前时间 |
| `timewarrior` | [timewarrior](https://timewarrior.net/) 跟踪状态 |
| `todo` | [todo](https://github.com/todotxt/todo.txt-cli) 事项 |
| `toolbox` | [toolbox](https://github.com/containers/toolbox) 名称 |
| `vcs` | Git 存储库状态 |
| `vim_shell` | [vim](https://www.vim.org/) shell (`:sh`) |
| `virtualenv` | [venv](https://docs.python.org/3/library/venv.html) 环境中的python |
| `vi_mode` | vi 模式（如果已启用prompt_char，则不需要此内容） |
| `vpn_ip` | 虚拟专用网络指示器 |
| `wifi` | WiFi速度 |
| `xplr` | [xplr](https://github.com/sayanarijit/xplr) shell |

### 可扩展性

如果没有提示符段实现您所需的功能，请实现自己的提示符段。Powerlevel10k提供了公共API，用于定义与内置提示符段一样快速和灵活的提示符段。

<details>
  <summary>屏幕截图</summary>

  ![Powerlevel10k Custom Segment](
    https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/custom-segment.gif)
</details>

在Linux上，可以通过读取 `/sys/class/thermal/thermal_zone0/temp`。获取当前CPU温度。影片演示了如何定义一个提示符段来显示此值。
定义完提示符段后，可以像任何其他提示符段一样使用它。所有标准的定制参数都将默认为您的提示符段工作。

输入 `p10k help segment` 以获取参考。

*提示*: 将您自己的提示符段的名称前缀更改为 `my_` 以避免与未来版本的Powerlevel10k发生冲突。

## 安装

- [Manual(手动)](#manual) 👈 **如果感到困惑或不确定**
- [Oh My Zsh](#oh-my-zsh)
- [Prezto](#prezto)
- [Zim](#zim)
- [Antibody](#antibody)
- [Antidote](#antidote)
- [Antigen](#antigen)
- [Zplug](#zplug)
- [Zgen](#zgen)
- [Zplugin](#zplugin)
- [Zinit](#zinit)
- [Zi](#zi)
- [Zap](#zap)
- [Homebrew](#homebrew)
- [Arch Linux](#arch-linux)
- [Alpine Linux](#arch-linux)
- [Fig](#fig)

### Manual

```zsh
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ~/powerlevel10k
echo 'source ~/powerlevel10k/powerlevel10k.zsh-theme' >>~/.zshrc
```

Users in China can use the official mirror on gitee.com for faster download.<br>
中国用户可以使用 gitee.com 上的官方镜像加速下载.

```zsh
git clone --depth=1 https://gitee.com/romkatv/powerlevel10k.git ~/powerlevel10k
echo 'source ~/powerlevel10k/powerlevel10k.zsh-theme' >>~/.zshrc
```

这是最简单的安装方式，即使您使用插件管理器也可以正常工作。只需确保在插件管理器中禁用当前主题。
有关帮助，请参见[故障排除](#无法使powerlevel10k与我的插件管理器配合使用) 。

### Oh My Zsh

1. 克隆存储库:
    ```zsh
    git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
    ```
    Users in China can use the official mirror on gitee.com for faster download.<br>
    中国用户可以使用 gitee.com 上的官方镜像加速下载.

    ```zsh
    git clone --depth=1 https://gitee.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
    ```
2. 在 `~/.zshrc` 中设置 `ZSH_THEME="powerlevel10k/powerlevel10k"` 。

### Prezto

将 `zstyle :prezto:module:prompt theme powerlevel10k` 添加到 `~/.zpreztorc`。

### Zim

将 `zmodule romkatv/powerlevel10k --use degit` 添加到 `~/.zimrc` ，然后运行 `zimfw install`。

### Antibody

将 `antibody bundle romkatv/powerlevel10k` 添加到 `~/.zshrc`。

### Antidote

将 `romkatv/powerlevel10k` 添加到 `~/.zsh_plugins.txt`。

### Antigen

将 `antigen theme romkatv/powerlevel10k` 添加到 `~/.zshrc` 。确保在这后面还有 `antigen apply` 。

### Zplug

将 `zplug romkatv/powerlevel10k, as:theme, depth:1` 添加到 `~/.zshrc`。

### Zgen

将 `zgen load romkatv/powerlevel10k powerlevel10k` 添加到 `~/.zshrc`。

### Zplugin

将 `zplugin ice depth=1; zplugin light romkatv/powerlevel10k` 添加到 `~/.zshrc`。

使用 `depth=1` 是可选的。 Powerlevel10k 不建议使用其他类型的 ice，也不官方支持其他类型的 ice。

### Zinit

将 `zinit ice depth=1; zinit light romkatv/powerlevel10k` 添加到 `~/.zshrc`。

使用 `depth=1` 是可选的。 Powerlevel10k 不建议使用其他类型的 ice，也不官方支持其他类型的 ice。

### Zi

将 `zi ice depth=1; zi light romkatv/powerlevel10k` 添加到 `~/.zshrc`。

使用 `depth=1` 是可选的。 Powerlevel10k 不建议使用其他类型的 ice，也不官方支持其他类型的 ice。

### Zap

将 `plug "romkatv/powerlevel10k"` 添加到 `~/.zshrc`。

### Homebrew

```zsh
brew install romkatv/powerlevel10k/powerlevel10k
echo "source $(brew --prefix)/opt/powerlevel10k/powerlevel10k.zsh-theme" >>~/.zshrc
```

### Arch Linux

```zsh
yay -S --noconfirm zsh-theme-powerlevel10k-git
echo 'source /usr/share/zsh-theme-powerlevel10k/powerlevel10k.zsh-theme' >>~/.zshrc
```

上面的 [zsh-theme-powerlevel10k-git](https://aur.archlinux.org/packages/zsh-theme-powerlevel10k-git/)是 Powerlevel10k 的官方包。

还有一个名为 [zsh-theme-powerlevel10k](
  https://www.archlinux.org/packages/community/x86_64/zsh-theme-powerlevel10k/) 的社区包。
按过去的反馈来看， [这个包经常会出问题](
  https://github.com/romkatv/powerlevel10k/pull/786)。 **不建议使用。**

### Alpine Linux

```zsh
apk add zsh zsh-theme-powerlevel10k
mkdir -p ~/.local/share/zsh/plugins
ln -s /usr/share/zsh/plugins/powerlevel10k ~/.local/share/zsh/plugins/
```

### Fig

请按照本页面上的说明操作。
[this page](https://fig.io/plugins/other/powerlevel10k).

## 配置

- [对于新用户](#对于新用户)
- [对于Powerlevel9k用户](#对于powerlevel9k用户)

### 对于新用户

在第一次运行时， [配置向导](#配置向导) 会问你几个问题并配置你的提示。如果它没有自动触发，请输入 `p10k configure`。配置向导会根据你的偏好创建 `~/.p10k.zsh` 。
可以通过编辑此文件来进行其他提示自定义。它有许多注释来帮助您导航配置选项。

*常见问题解答*:

- [在配置向导中哪种提示样式最好？](#在配置向导中哪种提示样式最好)
- [Git状态中不同符号的含义是什么？](#git状态中不同符号的含义是什么)
- [如何更改Git状态的格式？](#如何更改git状态的格式)
- [如何将用户名和/或主机名添加到提示中？](#如何将用户名和或主机名添加到提示中)
- [如何更改提示颜色？](#如何更改提示颜色)
- [为什么当我在输入时有些提示段会出现并再次消失？](#为什么当我在输入时有些提示段会出现并再次消失)

*故障排除*:

- [提示中标出的问号](#提示中标出的问号)。
- [ 图标、字符或powerline符号无法呈现](#图标字符或powerline符号无法呈现)。
- [powerline符号周围的Sub-pixel渲染不完美](#powerline符号周围的sub-pixel渲染不完美)。
- [使用Rainbow样式时，提示中的目录难以看清](#使用rainbow样式时提示中的目录难以看清)。

### 对于Powerlevel9k用户

如果之前使用过Powerlevel9k， **do not remove the configuration options**。Powerlevel10k会捕获它们，并为您提供熟悉的提示UI。
参见[对于Powerlevel9k的兼容性](#对于powerlevel9k的兼容性).

*常见问题解答*:

- [如何迁移我正在Oh-My-Zsh上使用的Powerlevel9k](#如何迁移我正在oh-my-zsh上使用的powerlevel9k)
- [Powerlevel9k和Powerlevel10k之间的关系是什么？](#powerlevel9k和powerlevel10k之间的关系是什么)
- [对于给定的相同配置，Powerlevel10k是否始终渲染与Powerlevel9k完全相同的提示？](#对于给定的相同配置powerlevel10k是否始终渲染与powerlevel9k完全相同的提示)

*故障排除*: [与Powerlevel9k相比，提示中的额外或缺少的空格](#与powerlevel9k相比提示中的额外或缺少的空格).

## 字体

Powerlevel10k不需要自定义字体，但如果有的话可以使用它们。它与 [Nerd Fonts](https://github.com/ryanoasis/nerd-fonts),
[Source Code Pro](https://github.com/adobe-fonts/source-code-pro),[Font Awesome](https://fontawesome.com/), 
[Powerline](https://github.com/powerline/fonts),甚至默认系统字体都很好用。仅在使用[Nerd Fonts](https://github.com/ryanoasis/nerd-fonts)时才能使用完整的样式选项。

👇 **推荐字体**: 为Powerlevel10k定制的Meslo Nerd Font. 👇

### <a name='为powerlevel10k定制的meslo-nerd-font'></a><a name='font'></a>为Powerlevel10k定制的Meslo Nerd Font

Bitstream是由Jim Lyles设计的华丽的等宽字体，后来他又为苹果公司自定义了这款字体，又由André Berg进一步自定义，最后由我自定义，使用Nerd Fonts的Ryan L McIntyre最初开发的自定义脚本。
包含Powerlevel10k可能需要的所有字形和符号。在所有主要操作系统的几十个不同终端中进行了战斗测试。

*常见问题解答*: [推荐字体是如何创建的？](#推荐字体是如何创建的)

#### 自动字体安装

如果您使用iTerm2或Termux， `p10k configure` 可以为您安装推荐的字体。在被询问是否安装 *Meslo Nerd Font* 时回答 `Yes` 即可。

如果您使用的是其他终端，请执行手动字体安装。👇

#### 手动字体安装

1. 下载这四个ttf文件:
   - [MesloLGS NF Regular.ttf](
       https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Regular.ttf)
   - [MesloLGS NF Bold.ttf](
       https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Bold.ttf)
   - [MesloLGS NF Italic.ttf](
       https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Italic.ttf)
   - [MesloLGS NF Bold Italic.ttf](
       https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Bold%20Italic.ttf)
1. 双击每个文件，然后点击 "安装"。这将使 `MesloLGS NF` 字体对系统中的所有应用程序均可用。
1. 配置终端使用此字体:
   - **iTerm2**: 键入 `p10k configure` ，在被询问是否安装 *Meslo Nerd Font* 时回答 `Yes` 。
     或者，打开 *iTerm2 → Preferences → Profiles → Text* ，将 *Font* 设置为 `MesloLGS NF`。
   - **Apple Terminal**: 打开 *Terminal → Preferences → Profiles → Text*，点击 *Font* 下的 *Change* ，然后选择 `MesloLGS NF` 系列。
   - **Hyper**: 打开 *Hyper → Edit → Preferences* ，将 `module.exports.config` 下的 `fontFamily` 的值更改为 `MesloLGS NF`。
   - **Visual Studio Code**: 打开 *File → Preferences → Settings* (PC) 或*Code → Preferences → Settings* (Mac), 
     在 *Settings* 选项卡顶部的搜索框中输入 `terminal.integrated.fontFamily` ，并将下方的值设置为 `MesloLGS NF`。请参阅 [此屏幕截图](
       https://raw.githubusercontent.com/romkatv/powerlevel10k-media/389133fb8c9a2347929a23702ce3039aacc46c3d/visual-studio-code-font-settings.jpg)
     了解应该如何看起来，或参阅 [此问题](
       https://github.com/romkatv/powerlevel10k/issues/671) 以获取额外信息。
   - **GNOME Terminal** (Ubuntu默认终端): 打开 *Terminal → Preferences* ，点击 *Profiles* 下的选定的配置文件。在  *Text Appearance* 下选中 *Custom font* ，然后选择
     `MesloLGS NF Regular` 。
   - **Konsole**: 打开 *Settings → Edit Current Profile → Appearance*，点击 *Select Font* ，然后选择 `MesloLGS NF Regular`。
   - **Tilix**: 打开 *Tilix → Preferences* ，点击 *Profiles*下的选定的配置文件。在 *Text Appearance* 下选中 *Custom font* ，然后选择 `MesloLGS NF Regular`。
   - **Windows Console Host** (旧版本): 点击左上角的图标，然后选择 *Properties → Font* ，将 *Font* 设置为 `MesloLGS NF`。
   - **Windows Terminal** by Microsoft (新版本): 打开 *Settings* (<kbd>Ctrl+,</kbd>)，点击 *Profiles* 下的所选配置文件或点击 *Defaults*，点击 *Appearance* ，
     将 *Font face* 设置为 `MesloLGS NF`。
   - **IntelliJ** (和 Jet Brains 的其他 IDEs): 打开 *IDE → Edit → Preferences → Editor → Color Scheme → Console Font*。
     选择 *Use console font instead of the default* ，并将字体名称设置为 `MesloLGS NF`。
   - **Termux**: 输入 `p10k configure` ，在问是否安装 *Meslo Nerd Font* 时回答 `Yes`。
   - **Blink**: 输入 `config`，转到 *Appearance*，点击 *Add a new font*，点击 *Open Gallery*，选择 *MesloLGS NF.css*，点击 *import* ，在主视图中输入 `exit` 重新加载字体。
   - **Terminus**: 打开 *Settings → Appearance* ，将字体设置为 *Font* to `MesloLGS NF`。
   - **Terminator**: 使用右键菜单打开 *Preferences* 。在 *Profiles* 下，选择 *General* 选项卡（应该已被选中），取消选中 *Use the system fixed width font* （如果未选中），
     并选择 `MesloLGS NF Regular`。通过点击 *Close*退出偏好设置对话框。
   - **Guake**: 右键点击打开的终端，然后点击 *Preferences*。在 *Appearance* 选项卡中，取消选中 *Use the system fixed width font* (if not already) （如果未选中），
     并选择 `MesloLGS NF Regular`。通过点击 *Close*退出首选项对话框。
   - **MobaXterm**: 打开 *Settings* → *Configuration* → *Terminal* → (在 *Terminal look and feel*下) 将 *Font* 设置为 `MesloLGS NF`。
   - **Asbrú Connection Manager**: 打开 *Preferences → Local Shell Options → Look and Feel*，启用 *Use these personal options* ，
     并将在 *Terminal UI*下的*Font:* 设置为 `MesloLGS NF Regular`。要更改远程主机连接的字体，请转到 *Preferences → Terminal Options → Look and Feel* ，
		 并将 *Terminal UI*下的*Font:* 设置为 `MesloLGS NF Regular`。
   - **WSLtty**: 在打开的终端上点击右键，然后点击 *Options*。在 *Text* 部分下的 *Font*中，点击 *"Select..."* ，并将字体设置为 `MesloLGS NF Regular`。
   - **Yakuake**: 点击 *≡* → *Manage Profiles* → *New* → *Appearance*。 点击 *Font* 下拉菜单旁边的 *Choose* ，选择 `MesloLGS NF` 并点击 *OK*。
	   点击 *OK* 保存资料。 选择新资料并点击 *Set as Default*。
   - **Alacritty**: 创建或打开 `~/.config/alacritty/alacritty.yml` ，并在其中添加以下部分：
     ```yaml
     font:
       normal:
         family: "MesloLGS NF"
     ```
    - **kitty**: 创建或打开 `~/.config/kitty/kitty.conf` ，并在其中添加以下行：
      ```text
      font_family MesloLGS NF
      ```
      重新启动kitty，关闭所有会话并打开新会话。
   - **puTTY**: 将 *Window* → *Appearance* → *Font* 设置为 `MesloLGS NF`。需要 puTTY版本 >= 0.75。
   - **WezTerm**: 创建或打开 `$HOME/.config/wezterm/wezterm.lua` ，并添加以下内容：
     ```lua
     local wezterm = require 'wezterm';
     return {
         font = wezterm.font("MesloLGS NF"),
     }
     ```
     如果文件已存在，请仅将字体行添加到现有return中。如果第一行尚未存在，还应添加第一行。
   - **urxvt**: 创建或打开 `~/.Xresources` ，并在其中添加以下行：
     ```text
     URxvt.font: xft:MesloLGS NF:size=11
     ```
     您可以根据需要调整字体大小。更改配置后，运行 `xrdb ~/.Xresources` 重新加载它。新配置适用于所有新终端。
   - **xterm**: 创建或打开 `~/.Xresources` ，并在其中添加以下行：
     ```text
     xterm*faceName: MesloLGS NF
     ```
     更改配置后，运行 `xrdb ~/.Xresources` t重新加载它。新配置适用于所有新终端。
   - Crostini (Linux on Chrome OS): 打开chrome-untrusted://terminal/html/nassh_preferences_editor.html，将 *Text font family* 设置为
      `'MesloLGS NF'` （包括引号），并将 *Custom CSS (inline text)* 设置为以下内容：
     ```css
     @font-face {
      font-family: "MesloLGS NF";
      src: url("https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/MesloLGS%20NF%20Regular.ttf");
      font-weight: normal;
      font-style: normal;
     }
     @font-face {
         font-family: "MesloLGS NF";
         src: url("https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/MesloLGS%20NF%20Bold.ttf");
         font-weight: bold;
         font-style: normal;
     }
     @font-face {
         font-family: "MesloLGS NF";
         src: url("https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/MesloLGS%20NF%20Italic.ttf");
         font-weight: normal;
         font-style: italic;
     }
     @font-face {
         font-family: "MesloLGS NF";
         src: url("https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/MesloLGS%20NF%20Bold%20Italic.ttf");
         font-weight: bold;
         font-style: italic;
     }
     ```
     **_警告_**: 如果您打开常规终端首选项，这些设置将被覆盖。
1. 运行 `p10k configure` 以生成新的 `~/.p10k.zsh`。旧配置可能会与新字体不正常工作。

_使用不同的终端并知道如何为其设置字体？通过发送 PR 来扩展列表，分享您的知识！_

## 在Docker中尝试

在 Docker 中尝试 Powerlevel10k。您可以在尝试主题时安全地对文件系统进行任何更改。退出 Zsh 后，将删除该映像。

```zsh
docker run -e TERM -e COLORTERM -e LC_ALL=C.UTF-8 -it --rm alpine sh -uec '
  apk add git zsh nano vim
  git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ~/powerlevel10k
  echo "source ~/powerlevel10k/powerlevel10k.zsh-theme" >>~/.zshrc
  cd ~/powerlevel10k
  exec zsh'
```

*提示*: 在运行 Docker 命令之前，安装 [推荐字体](#为powerlevel10k定制的meslo-nerd-font) ，以获得访问所有提示样式的权限。

*提示*: 在 Docker 中运行 `p10k configure` 以尝试不同的提示样式。

## 许可证

Powerlevel10k发布在[MIT 许可证](https://github.com/romkatv/powerlevel10k/blob/master/LICENSE)下。

## 常见问题解答

- [如何更新Powerlevel10k？](#如何更新powerlevel10k)
- [如何卸载Powerlevel10k？](#如何卸载powerlevel10k)
- [如何在没有Internet连接的机器上安装Powerlevel10k？](#如何在没有internet连接的机器上安装powerlevel10k)
- [在哪里可以寻求帮助并报告错误？](#在哪里可以寻求帮助并报告错误)
- [Powerlevel10k会影响哪些shell和终端的方面？](#powerlevel10k会影响哪些shell和终端的方面)
- [如何迁移我正在Oh-My-Zsh上使用的Powerlevel9k](#如何迁移我正在oh-my-zsh上使用的powerlevel9k)
- [真的很快吗？](#真的很快吗)
- [如何配置即时提示？](#如何配置即时提示)
- [使用即时提示时如何初始化direnv？](#使用即时提示时如何初始化direnv)
- [使用即时提示时如何导出GPG_TTY？](#使用即时提示时如何导出gpg_tty)
- [Git状态中不同符号的含义是什么？](#git状态中不同符号的含义是什么)
- [如何更改Git状态的格式？](#如何更改git状态的格式)
- [为什么`$HOME/.git`中的Git状态不会显示在提示中？](#为什么homegit中的git状态不会显示在提示中)
- [为什么Git状态有时会显示灰色，然后在短时间后变成彩色？](#为什么git状态有时会显示灰色然后在短时间后变成彩色)
- [如何将用户名和/或主机名添加到提示中？](#如何将用户名和或主机名添加到提示中)
- [为什么当我在输入时有些提示段会出现并再次消失？](#为什么当我在输入时有些提示段会出现并再次消失)
- [如何更改提示颜色？](#如何更改提示颜色)
- [为什么Powerlevel10k会产生额外的进程？](#为什么powerlevel10k会产生额外的进程)
- [有哪些配置选项会使Powerlevel10k变慢？](#有哪些配置选项会使powerlevel10k变慢)
- [Powerlevel10k加载起来快吗？](#powerlevel10k加载起来快吗)
- [Powerlevel9k和Powerlevel10k之间的关系是什么？](#powerlevel9k和powerlevel10k之间的关系是什么)
- [对于给定的相同配置，Powerlevel10k是否始终渲染与Powerlevel9k完全相同的提示？](#对于给定的相同配置powerlevel10k是否始终渲染与powerlevel9k完全相同的提示)
- [在配置向导中哪种提示样式最好？](#在配置向导中哪种提示样式最好)
- [如何使 Powerlevel10k 看起来像 robbyrussell Oh My Zsh 主题？](#如何使-powerlevel10k-看起来像-robbyrussell-oh-my-zsh-主题)
- [已完成的命令的提示是否可以显示*那些*命令的错误状态，而不是前面的命令？](#已完成的命令的提示是否可以显示那些命令的错误状态而不是前面的命令)
- [最低支持的 Zsh 版本是多少？](#最低支持的 Zsh 版本是多少)
- [这些截图和动画 gif 是如何创建的？](#这些截图和动画 gif 是如何创建的)
- [推荐字体是如何创建的？](#推荐字体是如何创建的)
- [如何为分发打包 Powerlevel10k？](#如何为分发打包 Powerlevel10k)

### 如何更新Powerlevel10k？

更新Powerlevel10k的命令取决于它的安装方式。

| 安装方式                  | 更新命令                                              |
|-------------------------------|-------------------------------------------------------------|
| [Manual](#manual)             | `git -C ~/powerlevel10k pull`                               |
| [Oh My Zsh](#oh-my-zsh)       | `git -C ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k pull` |
| [Prezto](#prezto)             | `zprezto-update`                                            |
| [Zim](#zim)                   | `zimfw update`                                              |
| [Antigen](#antigen)           | `antigen update`                                            |
| [Antidote](#antidote)         | `antidote update`                                           |
| [Zplug](#zplug)               | `zplug update`                                              |
| [Zgen](#zgen)                 | `zgen update`                                               |
| [Zplugin](#zplugin)           | `zplugin update`                                            |
| [Zinit](#zinit)               | `zinit update`                                              |
| [Zi](#zi)                     | `zi update`                                                 |
| [Zap](#zap)                   | `zap --update`                                              |
| [Homebrew](#homebrew)         | `brew update && brew upgrade`                               |
| [Arch Linux](#arch-linux)     | `yay -S --noconfirm zsh-theme-powerlevel10k-git`            |
| [Alpine Linux](#alpine-linux) | `apk update && apk upgrade`                                 |

**重要**: 在更新Powerlevel10k后重新启动Zsh。 [不要使用 `source ~/.zshrc`](#输入source-zshrc后出现奇怪的事情)。

### 如何卸载Powerlevel10k？

1. 从 `~/.zshrc`中删除所有引用 "p10k" 的内容。你可能在顶部有这个片段：
   ```zsh
   if [[ -r "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh" ]]; then
     source "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh"
   fi
   ```
   在底部有这个：
   ```zsh
   [[ ! -f ~/.p10k.zsh ]] || source ~/.p10k.zsh
   ```
   这些都是 [配置向导](#配置向导)添加的。删除它们。
2. 从 `~/.zshrc`, `~/.zpreztorc` 和 `~/.zimrc` 中删除所有引用 "powerlevel10k" 的内容（这些文件中可能有一些文件不存在 -- 这是正常的）。
   这些引用是在安装Powerlevel10k时由您自己手动添加的。如果需要提醒，请参阅 [安装说明](#安装)。
4. 验证 `~/.zshrc`, `~/.zpreztorc` 和 `~/.zimrc`中 "p10k" 和 "powerlevel10k" 的所有引用都已删除。
   ```zsh
   grep -E 'p10k|powerlevel10k' ~/.zshrc ~/.zpreztorc ~/.zimrc 2>/dev/null
   ```
   如果此命令产生输出，则仍有对 "p10k" 或 "powerlevel10k"的引用。您需要删除它们。
4. 删除Powerlevel10k配置文件。此文件是由[配置向导](#配置向导)创建的，可能包含您自己的手动编辑。
   ```zsh
   rm -f ~/.p10k.zsh
   ```
5. 删除Powerlevel10k源文件。这些文件是在安装Powerlevel10k时下载的。删除它们的命令取决于您选择的安装方法。如果需要提醒，请参阅[安装说明](#安装)。

   | 安装方法                  | 卸载命令                                                |
   |-------------------------------|------------------------------------------------------------------|
   | [Manual](#manual)             | `rm -rf ~/powerlevel10k`                                         |
   | [Oh My Zsh](#oh-my-zsh)       | `rm -rf -- ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k` |
   | [Prezto](#prezto)             | n/a                                                              |
   | [Zim](#zim)                   | `zimfw uninstall`                                                |
   | [Antigen](#antigen)           | `antigen purge romkatv/powerlevel10k`                            |
   | [Antidote](#antidote)         | `antidote purge romkatv/powerlevel10k`                           |
   | [Zplug](#zplug)               | `zplug clean`                                                    |
   | [Zgen](#zgen)                 | `zgen reset`                                                     |
   | [Zplugin](#zplugin)           | `zplugin delete romkatv/powerlevel10k`                           |
   | [Zinit](#zinit)               | `zinit delete romkatv/powerlevel10k`                             |
   | [Zi](#zi)                     | `zi delete romkatv/powerlevel10k`                                |
   | [Zap](#zap)                   | `zsh -ic 'zap --clean'`                                          |
   | [Homebrew](#homebrew)         | `brew uninstall powerlevel10k; brew untap romkatv/powerlevel10k` |
   | [Arch Linux](#arch-linux)     | `yay -R --noconfirm zsh-theme-powerlevel10k-git`                 |
   | [Alpine Linux](#alpine-linux) | `apk del zsh-theme-powerlevel10k`                                |
6. 重新启动Zsh。 [不要使用`source ~/.zshrc`](#输入source-zshrc后出现奇怪的事情)。
7. 请删除 Powerlevel10k 缓存文件。
   ```zsh
   rm -rf -- "${XDG_CACHE_HOME:-$HOME/.cache}"/p10k-*(N) "${XDG_CACHE_HOME:-$HOME/.cache}"/gitstatus
   ```

### 如何在没有Internet连接的机器上安装Powerlevel10k？

1. 在没有 Internet 连接的机器上运行此命令：
   ```sh
   uname -sm | tr '[A-Z]' '[a-z]'
   ```
2. 在连接到 Internet 的机器上运行以下命令，并用上一条命令的输出替换
   `target_uname` 的值：
   ```sh
   target_uname="replace this with the output of the previous command"
   git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ~/powerlevel10k
   GITSTATUS_CACHE_DIR="$HOME"/powerlevel10k/gitstatus/usrbin ~/powerlevel10k/gitstatus/install -f -s "${target_uname% *}" -m "${target_uname#* }"
   ```
3. 把 `~/powerlevel10k` 从连接到 Internet 的机器复制到没有 Internet 连接的机器上的。
4. 在没有 Internet 连接的机器上的 `~/.zshrc` 中添加 `source ~/powerlevel10k/powerlevel10k.zsh-theme` ：
   ```zsh
   echo 'source ~/powerlevel10k/powerlevel10k.zsh-theme' >>~/.zshrc
   ```
5. 如果没有 Internet 连接的机器上的 `~/.zshrc` 设置了 `ZSH_THEME`，请删除该行。
   ```zsh
   sed -i.bak '/^ZSH_THEME=/d' ~/.zshrc
   ```

要更新，请在两台机器上删除 `~/powerlevel10k` ，然后重复步骤 1-3。

### 在哪里可以寻求帮助并报告错误？

寻求帮助和报告错误的最佳方法是 [打开一个议题](
https://github.com/romkatv/powerlevel10k/issues)。

[Gitter](
  https://gitter.im/powerlevel10k/community?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge)
是另一种选择。

如果一切都失败了，请发送电子邮件至 roman.perepelitsa@gmail.com。

如有必要，请用 [这个 PGP](
  https://api.github.com/users/romkatv/gpg_keys)密钥加密您的通信。

### Powerlevel10k会影响哪些shell和终端的方面？

只定义提示符，不影响其他方面。它设置 [与提示符相关的选项](
  http://zsh.sourceforge.net/Doc/Release/Options.html#Prompting)，以及参数 `PS1` 和 `RPS1`。

![Prompt Highlight](
  https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/prompt-highlight.png)

屏幕截图中高亮区域内的所有内容都是 Powerlevel10k 生成的。Powerlevel10k 没有对这些区域外的终端内容或颜色进行控制。

Powerlevel10k 不影响：

- 终端窗口/标签标题。
- `ls` 使用的颜色。
- `git` 命令的行为。
- <kbd>Tab</kbd> 完成的内容和样式。
- 命令行颜色（语法突出显示、自动建议等）。
- 键绑定。
- 别名。
- 除了 `PS1` 和 `RPS1`之外的提示符参数。
- 除了 [与提示符相关的那些](
    http://zsh.sourceforge.net/Doc/Release/Options.html#Prompting)之外的 zsh 选项。

### 如何迁移我正在Oh-My-Zsh上使用的Powerlevel9k

1. 运行以下命令：
```zsh
# Add powerlevel10k to the list of Oh My Zsh themes.
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git $ZSH_CUSTOM/themes/powerlevel10k
# Replace ZSH_THEME="powerlevel9k/powerlevel9k" with ZSH_THEME="powerlevel10k/powerlevel10k".
sed -i.bak 's/powerlevel9k/powerlevel10k/g' ~/.zshrc
# Restart Zsh.
exec zsh
```
2. *可选的但强烈建议：*
   1. 安装 [推荐的字体](#为powerlevel10k定制的meslo-nerd-font)。
   1. 输入 `p10k configure` 并选择你喜欢的提示符样式。

*相关问题：*
  - [对于Powerlevel9k的兼容性。](#对于powerlevel9k的兼容性)
  - [对于给定的相同配置，Powerlevel10k是否始终渲染与Powerlevel9k完全相同的提示？](
      #对于给定的相同配置powerlevel10k是否始终渲染与powerlevel9k完全相同的提示)
  - [与Powerlevel9k相比，提示中的额外或缺少的空格。](
      #与powerlevel9k相比提示中的额外或缺少的空格)
  - [配置向导。](#配置向导)

### 真的很快吗？

是的。参见 [zsh-bench](https://github.com/romkatv/zsh-bench) 或与
[Powerlevel9k](https://asciinema.org/a/NHRjK3BMePw66jtRVY2livHwZ) 和
[Spaceship](https://asciinema.org/a/253094)的直接比较。

### <a name='如何配置即时提示'></a>如何配置即时提示？

参见 [即时提示](#即时提示) 了解即时提示符的信息。本节解释了如何启用和配置它，并列出了您应该注意的注意事项。

即时提示符可以通过 `p10k configure` 或通过手动在 `~/.zshrc`顶部添加以下代码片段来启用：

```zsh
# 启用 Powerlevel10k 即时提示符。应该保持在 ~/.zshrc 的顶部。
# 可能需要控制台输入的初始化代码 (密码提示, [y/n]
# 确认，等) 必须在此块之上；其他所有内容可以放在此块之下。
if [[ -r "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh" ]]; then
  source "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh"
fi
```

重要的是，你要按照字面复制这些行。不要用其他内容替换`source` ，不要调用 `zcompile`，不要重定向输出等。

当启用即时提示时，在 Zsh 初始化期间，标准输入将重定向到 `/dev/null` ，标准输出与标准错误将重定向到一个临时文件。
一旦 Zsh 完全初始化，标准文件描述符就会被恢复，临时文件的内容会被打印出来。

当使用即时提示时，你应该仔细检查在 Zsh 启动时出现的任何输出，因为它可能表明初始化已被即时提示前言所改变，甚至已经损坏。
可能需要控制台输入的初始化代码，例如询问钥匙链密码或*[y/n]* 确认，必须移到 `~/.zshrc`中的即时提示前言之上。
仅在控制台打印但从未从中读取的初始化代码将与即时提示一起正常工作，尽管通常有颜色的输出可能会出现无色。你可以让它保留下来，抑制输出，或者将它移到即时提示前言之上。

以下是当启用即时提示时，会破坏的 `~/.zshrc` 的例子：

```zsh
if [[ -r "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh" ]]; then
  source "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh"
fi

keychain id_rsa --agents ssh  # 询问密码
chatty-script                 # 即使一切正常也会向 stdout 输出垃圾邮件。
# ...
```

修复版本：

```zsh
keychain id_rsa --agents ssh  # 移动到即时提示之前

# 在此之前可以执行控制台I/O。
if [[ -r "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh" ]]; then
  source "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh"
fi
# 从这一点开始，直到zsh完全初始化，控制台输入将不起作用，
# 控制台输出可能显示为未着色。

chatty-script >/dev/null      # 抑制输出垃圾邮件
# ...
```

如果 `POWERLEVEL9K_INSTANT_PROMPT` 未设置或设置为 `verbose`， Powerlevel10k 在检测到初始化期间的控制台输出时将打印警告，以引起对潜在问题的关注。
您可以通过 `POWERLEVEL9K_INSTANT_PROMPT=quiet`将此警告静音（而不会抑制控制台输出）。
如果在 `~/.zshrc` 中的某些初始化代码向控制台输出，并且无法将其移动到立即提示的前置程序之上或抑制其输出，则建议这样做。
您可以使用 `POWERLEVEL9K_INSTANT_PROMPT=off`完全禁用即时提示。如果即时提示打破了 Zsh 初始化，您不知道如何修复，请这样做。

可以通过运行 `p10k configure` 并在*即时提示*屏幕上选择适当的选项来更改 `POWERLEVEL9K_INSTANT_PROMPT` 的值。或者，您可以在现有的 `~/.p10k.zsh` 中搜索
`POWERLEVEL9K_INSTANT_PROMPT` 并更改其值。

*注意*: 即时提示需要 Zsh >= 5.4。即使使用的是较旧版本的 Zsh，也可以启用它，但它不会有任何作用。

*常见问题解答*:

- [使用即时提示时如何初始化direnv？](#使用即时提示时如何初始化direnv)
- [使用即时提示时如何导出GPG_TTY？](#使用即时提示时如何导出gpg_tty)

### 使用即时提示时如何初始化direnv？

如果您已启用 [即时提示](#即时提示)，则应在
`~/.zshrc`的顶部有这些行：

```zsh
if [[ -r "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh" ]]; then
  source "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh"
fi
```

要初始化 direnv，您需要在该块上方和下方添加一行。

```zsh
(( ${+commands[direnv]} )) && emulate zsh -c "$(direnv export zsh)"

if [[ -r "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh" ]]; then
  source "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh"
fi

(( ${+commands[direnv]} )) && emulate zsh -c "$(direnv hook zsh)"
```

*相关问题*: [使用即时提示时如何导出GPG_TTY？](#使用即时提示时如何导出gpg_tty)

### 使用即时提示时如何导出GPG_TTY？

您可以在 `~/.zshrc` 的任何位置使用以下方式导出 `GPG_TTY` ：

```zsh
export GPG_TTY=$TTY
```

无论是否使用 [即时提示](#即时提示) ，此操作都有效。 即使您没有使用 powerlevel10k，它也有效。附带一个额外的好处是，它比常用的 `export GPG_TTY=$(tty)` 快得多。

*相关问题*: [使用即时提示时如何初始化direnv？](#使用即时提示时如何初始化direnv)

### Git状态中不同符号的含义是什么？

当使用 Lean, Classic 或 Rainbow 风格时，Git状态可能看起来像这样：

```text
feature:master wip ⇣42⇡42 ⇠42⇢42 *42 merge ~42 +42 !42 ?42
```

| 符号    | 意义                                                              | 源代码                                                 |
| --------- | -------------------------------------------------------------------- | ------------------------------------------------------ |
| `feature` | 当前分支的名称；如果不在分支上，则会被替换为 `#tag` 或 `@commit` | `git status --ignore-submodules=dirty`                 |
| `master`  | 远程跟踪分支的名称；只在本地分支和远程跟踪分支名称不同时显示    | `git rev-parse --abbrev-ref --symbolic-full-name @{upstream}` |
| `wip`     | 最新提交的摘要中包含 "wip" 或 "WIP"                  | `git show --pretty=%s --no-patch HEAD`                 |
| `⇣42`     | 本地分支落后远程分支多少个提交                                  | `git rev-list --right-only --count HEAD...@{upstream}` |
| `⇡42`     | 本地分支领先远程分支多少个提交                                | `git rev-list --left-only --count HEAD...@{upstream}`  |
| `⇠42`     | 本地分支落后推送分支多少个提交                             | `git rev-list --right-only --count HEAD...@{push}`     |
| `⇢42`     | 本地分支领先推送分支多少个提交                           | `git rev-list --left-only --count HEAD...@{push}`      |
| `*42`     | 有多少个 stash                                                    | `git stash list`                                       |
| `merge`   | 仓库的状态                                                     | `git status --ignore-submodules=dirty`                 |
| `~42`     | 有多少个合并冲突                                            | `git status --ignore-submodules=dirty`                 |
| `+42`     | 有多少个已暂存的变更                                             | `git status --ignore-submodules=dirty`                 |
| `!42`     | 有多少个未暂存的变更                                           | `git status --ignore-submodules=dirty`                 |
| `?42`     | 有多少个未跟踪的文件                                            | `git status --ignore-submodules=dirty`                 |
| `─`       | 有多少个已暂存、未暂存或未跟踪的文件是未知的         | `echo $POWERLEVEL9K_VCS_MAX_INDEX_SIZE_DIRTY` or `git config --get bash.showDirtyState` |

*相关内容*: [如何更改Git状态的格式？](#如何更改git状态的格式)

### 如何更改Git状态的格式？

要更改Git状态的格式，请打开 `~/.p10k.zsh`，搜索 `my_git_formatter` 并编辑其源代码。

*相关内容*: [Git状态中不同符号的含义是什么？](#git状态中不同符号的含义是什么)

### 为什么`$HOME/.git`中的Git状态不会显示在提示中？

当使用 Lean, Classic or Rainbow 样式时，`~/.p10k.zsh` 包含以下参数：

```zsh
# 在提示符中不显示工作目录匹配此模式的存储库的Git状态。
# 例如，如果设置为 '~'，则会忽略 $HOME/.git 中的Git存储库。
# 可以使用 '|'将多个模式组合在一起：'~(|/foo)|/bar/baz/*'。
typeset -g POWERLEVEL9K_VCS_DISABLED_WORKDIR_PATTERN='~'
```

要在提示中看到 `$HOME/.git` 的Git状态，请打开 `~/.p10k.zsh` 并删除 `POWERLEVEL9K_VCS_DISABLED_WORKDIR_PATTERN`。

### 为什么Git状态有时会显示灰色，然后在短时间后变成彩色？

简要说明: 当提示中的Git状态被灰化时，这意味着Powerlevel10k正在后台计算最新的Git状态。当计算完成时，提示将自动刷新。

当你的当前目录在Git存储库中时，Powerlevel10k在每个命令之后计算最新的Git状态。如果存储库很大，或者计算机很慢，这个计算可能需要很长时间。
如果计算时间超过10毫秒（可以通过`POWERLEVEL9K_VCS_MAX_SYNC_LATENCY_SECONDS`进行配置），Powerlevel10k将以灰色显示最后一个已知的Git状态，
并在后台继续计算最新的Git状态。当计算完成时，Powerlevel10k将使用新信息刷新提示，这次是彩色Git状态。

当使用 *Rainbow* 风格时，Git状态在计算过程中显示为黑色在灰色背景。根据终端颜色配色方案，这可能很难读取。在这种情况下，您可能希望将背景颜色更改为更浅的颜色以获得更多对比度。
要做到这一点，请打开 `~/.p10k.zsh`，搜索 `POWERLEVEL9K_VCS_LOADING_BACKGROUND`，如果被注释掉，请取消注释，并更改值。

```zsh
typeset -g POWERLEVEL9K_VCS_LOADING_BACKGROUND=244
```

输入 `source ~/.p10k.zsh` 以将更改应用于当前的Zsh会话。

*相关问题*: [如何更改提示颜色？](#如何更改提示颜色)

### 如何将用户名和/或主机名添加到提示中？

当使用 Lean, Classic 或 Rainbow 风格时，当您以root用户或通过SSH登录时，提示符会显示 `username@hostname`。
当您以普通用户登录到本地机器时，显示 `username` 或 `hostname` 几乎没有价值。因此，在提示符中缺少 `username@hostname` 是指您正在本地工作，并且您不是root用户。
但是，您可以更改它。

请打开 `~/.p10k.zsh`。在顶部附近，您可以看到定义在提示符中显示哪些段的最重要参数。所有通常有用的提示符段都在其中列出。其中一些已启用，另一些已被注释掉。其中一个对您有用。

```zsh
typeset -g POWERLEVEL9K_RIGHT_PROMPT_ELEMENTS=(
  ...
  context  # user@hostname
  ...
)
```

搜索 `context` 以找到在配置中列出该提示符段特定参数的部分。您应该会看到以下行：

```zsh
# 除非使用特权或在SSH中运行，否则不要显示上下文。
# 提示: 删除下一行以始终显示上下文。
typeset -g POWERLEVEL9K_CONTEXT_{DEFAULT,SUDO}_{CONTENT,VISUAL_IDENTIFIER}_EXPANSION=
```

如果您按照提示，删除（或注释掉）最后一行，则提示符中总会显示`username@hostname` 。您可以通过调整附近的参数的值来将格式更改为仅 `username`，或更改颜色。有许多注释可帮助您导航。

您还可以将 `context` 移动到 `POWERLEVEL9K_RIGHT_PROMPT_ELEMENTS` 的其他位置，甚至移动到 `POWERLEVEL9K_LEFT_PROMPT_ELEMENTS`。

### 为什么当我在输入时有些提示段会出现并再次消失？

提示段可以配置为只在当前命令调用相关工具时显示。

```zsh
# 仅在您输入的命令调用kubectl，helm，kubens，kubectx，oc，istioctl，kogito，k9s，helmfile，flux，fluxctl，stern，kubeseal或skaffold时显示提示符段“kubecontext”。
typeset -g POWERLEVEL9K_KUBECONTEXT_SHOW_ON_COMMAND='kubectl|helm|kubens|kubectx|oc|istioctl|kogito|k9s|helmfile|flux|fluxctl|stern|kubeseal|skaffold'
```

`p10k configure` 创建的配置可能包含这种类型的参数。要自定义显示不同提示段的时间，请打开 `~/.p10k.zsh`，搜索 `SHOW_ON_COMMAND` 并删除这些参数或更改它们的值。

您还可以在 `~/.zshrc` 中定义一个函数来在*always* 和 *on command*之间切换提示段的显示。这与[kube-ps1](https://github.com/jonmosco/kube-ps1) 中的 `kubeon`/`kubeoff` 类似。

```zsh
function kube-toggle() {
  if (( ${+POWERLEVEL9K_KUBECONTEXT_SHOW_ON_COMMAND} )); then
    unset POWERLEVEL9K_KUBECONTEXT_SHOW_ON_COMMAND
  else
    POWERLEVEL9K_KUBECONTEXT_SHOW_ON_COMMAND='kubectl|helm|kubens|kubectx|oc|istioctl|kogito|k9s|helmfile|flux|fluxctl|stern|kubeseal|skaffold'
  fi
  p10k reload
  if zle; then
    zle push-input
    zle accept-line
  fi
}
```

通过输入 `kube-toggle`来调用此函数。您还可以通过在 `~/.zshrc`中添加两行将其绑定到键：

```zsh
zle -N kube-toggle
bindkey '^]' kube-toggle  # ctrl-] to toggle kubecontext in powerlevel10k prompt
```

### 如何更改提示颜色？

您可以 [更改终端使用的颜色板](#更改终端使用的颜色板) 或[通过 Powerlevel10k 配置参数设置颜色](#通过 Powerlevel10k 配置参数设置颜色).

#### 更改终端使用的颜色板

如何更改终端的颜色板 (也称为颜色方案或主题) 取决于您使用的终端类型。在终端的设置/首选项中查找或参阅文档。

当您更改终端的颜色板时，通常仅会影响从 0 到 15 编号的前 16 个颜色。 要在 Powerlevel10k 提示符上看到任何效果，您需要使用使用这些低编号颜色的提示符样式。
输入 `p10k configure` 并选择 *Rainbow*, *Lean* → *8 colors* 或 *Pure* → *Original*。 其他样式使用高编号的颜色，因此在任何终端颜色板中看起来都是一样的。

#### 通过 Powerlevel10k 配置参数设置颜色

打开 `~/.p10k.zsh`，搜索 "color", "foreground" 和 "background" ，并更改适当参数的值。 例如，以下是如何将 `time` 提示段的前景设置为明亮红色：

```zsh
typeset -g POWERLEVEL9K_TIME_FOREGROUND=160
```

使用0到255之间的数字指定颜色。从0到15的颜色在不同的终端中看起来不同。许多终端也支持通过调色板（也称为配色方案或主题）自定义这些颜色。从16到255的颜色始终看起来相同。

输入 `source ~/.p10k.zsh` 将更改应用于当前的Zsh会话。

要查看不同的颜色在终端中的样子，请运行以下命令：

```zsh
for i in {0..255}; do print -Pn "%K{$i}  %k%F{$i}${(l:3::0:)i}%f " ${${(M)$((i%6)):#3}:+$'\n'}; done
```

*相关内容：*
  - [使用Rainbow样式时，提示中的目录难以看清。](#使用rainbow样式时提示中的目录难以看清)

### 为什么Powerlevel10k会产生额外的进程？

Powerlevel10k使用 [gitstatus](https://github.com/romkatv/gitstatus) 作为 `vcs` 提示符背后的后端; gitstatus产生 `gitstatusd` 和 `zsh`。
有关详情，请参阅[gitstatus](https://github.com/romkatv/gitstatus) 。 Powerlevel10k也可能产生 `zsh` 来执行不阻塞提示符的计算。
为了避免安全隐患，这些后台进程不会由不同的交互式 shell 共享。当父 `zsh` 进程终止或运行 `exec(3)`时，它们会自动终止。

### 有哪些配置选项会使Powerlevel10k变慢？

不，Powerlevel10k总是很快，无论您使用什么配置。如果使用Powerlevel10k时有明显的提示延迟，请[打开一个议题](https://github.com/romkatv/powerlevel10k/issues)。

### Powerlevel10k加载起来快吗？

是的。请参见 [zsh-bench](https://github.com/romkatv/zsh-bench)。

### Powerlevel9k和Powerlevel10k之间的关系是什么？

Powerlevel10k在2019年3月从Powerlevel9k分支出来，在[powerlevel9k#1170](https://github.com/Powerlevel9k/powerlevel9k/issues/1170)的一周讨论之后。
Powerlevel9k已经是一个成熟的项目，有大量用户和几个月的发布周期。Powerlevel10k被转出来，以更快的速度进行性能改进和新功能。

Powerlevel9k和Powerlevel10k是独立的项目。使用其中一个时，你不应该安装另一个。应该针对你实际使用的项目提交问题。没有个人在两个存储库中都有提交权限。
所有提交到Powerlevel9k存储库的错误修复和新功能都会移植到Powerlevel10k。

随着时间的推移，Powerlevel10k中的几乎所有代码都被重写了。目前Powerlevel9k和Powerlevel10k的实现没有有意义的重叠。

Powerlevel10k致力于永久保持与所有配置的向后兼容性。
这个承诺涵盖了Powerlevel9k所有的配置参数 (见[对于Powerlevel9k的兼容性](#对于powerlevel9k的兼容性)) 和只有Powerlevel10k理解的其他参数。
Powerlevel10k中所有参数的名称均以 `POWERLEVEL9K_` 开头，以保持一致性。

### 对于给定的相同配置，Powerlevel10k是否始终渲染与Powerlevel9k完全相同的提示？

几乎是的。有一些差异。

- 默认情况下，Powerlevel10k 中仅启用了 `git` 后端。如果需要 `svn` 和 `hg`，请将它们添加到 `POWERLEVEL9K_VCS_BACKENDS`中。
  这些后端在 Powerlevel10k 中尚未优化，因此启用它们会使提示变得 *非常慢*。
- Powerlevel10k 不支持`POWERLEVEL9K_VCS_SHOW_SUBMODULE_DIRTY=true`。
- Powerlevel10k 努力与 Powerlevel9k 兼容，但在严重 bug 方面不是如此。如果您意外地依赖这些 bug，则 Powerlevel9k 和 Powerlevel10k 的提示将不同。一些示例：
  - Powerlevel9k 忽略在主题被导入之后设置的一些选项，而 Powerlevel10k 则会采用所有选项。如果在 Powerlevel9k 和 Powerlevel10k 中看到不同的图标，
    则可能是在导入主题之前定义了 `POWERLEVEL9K_MODE` 。Powerlevel9k 忽略此参数，但 Powerlevel10k 采用此参数。
		如果希望 Powerlevel10k 的提示与 Powerlevel9k 的提示完全相同，请删除 `POWERLEVEL9K_MODE`。
  - Powerlevel9k 不采用 `ZLE_RPROMPT_INDENT`。因此，Powerlevel10k 中的右提示可能会比 Powerlevel9k 多出一个空格。
    如果你不想有这个空格，请设置 `ZLE_RPROMPT_INDENT=0`。更多细节请参考[故障排除](#右提示的右侧没有背景的额外空间)。
  - owerlevel9k 图标周围的空格不一致。这在 Powerlevel10k 中得到了修复。设置`POWERLEVEL9K_LEGACY_ICON_SPACING=true` 可以获得与 Powerlevel9k 中相同的空格。
    更多细节请参考 [故障排除](#图标周围多出或少了空格).
  - Powerlevel9k 中还有许多其他不存在于 Powerlevel10k 中的 bug。

如果在从 Powerlevel9k 切换到 Powerlevel10k 时发现提示外观的其他任何变化，请 [打开一个议题](https://github.com/romkatv/powerlevel10k/issues)。

### 在配置向导中哪种提示样式最好？

关于什么构成最好的提示，有许多不同的意见，因为有许多人。大多数情况下，这取决于个人喜好。然而，有一些不同选择的隐含含义。

Pure style 是 [Pure Zsh theme](https://github.com/sindresorhus/pure)的精确复制。 它的存在是为了帮助这个主题的用户迁移。除非你是其中之一，否则选择 Lean style 代替 Pure。

如果你想将提示颜色限制在选定的终端颜色调色板（例如 *Solarized Dark*）中，使用 *Rainbow*, *Lean* → *8 colors* 或 *Pure* → *Original*。
其他样式使用固定的颜色，因此在任何终端颜色调色板中看起来都是一样的。

除了 Pure 之外，所有样式都有使用 *ASCII* 字符集的选项。提示看起来会不太漂亮，但是在所有字体和所有区域设置中都会正确呈现。

如果启用了瞬时提示，则应使用两行提示。您将获得输入命令所需的额外空间，而不会有通常会出现的减少滚动回溯密度的缺点。同样，所有命令从相同的偏移量开始也很不错。

同样，如果启用瞬态提示，稀疏提示（在提示前有一个空行）是一个很好的选择。

如果你使用的是vi键映射，选择包含 `prompt_char` 的提示（在向导中显示为绿色 `❯` ）。这个符号根据vi模式而变化：插入、命令、视觉和替换模式分别为 `❯`, `❮`, `V`, `▶` 。
当命令失败时，符号变为红色。*Lean* 样式总是包含 `prompt_char` 。 *Rainbow* 和 *Classic* 样式仅在没有左框架的两行配置中有它。

如果你重视水平空间或喜欢极简主义美学：

- 使用等宽字体，例如 [推荐的字体](#为powerlevel10k定制的meslo-nerd-font)。非等宽字体需要在单个列以下的图标后面额外空间。
- 使用Lean样式。与Classic和Rainbow相比，它每个提示段节省了两个字符。
- 禁用 *当前时间* 和 *框架*。
- 使用 *少量图标*。 *many icons* 选项启用的额外图标主要具有装饰功能。 信息图标, 如后台作业指示器, 无论如何都会显示。

*注意*: 你可以运行配置向导多次。输入 `p10k configure` 尝试新的提示样式。

### 如何使 Powerlevel10k 看起来像 robbyrussell Oh My Zsh 主题？

使用 [这个配置](
  https://github.com/romkatv/powerlevel10k/blob/master/config/p10k-robbyrussell.zsh)。

你可以下载它，将其保存为 `~/.p10k.zsh` 并从 `source ~/.p10k.zsh` 中源 `~/.zshrc`，或者直接从克隆的 `powerlevel10k` 仓库中源 `p10k-robbyrussell.zsh` 。

### 已完成的命令的提示是否可以显示*那些*命令的错误状态，而不是前面的命令？

不行。当你按下 *ENTER* 并开始运行你输入的命令时，它的错误状态尚未确定，因此无法在提示中显示。当命令完成时，错误状态已经确定，但无法再更新*那个*命令的提示。
这就是为什么每个命令的错误状态都会反映在下一个提示中。

有关详情，请参见 [/r/zsh 上的这篇文章](
https://www.reddit.com/r/zsh/comments/eg49ff/powerlevel10k_prompt_history_exit_code_colors/fc5huku)。

### 最低支持的 Zsh 版本是多少？

Zsh 5.3 或更新的版本应该可以工作。快速启动需要 Zsh >= 5.4.

### 这些截图和动画 gif 是如何创建的？

所有截图和动画 gif 都是在 GNOME 终端中录制的，
并使用[推荐的字体](#为powerlevel10k定制的meslo-nerd-font) 和 Tango Dark 配色方案以及自定义背景颜色（`#171A1B` 而不是 `#2E3436` -- 两倍暗）。

![GNOME Terminal Color Settings](
  https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/gnome-terminal-colors.png)

在此处存在的语法高亮是由[zsh-syntax-highlighting](
  https://github.com/zsh-users/zsh-syntax-highlighting)提供的。

### 推荐字体是如何创建的？

[推荐字体](#为powerlevel10k定制的meslo-nerd-font) 是许多个体的产物。它的起源是 *Bitstream Vera Sans Mono*，它衍生出了 *Menlo*, 接着衍生出了 *Meslo*。
最后，使用Nerd Fonts的脚本为 *Meslo* 添加了额外的字形。最终字体根据[Apache License](
  https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/MesloLGS%20NF%20License.txt)发布。

MesloLGS NF字体可以使用以下命令重新创建（需要 `git` 和 `docker`）：

```zsh
git clone --depth=1 https://github.com/romkatv/nerd-fonts.git
cd nerd-fonts
./build 'Meslo/S/*'
```

如果一切顺利，`./out` 中将出现四个 `ttf` 文件。

### 如何为分发打包 Powerlevel10k？

目前不容易也不建议打包和分发Powerlevel10k。目前没有可供您遵循的说明，使您能够在发布新版本的Powerlevel10k时轻松更新您的包。这可能在未来改变，但不会很快。

## 故障排除

- [提示中标出的问号](#提示中标出的问号)
- [ 图标、字符或powerline符号无法呈现](#图标字符或powerline符号无法呈现)
- [powerline符号周围的Sub-pixel渲染不完美](#powerline符号周围的sub-pixel渲染不完美)
- [错误：字符超出范围](#错误字符超出范围)
- [光标位置错误](#光标位置错误)
- [提示以奇怪的方式换行](#提示以奇怪的方式换行)
- [右提示在错误的位置](#右提示在错误的位置)
- [每次启动Zsh时都会自动运行配置向导](#每次启动zsh时都会自动运行配置向导)
- [配置向导中缺少一些提示样式](#配置向导中缺少一些提示样式)
- [无法安装推荐字体](#无法安装推荐字体)
- [与Powerlevel9k相比，提示中的额外或缺少的空格](#与powerlevel9k相比提示中的额外或缺少的空格)
  - [右提示的右侧没有背景的额外空间](#右提示的右侧没有背景的额外空间)
  - [图标周围多出或少了空格](#图标周围多出或少了空格)
- [输入`source ~/.zshrc`后出现奇怪的事情](#输入source-zshrc后出现奇怪的事情)
- [一段时间后临时提示停止工作](#一段时间后临时提示停止工作)
- [无法使Powerlevel10k与我的插件管理器配合使用](#无法使powerlevel10k与我的插件管理器配合使用)
- [使用Rainbow样式时，提示中的目录难以看清](#使用rainbow样式时提示中的目录难以看清)
- [调整终端窗口大小时出现恐怖的混乱](#调整终端窗口大小时出现恐怖的混乱)
- [在Konsole中截断图标](#在konsole中截断图标)
- [Arch Linux徽标在右下角有一个圆点](#arch-linux徽标在右下角有一个圆点)

### 提示中标出的问号

如果它看起来像一个普通的 `?`，那就正常。它意味着当前Git存储库中有未跟踪的文件。键入 `git status` 来查看这些文件。您可以更改此符号或完全禁用显示未跟踪的文件。
在 `~/.p10k.zsh` 中搜索 `untracked files` .

*常见问题解答*: [Git状态中不同符号的含义是什么？](#git状态中不同符号的含义是什么)

如果您的终端的字体缺少一些字形，您还可以在提示中看到奇怪的问号。请参阅 [ 图标、字符或powerline符号无法呈现](#图标字符或powerline符号无法呈现).

###  图标、字符或powerline符号无法呈现

重新启动您的终端， [安装推荐的字体](#为powerlevel10k定制的meslo-nerd-font)并运行 `p10k configure`.

### powerline符号周围的Sub-pixel渲染不完美

![Powerline Prompt Imperfections](
  https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/powerline-imperfections.png)

这张截图上有三个不完美之处。从左到右分别为：

1. 提示段内容和后续powerline连接之间的细蓝线（子像素间隙）。
1. powerline连接和后续提示段的不正确对齐。连接似乎向右移动了。
1. powerline连接下面的细红线。连接似乎向上移动了。

Zsh 主题无法对终端内容进行精确控制。屏幕上看到的所有内容都是由等宽字符组成的。白色powerline提示段由白色背景上的文本和 U+E0B0（右指向三角形）组成。

![Powerline Prompt Imperfections](
  https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/powerline-anatomy.png)

如果 Powerlevel10k 提示周围有powerline符号的不完美之处，你将与所有powerline主题（Agnoster、Powerlevel9k、Powerline 等）看到完全相同的不完美之处。

有几件事你可以尝试来解决这些不完美之处：

- 尝试 [推荐的字体](#为powerlevel10k定制的meslo-nerd-font)。如果你已经在使用它，切换到另一种字体可能有所帮助，但不太可能。
- 将终端字体大小调整一点。例如，在 iTerm2 中，powerline提示在字体大小 11 和 13 时看起来完美，但在 12 时会崩溃。
- 将终端设置中的内置powerline字形启用（支持 iTerm2）。
- 在终端设置中更改字体提示和/或抗锯齿模式。
- 如果您的终端有选项，请将所有文本向上/下/左/右移一个像素。
- 尝试使用不同的终端。

一个更激进的解决方案是切换到没有背景的提示样式。键入 `p10k configure` 配置并选择 *Lean*。这种样式具有现代轻量级外观。
作为一个奖励，它不会受到powerline样式提示所受的呈现不完美的影响。

### 错误：字符超出范围

输入 `echo '\u276F'`。如果您收到 "zsh: character not in range"错误，则您的本地化不支持 UTF-8。您需要修复它。如果您在 SSH 上运行 Zsh，
请参见[此处](https://github.com/romkatv/powerlevel10k/issues/153#issuecomment-518347833)。如果您在本地运行 Zsh，请Google搜索 "在*您的操作系统*中设置 UTF-8 本地化"。

### 光标位置错误

输入 `echo '\u276F'`。如果您收到 "zsh: character not in range"错误，请参阅[上一节](#错误字符超出范围)。

如果 `echo` 命令输出 `❯` ，但光标仍然位置不正确，请安装[推荐的字体](#为powerlevel10k定制的meslo-nerd-font)并运行 `p10k configure` 。

如果这没有帮助，在 `~/.zshrc` 的末尾添加 `unset ZLE_RPROMPT_INDENT`。

仍然有问题？运行以下命令来诊断问题：

```zsh
() {
  emulate -L zsh
  setopt err_return no_unset
  local text
  print -rl -- 'Select a part of your prompt from the terminal window and paste it below.' ''
  read -r '?Prompt: ' text
  local -i len=${(m)#text}
  local frame="+-${(pl.$len..-.):-}-+"
  print -lr -- $frame "| $text |" $frame
}
```

#### 如果提示线与框架对齐

```text
+------------------------------+
| romka@adam ✓ ~/powerlevel10k |
+------------------------------+
```

如果该命令的输出对每个提示的所有部分（左侧和右侧）对齐，则表明主题或配置中存在错误。使用此命令来诊断它：

```zsh
print -rl -- ${(eq+)PROMPT} ${(eq+)RPROMPT}
```

寻找 `%{...%}` 和反斜杠转义在输出中。如果有任何，他们是可能的罪魁祸首。如果您卡住了，请打开一个议题。

#### 如果提示线比框架长

```text
+-----------------------------+
| romka@adam ✓ ~/powerlevel10k |
+-----------------------------+
```

这通常是由终端错误或配置错误引起的，使它将不确定宽度字符打印为双宽而不是单宽。例如，[这个问题](https://github.com/romkatv/powerlevel10k/issues/165)。

#### 如果提示线比框架短并损坏

```text
+------------------------------+
| romka@adam ✓~/powerlevel10k |
+------------------------------+
```

注意，这个提示与原来的不同，因为它在勾号后缺少了一个空格。

这可能是macOS低级bug导致的。看看[这个问题](https://github.com/romkatv/powerlevel10k/issues/241).

如果提示中包含被Unicode标准指定为“宽”的字形，并且你的终端错误地将它们显示为非宽字形，也可能会发生这种情况。
受到这一限制的终端包括Konsole、Hyper和集成的VSCode Terminal。解决方案是使用另一个终端或从提示中删除所有宽字形。

#### 如果提示行比框架短且未被损坏

```text
+--------------------------------+
| romka@adam ✓ ~/powerlevel10k |
+--------------------------------+
```

这可能是因为区域设置配置错误造成的。看看[这个问题](https://github.com/romkatv/powerlevel10k/issues/251)。

### 提示以奇怪的方式换行

See [光标位置错误](#光标位置错误).

### 右提示在错误的位置

See [光标位置错误](#光标位置错误).

### 每次启动Zsh时都会自动运行配置向导

当 Powerlevel10k 启动时，如果没有定义 `POWERLEVEL9K_*` 参数，它会自动运行 `p10k configure` 。
根据您选择的提示样式，配置向导会在 `~/.p10k.zsh` 中创建一堆 `POWERLEVEL9K_*` 参数，并在 `~/.zshrc` 中添加一行以引用此文件。下次启动 Zsh 时，配置向导不应自动运行。
如果它运行了，这意味着在到达引用 `~/.p10k.zsh` 的行之前，对 `~/.zshrc` 的评估提前终止了。这通常是由于 `~/.zshrc` 中的语法错误导致的。
这些错误会被配置向导屏幕隐藏，所以你没有注意到它们。退出配置向导时，查找错误消息。
您还可以使用 `POWERLEVEL9K_DISABLE_CONFIGURATION_WIZARD=true zsh` 在不自动运行配置向导的情况下启动 Zsh。一旦您可以看到错误，就修复 `~/.zshrc` 来消除它们。

### 配置向导中缺少一些提示样式

如果 Zsh 版本低于 5.7.1 或 `COLORTERM` 环境变量既不是 `24bit` 也不是 `truecolor`，配置向导将不会提供带有 Snazzy 颜色方案的 Pure 样式。
*修复方法*F：安装 Zsh >= 5.7.1 并使用带有 truecolor 支持的终端。使用 `print -P '%F{#ff0000}red%f'` 进行验证。
如果终端可以显示的颜色少于256种颜色，配置向导将预选择8种颜色的Lean样式。所有其他样式都需要至少256种颜色。
*解决方法*：使用支持256种颜色的终端，并确保 `TERM` 环境变量设置正确。使用 `print $terminfo[colors]` 进行验证。
如果系统上没有UTF-8语言环境，配置向导不会提供使用Unicode字符的提示样式。*解决方法*：安装UTF-8语言环境。使用 `locale -a` 进行验证。
当可用UTF-8语言环境时，配置向导会首先评估终端字体的能力。如果您的答案表明有些字形没有正确呈现，配置向导不会提供使用它们的提示样式。
*解决方法*：重新启动终端并安装[推荐的字体](#为powerlevel10k定制的meslo-nerd-font)。通过运行 `p10k configure` 并检查所有字形是否正确呈现来验证。

### 无法安装推荐字体

下载[推荐字体](#为powerlevel10k定制的meslo-nerd-font)后,您可以像安装其他字体一样安装它。在Google上搜索“如何在*您的操作系统*上安装字体”。

### 与Powerlevel9k相比，提示中的额外或缺少的空格

简要说明: 在 `ZLE_RPROMPT_INDENT=0` 中添加 `POWERLEVEL9K_LEGACY_ICON_SPACING=true` 和 `~/.zshrc`，可以得到与 Powerlevel9k 相同的提示符间距。

在使用 Powerlevel10k 配合 Powerlevel9k 配置时，可能会在提示符中添加额外的空格。这有两种情况。

#### 右提示的右侧没有背景的额外空间

简要说明: 在 `ZLE_RPROMPT_INDENT=0` 中添加 `~/.zshrc` 可以消除这个空间。

从 [Zsh 文档](
  http://zsh.sourceforge.net/Doc/Release/Parameters.html#index-ZLE_005fRPROMPT_005fINDENT):

> `ZLE_RPROMPT_INDENT <S>`
>
>如果设置，用于在行编辑器中给出由 `RPS1` 或 `RPROMPT` 给出的右提示符右侧和屏幕右侧之间的缩进。如果没有设置，则使用 `1`。
>
> 通常将此值设置为 `0`，以使提示符与屏幕右侧接触。

Powerlevel10k 采用这个参数。如果设置 `ZLE_RPROMPT_INDENT=1` (或未设置，这是与设置为 `1`相同的），则右提示符的右侧将有一个空格。
如果设置 `ZLE_RPROMPT_INDENT=0`，则提示符将达到终端的边缘。除 Powerlevel9k 之外的所有主题都是这样工作的。

![ZLE_RPROMPT_INDENT: Powerlevel10k vs Powerlevel9k](
  https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/p9k-vs-p10k-zle-rprompt-indent.png)

Powerlevel9k 问题: [powerlevel9k#1292](https://github.com/Powerlevel9k/powerlevel9k/issues/1292)。 它已在 Powerlevel9k 的开发分支中修复，但修复尚未在 `master`分支中实现。

在 `ZLE_RPROMPT_INDENT=0` 中添加 `~/.zshrc` 可获得与 Powerlevel9k 中提示符右边缘的相同间距。

*注意:* 几个版本的 Zsh 在将 `ZLE_RPROMPT_INDENT=0`设置为时会触发错误。 Powerlevel10k 可以在使用 powerline 提示符样式时绕过这些错误。
如果在提示符中注意到视觉伪像或光标位置错误，请尝试从 `~/.zshrc` 中删除 `ZLE_RPROMPT_INDENT` 。

#### 图标周围多出或少了空格

简要说明: 将 `POWERLEVEL9K_LEGACY_ICON_SPACING=true` 添加到 `~/.zshrc` 中，以获得与Powerlevel9k中相同的图标周围的空格。

Powerlevel9k中的图标周围的空格不一致。

![ZLE_RPROMPT_INDENT: Powerlevel10k vs Powerlevel9k](
  https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/p9k-vs-p10k-icon-spacing.png)

这种不一致是一个持久的麻烦，因此在Powerlevel10k中解决了这个问题。
您可以将 `POWERLEVEL9K_LEGACY_ICON_SPACING=true` 添加到 `~/.zshrc` 中，以获得与Powerlevel9k中相同的图标周围的空格。

*注意:* 在使用 `POWERLEVEL9K_LEGACY_ICON_SPACING` 时定义 `p10k configure`并不是个好主意。

### 输入`source ~/.zshrc`后出现奇怪的事情

无论您是否使用Powerlevel10k，运行 `source ~/.zshrc`都是一个坏主意。此命令可能导致随机错误，代码不良和Zsh的逐步减速。

如果您已经对 `~/.zshrc` 或其所源文件进行了更改，请重新启动Zsh以应用这些更改。最可靠的方法是输入 `exit` 并启动一个新的Zsh会话。您还可以使用 `exec zsh`。
虽然与完整的Zsh重新启动不完全相同，但这个命令比source `source ~/.zshrc`要可靠得多。

### 一段时间后临时提示停止工作

参见 [输入`source ~/.zshrc`后出现奇怪的事情](#输入source-zshrc后出现奇怪的事情).

### 无法使Powerlevel10k与我的插件管理器配合使用

如果 [安装说明](#安装) 对您无效，请尝试禁用当前主题（这样您就不会有主题），然后手动安装 Powerlevel10k。

1. 禁用框架/插件管理器中的当前主题。

- **oh-my-zsh:** 打开 `~/.zshrc` 并删除设置 `ZSH_THEME`的行。它可能看起来像这样： `ZSH_THEME="powerlevel9k/powerlevel9k"`。
- **zplug:** 打开 `~/.zshrc` 并删除引用当前主题的 `zplug` 命令。例如，如果您当前使用 Powerlevel9k，请查找 `zplug bhilburn/powerlevel9k, use:powerlevel9k.zsh-theme`。
- **prezto:** 打开 `~/.zpreztorc` 并在其中放置 `zstyle :prezto:module:prompt theme off` 。
  删除任何其他设置 `theme` 的命令，例如 `zstyle :prezto:module:prompt theme powerlevel9k`。
- **antigen:** 打开 `~/.zshrc` 并删除设置 `antigen theme`。它可能看起来像这样： `antigen theme powerlevel9k/powerlevel9k`。

2. 手动安装 Powerlevel10k。

```zsh
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ~/powerlevel10k
echo 'source ~/powerlevel10k/powerlevel10k.zsh-theme' >>~/.zshrc
```

此安装方法不会使任何东西变慢或其他问题。

### 使用Rainbow样式时，提示中的目录难以看清

在 Rainbow 样式中，当前工作目录使用蓝色背景上的亮白色文本显示。白色是固定的，看起来总是一样的，但"蓝色"的外观由您的终端颜色调色板定义。如果很浅，可能很难看到白色文本。

有几种解决方法。

- 键入 `p10k configure` 配置并选择更可读的提示样式。
- [更改终端颜色调色板](#更改终端使用的颜色板). 。尝试 Tango Dark 或 Solarized Dark，或仅更改 "蓝色" 颜色。
- [更改目录背景和/或前景颜色](#通过 Powerlevel10k 配置参数设置颜色).您要查找的参数称为`POWERLEVEL9K_DIR_BACKGROUND`,`POWERLEVEL9K_DIR_FOREGROUND`,
  `POWERLEVEL9K_DIR_SHORTENED_FOREGROUND`,`POWERLEVEL9K_DIR_ANCHOR_FOREGROUND` 和`POWERLEVEL9K_DIR_ANCHOR_BOLD`。您可以在 `~/.p10k.zsh`中找到它们。

### 调整终端窗口大小时出现恐怖的混乱

当您水平调整终端窗口几次时，您可能会看到这个混乱的图片。

![Powerlevel10k Resizing Mess](
  https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/resizing-mess.png)

简要说明: 当终端重新排列 Zsh 提示时，这个问题就会出现。它不是特定于 Powerlevel10k 的。见 [优化](#优化).

*注意: 这一节 [原本提到了](
  https://github.com/romkatv/powerlevel10k/blob/dce00cdb5daaa8a519df234a7012ba3257b644d4/README.md#horrific-mess-when-resizing-terminal-window)
这个问题是由 Zsh 的 bug 引起的。虽然在许多情况下通过修改 Zsh 可以避免这个问题，但是无法完全解决。因此将责任归咎于 Zsh 不公平。*

#### 问题的本质

当终端窗口调整大小时，当前提示符开始处和光标之间的垂直距离（以下称为 `VD` ）会发生变化，这就是问题的体现。

当终端窗口水平缩小时，有两种方法处理不再适合的长行：*重排*或*截断*。

缩小前的终端内容：

![Terminal Content Before Shrinking](
  https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/resize-original.png)

缩小时终端重排文本：

![Terminal Reflows Text When Shrinking](
  https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/resize-reflow.png)

缩小时终端截断文本：

![Terminal Truncates Text When Shrinking](
  https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/resize-truncate.png)

重排策略可能会改变终端内容的高度。如果这样的内容在当前提示符开始处和光标之间，Zsh 就会在错误的行上打印提示符。截断策略永远不会改变内容的高度，因此不会引发这个问题。

让我们慢慢看看这个问题是如何进行的。我们首先使用 `zsh -f`启动并粘贴以下代码：

```zsh
function pause() { read -s }
functions -M pause 0

reset
print -l {1..3}
setopt prompt_subst
PROMPT=$'${$((pause()))+}left>${(pl.$((COLUMNS-12))..-.)}<right\n> '
```

当 `PROMPT` 被展开时，它会调用 `pause` 来让我们观察终端的状态。下面是初始状态：

![Terminal Resizing Bug 1](
  https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/resize-bug-1.png)

Zsh 跟踪光标相对于当前提示符的开始位置。在这种情况下，它知道光标在一行下面。当我们缩小终端窗口时，它看起来像这样：

![Terminal Resizing Bug 2](
  https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/resize-bug-2.png)

此时，终端会向 Zsh 发送 `SIGWINCH` 以通知它有关终端尺寸更改的信息。请注意，这个信号是在终端内容被重排*之后*发送的。 

当 Zsh 收到 `SIGWINCH`, 时，它会尝试擦除当前提示符并重新打印它。它会去它*认为*当前提示符的位置 -- 光标上方的一行（!） -- 擦除所有终端内容并在那里打印重新展开的提示符。
然而，调整提示符后不再在光标上方一行。它在光标上方两行！ Zsh 最终将新提示符打印太低了一行。

![Terminal Resizing Bug 3](
  https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/resize-bug-3.png)

在这种情况下，我们得到了不想要的垃圾内容，因为 `VD` *增加*了。当你使终端窗口更宽时， `VD` 也可能会 *降低*，这会导致新提示打印在预期之上，可能会在过程中抹除有用的内容。

这里还有几个例子，缩小终端窗口会导致 `VD`增加。

- 简单的一行左提示符和右提示符。没有 `prompt_subst`。请注意，光标在提示符行下面（按 *ESC-ENTER* 获得它）。
  ![Zsh Prompt That Breaks on Terminal Shrinking 1](
    https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/resize-breakable-1.png)
- 简单的一行左提示符。没有 `prompt_subst`，没有右提示符。在这里，`VD` 缩小时会由于命令行换行而增加。
  ![Zsh Prompt That Breaks on Terminal Shrinking 2](
    https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/resize-breakable-2.png)

#### Zsh 补丁

[这个 Zsh 补丁](https://github.com/romkatv/zsh/tree/fix-winchanged) 补丁在某些终端修复了这个问题。
补丁的思想是在打印提示符之前使用 `sc` （保存光标）终端功能，并在需要刷新提示符时使用 `rc` （恢复光标）将光标移回原始位置。

这个补丁只能在当终端窗口调整大小时，一起重排保存的光标位置和文本的终端上使用。
在不在调整大小时重排文本的终端（无论是补丁版本的 Zsh 还是未补丁版本的 Zsh）以及在重排文本但不重排保存的光标位置的终端（无论是补丁版本的 Zsh 还是未补丁版本的 Zsh）上，
补丁没有任何明显的效果。换句话说，这个补丁在一些终端上修复了调整大小的问题，而在其他终端上保持了原有的行为。

有两种补丁 Zsh 的替代方法可能看起来有效，但实际上并不行：

- 使用 `u7` 终端功能查询当前光标位置，然后使用 `cup` 返回到它来代替 `sc`。这不起作用，因为文本重排时当前提示符的开始的绝对位置会改变。
- 在尝试刷新提示符之前，根据新的终端尺寸重新计算 `VD`。这不起作用，因为 Zsh 不知道终端是重排文本还是截断文本。
  如果 Zsh 能够知道终端重排文本，这种方法在窗口调整大小时不断重排文本并快速触发 `SIGWINCH` 的终端仍然不起作用。在这种环境下，实际终端尺寸与 Zsh 认为的尺寸不同步。

在这种环境下，真正的终端尺寸与 Zsh 认为的尺寸不同步。 没有补丁进入上游 Zsh 的 ETA。 见 [讨论](
  https://www.zsh.org/mla/workers//2019/msg00561.html)。

#### 优化

这个问题有几种优化选项。

- 使用 [kitty](https://sw.kovidgoyal.net/kitty/) 终端版本 >= 0.24.0，并在 Powerlevel10k 中启用终端-shell 集成，
  通过在 `~/.p10k.zsh` 中定义`POWERLEVEL9K_TERM_SHELL_INTEGRATION=true` 。
- [从源代码中重新构建 Zsh](
    https://github.com/zsh-users/zsh/blob/master/INSTALL)并应用 [补丁](#zsh-补丁)。
	如果您使用 Alacritty、kitty 或其他在大小调整时重排文本但不重排保存的光标位置的终端，这将无济于事。 在这样的终端上，补丁将没有明显的效果。
  在终端设置中禁用窗口调整大小时的文本重排。 如果您的终端没有此设置，请尝试使用不同的终端。
- 避免在提示符开始和光标之间的长行。
  1. 使用 `POWERLEVEL9K_SHOW_RULER=false`禁用标尺。
  2. 使用 `POWERLEVEL9K_MULTILINE_FIRST_PROMPT_GAP_CHAR=' '`禁用提示符连接。
  3. 使用 `POWERLEVEL9K_MULTILINE_FIRST_PROMPT_SUFFIX=''`,
	`POWERLEVEL9K_MULTILINE_NEWLINE_PROMPT_SUFFIX=''` 和 `POWERLEVEL9K_MULTILINE_LAST_PROMPT_SUFFIX=''`禁用右侧框架。
  4.使用 `POWERLEVEL9K_RIGHT_PROMPT_ELEMENTS=()`。右提示在最后一个提示行上将导致调整大小问题，但仅当光标在其下方时才会发生。
  这不是很常见，所以您可能希望在 `POWERLEVEL9K_RIGHT_PROMPT_ELEMENTS` 中保留一些元素，只要它们没有被 `newline` 所继承即可。

### 在Konsole中截断图标

当使用非等宽字体的 Konsole 时，图标可能在右侧被截断。在这里，"non-monospace" 指的是任何字形宽度超过单列的字体，或者是在 Unicode 标准中被指定为 "wide" 的字形宽度超过两列的字体。

![Icons cut off in Konsole](
  https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/konsole-non-monospace-font.png)

截图的最后一行显示了一个截断的 Arch Linux 图标。

有几种优化此问题的选项。

1. 使用其他终端。 Konsole 是唯一表现出这种行为的终端。
2. 使用等宽字体。
3. 手动在被截断的图标之后添加额外的空格。例如，如果 `os_icon` 提示片段的内容被截断，请打开 `~/.p10k.zsh` ，搜索 `POWERLEVEL9K_OS_ICON_CONTENT_EXPANSION` ，并按如下方式更改：

```zsh
typeset -g POWERLEVEL9K_OS_ICON_CONTENT_EXPANSION='${P9K_CONTENT} '  # 结尾处的额外空格
```
4. 使用一个不同的等宽字体图标。例如，如果 Arch Linux logo 被截断，请在 `~/.p10k.zsh`中添加以下参数：
```zsh
typeset -g POWERLEVEL9K_LINUX_ARCH_ICON='Arch'  # 替代 logo 的普通 “Arch”
```
5. 禁用被截断的图标的显示。例如，如果 `os_icon` 提示段的内容被截断，
请打开 `~/.p10k.zsh` 并从 `POWERLEVEL9K_LEFT_PROMPT_ELEMENTS` 和 `POWERLEVEL9K_RIGHT_PROMPT_ELEMENTS` 中删除 `os_icon`。

*注意: [Konsole 不正式支持非等宽字体。](
  https://bugs.kde.org/show_bug.cgi?id=418553#c5).

### Arch Linux徽标在右下角有一个圆点

![Arch Linux Logo with a dot](
  https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/arch-linux-logo-dot.png)

有些字体在粗体中有一个错误的带点图标。有两种解决方法。

1. 使用一种字体，其中粗体中有正确的 Arch Linux logo。例如，[推荐的 Powerlevel10k 字体](#为powerlevel10k定制的meslo-nerd-font)。
2. 在常规（非粗体）字体中显示图标。要做到这一点，请打开 `~/.p10k.zsh`，搜索`POWERLEVEL9K_OS_ICON_CONTENT_EXPANSION` 并从其值中删除 `%B` 。
```zsh
typeset -g POWERLEVEL9K_OS_ICON_CONTENT_EXPANSION='${P9K_CONTENT}'  # 不是粗体
```
