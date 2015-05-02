---
layout: post
title: "iTunesの動画や音楽の再生スピードを変える方法"
date: 2014-06-11
comments: true
categories: [iTunes, Automator, AppleScript, OSX]
categories: [programming]
---

iPhoneのPodcastアプリでは再生スピードをコントロール出来て便利なのに、iTunesではその機能が無いので、AppleScriptなど使って出来るようにしてみた。
本当はiTunesに閉じて実現したいところだけど、それはちょっと難しそう。

## QuickTime Player 7のインストール

<!-- more -->

新しめのOSXに標準インストールされているQuickTimeはかっこいいけど機能がしょぼいので、再生スピードを変えるにはQuickTime Player 7をインストールする必要がある。

幸いまだ[QuickTime Player 7](http://support.apple.com/kb/DL923?viewlocale=ja_JP)からダウンロード出来る。

> QuickTim 7 は、 Snow Leopard および OS X Lion 上で QTVR、対話型の QuickTime ムービー、MIDI などの古いメディアフォーマットをサポートしています。また、QuickTime Pro の機能を有効にするための QuickTime 7 Pro の登録コードを使用できます。

とりあえずQucikTime 7をインストールして、「Show A/V Control」(Command + K)で再生スピードなどコントロール出来るウインドウが開くので、機能的にはここまでで完結。

## Automatorでアプリ化

上記までだと、一々ファイルをFinderで開いて、QuickTime Player 7で起動するという手順が必要なので、Automatorを使って省力化してみる。

```
tell application "iTunes"
	pause
	--iTunesで選択中・再生中のファイルおよびその再生位置を保持
	set my_track to location of selection
	set my_seconds to player position
end tell
tell application "QuickTime Player 7"
	open my_track
	set my_movie to first document
	set ts to time scale of my_movie
	--とりあえず1.5倍に
	set rate of my_movie to 1.5
end tell
```

これをアプリとして保存してDockなどの配置しておけば、iTunesで曲を選択中あるいは再生中の状態で、実行するとQuick Time 7が起動して、その曲を1.5倍速再生してくれる。アプリ形式だと、倍速の数字を指定するパスが無いが、「Show A/V Control」ウインドウを開けば一応あとから変更可能。

[GitHub](https://github.com/mono0926/AppleScript)の[ChangeSpeed](https://github.com/mono0926/AppleScript/raw/master/ChangeSpeed.zip)からダウンロードできます。

## AlfredのWorkflow化

Automatorでアプリ化の方法だと、Dockクリックしたりが面倒なのと、倍速の数字を与えられないので、それをAlfredのWorkflowで解消。
コードとしては、上記のものに、Alfredのオプション引数を与えるようにした(無指定の場合は同じく1.5倍速)程度でほとんどそのまま。
AppleScriptを実行するWorkflowを新規作成するだけ。
個人的にはこっちを使おうかな。

[GitHub](https://github.com/mono0926/AlfredWorkflow)の[ChangeITunesSpeed.alfredworkflow](https://github.com/mono0926/AlfredWorkflow/raw/master/changeSpeed/ChangeITunesSpeed.alfredworkflow)からダウンロード出来ます。

今まで出来なくて不便に感じていたMac上での可変速再生が実現して、満足（´-ω-｀）


YosemiteでJavaScriptでAppleScript書けるようになったので、リリースしたら書き換えたい(　´･‿･｀)
