---
title: OGP画像の動的生成を試してみた
date: 2021-10-28 15:01:40
toc: true
tags:
  - ブログ開発
  - Hexo
  - ICARUS
  - Cloudinary
categories:
  - Web開発
  - 実装
---

<!-- textlint-disable -->

こんにちはー！Cloudinary を利用して、ブログの OGP 画像を動的に生成出来るように設定したので記事にします。

## 目次

<!-- toc -->

<!--more-->

## OGP とは？

Open Graph Protocol の略です。Twitter などの SNS をやっているとよく見る、ページのタイトル、URL、概要、画像が表示される仕組みのことです。
Qiita や Zenn のリンクを共有すると、このように記事のタイトルが画像になってリンクが生成されます。

<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">500LGTM！ | 全社員フルリモートで1兆2000億円で上場したGitLabに学ぶリモートワークの心得 by <a href="https://twitter.com/TAQRO_?ref_src=twsrc%5Etfw">@TAQRO_</a> <a href="https://t.co/bJiY3fQYpF">https://t.co/bJiY3fQYpF</a></p>&mdash; Qiita (キータ) 公式 (@Qiita) <a href="https://twitter.com/Qiita/status/1453235011457626113?ref_src=twsrc%5Etfw">October 27, 2021</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

このように、背景画像 + 記事のタイトル といった形の画像を自動で生成して ogp に割り当てるみたいな機能を実装したいなと考えました。

> 参考にした記事
> Cloudinary を利用して、OGP 画像を動的生成する
> https://blog.kentarom.com/generate-ogp-images-using-cloudinary/

## Cloudinary で背景画像に文字を入れてみる

Cloudinary に画像を取り込み、パラメーターを設定すると画像の色や大きさを設定することが出来ます。

<a href="https://gyazo.com/d6e7f1d011375f8e255db1cd3d2ae188"><img src="https://i.gyazo.com/d6e7f1d011375f8e255db1cd3d2ae188.jpg" alt="Image from Gyazo" width="1917"/></a>

パラメーターを設定すると、画像を呼び出す際に利用できる URL が生成されますので、この URL を meta タグに反映されるようにコードを書き換えてみます。

## ICARUS のテンプレートを改造する

ICARUS では、head を定義しているファイルがあります。/themes/icarus/layout/head.jsx が head の定義ファイルとなっています。

<a href="https://gyazo.com/935aa458afb0c8a48e0edae04a29383e"><img src="https://i.gyazo.com/935aa458afb0c8a48e0edae04a29383e.png" alt="Image from Gyazo" width="1920"/></a>

openGraphImages 変数に画像の URL を定義しているようでしたので、こちらの変数を定義している箇所に、先程 Cloudinary で生成した画像への URL と表示したいタイトルを入れます。

<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">OGP画像の設定を変更して、記事のタイトルを動的にOGP画像に反映させる仕組みを入れてみたー！<br>これで、リンクを共有するときにタイトルが分かりやすくなると思う。<a href="https://t.co/c6bYgCW2yf">https://t.co/c6bYgCW2yf</a></p>&mdash; 慕狼ゆに (@YYa0928) <a href="https://twitter.com/YYa0928/status/1453602111468421126?ref_src=twsrc%5Etfw">October 28, 2021</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

このように、思ったよりも簡単に実装できました。

## 次はこうしたい

もう少し見やすい背景画像を作成したり、文字を見やすいフォントのものに変更してみたいです。Cloudinary はフォントのデータを導入すれば自分の好きなフォントを利用することが出来るらしいので、見栄えの良いフォントを導入してみたいです。
