+++
categories = ["programming"]
comments = true
date = "2013-07-25"
layout = "post"
tags = ["leap_motion"]
title = "Leap Motionが届いた"

+++

Leap Motionを買ってみた。  
多分1年ちょっと前に[指先を1/100ミリ単位で捉える3Dモーション入力機器 LEAP、70ドルで予約受付開始 (動画)](http://japanese.engadget.com/2012/05/21/1-100-3d-leap-70/)などの記事を見て、コンセプト動画なのか実動画像なのか知らないけど、すごいなーと思って放置してたけど、今週けっこう話題になってて、記事とか読んでたらいつの間にかポチってた感じ。

ハード的には、劣化版Kinect？とかも思ったけど、対象距離が近距離な[Kinect for Windows](http://www.amazon.co.jp/gp/product/B0074BN0VO/ref=as_li_ss_tl?ie=UTF8&camp=247&creative=7399&creativeASIN=B0074BN0VO&linkCode=as2&tag=mono0926-22)は少しお高いし、設置の制約あるし、とか思ってとりあえず今回はこっち。
KinectはごくたまにXboxで遊んだりと、なかなか好きなデバイス。

Leap Motionって何？とかどんなことできるの？とかについては下の動画見れば大体分かる。
<iframe width="560" height="315" src="//www.youtube.com/embed/3b4w749Tud8" frameborder="0" allowfullscreen></iframe>

<!-- more -->

### 届くまで

実は、いいなーと思いつつも購入をためらっていたけど、偶然[BetterTouchTool]()のアップデートが走ってリリース文章見ていたら、Leap Motionの文字があって、「おっ!」と思いそのまま買ってしまった感じ。
今見たら、[紹介ブログ](http://blog.boastr.net/?page_id=3023)があった。
元々愛用しているツールだけど、こういう早くて先進的な対応は好感度上がる。
OSもアプリもわりとリリース文には目を通している(利用者目線でも開発目線でも読んでいるとけっこう有用に思う)けど、良いきっかけになってよかった。

[この購入サイト](https://www.leapmotion.com/product)で購入。
PayPal決済でトータル1万円弱。カード決済用のトータル表示より安かったような(見間違えかも)。

入荷や発送の関係でしばらく待つかなーと思っていたら、翌朝発送しましたメールが来てびっくり。
[FedEx](http://www.fedex.com/us/)という郵送会社だった。
たまに海外購入はするけど、多分初めての利用。
翌々日に届くとのこと。お早い。

というわけで、一昨日の晩に頼んだLeap Motionが到着。


### 簡単なレビュー

詳細なレビューとかはすでにけっこうあるので、下記参照。

- [Leap Motion は本当に革新的なUIデバイスなのか? 本体レビューとその雑感【@maskin】](http://techwave.jp/archives/leap-motion-1st-review.html)
- [手と指の動きを感知して奥行きまで含めた立体的な操作ができる「Leap Motion」は一体何がすごいのかまとめ](http://gigazine.net/news/20130723-leap-motion-store-airspace-launched/)

#### 開封まで

シンプルな箱。

![leap1](/images/leap1.jpg)

本体とUSBケーブルとしょぼい冊子だけ。

![leap2](/images/leap2.jpg)

ガムくらいの大きさ。

![leap3](/images/leap3.jpg)

#### セットアップ

マニュアル無いから適当にググったら、[このセットアップサイト](https://www.leapmotion.com/setup)でドライバ&アプリをインストールするとのこと。(あとで見たらボール紙みたいなものにそのURL書いてあったけど)

そこにたどり着けばすごく簡単で、ぽちぽちっと適当にインストールしてチュートリアルで試用する感じ。

### どうやって使おう

とりあえずBetterTouchToolと組み合わせて、良い感じに普段使い出来ないか試してみてるところ。
人差し指をクルクルすると、音量上げ下げしたり、手を叩くとスリープするようにしたりして、意外と実用的に使えそう。

↓YouTubeにアップしてみた。

<iframe width="420" height="315" src="//www.youtube.com/embed/rFNnymc967w" frameborder="0" allowfullscreen></iframe>

セッティングはMagic Trackpadのジェスチャー登録するような感じでとても簡単。若干認識が微妙だけど、ハードウェア性能とソフトウェアとどっちのせいかは不明。現状でもそんなに悪くないし、今後のソフトウェア改良に期待は持てる感じはしてる。	


あと、[アプリストア「Airspace」](https://airspace.leapmotion.com/)とかのアプリで遊んでみようとも思うけど、ゲーム系はすぐ飽きちゃいそう…（´-ω-｀）


というわけでまだあまり弄れてないけど、これから色々遊んでみたり、開発にも手を出していきたいなと思ったり。

[開発リソース](https://www.leapmotion.com/developers)はけっこう整っている感。
これ系の開発は結構前にカメラ + OpenCVを少しやった程度だったりして、個人的にはけっこう苦労しそうだけど（´-ω-｀）

* SDK
* [Documentation](https://developer.leapmotion.com/docs)
  - C++
  - Java
  - Python
  - C#
  - JavaScript
  - Objective-C (この一覧には明記されていないけど対応してる)
* [Forums](https://developer.leapmotion.com/forums)
* [LeapMotion(YouTube)](https://www.youtube.com/user/leapmotion)
* [C#開発者から見たLeap Motion開発のファースト・インプレッション](http://www.buildinsider.net/small/leapmotionfirstimp/01)
* [Developing for Leap Motion in C# Tutorial (video, slides and code)](http://www.irisclasson.com/2013/05/02/developing-for-leap-motion-in-c-tutorial-video-slides-and-code/)
* [JavaScriptでLeapMotionアプリを作る方法](http://kray.jp/blog/leap-motion-javascript/)


#### Windows 8を操作しているデモ動画

なかなか操作の相性が良さそう。動画を見ただけだと実はタッチよりも快適？とか思ったり。

<iframe width="560" height="315" src="//www.youtube.com/embed/21LtA5-wiwU" frameborder="0" allowfullscreen></iframe>

#### Google Earthを操作する様子
<iframe width="560" height="315" src="//www.youtube.com/embed/RebX7YEn3GQ" frameborder="0" allowfullscreen></iframe>

しばらく遊べそうなおもちゃが手に入ってとても嬉しい（´-ω-｀）

とりあえず、直近の悩みは明日会社に持って行って、積極的に披露するか、色々ジェスチャーして気づかれるのを待つか(あるいは頭がおかしくなったと思われるか)どうしよう（´-ω-｀）
