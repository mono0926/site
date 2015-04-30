---
layout: post
title: "OSX 10.10(Yosemite)やiOS 8にアップデートして困ったこと"
date: 2014-06-04
comments: true
categories: yosemite ios8
---

例のごとく、何も考えずにメインマシンをOSX 10.10(Yosemite)・iOS 8にしてしまいましたが、いくつか細かいトラブルが。
でも概ね問題無く使えていて満足（´-ω-｀）

NDAに気をつけつつ困ったことや解決法など(　´･‿･｀)


## OSX 10.10(Yosemite)にアップデートして困ったこと

### [PCKeyboardHack](https://github.com/tekezo/PCKeyboardHack)が起動しない

#### 【追記】[PCKeyboardHack-10.7.0](https://pqrs.org/macosx/keyremap4macbook/files/PCKeyboardHack-10.7.0.dmg)がリリースされました！

去年もこれで困ったことを思い出しました。
Realforceでスペースの両隣のキーでの日本語入力切り替えが効かずにとても不便です。
Apple純正キーボードだと問題ないですが。

と思いつつ、Issuesを覗いたら、[Add 10.10 support #31](https://github.com/tekezo/PCKeyboardHack/issues/31)ですんなり解決(　´･‿･｀)

何も考えずこれを打ったら問題無く動くように。

```
sudo /sbin/kextload '/Applications/PCKeyboardHack.app/Contents/Library/PCKeyboardHack.10.9.signed.kext'
```

### [BetterTouchTool](http://blog.boastr.net/)が起動しない

<!-- more -->

#### 【追記】[Yosemite対応版のBetterTouchTool](http://boastr.net/releases/btt0.997.zip)がダウンロード出来るようになりました！

これも[OS X 10.10 Yosemite » BetterTouchTool, BetterSnapTool & SecondBar](http://blog.boastr.net/os-x-10-10-yosemite/)にすでに記事が上がっていて、現時点ではまだダウンロード出来ないけどまもなく対応版がリリースされる模様。

> BetterTouchTool crashes on startup, but I already identified the issue and will fix it tomorrow.


[Alfred](http://www.alfredapp.com/)も、Keynotes直後にすぐこんなポスト投稿するなど、どこも動きが速くて素晴らしい(　´･‿･｀)

<blockquote class="twitter-tweet" lang="en"><p>Calm down everybody, Alfred isn’t going anywhere (but up) in OS X Yosemite :) <a href="http://t.co/wh1mMnxrkt">http://t.co/wh1mMnxrkt</a></p>&mdash; Alfred App (@alfredapp) <a href="https://twitter.com/alfredapp/statuses/473517537939185665">June 2, 2014</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>


ただ、Yosemiteはインストールにすごく時間がかかって、残り4分で数十分固まったようになった(大量のファイルコピーなどしている模様・同様の報告多数)ので、失敗したかと思いけっこう怖かったです(　´･‿･｀)

### Homebrewが動かなくなってしまった

```
/usr/local/bin/brew: /usr/local/Library/brew.rb: /System/Library/Frameworks/Ruby.framework/Versions/1.8/usr/bin/ruby: bad interpreter: No such file or directory
```

`brew doctor`さえ動かない状態。

ログに書いてあるとおりSystemのRubyのバージョンが変わったのかーと思いつつ、`/usr/local/Library/brew.rb`の以下の`1.8`の箇所を`2.0`にすれば直った。

```
#!/System/Library/Frameworks/Ruby.framework/Versions/1.8/usr/bin/ruby -W0
```

しかし、この編集後に`brew update`をすると、ローカルの変更が原因でPULL出来ないと怒られる（´-ω-｀）
とはいえ、この編集をしないとbrewコマンド自体効かないし…と困りつつ、`2.0`に編集して`brew update`するや否や`1.8`に戻せばPULLのタイミングでは変更無し状態になってうまくいった(　´･‿･｀)
ちょっと不便だけど、そんなにする操作じゃないし、こんな運用でしばらく我慢しよう(　´･‿･｀)

### ~~Sleepでクラッシュ~~Sleep時にクラッシュしたのは偶然だったっぽい

まだきちんと確かめてないけど、Sleep後に起こそうとしたら再起動がかかって、こんなログが出てた。
Sleep後だったのは偶然かも。

```
panic(cpu 7 caller 0xffffff801600f06c): "TLB invalidation IPI timeout: " "CPU(s) failed to respond to interrupts, unresponsive CPU bitmap: 0x3d, NMIPI acks: orig: 0x0, now: 0x0"@/SourceCache/xnu/xnu-2738.0.0.0.5/osfmk/x86_64/pmap.c:2470
```

## iOS 8にアップデートして困ったこと

### iPhoneで[1Password](https://agilebits.com/onepassword)が同期できなくなってクラッシュする

#### 【追記】[iOS8で1Passwordが使えるようになった - monoHub](http://mono0926.com/blog/2014/06/13/password/)で解決（｀・ω・´）

けっこう依存度が高いので、これけっこう困る(　´･‿･｀)
Beta版使っているのが悪いししばらく我慢かなあと思っていたら、すでに問題認識しているらしく、わりと前向きな対応してもらえそうな雰囲気(　´･‿･｀)
ついでに秋くらいに指紋認証でアンロックも実装してくれることを期待(　´･‿･｀)

<blockquote class="twitter-tweet" lang="en"><p>iOS 8 folks, there sure are a lot of you using the beta! I’m a bit…broken. Sorry. My devs are working on it!&#10;&#10;[…]</p>&mdash; 1Password Beta (@1PasswordBeta) <a href="https://twitter.com/1PasswordBeta/statuses/473747191228399616">June 3, 2014</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

### LINEスタンプが買えない・使えない

買おうとするとエラーになってしまうし、使おうとすると進捗ダイアログが終わらない（´-ω-｀）けっこう困る（´-ω-｀）
[申請中の個人スタンプ](http://a.scn.jp/s/0VrEMIHAB)も買えないし使えなくなりそう（´・д・｀）
これに関しては調べても困っている人はいても解決手段は現状無さそう。

とりあえずパソコン版でしのごう（´-ω-｀）Yosemite上のLINEは問題無いし。

### Tweetbot

UI周りかなりがんばってるのが裏目に出て、動作がボロボロ。
特に、URLをPocketに保存出来ないのがつらたん。
困っている人が他にもいるという程度しか情報無かったので、とりあえずEchofonでしのごう(　´･‿･｀)


iOS 8については、あとはクラッシュ率が高いとかですかね。
NDAで細かいところは書けないけど、使用感も特に大きな変化無く(　´･‿･｀)


というわけで、ちょくちょく問題はありつつ、最新の環境楽しめているので、アップデートして良かった(　´･‿･｀)
趣味みたいなもののあので、仮想環境とか検証機とかで試しても個人的にはあまり意味がなく、やはり普段マシンで楽しんでこそと思う(　´･‿･｀)
