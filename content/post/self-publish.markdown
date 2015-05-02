---
layout: post
title: "電子書籍自費出版系情報まとめ"
date: 2013-07-14
comments: true
categories: [kindle, self_publish, pandoc]
categories: [lifehack]
---

最近、電子書籍系のアプリ開発中で、色々調べています。
ちょっと情報が頭に乗り切らなくなってきたので、整理。

----------------
### ツール

#### [Kindlegen](http://www.amazon.com/gp/feature.html?ie=UTF8&docId=1000765211)

Amazon謹製の、HTMLやEPUB形式からMobi形式に変換するツール。
成果物は、MacなどのKindleアプリでも見られるし、[Kindle Previewer](http://www.amazon.com/gp/feature.html/ref=amb_link_359603222_5?ie=UTF8&docId=1000765261&pf_rd_m=ATVPDKIKX0DER&pf_rd_s=center-8&pf_rd_r=05Y1JB4SCG6HF48FKJFX&pf_rd_t=1401&pf_rd_p=1342416142&pf_rd_i=1000765211)で、各プラットフォームでの動作チェック可能。

クラス構造を一旦HTMLに落とし込んで、Mobi形式にエクスポートするところまでは出来たけど、いくつか警告が出てたりしてまだ対処出来ていない状態。
あと、ライセンス的にアプリのサーバー側で使ったりOKなのか気になる。

- リファレンスなど
  * [Amazon Kindle Publishing Guidelines](http://kindlegen.s3.amazonaws.com/AmazonKindlePublishingGuidelines.pdf)
    - 和訳：[Amazon Kindle パブリッシング・ガイドライン](http://kindlegen.s3.amazonaws.com/AmazonKindlePublishingGuidelines_JP.pdf)


#### [Pandoc](http://johnmacfarlane.net/pandoc/)

ドキュメント形式変換ツール。Markdown, HTMLなどからEPUB, PFDなどなどなど色々変換可能。
Linux, Mac, Windowsなどに対応。


<!-- more -->

- リファレンスなど
  - [ソース(GitHub)](https://github.com/jgm/pandoc)
  - [Pandoc User’s Guide](http://johnmacfarlane.net/pandoc/README.html)
    * 使い方がたくさん書いてある。

例えばMarkdown形式からEPUB形式にしたいときの、タイトルや筆者などのメタ情報とかこう書いたりするらしい。まだ色々調べ中。
これを使って、クラス構造をEPUB形式でエクスポートできるところまでは出来たけど、細かい詰めがまだまだ（´-ω-｀）縦書きとか出来るのだろうか…。


```
% title
% author(s) (separated by semicolons)
% date
```

- 参考
  * [多様なフォーマットに対応！ドキュメント変換ツールPandocを知ろう](http://qiita.com/sky_y/items/80bcd0f353ef5b8980ee)
    - 素晴らしい説明
  * [githubとかにあるMarkdown形式のﾌｧｲﾙをhtmlとかEPUBとかに変換する](http://d.hatena.ne.jp/tweeeety/20130607/1370591989)



----------------
### 本

#### Amazon和書
- [Kindle自費出版ガイド 米アマゾンの先例から学ぶ電子書籍の作り方](http://www.amazon.co.jp/gp/product/B009XKLTGW/ref=as_li_ss_tl?ie=UTF8&camp=247&creative=7399&creativeASIN=B009XKLTGW&linkCode=as2&tag=mono0926-22)
  * Google Documentを使った作成法指南
  * Webで最新版を無料公開中：[「Kindle 自費出版ガイド 米アマゾンの先例から学ぶ 電子書籍の作り方」(前半)](http://kdpguide.hatenablog.com/entry/2013/03/25/234230)
- [アマゾンで売る！　一番簡単な電子書籍の作り方](http://rcm-fe.amazon-adsystem.com/e/cm?lt1=_blank&bc1=000000&IS2=1&bg1=FFFFFF&fc1=000000&lc1=0000FF&t=mono0926-22&o=9&p=8&l=as4&m=amazon&f=ifr&ref=ss_til&asins=B00AGZ1X3C)
  * Google Documentは参考程度に、aozoraEpub3やSigilを利用
- [一万冊売ってわかった！電子書籍を売る方法](http://www.amazon.co.jp/gp/product/B00DNRE77O/ref=wms_ohs_product?ie=UTF8&psc=1)
  * 世界一周紀行など書いている人の本。ライブドアブログのEPUBエクスポートを利用。

うーん、作り方がバラバラ。わりとGoogle Documentで作るのが多数派な印象だけど。
みんなGUIベースだから直接は利用できないけど、参考程度に読んでる。


#### Amazon洋書
- [Building Your Book for Kindle](http://www.amazon.com/Building-Your-Book-Kindle-ebook/dp/B007URVZJ6/ref=sr_1_1?s=digital-text&ie=UTF8&qid=1373770883&sr=1-1&keywords=kindlegen)
  * 無料の公式本。Word系のアプリで作ってHTML出力して、アップロードするところまでで、かなりボリューム少ないけど、一読しておいた方が良い内容。
- [The eBook Design and Development Guide](http://rcm-na.amazon-adsystem.com/e/cm?lt1=_blank&bc1=000000&IS2=1&bg1=FFFFFF&fc1=000000&lc1=0000FF&t=mono0926-20&o=1&p=8&l=as4&m=amazon&f=ifr&ref=ss_til&asins=B009G2JMRK)
  * まだほとんど読んでないけど、Kindlegen周りの使い方中心に詳しく書いてありそう。
    - Webで公開中：[The eBook Design and Development Guide](http://bbebooksthailand.com/bb-epub-kindlegen-tutorial.html)
- [Kindle Formatting Formula: Convert Your Book into a Kindle eBook Format in Less than an Hour](http://rcm-na.amazon-adsystem.com/e/cm?lt1=_blank&bc1=000000&IS2=1&bg1=FFFFFF&fc1=000000&lc1=0000FF&t=mono0926-20&o=1&p=8&l=as4&m=amazon&f=ifr&ref=ss_til&asins=B006SBRA1M)
  * 中身見てない。
- [How to Publish and Sell Your Article on the Kindle: 12 Tips for Short Documents](http://rcm-na.amazon-adsystem.com/e/cm?lt1=_blank&bc1=000000&IS2=1&bg1=FFFFFF&fc1=000000&lc1=0000FF&t=mono0926-20&o=1&p=8&l=as4&m=amazon&f=ifr&ref=ss_til&asins=B004MDLKKK)
  * 中身見てない。

----------------

### JSON周りの開発用ライブラリ(iOS, .NET)

iPhoneアプリで編集してサーバー(ASP.NET)で変換して返すみたいなことをしているけど、その場合やっぱりJSONでのやり取りかなということで、以下が手軽に出来るようにしたかった。

- Objective-CのクラスからJSONへ変換
- JSONからC#のクラスへマッピング

#### Objective-CのクラスからJSONへ変換

[Mantle](https://github.com/github/Mantle)というライブラリでさくっとできた。もちろんCocoaPods対応なので導入も楽。

- JSON化したいクラスで`MTLModel<MTLJSONSerializing>`を継承
- オブジェクトのプロパティ名とJSONのプロパティ名のマッピング
- 配列構造のプロパティに対しては、その定義
- 上記の設定をしとけば定型的な数行でJSON化

<script src="https://gist.github.com/mono0926/5992878.js"></script>

<script src="https://gist.github.com/mono0926/5992916.js"></script>


#### JSONからC#のクラスへマッピング
[.NETの標準シリアライザ(XML/JSON)の使い分けまとめ](http://neue.cc/2011/12/10_357.html) にあるとおり、`DataContractJsonSerializer`を使用。
ちなみに上記サイトは僕の作ったこのブックマークレットで目に優しくなります。
<script src="https://gist.github.com/mono0926/5992885.js"></script>

基本的にはクラスに`DataContract`属性、プロパティに`DataMember`を付けるだけと楽ちん（´-ω-｀）
強いていえば、大文字小文字マッピングの設定を忘れずに。

```csharp
[DataMember(Name = "title")]
public string Title { get; set; }
```

----------------

### その他リンク

色々調べる中で目に入ったリンクなど。

- [でんでんコンバーター](http://conv.denshochan.com/)
  * Markdown形式のファイルをアップロードすると、ePubに変換してくれるサイト。正直、このAPIが叩けるようになると、変換周りを自前で作らなくてよくなって楽なのだけれど…（´-ω-｀）
- [無料で使えるEPUB 3作成ソフト／サービスガイド](http://ebook.itmedia.co.jp/ebook/articles/1107/25/news019.html)
  * FUSEe β
  * epubpack
  * MyBooks.jp
- [GoogleのSigilパワー](http://nakusou.zatunen.com/sigil.html)
  * [sigil](https://code.google.com/p/sigil/)というアプリを使う。
  - [Sigilの使い方](http://sigil.tsukaikata.info/)
- [ePubをフリーで作成できるソフト](http://iphone.f-tools.net/E-book-Jisui/ePub-Free-Sakusei.html)
  * chanLP使った方式

----------


### 所感

色々調べごとが多くて、開発自体がなかなか進まない（´-ω-｀）

あと、[Dropbox API](https://www.dropbox.com/developers) が今回良い感じに組み合わせられそうで、ちょっと検討中。
