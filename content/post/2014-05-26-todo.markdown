---
layout: post
title: "NodeJS + Express + Stylus + Jade + AngularJS + Redisなどなどで、簡単なTODOアプリ"
date: 2014-05-26
comments: true
categories: NodeJS Express Stylus Jade AngularJS Redis
---

NodeJS + Express + Stylus + Jade + AngularJS + Redisなどなどで、[簡単なTODOアプリ](http://ice-me.herokuapp.com/todos)作った。

[TypeScriptリファレンス Ver.1.0対応](http://www.amazon.co.jp/gp/product/484433588X/ref=as_li_ss_tl?ie=UTF8&camp=247&creative=7399&creativeASIN=484433588X&linkCode=as2&tag=mono0926-22)のサンプルを参考に、アレンジした感じ(オリジナルはSQLiteなど使用)。

Redisでのデータの持ち方は[ケーススタディ — redis 2.0.3 documentation](http://redis.shibu.jp/tutorial/)である程度分かったけど、なかなか迷うところや困るところも多いので、Redis入門読んでじっくり勉強中。
[TODOアプリ](http://ice-me.herokuapp.com/todos)では、なんとか動作自体は出来たけど、ちょっとしっくり来ないところもあったり。

<a href="http://www.amazon.co.jp/gp/product/B00HSC64P8/ref=as_li_ss_il?ie=UTF8&camp=247&creative=7399&creativeASIN=B00HSC64P8&linkCode=as2&tag=mono0926-22"><img border="0" src="http://ws-fe.amazon-adsystem.com/widgets/q?_encoding=UTF8&ASIN=B00HSC64P8&Format=_SL160_&ID=AsinImage&MarketPlace=JP&ServiceVersion=20070822&WS=1&tag=mono0926-22" ></a><img src="http://ir-jp.amazon-adsystem.com/e/ir?t=mono0926-22&l=as2&o=9&a=B00HSC64P8" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" />

「Redis入門」というタイトルだけど、原書は[Redis in Action](http://www.amazon.com/gp/product/1617290858/ref=as_li_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=1617290858&linkCode=as2&tag=mono0926-20&linkId=TTS6QNHCUFJDJESI)なだけあって、けっこう歯ごたえのある内容。一通り理解して手を動かせば、RedisやKVSのパラダイムに慣れられそう。


サーバーサイドは外部モジュール使ってるけど(`import xxx = require('yyy')`形式)、クライアント側は内部モジュール形式で書いて手動で下記を実行して連結しているのも微妙なので、改善したい（´-ω-｀）他はWebStormで普通に実行したり、herokuへのデプロイはGitのPUSHで出来て楽なのだけれど（´-ω-｀）
```
tsc @compile.tscparams
```

AngularJSとJadeのおかげで、HTML部分がすごくクリーンになっているのはとても良い感じ(　´･‿･｀)

<script src="https://gist.github.com/mono0926/3ee7f4c5016e88a6c6a3.js"></script>
