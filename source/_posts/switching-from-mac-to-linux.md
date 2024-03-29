---
title: switching from Mac to Linux
excerpt: 尝试从 Mac 迁移到 Linux，选择了 ArchLinux 和对应的各种日常软件，完成了初步配置。
---

2016 年买了第一台 13 寸 MacBook Air 2015 之后，这些年一直在用 Mac。这台 Mac 是我最满意的电脑。虽然是最便宜的入门款，一直用到 2018 年没出过任何问题，后来送人了，对方一直用到现在。到 2018 年觉得性能不够需要换电脑时，毫不犹豫地选择了 MacBook Pro。由于苹果将内存固态直接焊接在主板上，无法后续升级，最终选择了最高配置的 15 寸 MacBook Pro 2018。

随后两年的使用体验让我觉得是一笔很糟糕的付出——虽然是最高配置，但还是时不时会遇到不响应，除此之外还遇到了电池膨胀、外接显示器唤醒等问题。更不用说键盘、touchbar 等固有缺陷。除此之外，Mac 使用的老旧 BSD 命令行跟 GNU 的不一致也时不时惹人恼火。

由于不想绑定在苹果的封闭生态上。两年前从 iPhone 换到了 Samsung，使用了两年倒是没有任何的不适。最近开始考虑将 Linux 作为主要平台使用。

就像选择 Android 需要选择具体的厂商，选择 Linux 则需要选择具体的 Distribution。在使用第一台 MacBook 之前，曾经在 Laptop 上使用过一段时间 Ubuntu。在 Mac 为了使用一些 Linux only 的功能也是在 virtual box 安装了 Ubuntu Server。

我认为 Ubuntu 的优缺点如下，

优点：
- 新手友好
- 开箱即用，可以不用花时间定制配置
- 硬件支持比较新和广泛
- 软件丰富，各种日常办公软件提供 Linux 支持时，Ubuntu 一般是官方支持平台

缺点：
- 商业公司运营，而非社区
- 打包和强推一些不少不需要的东西，比如 snap
- 出了问题比较难明白到底怎么回事，有时不得不重装系统

在接触了一段时间 ArchLinux 中文社区和看了一些 ArchLinux 官方介绍之后，决定选择 ArchLinux（还有部分原因是觉得 ArchLinux Logo 好看）。

在此之前还看到了不少推荐 Manjaro 的文章，不过看了 ArchLinux 的[介绍](https://wiki.archlinux.org/title/Arch_Linux)之后，并不认同 Manjaro 是更友好的 ArchLinux。后来又看到了 [Manjaro 悖论](https://szclsya.me/zh-cn/posts/linux/manjaro_controversies/) 这篇文章，发现之前的判断没错。

家里日常用的电脑是安装了 Hackintosh 的 NUC 8。为了不影响当前使用，慢慢开始尝试 ArchLinux，我单独购入了一块 1TB Sata SSD 用于安装 ArchLinux。然后跟着官方的 [installation guide](https://wiki.archlinux.org/title/installation_guide)，开始安装系统。随后，又跟着 [general recommendations](https://wiki.archlinux.org/title/general_recommendations) 配置。

对 ArchLinux 的学习是从安装系统就开始的。每一步要安装配置时，都需要先大概搞明白安装的东西是做什么的，大概是怎么工作的。因此，出了问题也可以自行分析并解决，而不是想以往一样搜索别人是怎么做的，然后照着做。每个人的环境和出问题的场景总是千奇百怪，许多时候没有一个直接的例子可以照着做。依靠自己分析解决问题，因为理解了问题所在，因而不会想没头苍蝇一样到处搜索答案，屡次不行就会烦躁郁闷。同时，随着解决问题的增加，相应的知识和经验也会增加，后续遇到常规的问题可以很快解决。

此外，ArchLinux 的 wiki 质量很高，应该是首要的参考资料（而不是质量参差不齐的博客文章）。在配置 4K 显示器 DPI 和 fctix5 词库时都在别的地方走了弯路，最终发现还是 ArchLinux wiki 上的操作是对的。其实最初也是参考 wiki 进行操作的，不过由于没有观测到预期的结果，又去搜索别的方法了，试了种种方法都不行，最终回到 wiki 发现可以 work；应该是此前某个步骤有错。

使用 Linux 让选择困难的我最头疼的就是每一步都有许多选项。选完了发行版之后，又要开始选择桌面环境（DE）。一开始并不是很清楚桌面环境和窗口管理器（WM）之间的区别，打算试试 KDE + i3wm。后来了解到完全可以不用桌面环境，直接用窗口管理器。对于平时主要就用浏览器和终端的我来说，确实很适合。接下来又发现 Linux 下的窗口方案也有两套——X window 和 wayland。X window 看起来老旧且配置繁多，因而选择了 wayland 下的 i3 兼容的窗口管理器 sway。随后发现基于 Electron 的 LogSeq 无法使用，原来是 wayland 不支持。由于不想引入 xwayland，最终还是放弃 sway，使用 i3。

然后在 i3wm 下完成了常用软件的基本配置：
- rofi：app launcher，替代默认的 dmenu
- polybar：status bar，替代 i3 bar
- alacritty：终端
- fish：shell
- flameshot：截图
- fcitx5-rime：输入法，同时导入了 zhwiki 和 moegirl 词库
- feh：壁纸和图片查看
- i3lock & systemd：锁屏和休眠
- xmodmap：键盘改键
- neovim：coding, blog, doc
- logseq：笔记
- firefox
- telegram
- onedrive

这个过程中确实花了不少时间。一度也觉得把时间花在做这些事情上有什么意义吗？最初一周的的热情过了之后，两周后才有又继续开始完善配置。不过，我一开始就没想着要一下全部迁移到 Linux 上，只是慢慢完善配置。到现在也基本可用了，后续使用过程中再去优化调整。

最近一周看了 [linux on the desktop](https://マリウス.com/linux-on-the-desktop-part-two/) 的文章后，又开始想要 DIY 一个类似的 Linux workstation。甚至都已经找到了所有对应组件在哪里可以买到。然而还不确认是否能够完全迁移到 Linux 上，且 6000 显卡溢价过高，一直犹豫。看了几篇 switching from Mac to Linux 的文章（包括前面这一篇），发现都是先随便搭建一个 Linux 系统，慢慢迁移上去并试着使用一年左右试试；日常使用完全没有问题后，再完全迁移到 Linux。这是一个很不错的思路，不是一步到位，而是要逐步验证和优化。因而，现在打算先在家里的 NUC 8 上日常使用 ArchLinux 。一年后再根据体验考虑是否要搭建 Linux workstation 作为主要使用平台；就算如此，在有移动的场景中可能还是会继续使用 MacBook 。

