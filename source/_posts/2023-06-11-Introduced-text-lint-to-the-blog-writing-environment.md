---
title: ブログの執筆環境にtext-lintを導入した
toc: true
tags:
  - null
categories:
  - null
date: 2023-06-11 23:35:51
---

## 概要

ブログの執筆環境に text-lint を導入しました。
どういうことをしたのかについてのメモを残しておきます。

## 目次

<!-- toc -->

<!--more-->

## やったこと

- devDependencies に textlint と、textlint の rule を 4 つ追加しました。

```
"devDependencies": {
    "textlint": "^13.3.2",
    "textlint-filter-rule-comments": "^1.2.2",
    "textlint-rule-preset-ja-spacing": "^2.3.0",
    "textlint-rule-preset-ja-technical-writing": "^7.0.0",
    "textlint-rule-spellcheck-tech-word": "^5.0.0"
  }
```

- vscode-textlint を導入しました。

  - ついでに、.vscode/extensions.json を設定して、ブログプロジェクトの推奨拡張機能に設定しました。
    https://github.com/yuya-0928/yuniblog/blob/master/.vscode/extensions.json

- [textlint-filter-rule-comments](https://github.com/textlint/textlint-filter-rule-comments)

  - [JSer.info](https://jser.info/)のライターで有名な azu さんが作っているリポジトリです。

  ```
  textlintでエラーになる

  <!-- textlint-disable -->

    このテキストにはtextlintがかからない

  <!-- textlint-enable -->

  textlintでエラーになる
  ```

  このようにマークダウンにコメントを入れることで、一部の行に textlint のルールを当てない状態にできます。

- [textlint-rule-spellcheck-tech-word](https://github.com/azu/textlint-rule-spellcheck-tech-word)

  - こちらも azu さんが作っているリポジトリです。web エンジニア向けの技術用語チェックをしてくれます。今はメンテされていないみたいなのですが、こちらを導入すると[WEB+DB PRESS 用語統一ルール](https://gist.github.com/inao/f55e8232e150aee918b9)の辞書に従って lint がかかるので、簡単にこちらを導入しました。
  - textlint-rule-spellcheck-tech-word のリポジトリで、azu さんは[Proofdict](https://github.com/proofdict/proofdict)を使っていると案内がありましたので、時間がある時にこちらへ切り替える作業をします。Proofdict も azu さんが関わっているプロジェクトです。

- [textlint-rule-preset-ja-spacing](https://github.com/textlint-ja/textlint-rule-preset-ja-spacing)

  - こちらは[textlint-ja](https://github.com/textlint-ja)というコミュニティによって管理されているプロジェクトです。日本語周りにおけるスペースの有無を決定する textlint ルールプリセットを提供してくれます。

- [textlint-rule-preset-ja-technical-writing](https://github.com/textlint-ja/textlint-rule-preset-ja-technical-writing)
  - こちらも textlint-ja が管理しているプロジェクトです。技術文書向けの textlint ルールプリセットです。二重否定やら抜き言葉のチェック、「<!-- textlint-disable -->思います<!-- textlint-enable -->」と文章を締めると、弱い表現なので直すべきと指摘が入ったり、「ですます調」と「<!-- textlint-disable -->である<!-- textlint-enable -->調」を統一してくれます。ブログを書く上では不要なチェックがいくつか入っていたため、デフォルトの設定を少し改変して使います。

## 困ったこと

- VSCode で「Format On Save」を ON にしていると、日本語と英数字の間に自動でスペースが入ってしまう。prettier が原因と予想できる挙動をしているのですが、prettier の設定に日本語と英数字の間にスペースを入れる設定をしているわけではなかった。デフォルトの textlint の設定では、日本語と英数字の間にスペースは入れない設定になっている。
- どうやら調べてみると、prettier では日本語と英数字の間に自動でスペースをいれるのが強制仕様になっているらしい。どうやら、prettier の v3.0 で修正される予定のようで、試しに 3.0.0-alpha.6 を導入してみたところ、自動でスペースを入れる挙動はなくなっていた。
  - [textlint と VSCode を使って記事を書く](https://qiita.com/bon10/items/3f2e29a614797f654518)

## 日本語と英数字の間にスペースを入れるべきか否か？

- 調べてみたところ、この記事が一番よくまとまっていた。どうやら、だいぶ根深い論争になっているらしい。個人的には、ブログを書く上ではどっちでも良いなと思っている。
  - [[Solved] 日本語文章中、英単語の両端にスペースをつける人](https://qiita.com/CodeOne/items/43d2b8e4247b020652b2)
- 現在のバージョンの prettier v2.8.8 の挙動に従って、日本語と英数字の間にはスペースを入れる状態でブログを書き進めていこうと思いました。
- 考えたこと
  - prettier で自動的にスペースを入れてくれるのならば特に執筆する際に問題は起きない。
  - スペースが入っても、入らなくても、文章の見た目に大きな差は無いなと思った。
  - 将来的に prettier が v3.0 に上がってスペースが自動で入らないようになったとしても、ブログを書くのに支障は出ない。
    - もしそうなったら、textlint の設定を変更するか、可能なら prettier の設定を変更して対応をすればよいと思った。
    - ブログを執筆する上では、「textlint のルールを守っていないと master ブランチにマージしない」みたいな、厳密なルールを適用することはしないことにする。
      - 複数人で共同執筆している書籍を作っているわけではないので、そのあたりを厳密にするメリットがない。

## 感想

- ブログの執筆環境に textlint を導入する作業をするだけのはずだった。作業の中で prettier の仕様の話に触れたり、「日本語と英数字の間にスペースを入れるべきか？」の問題を調べることになり、想像よりも時間のかかる作業だった。
- textlint を真面目に導入する作業を初めてした。エンジニア集会でブログを共同執筆するための環境を整える活動をしていて、そのプロジェクトでも textlint の導入をする必要があり、必要な知識を勉強できた。
- lint をどうするか考えるために試行錯誤するのがとても楽しかった。
- ブログのリポジトリは公開しています。今回設定した、textlintrc はこちら。
  - [https://github.com/yuya-0928/yuniblog/blob/master/.textlintrc.json](https://github.com/yuya-0928/yuniblog/blob/master/.textlintrc.json)
