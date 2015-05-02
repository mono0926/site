---
layout: post
title: "Octopressへの投稿やdeployをAlfredのWorkflowで"
date: 2013-07-07
comments: true
tags: [octopress, alfred]
categories: [programming]
---

今日初めてOctopressを触ったら、けっこう気に入ったので、さらに気軽に書ける環境を整えれば捗るのではと思い、AlfredのWorkflowを作ってみました。


```
# deploy用
OCTOPATH='/Documents/Git/Private/octopress'
cd ~/$OCTOPATH
rake gen_deploy
git add .
git commit -m "deployed via workflow."
git push
```

```
# 投稿用
OCTOPATH='/Documents/Git/Private/octopress'
cd ~/$OCTOPATH
OCTOPOST=$(rake new_post[$1]| grep -o 'source/_posts/.*')
open ~/$OCTOPATH/$OCTOPOST
```

すんなり出来るかと思いきや、これだけでは動かず、

> In my bash script I had to add some extras because Alfred runs the bash script in a subshell and in this subshell the rvm environment is not available by default.
[Alfred Workflow for Octopress](http://tooh.github.io/blog/2013/04/23/Alfred_workflow_for_Octopress/)

とある通り、下記のような設定をする必要があったようです。
かなりハマりました（´-ω-｀）
よく分からないけど、別ファイルにしたら動かないので、とりあえず全て冒頭にこれを挟みました（´-ω-｀）

<!-- more -->

```
# rv設定
if [[ -s "$HOME/.rvm/scripts/rvm" ]] ; then
	source "$HOME/.rvm/scripts/rvm"
fi
```

さらに一応previewコマンドも作成
```
if [[ -s "$HOME/.rvm/scripts/rvm" ]] ; then
	source "$HOME/.rvm/scripts/rvm"
fi
OCTOPATH='/Documents/Git/Private/octopress'

cd ~/$OCTOPATH
rake generate
# open in a browser
open http://localhost:4000/
rake preview
```

こちらはコマンドを実行するだけではウインドウが開かれずプロセスがゾンビ状態になってしまうので、Alfredで呼び出す時に
```
open -a Terminal.app preview.sh
```
と少しだけ工夫。

[Temikus/alfred-octopress](https://github.com/Temikus/alfred-octopress/blob/master/post.sh) など、同じようなもの作っている人もいたり。

とりあえず、これでいつでもランチャー起動して`post titleなど`と入力すると、記事が生成されて開かれて、書き終わったら`preview`で確認して、`deploy`実行すればサイトへの反映とレポジトリへのPushが行われる便利な環境が出来ました。
(Alfredのテーマもかっこよくして遊んでました。)

![post workflow](/images/post/post.png)

#### Octopress気に入ったけど…

Qiitaもよく見たらMarkdownでかなり使いやすそう。
色々ツールもあるし。

- [Kobito](http://kobito.qiita.com/)
  * Qiitaに投稿出来るクライアントアプリ。同時にGistにスニペット登録も可能。
- [GistBox](http://www.gistboxapp.com/)
  * Gist用Webアプリ。Chrome App版はネイティブっぽい操作感。

最近久しく何も書いてなかったけど、あまり脈絡の無い雑多メモなどはこちらで、技術系TipsはQiitaあたりにまとめる習慣付けたい（´・ω・｀）
