+++
comments = true
date = "2014-05-14"
layout = "post"
tags = ["angularjs", "jade", "stylus"]
title = "TypeScript・AngularJS・Jade・Stylusでサンプルコード"

+++

最近Web系の勉強してて、Node.js・Express・Redis・Herokuなどサーバーサイド周り弄ってたけど、そろそろフロントエンドもという感じで色々やってみた。

### [サンプル置いとく](http://ice-me.herokuapp.com/angular#/)

AngularJSはけっこうリッチなライブラリで、全部身につけるのはしばらくかかりそうだけど、今日主要な機能はざっくり書けるようになった感(　´･‿･｀)
[Vue.js](http://vuejs.org/)と迷ったけど、[borisyankov/DefinitelyTyped](https://github.com/borisyankov/DefinitelyTyped)にまだ無かったし、とりあえず今メジャーなAngularJSやっとこうか、という感じ。

JadeとStylusは記法いくつか覚えらればわりとサクサク書けて、気に入った。これ系いくつかあるけど、どれがいいんですかね。あまり比較検討せずに決めてしまった。


- AngularJS: MVW(Model-View-Whatever)フレームワークというらしい。Whatever=厳密に定義しない、みたいな意味らしい。JS・HTML周りのスパゲッティコード解消。MV*とかはともかく、とりあえずバインディング機構あるのが嬉しい。
- Jade: HTMLの簡易記法 + αの機能
- Stylus: SASS・LESSの後発版みたいな感じ？

<!-- more -->

## 資料

- [AngularJS使い方メモ - Qiita](http://qiita.com/opengl-8080/items/2fe0a20c314b1c824cc5)
- [AngularJS - お前のAngular.jsはもうMVCではない。と言われないためのTutorial - Qiita](http://qiita.com/icoxfog417/items/2ac773c33a8b34288551)
- [AngularJSのMVWパターンを理解する - Qiita](http://qiita.com/zoetro/items/a45dbc18bb2b22e944b2)
- [AngularJS: Developer Guide: Conceptual Overview](https://docs.angularjs.org/guide/concepts)
- [Node.js - Jadeの記法について（あまりまとまっていない） - Qiita](http://qiita.com/sasaplus1/items/189560f80cf337d40fdf)
- [Jade Template Syntax Documentation by Example](http://naltatis.github.io/jade-syntax-docs/)


一気に色々やると破綻しそうかと心配だったけど、意外とスムーズに出来たのは良かった。

AngularJS、[AngularJS使い方メモ - Qiita](http://qiita.com/opengl-8080/items/2fe0a20c314b1c824cc5)の「ページの一部に動的にテンプレートを読み込む」くらいまでで、まだシングルページアプリケーション周りの機能は終えてないから、また続きやろう（´-ω-｀）


## コード

<script src="https://gist.github.com/mono0926/30e00a6a26498eff5973.js"></script>

<script src="https://gist.github.com/mono0926/2e8b58d3003f1fcbfa1c.js"></script>

<script src="https://gist.github.com/mono0926/780a92e2fe8c7c80e80f.js"></script>
