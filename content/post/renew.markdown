+++
categories = ["プログラミング"]
comments = true
date = "2014-05-06"
layout = "post"
tags = ["osx"]
title = "OSXの開発環境を整えた"

+++

Node.jsで色々遊ぼうと思いつつ、開発環境がけっこう汚れていることに気づいたので、整理。
Node.jsのgenerator使いたくて、バージョン0.11系と0.10系をスイッチしたいなとか思ったのが発端。  
参考: [Node.jsのコールバック地獄をPromiseやGeneratorを使って解消する - HackerNews翻訳してみた](http://rdepf.hatenablog.jp/entry/2014/03/07/122337)

わりと`brew install XXX`で雑に各種環境インストールしてたので、これを気に色々直した。

## Homebrewアンインストール

ゴミが残るのいやだったので、[Uninstall Homebrew](https://gist.github.com/mxcl/1173223)でhomebrewをアンインストール。

<!-- more -->

## Brewfile導入

以下など見て便利そうだと思っていたので、Brewfile導入。

- [Mac OSX をクリーンインストールしてからの環境構築メモ - Shin x blog](http://www.1x1.jp/blog/2014/04/how-to-setup-application-on-osx.html)
- [「BrewfileでHomebrewパッケージを管理する」をやってみた - sonots:blog](http://blog.livedoor.jp/sonots/archives/35251881.html)
- [MacBook にインストールしているアプリやツールをメモする代わりに Brewfile を作った - present](http://tnakamura.hatenablog.com/entry/2014/04/29/113727)


これだけで一気にインストール出来てとても便利。

```
brew bundle
```

僕の：[Environment/OSX/Brewfile at master · mono0926/Environment](https://github.com/mono0926/Environment/blob/master/OSX/Brewfile)

今後も、Homebrewで何か新しくインストールするときメンテナンスしていくようにしよう。

## その他開発環境

`brew install XXX`で適当にインストールせずに、バージョンの切り替えが容易なようにした。
いくつか種類あったけど、基本後発のを導入してみた。

- Python: [yyuu/pyenv](https://github.com/yyuu/pyenv)
- Ruby: [sstephenson/rbenv](https://github.com/sstephenson/rbenv)
- Node.js: [creationix/nvm](https://github.com/creationix/nvm)
    - nvmはzshとの相性悪くて日本では[hokaccha/nodebrew](https://github.com/hokaccha/nodebrew)がけっこう人気っぽかったけど特に問題無かったのでnvmにした。

諸々雑なところがあるけど、[Environment/OSX at master · mono0926/Environment](https://github.com/mono0926/Environment/tree/master/OSX)でセットアップスクリプト管理。

## IDE導入

スクリプト系言語は、最近はわりとSublime Textで書いていたけど、やっぱり補完がもう少し聞いてくれないと厳しいので、なるべくIDE使うようにしようと思う。  
IDEに慣れるのもそこそこコストだけど、JetBrain系で統一すれば捗るかなと。  
今まではNetBeansかたまにEclipseだったけど、乗り換え。少しずつ慣れていこう（´-ω-｀）

- [WebStorm :: The smartest JavaScript IDE](http://www.jetbrains.com/webstorm/)
- [Ruby on Rails IDE :: JetBrains RubyMine](http://www.jetbrains.com/ruby/)
- [Python IDE & Django IDE for Web developers : JetBrains PyCharm](http://www.jetbrains.com/pycharm/)
    - CE版は無料
