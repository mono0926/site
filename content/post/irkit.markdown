---
layout: post
title: "IRKitで遊び始めた〜とりあえずTerminalで操作〜"
date: 2014-05-05
comments: true
tags: [irkit, nodejs]
categories: [programming]
---

冬場忙しかったりで既存アプリで部屋のリモコン登録する程度しかいじれてなかったけど、最近ようやく落ち着いてきたので、[IRKit](http://www.amazon.co.jp/gp/product/B00H91KK26/ref=as_li_ss_tl?ie=UTF8&camp=247&creative=7399&creativeASIN=B00H91KK26&linkCode=as2&tag=mono0926-22)で遊んでみる(　´･‿･｀)

## セットアップ

[IRKit - Open Source WiFi Connected Infrared Remote Controller](http://getirkit.com/)を参考に、諸々設定。

```
# dns-sdコマンドで、IRKitのインスタンス名取得。
Pro:b4 mono$ dns-sd -B _irkit._tcp
Browsing for _irkit._tcp
DATE: ---Mon 05 May 2014---
14:41:16.669  ...STARTING...
Timestamp     A/R    Flags  if Domain               Service Type         Instance Name
14:41:16.880  Add        2   4 local.               _irkit._tcp.         iRKitA2C4
```

<!-- more -->

```
# インスタンス名から、IPアドレス取得
Pro:b4 mono$ dns-sd -G v4 irkita2c4.local
DATE: ---Mon 05 May 2014---
14:41:43.565  ...STARTING...
Timestamp     A/R Flags if Hostname                               Address                                      TTL
14:41:43.566  Add     2  4 irkita2c4.local.                       192.168.0.4                                  10
```

```
# IPアドレスからMACアドレスを調べる(もっとスマートなやり方ある？)
# とりあえずping
Pro:~ mono$ ping 192.168.0.4
PING 192.168.0.4 (192.168.0.4): 56 data bytes
64 bytes from 192.168.0.4: icmp_seq=0 ttl=255 time=3.958 ms
# arpで確認
Pro:~ mono$ arp -a
? (192.168.0.4) at 20:f8:5e:a6:a2:c4 on en0 ifscope [ethernet]
```

ルーターの設定で、固定IPを今さらながら割り当ててみる。
これで、家の中では安心して```192.168.0.4```でアクセス出来るようになった（´-ω-｀）


## Terminalから操作

普通にリモコンを操作して、その赤外線の範囲内にIRKitが入っていると、青いライトが点滅して、赤外線の信号を取得したことを示してくれる。

そこで、curlすると、その信号が分かる。
うちのNECのLEDシーリングライトのオンオフボタンを押した後だとこんな感じ。

```
Pro:~ mono$ curl -i http://192.168.0.4/messages
HTTP/1.0 200 OK
Access-Control-Allow-Origin: *
Server: IRKit/1.3.5.0.gce6ac15
Content-Type: text/plain

{"format":"raw","freq":38,"data":[17421,9061,935,1232,1037,3458,1037,1232,935,1232,935,1232,1037,1190,1037,1190,1037,3458,1037,3458,1037,1037,1037,3458,1037,3458,1037,1150,1037,3341,1073,3341,1073,1232,935,3458,935,3458,935,1232,1037,3341,935,1190,1073,3458,935,1190,1002,3458,1073,1073,1073,1190,1037,3458,1037,1190,1190,3228,968,1190,1073,3341,1073,1190,1002]}
```

これをPOSTすれば、リモコンオンオフボタンと同じ信号をIRKitが発行してくれる。
```
curl -i http://192.168.0.4/messages -d '{"format":"raw","freq":38,"data":[17421,9061,1037,1232,935,3458,935,1190,1073,1190,1073,1190,1190,1190,1073,1190,935,3458,1037,3341,1037,1190,935,3458,1002,3458,1002,1111,1111,3341,968,3458,968,1150,1150,3458,1037,3341,1037,1275,1002,3458,1002,1190,1037,3341,1037,1150,1150,3341,1037,1190,935,1275,935,3458,1037,1190,1002,3458,1037,1232,935,3458,1111,1111,1111]}'
```

つまり、これをaliasなりシェルスクリプトにしておけば、もうそれだけでキーボードでライトのオンオフが出来るようになる。

楽ちん過ぎる、素晴らしい（´-ω-｀）


ちなみに、うちではこんな風に部屋の真ん中あたりの壁に、両面テープ付けて配置してる。これでも、受信感度の悪い一部機器は反応しなかったりで悩み中。
その機器は、添付のリモコンでもけっこう近くで方向もけっこう合わせないと反応しないので、IRKitのせいではないのだけれど。

![irkit](/images/post/irkit.jpg)

8,000円切る価格で完成度高くて、色々弄りやすいの素晴らしい(　´･‿･｀)

<iframe src="http://rcm-fe.amazon-adsystem.com/e/cm?lt1=_blank&bc1=000000&IS2=1&bg1=FFFFFF&fc1=000000&lc1=0000FF&t=mono0926-22&o=9&p=8&l=as4&m=amazon&f=ifr&ref=ss_til&asins=B00H91KK26" style="width:120px;height:240px;" scrolling="no" marginwidth="0" marginheight="0" frameborder="0"></iframe>


リモコンが付いていないサーキュレーターとかは、この、コンセントのオンオフをリモコンで切り替えられるやつを買おうかな（´-ω-｀）

<iframe src="http://rcm-fe.amazon-adsystem.com/e/cm?lt1=_blank&bc1=000000&IS2=1&bg1=FFFFFF&fc1=000000&lc1=0000FF&t=mono0926-22&o=9&p=8&l=as4&m=amazon&f=ifr&ref=ss_til&asins=B0013L6ACM" style="width:120px;height:240px;" scrolling="no" marginwidth="0" marginheight="0" frameborder="0"></iframe>


外からアクセス出来るようにしたり、WEBアプリやiPhoneアプリでもっと便利にしていきたいところ(　´･‿･｀)
