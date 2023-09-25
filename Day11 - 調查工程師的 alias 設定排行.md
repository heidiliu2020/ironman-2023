###### tags: `2023鐵人賽` `qiita` `alias`
# [2023 15th鐵人賽] Day11 - 調查工程師的 alias 設定排行

> 原文連結：[世の中のエンジニアのalias設定 - Qiita](https://qiita.com/reireias/items/d906ab086c3bc4c22147)

alias 是什麼？文章中也有稍微介紹到，簡單來說，就是「設定命令別名」，通常用於慣用指令特別長的情況，或是增設預設屬性在一些慣用指令，避免發生誤刪等憾事。

> 詳細可以參考鳥哥的文章：[第十章、認識與學習BASH](https://linux.vbird.org/linux_basic/mandrake9/0320bash.php)

以下正文開始！

---

[toc]

前幾天，我和同事們進行一次討論，內容是關於「工程師都在終端機上設置什麼樣的 alias？」，因此我試著從 GitHub 上的 **1000 個 Repository** 程式碼中進行調查。

2019/04/10 根據評論進行微幅修改。感謝所有留下評論的人。
2019/04/11 嘗試寫了這篇文章： [常用的 vimrc 設置排名](https://qiita.com/reireias/items/230c77b3ff5575832654)
2019/04/15 也寫了插件版本：[最常用的 vim 插件 top20](https://qiita.com/reireias/items/5364dcaada1a5b88a206)

## 什麼是 alias

根據 wikipedia：

> 在 UNIX 等系統中，註冊指令的替代名稱。也就是指令的別名。

每次都要輸入冗長的指令，或輸入經常使用的選項，感覺很麻煩對吧？
透過在終端機的設定檔中編寫 alias，即可定義指令的別名。

## 調査方法

- 使用 GitHub API
- 依照星星數排序，選出標有 `dotfiles` 主題標籤的 Repository 前 1000 個
- 在 Repository 中搜索名稱為 `.bashrc`、`.bash_profile`、`.zshrc`、`.zsh_profile` 的檔案
    - 開頭有無句點均可
- 從檔案中提取包含 `alias` 的行數
- 共有 **1602 個檔案**符合條件

用來執行 API 的 [Source Code](https://github.com/reireias/dotseeker)

## 結果

我將調查結果分別依照「出現頻率」和「字母順序」列在 gist 中。

### 依出現頻率排序

+ [reireias/alias_ranking.md](https://gist.github.com/reireias/b986af3382d41c962ca6e8a78664c651)

### 依字母排序

+ [reireias/alias.md](https://gist.github.com/reireias/253ba410244e999a15002efb17311d34)

## 介紹

當初雖然想以排名的形式撰寫這篇文章，但只根據出現次數來排名感覺不太有趣，因此決定以分組結果和較被關注的 alias 進行介紹。

## ls 系

在出現次數方面，這個系列的排名相當高。

嗯，這結果準沒錯。

```bash
alias ls='ls --color=auto'
alias ls='ls -G'
alias ll='ls -alF'
alias ll='ls -lh'
alias ll='ls -l'
alias la='ls -A'
alias la='ls -a'
alias l='ls -CF'
# 也有這種
alias l='clear && ll'
alias l='clear && ls'
```

## cd 系列

目錄移動系列的相關操作如下，有許多指令可用來快速移動到常用目錄：

```bash
# 和常用目錄的字母首結合使用
alias abc='cd ~/aaa/bbb/ccc'

# 即使都是 'd'，也可能代表各種路徑
alias d='cd ~/.dotfiles'
alias d='cd ~/Desktop'
alias d='cd ~/Documents/Dropbox'
alias d='cd ~/Dropbox'
```

意外地大家都有定義這樣的別名。

使用數字來表示的方法似乎非常方便。

```bash
# 用點的數目表示
alias ..='cd ..'
alias ...='cd ../..'
alias ....='cd ../../..'

# 用數字表示
alias ..2='cd ../..'
alias ..3='cd ../../..'
```

## git 系列

將 git 指令依照使用多寡排序結果如下，我也有設定幾乎相同的 alias：

```bash
alias g='git'
alias ga='git add'
alias gd='git diff'
alias gs='git status'
alias gp='git push'
alias gb='git branch'
alias gst='git status'
alias gco='git checkout'
alias gf='git fetch'
alias gc='git commit'
```

## dotfiles 相關

接著介紹有關設定 alias 的 dotfiles（點文件，指各種程式的配置文件）相關指令。

編輯系列感覺相當方便，之後也來設定看看吧。

```bash
# 縮寫因人而異
alias d='/path/to/dotfiles'
alias dot='/path/to/dotfiles'
alias dotfiles='/path/to/dotfiles'
# 編輯系列
alias zshrc='vi /path/to/dotfiles/.zshrc'
alias zshconfig='vi /path/to/dotfiles/.zshrc'
```

## apt 系列

主要是針對 ubuntu 的設定。

```bash
# apt
alias agi='sudo apt install'
alias agr='sudo apt remove'
alias agu='sudo apt update'

# apt-get
alias ag='sudo apt-get'
alias agi='sudo apt-get install'
alias agr='sudo apt-get remove'
alias agu='sudo apt-get update'
```

順帶一提，使用 `apt` 指令比 `apt-get` 更好。

可參考：[「apt-get」已過時？使用新的「apt」指令進行 Ubuntu 套件管理](https://linuxfan.info/package-management-ubuntu)

## bundle 系列

這是 Ruby on Rails 中熟悉的 `bundle`。

這裡分成幾種流派。

```bash
alias b='bundle'
alias be='bundle exec'
alias bx='bundle exec'
alias bi='bundle install'
alias bo='bundle outdated'
alias bu='bundle update'
alias rc='bundle exec rails c'
```

## top 系列

意外と定義されていた系その2。

`cpu`や`mem`は忘れっぽい人にはいいかもしれないです。

出奇不意地定義了第二類。對於健忘的人來說，`cpu`和`mem`可能很有用。

```bash
# 人それぞれ
alias top='htop'
alias top='gtop'
alias top='vtop'
alias top='gotop'
# 別名
alias mem='top -o rsize'
alias cpu='top -o cpu'
```

## 安全策略

- 指令加上 `-interactive`（`-i`）參數時，將會在發生覆寫時以互動形式詢問。

```bash
alias cp='cp -i'
alias mv='mv -i'
alias rm='rm -i'
```

## 宗教戰爭系列

使用某些 alias 也可能被視為公布宣戰。

```bash
# 對異教徒的攻撃
alias atom='code'
alias v='code'
alias emacs='vi'
# 激烈的 edit 之爭
alias ed='atom .'
alias ed='emacs --daemon'
alias ed='vim'
alias edit="emacs -nw"
alias edit='subl'
alias edit='subl3'
alias edit='vim'
```

## 一字別名系列

可能有些激進，但熟悉後感覺很容易使用。

由於篇幅太長，僅附上提供參考或有趣的部分。

```bash
# a
alias a='alias'
alias a='ansible'
alias a='apt'
alias a='apt-get'
alias a='atom'

# b
alias b='brew'
alias b='bundle exec'
alias b='bundle'
alias b='bundler'
alias b='cd ..'

# c
alias c='curl'
alias c='cd'
alias c='clear'
alias c='cat'
alias c='rails console'
alias c='pbcopy' # 這感覺很方便

# d
alias d='cd ~/.dotfiles'
alias d='cd ~/Desktop'
alias d='cd ~/Dropbox'
alias d='date +%Y%m%d'
alias d='docker' # 這個有在使用
alias d='du -h -d=1'
alias d='git diff'
alias d='less'   # display?
alias d='pwd'

# e
alias e='atom'
alias e='emacs'
alias e='emacsclient'
alias e='exit'  # 有點過激了吧？
alias e='vim'

# f
alias f='fg'
alias f='file'
alias f='find . -name'
alias f='finger'
alias f='fuck'
alias f='open -a Finder ./'

# g
alias g='git status'
alias g='git' # 一定會有的之 1
alias g='googleit' # google
alias g='googler'  # google
alias g='grep --color=auto'
alias g='grep' # 一定會有的之 2

# h
alias h='cd ~' # home
alias h='git reset HEAD' # head
alias h='heroku'
alias h='history | grep'
alias h='history'
alias h='tldr' # 這感覺也蠻方便的。help?

# i
alias i='sudo apt install --yes'

#j
alias j='jobs'
alias j='jump'

# k
alias k='kill -9'
alias k='kubectl' # 有在使用
alias k='kwrapper'
alias k='tree'    # 因為在 l 的旁邊嗎?

# l
# 大多為 ls 系列因此割愛

# m
alias m='cd ~/Music && ls -a' # music 的 m!!!
alias m='make'
alias m='man'
alias m='mkdir' # 就個人來說也是這個吧
alias m='rake db:migrate db:rollback && rake db:migrate db:test:prepare' # 感覺有點超過
alias m='mv'
alias m='mvn'

# n
alias n='git checkout -b' # new branch
alias n='nano'
alias n='npm run'
alias n='npm' # 實際上比 node 還要常使用？
alias n='nvim'
alias n='sudo netctl'
alias n='node'

# o
alias o='open' # 大多是這個的衍生

# p
alias p='cd ~/Documents/projects'
alias p='cd ~/Dropbox/Projects'
alias p='cd ~/Pictures && ls -a'
alias p='cd ~/Projects'
alias p='ping' # 意外的激戰區？
alias p='popd' # 和 zsh 的 AUTO_PUSHD 是一組的？
alias p='pwd'
alias p='python'
alias p='python3'
alias p='pacman' # 不是 game 唷

# q
alias q='exit' # 幾乎只有這個

# r
alias r='cd / && ls -a' # root 的 r
alias r='rails' # r 對於 rails 開發者可能會感到迷惘?
alias r='rake'
alias r='ranger'
alias r='rgrep'
alias r='rm -i'
alias r='rspec'
alias r='screen -D -R'
alias r='source ~/.zshrc' # reload?
alias r='radian'

# s
alias s='cd ~/src'
alias s='git status'
alias s='ls' # 避免錯誤
alias s='screen'
alias s='spring'
alias s='ssh -l root'
alias s='ssh'
alias s='sudo su'
alias s='sudo'
alias s='svn'

# t
alias t='date +"%H%M%S"' # time
alias t='telnet'
alias t='terraform'
alias t='tig'
alias t='tmux -2'
alias t='tmux attach'
alias t='tmux new-session -A -s main'
alias t='tmux'
alias t='tree -C'
alias t='tree -Cfh'
alias t='tree -I "node_modules"' # 感覺是我的？
alias t='tree -a --ignore ".git|node_modules|bower_components|.DS_Store" -l 3' # 強化版

# u
alias u='cd ..' # up

# v
alias v='code' # VSCode
alias v='vagrant'
# vim 的一族
alias v='mvim'
alias v='nvim'
alias v='vi'
alias v='vim'

# w 沒什麼特別

# x
alias x='exit'
alias x='screen -A -x'
alias x='startx' # IBM?
alias x='/mnt/c/Windows/explorer.exe' # 是 cygwin 嗎?

# y
alias y='yarn' # 來使用這個吧
alias y='yaourt' # ArcLinux

# z
alias z='zathura' # 好像是 PDF Viewer
```

## 其他

```bash
# 雖然很短...
alias _='sudo'

# 可能是參數很難記的情況？
alias allps='ps aux'

# 當前目錄的 path 複製到剪貼簿(cpwd, copypath 等)
alias pwdc='pwd | tr -d "\n" | pbcopy'
```

## 番外編

### global alias 全域別名

- zsh 功能
- 只在指令開頭有效，但使用定義帶有 `g` 的參數時，也可以在指令中途展開
- 常用於 pipe 等經常呼叫的指令

```bash
# 有幾個感覺蠻方便的
alias -g A='| awk'
alias -g C='| pbcopy' # copy
alias -g C='| wc -l'  # count
alias -g G='| grep --color=auto' # 總是會有
alias -g H='| head'   # 當然 tail 也是
alias -g L='| less -R'
alias -g X='| xargs'
```

### suffix alias 後綴別名

- zsh 的功能
- 根據指令的結尾執行相應操作

```bash
alias -s gz='tar -xzvf' # 可用 ./hoge.tar.gz 展開
alias -s html='open' # ./index.html 可在瀏覽器開啟
alias -s {mp3,mp4,wav,mkv,m4v,m4a,wmv,avi,mpeg,mpg,vob,mov,rm}='mplayer' # 也可以這麼定義
```

## 感想

- 很少 aws 系列的別名
    - 在 CLI 感覺這種 sub command 結構相當理想？
    - 或因為有自動補完，所以不需要 alias？
- Docker 和 kubectl 的部分比預期中少
- 也學到許多不熟悉的指令
