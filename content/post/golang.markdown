+++
categories = ["programming"]
comments = true
date = "2014-05-13"
layout = "post"
tags = ["golang"]
title = "golangの環境構築"

+++

[GoCon/2014spring.rst at master · GoCon/GoCon](https://github.com/GoCon/GoCon/blob/master/2014spring.rst)に備えて、とりあえずgolangのセットアップと、暇なときに[A Tour of Go](http://tour.golang.org/#1)をやっておこうかと(　´･‿･｀)

## gvmセットアップ

[moovweb/gvm](https://github.com/moovweb/gvm)に書いてある通りにやった。
mercurialのインストールが必要だったので、Brewfileに追記しておいた。

あと、`gvm install go1`に失敗したので、[Issues on OSX · Issue #38 · moovweb/gvm](https://github.com/moovweb/gvm/issues/38#issuecomment-39842170)に書いてある対応で何とかなった。

普通に`brew install go`のが楽だけど、ちょっとがんばった（´-ω-｀）

<!-- more -->

## 実行

以下を実行。

```
package main
import "fmt"
func main() {
    fmt.Printf("Hello world!")
}
```

[OSXの開発環境を整えた - monoHub](http://mono0926.com/blog/2014/05/06/renew/)でJetBrainのIDEいくつかインストールしてたけど、[IntelliJ IDEA — The Best Java and Polyglot IDE](http://www.jetbrains.com/idea/)で全部包含してるのね、情弱つらたん（´-ω-｀）

まあそこそこのお値段だし、適当に色々試用して、良かったら最終的にUltimate Edtion買おうかな（´-ω-｀）
Web StormでもGoのプラグインインストール出来たけど、SDKの設定とかうまく出来なかったりぐぐったりして出た説明と違うからCommunity Edition版のIntelliJでやった。

実行できたけど、`go build hoge.go`で生成されるような実行ファイルが生成出来なくて謎(　´･‿･｀)  
GOROOT・GOPATHもどこで設定すべきかとかその役割とかよく分からなくてつらたん（´-ω-｀）


### 解決
- [go-lang-idea-plugin/Missing ENV.md at master · go-lang-plugin-org/go-lang-idea-plugin](https://github.com/go-lang-plugin-org/go-lang-idea-plugin/blob/master/Missing%20ENV.md)を参考に設定したら、警告ダイアログが出なくなった。
- Run Configurationsで、Build before runにチェックを付けてディレクトリをbinに設定したら、実行ファイルも生成されるようになった。

![go](/images/post/go.png)

ただ、多分IntelliJがGoのデバッグ実行に対応していない？(無反応)のがつらたん（´-ω-｀）
[Support for debugging · Issue #25 · go-lang-plugin-org/go-lang-idea-plugin](https://github.com/go-lang-plugin-org/go-lang-idea-plugin/issues/25)を見ると、GAEプロジェクトのみ対応？？よく分からない（´-ω-｀）


あと、[ıɥɔınʎ (yabuchin_y) on Twitter](https://twitter.com/yabuchin_y)さんに[GopherCasts](https://gophercasts.io/)を教えてもらった(　´･‿･｀)
