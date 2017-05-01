+++
comments = true
date = "2014-05-05"
tags = ["irkit", "nodejs"]
title = "Node.jsのIRKitライブラリあったから試してみた"

+++

せっかく[Node.js the Right Way: Practical, Server-Side JavaScript That Scales [Kindle Edition]](http://www.amazon.com/gp/product/B00HSO6YD8/ref=as_li_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=B00HSO6YD8&linkCode=as2&tag=mono0926-20&linkId=SIVQ46LXCW3PK3IO)でNode.jsを勉強したので、IRKitをNode.jsの勉強題材に出来ないかなと思って、とりあえずNode.jsのクライアントライブラリ無いかな？と探したらあったので、叩いてみた。

### [dameleon/node-irkit](https://github.com/dameleon/node-irkit)


元々IRKitのAPIがシンプルなので、あまりNode.jsを使う必然性感じないけど、まあ勉強に（´-ω-｀）

本1冊やったとはいえ、色々まだ不慣れなので、コード読解にも良いかも。
ドキュメントは無いものの、テストはちゃんと書かれていたので、それを参考に使ってみた。


まずはインストール。

```
npm install node-irkit
```

とりあえずlocalApiを使ってみた。
実行する度に、部屋の電気がオンオフされて煩わしいので、テストは違う信号でやろうと思ったなう（´-ω-｀）

```
const
    irkit = require('node-irkit'),
    localApi = irkit.getLocalApi("http://192.168.0.4"),
    myRoomLight = '{"format":"raw","freq":38,"data":[17421,9061,1037,1232,935,3458,935,1190,1073,1190,1073,1190,1190,1190,1073,1190,935,3458,1037,3341,1037,1190,935,3458,1002,3458,1002,1111,1111,3341,968,3458,968,1150,1150,3458,1037,3341,1037,1275,1002,3458,1002,1190,1037,3341,1037,1150,1150,3341,1037,1190,935,1275,935,3458,1037,1190,1002,3458,1037,1232,935,3458,1111,1111,1111]}',
    myRoomLightMessage = JSON.parse(myRoomLight);
localApi.postMessages(myRoomLightMessage, function(err, res) {
    console.log(res); //空
});
```
