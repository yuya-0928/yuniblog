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
- 覚え書き
---

メモ書き＆覚え書きです。Hexo＆ICARUSで構築しているブログのogpを設定しようと思ったら上手くいかなかったので、現状どのようになってしまっているの確認しました。

## 目次
<!-- toc -->

<!--more-->

## やりたいこと
- Twitterで記事を共有する時に、ogp画像が表示されるようにしたい。
- 直近では、デフォルトで自分のプロフィール画像がogpとして表示されれば良い。
- 将来的には、記事のタイトル名をogp画像として動的に生成してくれるようにしておきたい。
- 方法として目にしたことある手段としては、Cloudinaryがあるらしい（触ったことはまだない）
https://catnose99.com/cloudinary-dynamic-ogp-image/

## 現状の症状
- ICARUSを導入した際に生成される設定ファイルに、"summary_large_image"の設定と、ogpとしてプロフィール画像のpathを指定した。
- Card validaterを利用すると、"summary_large_image"は設定されているみたいだが、ogp画像が反映されていない。
<a href="https://gyazo.com/489fccc718e0e3f562683967c7cdaf66"><img src="https://i.gyazo.com/489fccc718e0e3f562683967c7cdaf66.png" alt="Image from Gyazo" width="1917"/></a>

- Twitter上ではogp画像は反映されないけれど、Discordではogp画像が反映される。ただし、記事本文のページはogp画像が反映されない。
<a href="https://gyazo.com/b1105f71046b8136d2270fa064fdfd61"><img src="https://i.gyazo.com/b1105f71046b8136d2270fa064fdfd61.png" alt="Image from Gyazo" width="1365"/></a>

- 検証をかけると、`<meta og:image>`と`<meta twitter:image>`の両方が設定されている。og:imageの方は、こちらが意図しているURLになっているが、twitter:imageの方が自分の意図に合ったURLになっておらず、twitter側だとこちらが優先的に反映されているのが原因かもしれない。
2つのmetaタグは併用可能らしいとの情報はあるので、2つ存在すること事態は問題ないらしい？
https://www.granfairs.com/blog/staff/setting-twitter-cards
<a href="https://gyazo.com/431065b117f342a15bb2039e4a9b552e"><img src="https://i.gyazo.com/431065b117f342a15bb2039e4a9b552e.png" alt="Image from Gyazo" width="1920"/></a>

- 記事の詳細ページに入ると、og:imageのリンク内容が、記事の詳細リンク/ogpへの相対パスになるため、正しいリンクにならない。書き方を修正するべき
<a href="https://gyazo.com/431065b117f342a15bb2039e4a9b552e"><img src="https://i.gyazo.com/431065b117f342a15bb2039e4a9b552e.png" alt="Image from Gyazo" width="1920"/></a>