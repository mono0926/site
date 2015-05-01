---
layout: post
title: "GitHub + Octopressでブログ作ってみた"
date: 2013-07-07
comments: true
tags: [github, octopress]
categories: [blog]
---
Markdownで書けてなかなか良い感じかもしれない（´-ω-｀）

### 導入手順
ここらへん参考に。

- [GitHub pages + Octopressの導入](http://rcmdnk.github.io/blog/2013/03/07/setup-octopress/)
  * 最初は適当にMacに入っているRuby 1.7.3やHomebrewで入れた2系でインストールしようとしたらはまって結局Ruby 1.9.3にしたので、初めから素直に従った方がよさげです。
- rvmの導入がうまくできなかったので、それだけこれを参考に。
  * [(OS X::Mountain Lion) RVMでRubyの環境構築メモ](http://jitsu102.hatenablog.com/entry/2012/11/23/162034)

#### 個人的な運用

- [imathis/octopress](https://github.com/imathis/octopress)からForkしてそのままソース管理として利用
  * 下書きなどあっても人に見られちゃうからBitbucket使うっていう人が多いらしいですが、あまり気にならないのでGitHubで一元管理
- `setup_github_pages` と入力して、[GitHub上のこのページ](http://mono0926.github.io) にデプロイされるように

<!-- more -->

#### テーマの変更
テーマは、[imathis/octopress](https://github.com/imathis/octopress/wiki/3rd-Party-Octopress-Themes)から選べますが、あまり有名じゃないので、そんなに選択肢無いです。凝るなら自分で作るべきですかね。
こぎれいなテーマを適当に選んで使っています。
導入は簡単で、上記から選んで、下のコマンドですぐ反映されます。

```
$ cd octopress
$ git clone GIT_URL .themes/THEME_NAME
$ rake install['THEME_NAME']
$ rake generate
```


### Markdown 初めて書いた
なかなか便利ですね(　´･‿･｀)
このあたりよくまとまっててよかったです。

- [Markdown記法 チートシート](http://qiita.com/Qiita/items/c686397e4a0f4f11683d)
- [QA@ITで使えるMarkdown記法](http://qa.atmarkit.co.jp/docs/markdown)
