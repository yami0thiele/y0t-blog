+++
title = 'Vimium KeyBinding'
date = 2024-12-14T22:13:00+09:00
tags = ["意味なし"]
categories = ["デジタル"]
draft = false
+++

ブラウザの操作をできるだけキーボードで済ませるために [philc/vimium](https://github.com/philc/vimium) を Vivaldi に突っ込んでみました。
VimよりはEmacsのキーバインドの方が覚えているので以下の通りカスタマイズしてみています。

[dmgerman/vimium-emacs.md](https://gist.github.com/dmgerman/6f0e5f9ffc6484dfaf53) を参考にしています。Vivaldiの設定でショートカットを変更できるので、Commandキーを普通に使用しています。

```sh
# Vivium の全てのデフォルトキーバインディングを解除する。
# キーバインディングは全てこのファイルで定義する。
#
unmapAll

# note:
#  Vivaldi側のショートカットのうち、<m-*> のショートカットをいくつか削除している。
#  <a-*> を使えるよう、Vimiumを設定する。
#

#
# ヘルプ
#
map <c-h> showHelp

# 
# カーソル移動系 1
#
map <c-n> scrollDown
map <c-p> scrollUp
map <c-b> scrollLeft
map <c-f> scrollRight
map <c-a> scrollToLeft
map <c-e> scrollToRight
map <m-<> scrollToTop
map <m->> scrollToBottom
map <c-v> scrollFullPageDown
map <m-v> scrollFullPageUp

#
# カーソル移動系 2
#
map <c-s> enterFindMode
map <c-S> performFind
map <c-r> performBackwardsFind
map <c-R> performBackwardsFind

#
# ファイル・バッファ操作 => タブに関する操作
#
map <c-x>i createTab
map <c-x>k removeTab
map <c-x>b nextTab
map <c-x><left> previousTab
map <c-x><right> nextTab
map <c-x><c-b> Vomnibar.activateTabSelection
map <c-x><c-f> Vomnibar.activateInNewTab
map <c-x><c-v> reload

#
# その他のブラウザ操作
#
map <a-b> goBack
map <a-f> goForward
map <a-p> togglePinTab
map <a-u> copyCurrentUrl
map <a-o> openCopiedUrlInCurrentTab
map <a-O> openCopiedUrlInNewTab
map <a-i> focusInput
map <a-r> restoreTab

#
# Vimium
#
map <c-x><a-f> LinkHints.activateMode
map <c-x><a-F> LinkHints.activateModeToOpenInNewForegroundTab

#
# 上書きしたキーボードショートカットのメモ
#       Key            Vivaldi                   Custom                 Move-to
#       <c-p>          Print                     scrollUp               None                   
#       <c-r>          Reload                    performBackwardsFind   <c-x><c-v>
#       <c-R>          Force Reload              None                   None
#       <c-f>          Search In Page            scrollRight            <c-s>
#       <c-s>          Save as                   search                 None
#  
```

ゆくゆくはemacsそれ自体を覚えていきたいところです。

以上！
