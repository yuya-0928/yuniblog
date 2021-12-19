#  Hexoに関する備忘録
https://qiita.com/nyu___nS/items/3fca57ce133be69835ba

## 記事を新規作成する
```
$ hexo new [layout] "some tytle"
```

|layout|説明|
|:--|:--|
|post|記事|
|page|固定ページ|
|draft|下書き|

## Markdownのヘッダーに記載するメタ情報について（Front-matter）
```
---
title: marumaru
date: 2015-08-01 00:00:00
tags: works
toc: true
photos : marumaru.png
---
```

|setting|説明|
|:--|:--|
|title|タイトル|
|date|作った日にち|
|tags|タグ|
|photos|トップページに画像を出したい時に使う|


HEXOで目次を自動で作成してくれるhexo-tocをインストール
https://keijirotanabe.github.io/blog/2017/02/14/hexo-toc-install-170215/

