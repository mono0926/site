+++
categories = ["プログラミング"]
comments = true
date = "2013-08-04"
layout = "post"
tags = ["ginger", "python", "alfred", "english"]
title = "GingerをAlfredで使えるようにしてみた"

+++

[Ginger APIをPythonで叩いてみた](/blog/2013/08/03/ginger/)の続き。

元々はAlfredで英文校正が出来るようにしたかったので、ここからが本番。

### 完成版

こんなのが出来たという紹介から。

#### 校正

ginger というキーワードに続けて英文を打つと、正してくれる。(この場合、冠詞aの抜けが正される。)

![ginger](/images/post/ginger1.png)


#### 改善候補一覧

<!-- more -->

rephraseというキーワードに続けて適当な英文を打つと、より自然な言い回し候補を出してくれる。
"Thank you for your reply"は、メールの返信とかでよく使うけど、ワンパターン化を避けたい時とかに使えそう。

![ginger](/images/post/ginger2.png)

ともに、選択状態でエンターを押すと、クリップボードにコピーされて、フォーカスの当たっているアプリにペーストされるので、適当にメールとかエディタとか使いながら自然と正しそうな英文が打てるようになるはず。

### AlfredのWorkflowの作り方

一応[ドキュメント](http://support.alfredapp.com/workflows)はあるけど、肝心なところが書かれていなかったりして、[フォーラム](http://www.alfredforum.com/forum/3-share-your-workflows/)で聞いたり、既存のWorkflowのソースを読んで作り方を学ばなければいけない感じ。
作り方自体は基本簡単だけど、ちょくちょくはまりどころがあって苦労する。

#### キーワードの受け取り

{query}というキーワードでアクセス出来るので、それをスクリプトに引数ととして渡すのが一般的。

#### 結果の表示

処理終了時にnotification飛ばしたり、クリップボードにコピーとかはWorkflowのエディタでパーツをつなぎ合わせたりするだけで簡単だけど、上の例みたいに一覧するのはどうやるのかと思っていたら、XMLで標準出力するらしい。
関係ないechoやprint文があると壊れるので注意。
ここらへんも、既存のソース読み解いてやっと分かった。それも不慣れなPHPソースがけっこう多くてアレ。

こんな感じのXMLを標準出力すると、Itemの数だけ一覧される。

```
<?xml version="1.0" ?>
<items>
  <item arg="I am a programmer and writing bad English. I am Japanese." uid="d78b56b0-fcb7-11e2-9787-e80688cb3920">
    <title>I am a programmer and writing bad English. I am Japanese.</title>
    <subtitle>Gingered sentence</subtitle>
    <icon/>
  </item>
</items>
```

これも適当に文字列置換したりして作れるけど、PythonでXML組み立てて作る簡単なモジュール作って再利用できるようにしておいた。
ここらへんの下回りがけっこうこなれていない感。

#### インストール可能なパッケージの作り方

配布されているworkflowは、*.alfredworkflowという形式で、ダブルクリックでインストールできる。

簡単なやり方は自分のworkflowを右クリックしてExportすること。

逆にscript群からコマンドで作りたい場合は、必要なファイルをzip化して拡張子を変えればよい。
info.plistが必要で、それは多分コマンドラインじゃ作れないから、やっぱり最初はExportの過程が必要だけど、コードとか別管理したいならコマンドラインで修正版作るのがよさげな気がする。

適当にpackage作成スクリプト書いた。

```
cp ginger/info.plist .
cp ginger/*.png .
zip ginger.zip ginger_driver.py ginger/*.py info.plist *.png workflow/*.py
rm info.plist *.png
mv ginger.zip ginger.alfredworkflow
```

こんな管理で良いのか若干謎。


以上、[GitHub](https://github.com/mono0926/AlfredWorkflow)で管理するようにした。
今までworkflowの作り方がよく分からない部分があったり管理が適当だったりしたけど、これからはもっとサクサク作れそう。

今回の成果物：[Ginger Workflow](https://github.com/mono0926/AlfredWorkflow/raw/master/ginger.alfredworkflow)
