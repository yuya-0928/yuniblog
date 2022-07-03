# Hexo に関する備忘録

https://qiita.com/nyu___nS/items/3fca57ce133be69835ba

## 環境構築

`yarn`コマンドで環境をセットアップ.
`npm install`コマンドも実行する（こちらのコマンドはやらなくてもいいようにしていきたい）.

## コマンド

- サーバーを立ち上げる

```
yarn hexo server
```

- 記事の新規作成

```
yarn hexo new 記事タイトル
```

- 記事のドラフトを作成

```
yarn hexo new draft 記事タイトル
```

## TODO

- パッケージは yarn で管理をする。package-lock.json を削除して、npm でインストールしているパッケージを yarn で入れ直す

## 記事を新規作成する

```
$ hexo new [layout] "some tytle"
```

| layout | 説明       |
| :----- | :--------- |
| post   | 記事       |
| page   | 固定ページ |
| draft  | 下書き     |

## Markdown のヘッダーに記載するメタ情報について（Front-matter）

```
---
title: marumaru
date: 2015-08-01 00:00:00
tags: works
toc: true
photos : marumaru.png
---
```

| setting | 説明                                 |
| :------ | :----------------------------------- |
| title   | タイトル                             |
| date    | 作った日にち                         |
| tags    | タグ                                 |
| photos  | トップページに画像を出したい時に使う |

HEXO で目次を自動で作成してくれる hexo-toc をインストール
https://keijirotanabe.github.io/blog/2017/02/14/hexo-toc-install-170215/
