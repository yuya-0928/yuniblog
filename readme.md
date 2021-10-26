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

## Markdownのヘッダに記載するメタ情報について(Front-matter)
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

## 機能追加に関するメモ

Hexoプラグイン「目次・さらに読む」機能を追加しよう
https://www.yuuuki-blog.com/2020/09/15/Hexo%E3%83%97%E3%83%A9%E3%82%B0%E3%82%A4%E3%83%B3%E3%80%8C%E7%9B%AE%E6%AC%A1%E3%83%BB%E3%81%95%E3%82%89%E3%81%AB%E8%AA%AD%E3%82%80%E3%80%8D%E6%A9%9F%E8%83%BD%E3%82%92%E8%BF%BD%E5%8A%A0%E3%81%97%E3%82%88%E3%81%86/