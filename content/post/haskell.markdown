+++
categories = ["programming"]
comments = true
date = "2013-11-23"
layout = "post"
tags = ["haskell", "scala", "C#"]
title = "Haskell勉強中"

+++

2週間くらい前からHaskell勉強中。

各種言語使ってきて、今の本業(Objective-C)や一番得意な言語(C#)以外にも久々に手を出したいなと思って以下を検討。

- LL系(Pythonなど)をもう少し自由に使えるように
  - ベターな書き方やモジュール知らずに冗長な記述になっていそう
  - 日頃の自動化が捗りそう
- ネイティブ系
  - C言語が最低限しか書けない上に段々忘れていったりもしている
  - ネイティブ系(コンパイル型・非VM)で書かなきゃいけない時とか手駒がない
  - とはいいつつCもC++も積極的に書きたくないのでやるとしたら下記のいずれか
    - Go
    - D言語
- 関数型
  - C#でLINQとかラムダ式とか慣れたけど、関数型の書き方を一部取り入れたオブジェクト指向という感じで、純粋関数型言語を学びたい
  - [pandoc](https://github.com/jgm/pandoc)というドキュメント変換ツールのソース理解とか改変とかしたいと思いつつHaskellで書かれていて全然分からない

<!-- more -->

まあどれでも良いかなあと思いつつ、Scalaとかも勉強したいとか思っていたのもあり関数型かなあと、とりあえずKindleで安く手に入る[Guide to ScalaーScalaプログラミング入門](http://www.amazon.co.jp/gp/product/B00BOBYZTQ/ref=as_li_ss_tl?ie=UTF8&camp=247&creative=7399&creativeASIN=B00BOBYZTQ&linkCode=as2&tag=mono0926-22)をざっと読んだ。
結果、C#と大して変わらず(Scalaの方がより関数型っぽいけど)、ちゃんと勉強するなら純粋関数型言語だなあと思い、pandocの理解にも繋がるしHaskellを勉強することに。

コンパイル型といえども、記述もシンプルでコンパイル簡単なので、今Pythonとかで簡単な自動化スクリプト書いている代替にもなるかなと。

## 勉強計画

### [すごいHaskellたのしく学ぼう!](http://www.amazon.co.jp/gp/product/B009RO80XY/ref=as_li_ss_tl?ie=UTF8&camp=247&creative=7399&creativeASIN=B009RO80XY&linkCode=as2&tag=mono0926-22)

少し前に話題になっていたこの本をまず読むことに。
洋書にするか迷ったけど、せっかく和書のKindle版もあるのでそれに頼った。

そして、オンライン版はフリーで読めることもさっき知ったり：[Learn You a Haskell for Great Good!](http://learnyouahaskell.com/)

フリーということは…と思って探したら、[Kindle用のファイルを生成出来るプロジェクト](https://github.com/igstan/learn-you-a-haskell-kindle.git)もあったり。
ただ、本に出てくるソースコード集が見つからず、まあいいか。

本の前半は、Haskellの構文に慣れるのに少し苦労しつつ、後半のアプリカティブのあたりでけっこう理解が怪しくなってきた（´-ω-｀）
理論が理解出来ていなくてしっくりこないところが一部あるものの、コードの挙動などは何とか読み解けているのでまだなんとかいけるはず。

### その後

[Parallel and Concurrent Programming in Haskell](http://www.amazon.com/gp/product/B00DWJ1BIG/ref=as_li_ss_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=B00DWJ1BIG&linkCode=as2&tag=mono0926-20)が面白そうなので、次に読みたいところ。並列/並行処理周りがまだ弱い気がするのでその勉強もかねて。

あと、個人的に同じ本を繰り返し読むのが苦手(それが大事なのは理解している)なので、代わりに[本物のプログラマはHaskellを使う](http://itpro.nikkeibp.co.jp/article/COLUMN/20060915/248215/)とか読んで曖昧なところの理解を深めて行ければ。

## 実行環境

### GHCインストール

色々処理系があるようだけど、標準のGHCを導入。
よく分からないけど、Homebrewで良いかと、以下を実行してインストール。
Mavericksなどの場合は環境によっては前もって[Command Line Tools](https://developer.apple.com/downloads/index.action)のインストールをしないとビルド失敗したりするはず。

```
brew update
brew install haskell
brew install haskell-platform # これがなんだか理解していない
```

これで、ターミナルで```ghci```と打つと、Haskellのインタプリターが起動するはず。
今まで、わざわざファイルで書く必要の無い書き捨ての込み入った計算はPythonのインタプリターでやっていた(そこまでする必要の無い程度ならAlfredの電卓で)けど、これからはghciでやろうかなと。

コンパイルは```ghc --make hoge.hs```だけで出来るので、簡単。```hs hoge.hs```と打つと、以下実行してくれるオレオレコマンドかエイリアスか作ったらさらに手軽になりそう。

```
ghc --make hoge.hs
./hoge
```

### IDEの導入

[neue cc - Haskell用IDE 「Leksah」の紹介と導入方法](http://neue.cc/2010/01/04_233.html)を見てLeksahをインストールすることに。
すごく簡単なプログラムならSublime Textでもいいかなと思いつつ、やはりちゃんとした補完機能など欲しいので。

インストール直後に出てくるダイアログのソースのパスには、Homebrewでのインストール時にダウンロードされていた以下のソースをどこかに展開したディレクトリを指定すると標準ライブラリのメタデータ作ったりソース参照が楽になったりするみたい。
```
/Library/Caches/Homebrew/ghc-7.6.3.tar.bz2
```

Candyオプション(一部の文字が数学的記号に置換表示される)がインストール直後は文字化けしていたけど、お気に入りの[Ricty](http://save.sys.t.u-tokyo.ac.jp/~yusa/fonts/ricty.html)にしたら直った。

実は本を読んでいただけで、まだほとんどコード書いていないけど、そろそろ書き慣れていきたいところ。
何か目先の題材が欲しいけど思いつかず（´・ω・｀）

テスト書くと言語仕様とか挙動とかの理解がけっこう捗るので、そこらへんも調べつつ進めていきたいところ。
とりあえずLeksahのサンプルコードがQuickCheck(prep_の接頭辞がテスト対象になる)を使っててそれでよいかなと。


久々にブログ書いたけど、Octopress + 自動化したおかげで、Webページをコピーする時以外キーボードだけで書けてなかなか快適（´-ω-｀）
