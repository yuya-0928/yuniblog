---
title: ICARUSでogp設定しようと思ったら上手くいかなかったので調査と現状の整理
date: 2021-10-28 09:25:56
toc: true
tags:
  - ブログ開発
  - Hexo
  - ICARUS
  - 調査
categories:
  - Web開発
  - 覚え書き
---

メモ書き＆覚え書きです。Hexo＆ICARUS で構築しているブログの ogp を設定しようと思ったら上手くいかなかったので、現状どのようになってしまっているの確認しました。

## 目次

<!-- toc -->

<!--more-->

## やりたいこと

- Twitter で記事を共有する時に、ogp 画像が表示されるようにしたい。
- 直近では、デフォルトで自分のプロフィール画像が ogp として表示されれば良い。
- 将来的には、記事のタイトル名を ogp 画像として動的に生成してくれるようにしておきたい。
- 方法として目にしたことある手段としては、Cloudinary があるらしい（触ったことはまだない）
  https://catnose99.com/cloudinary-dynamic-ogp-image/

## 現状の症状

- ICARUS を導入した際に生成される設定ファイルに、"summary_large_image"の設定と、ogp としてプロフィール画像の path を指定した。
- Card validater を利用すると、"summary_large_image"は設定されているみたいだが、ogp 画像が反映されていない。
  <a href="https://gyazo.com/489fccc718e0e3f562683967c7cdaf66"><img src="https://i.gyazo.com/489fccc718e0e3f562683967c7cdaf66.png" alt="Image from Gyazo" width="1917"/></a>

- Twitter 上では ogp 画像は反映されないけれど、Discord では ogp 画像が反映される。ただし、記事本文のページは ogp 画像が反映されない。
  <a href="https://gyazo.com/b1105f71046b8136d2270fa064fdfd61"><img src="https://i.gyazo.com/b1105f71046b8136d2270fa064fdfd61.png" alt="Image from Gyazo" width="1365"/></a>

- 検証をかけると、`<meta og:image>`と`<meta twitter:image>`の両方が設定されている。og:image の方は、こちらが意図している URL になっているが、twitter:image の方が自分の意図に合った URL になっておらず、twitter 側だとこちらが優先的に反映されているのが原因かもしれない。
  2 つの meta タグは併用可能らしいとの情報はあるので、2 つ存在すること事態は問題ないらしい？
  https://www.granfairs.com/blog/staff/setting-twitter-cards
  <a href="https://gyazo.com/431065b117f342a15bb2039e4a9b552e"><img src="https://i.gyazo.com/431065b117f342a15bb2039e4a9b552e.png" alt="Image from Gyazo" width="1920"/></a>

- 記事の詳細ページに入ると、og:image のリンク内容が、記事の詳細リンク/ogp への相対パスになるため、正しいリンクにならない。書き方を修正するべき
  <a href="https://gyazo.com/431065b117f342a15bb2039e4a9b552e"><img src="https://i.gyazo.com/431065b117f342a15bb2039e4a9b552e.png" alt="Image from Gyazo" width="1920"/></a>

## 原因

相対パスの書き方が間違っていたっぽい。hexo のドキュメントに相対パスの書き方が乗ってた。
相対リンクにも対応させられるらしいので、記事の内容ごとに別の ogp 画像を表示させたい場合はそれを使うと良いのかも
https://hexo.io/docs/helpers.html#relative-url

## こうしたら解決した

ogp 画像の Path 指定方法を、相対パスから絶対パスに変更したら治った。

- 変更前  
  <a href="https://gyazo.com/cc775b5ab05c10f1c373c5cac6ea2a20"><img src="https://i.gyazo.com/cc775b5ab05c10f1c373c5cac6ea2a20.png" alt="Image from Gyazo" width="1308"/></a>

- 変更後  
  <a href="https://gyazo.com/31f21f9a2da62baa32ae6a9569e376f6"><img src="https://i.gyazo.com/31f21f9a2da62baa32ae6a9569e376f6.png" alt="Image from Gyazo" width="1311"/></a>

## 次はこうしたい

- ogp の画像を動的に生成するようにしたい。ogp で記事のタイトルを表示させる方が、記事のタイトルが見やすくていいと思う。
