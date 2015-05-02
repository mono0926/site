---
layout: post
title: "SourceTreeでブランチ名をコミットメッセージの先頭に自動挿入"
date: 2014-10-31
comments: true
tags: [sourcetree, git]
categories: [programming]
---

Git便利ですね。今やこれ無しで開発は無理、というレベルです。

そんな日々使っているGitですが、何かしらのツールでタスクやIssueを作ってそのIDをfeatureブランチ名としている運用は多いと思います。

その場合、コミットメッセージにそのIDが含まれているとコミットとタスクを紐づけてくれるので、コミットメッセージの先頭にブランチ名を挿入することが多いはずです。

それを打つのが一々面倒だしたまにミスして違うタスクに紐付かれちゃうし、で少し困っていました。

コマンドラインで作業している場合は、以下のようなにGitの`prepare-commit-msg`フックを利用することで、コミットメッセージ作成時に自動挿入させることが可能です。

- [Gitでcommitした時にブランチ名をcommitメッセージに自動でいれる - Qiita](http://qiita.com/ykyk1218/items/4c17eef472ae8c31991f)


ただ、SourceTreeで試そうとしたら、動いてくれず、調べたところ非対応のようです。

- [SourceTree and git prepare-commit-msg - Atlassian Answers](https://answers.atlassian.com/questions/169399/sourcetree-and-git-prepare-commit-msg)

[@yabuchin_y](https://twitter.com/yabuchin_y)さんに相談したら、`commit-msg`で書き換えてしまえばいけるのでは？ということで作ってもらえました。

(僕はこの時点で、`commit-msg`はバリデーションフェーズ的なもので、書き換えは不可能なのでは？と思って諦めてしまいそうでした。)

## 設定手順

<!-- more -->

### コミットメッセージのテンプレートを作成して指定の文章が自動挿入されるようにする

以下を、特定のレポジトリルートで実行。

```
# $HOME/.gitmessage.txtの置き場所は自由です
# グローバルな設定としたい場合は、--globalオプションを付ける
git config commit.template $HOME/.gitmessage.txt
```

```
# .gitmessage.txtの中身(末尾に半角スペースを入れておくこと推奨)
[branchname]
```

これで、コミットメッセージ作成時に、`[branchname] `が先頭に自動挿入されます。

### コミット後に[branchname]がブランチ名へ書き換えられるようにする

`commit-msg`フックを利用します。

以下を特定のレポジトリの`.git/hooks/commit-msg`として配置します。

```
#!/usr/bin/env ruby
message_file = ARGV[0]
message = File.read(message_file, :encoding => Encoding::UTF_8)

current_branch = `git branch | grep '*'`.chomp.sub('* ', '')
current_branch = current_branch[current_branch.rindex("/")+1 .. current_branch.length]

newmessage = message.sub(/\[branchname\]/, current_branch)

File.write(message_file, newmessage)
```

`feature/hoge/#35`などとなっている場合、`[branchname]`部分が`#35`と置換されるような処理をしています。
用途に応じて適宜書き換えてください。

## 挙動

文章だけではイメージが沸きにくいかもしれないので、スクリーンショット貼っておきます。

### コミットメッセージを入れようとすると先頭に[branchname]が自動挿入

![](/images/post/st1.png)

そのままその後にメッセージを入れてコミットします。

### [branchname]が置換されてブランチ名になってくれます

![](/images/post/st2.png)

## 実際に使って見て

先週から活用し初めましたがすこぶる快適です(　´･‿･｀)

[@yabuchin_y](https://twitter.com/yabuchin_y)さん、ありがとうございました(　´･‿･｀)

### 参考リンク

- [Git - Git フック](http://git-scm.com/book/ja/v1/Git-%E3%81%AE%E3%82%AB%E3%82%B9%E3%82%BF%E3%83%9E%E3%82%A4%E3%82%BA-Git-%E3%83%95%E3%83%83%E3%82%AF)
- [Git hooks まとめ - Qiita](http://qiita.com/khlizard/items/dfe1ec9d82c0ed5da7c6)
