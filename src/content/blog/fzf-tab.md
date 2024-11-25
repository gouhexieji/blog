---
title: 一个让你工作效率提高200%的zsh插件---fzf-tab
publishDate: '2024-11-25'
isFeatured: true
tags:
    - zsh
    - linux
seo:
  title: 一个让你工作效率提高200%的zsh插件
  description: fzf-tab
---
zsh的自动补全比bash的强了不止一点，但还是有点一言难尽。
> # 一些痛点
> - 补全速度慢
> - 不够智能
> - 部分命令不能补全
> - 丑(不要跟我说什么兼容性，桌面环境下颜值既正义

---

于是[fzf-tab](https://github.com/Aloxaf/fzf-tab "fzf-tab的GitHub仓库")。插件便应运而生。

先来介绍一下fzf-tab
故名思意，使用fzf来优化zsh的tab补全
fzf嘛，好用的嘞🤓

顺便说一下安装过程
这里就用Oh-My-Zsh为例
记得装fzf啊喂
```
git clone https://github.com/Aloxaf/fzf-tab ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/fzf-tab
```
然后在你的.zshrc中plugin里
```
plugins=(* fzf-tab *)
```
ps:要在zsh-autosuggestions、zsh-syntax-highlighting等插件之前加载fzf-tab

然后重启zsh按下tab试试

fzf-tab的配置采用和zsh自带的补全一样的zstyle
这里贴一下插件作者的博客里的配置
```
# kill 结束进程时时提供预览
zstyle ':completion:*:*:*:*:processes' command "ps -u $USER -o pid,user,comm,cmd -w -w"
zstyle ':fzf-tab:complete:kill:argument-rest' fzf-preview 'ps --pid=$word -o cmd --no-headers -w -w'
zstyle ':fzf-tab:complete:kill:argument-rest' fzf-flags '--preview-window=down:3:wrap'

# cd 时在右侧预览目录内容
zstyle ':fzf-tab:complete:cd:*' fzf-preview 'eza -1 --color=always $realpath'
```

fzf-tab还提供了一个二进制模块用来加快颜色渲染速度
```
build-fzf-tab-module
```




