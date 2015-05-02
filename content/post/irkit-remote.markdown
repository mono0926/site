---
layout: post
title: "IRKitに外からアクセス出来るようにした"
date: 2014-05-05
comments: true
tags: [irkit]
categories: [programming]
---

前回の[IRKitで遊び始めた〜とりあえずTerminalで操作〜 - monoHub](http://mono0926.com/blog/2014/05/05/irkit/)の続き。

前回触った[IRKit Device HTTP API](http://getirkit.com/#IRKit-Device-API)は同じWiFi内から操作するためのもので、外からアクセスするときは[IRKit Internet HTTP API](http://getirkit.com/#IRKit-Internet-API)を叩くことになる。

## IRKit Internet HTTP APIを叩けるように準備

まずは、clienttokenを取得。

```
Pro:~ mono$ curl -i http://192.168.0.4/keys -d ''
HTTP/1.0 200 OK
Access-Control-Allow-Origin: *
Server: IRKit/1.3.5.0.gce6ac15
Content-Type: text/plain

{"clienttoken":"**************************"} #伏せています
```

取得したclienttokenを元に、deviceidとclientkeyを取得。

<!-- more -->

```
Pro:~ mono$ curl -i -d "clienttoken=**************************" "https://api.getirkit.com/1/keys"
HTTP/1.1 200 OK
Server: ngx_openresty
Date: Mon, 05 May 2014 06:44:32 GMT
Content-Type: application/json; charset=utf-8
Content-Length: 94
Connection: keep-alive
Access-Control-Allow-Origin: *
Access-Control-Allow-Headers: X-Requested-With
X-Content-Type-Options: nosniff

{"deviceid":"XXXXXXXXXXXXXXXXXXXXXX","clientkey":"YYYYYYYYYYYYYYYYYYYYY"} #伏せています
```

## Internet HTTP APIを使ってみる

deviceid・clientkey・家のライトのオンオフ信号をhttps://api.getirkit.com/1/messages にポストすると、ちゃんと反応した、素晴らしい(　´･‿･｀)

```
curl -i "https://api.getirkit.com/1/messages" \
     -d 'clientkey=YYYYYYYYYYYYYYYYYYYYY' \
     -d 'deviceid=XXXXXXXXXXXXXXXXXXXXXX' \
     -d 'message={"format":"raw","freq":38,"data":[17421,9061,1037,1232,935,3458,935,1190,1073,1190,1073,1190,1190,1190,1073,1190,935,3458,1037,3341,1037,1190,935,3458,1002,3458,1002,1111,1111,3341,968,3458,968,1150,1150,3458,1037,3341,1037,1275,1002,3458,1002,1190,1037,3341,1037,1150,1150,3341,1037,1190,935,1275,935,3458,1037,1190,1002,3458,1037,1232,935,3458,1111,1111,1111]}'
```

上記操作で、IRKitサーバーがIRKit端末にアクセス出来るようになって、認証すれば外部から操作出来るようになるって感じかなあ。
特に、deviceid・clientkeyは漏れるとまずいですね（´-ω-｀）

## ついでにapiKeyを取得

iPhoneアプリを作ったりするのに使う用のkeyを取得するAPIもあったので、ついでに叩いてみた。
入力したメールアドレスに確認メールが来て、無事にapiKeyゲット。

```
Pro:~ mono$ curl -i -d "email=xxxxxx@gmail.com" "https://api.getirkit.com/1/apps"
HTTP/1.1 200 OK
Server: ngx_openresty
Date: Mon, 05 May 2014 07:00:31 GMT
Content-Type: application/json; charset=utf-8
Content-Length: 92
Connection: keep-alive
Access-Control-Allow-Origin: *
Access-Control-Allow-Headers: X-Requested-With
X-Content-Type-Options: nosniff
```

このapiKitと[irkit/ios-sdk](https://github.com/irkit/ios-sdk)でiPhoneアプリ簡単に作れるみたいだけど、[irkit/ios-sdk](https://github.com/irkit/ios-sdk)とかでけっこう充分だったりするし、どうしよう（´-ω-｀）  
やるならiBeaconと組み合わせたいけど、手軽で安いのがまだない感じ（´-ω-｀）  
[Estimote Beacons — real world context for your apps](http://estimote.com/)は洗練されてる感じだけど、$99/3個と割高感が否めない（´-ω-｀）
