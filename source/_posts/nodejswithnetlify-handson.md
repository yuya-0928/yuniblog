---
title: Node.js x Netlifyを試してみた
date: 2021-09-29 14:35:54
tags: 
- Node.js
- HEXO
- Web
categories:
- ハンズオン
---

## きっかけ
 [Fukuoka.rb](https://fukuokarb.connpass.com/)でワイワイと雑談をしていた際に、Jekyllという静的ファイルの生成が出来るライブラリの話題になり、そういったツールを使ってブログを作ってみることに興味が湧いたことがきっかけです。

 はじめはJekyll x Github Pagesでブログサイトのホスティングをしようと考えていましたが、Github Pagesで対応しているテーマのデザインと機能にあまり納得がいかなかったため他のサイトジェネレーターとホスティング方法を探すことにしました。ついでに、サイトホスティングの選択肢を複数把握したり、色々なジェネレーターを試してみて、ツールを使ったサイト構築の勘どころを掴むことができれば良いなとも思い、空いた時間を使って色々と触ってみました。

## 触ったジェネレーター
- Jekyll
 Rubyで動く静的サイトジェネレーターです。普段はRubyを触る機会が多いので、慣れた言語で利用できるというメリットがあります。gemで簡単に導入できるので全く難しくないです。
- Hugo
 goで動く静的サイトジェネレーターです。goで動いているためとにかく早いのが利点らしいです。goは最近少しだけ触ったことがあるので環境構築などで詰まることはありませんでした。
 `hugo new site "サイト名"`でサイトを構築した後はgoを書く必要も特になかったので、goの知識が無くても簡単に扱えます。
- Hexo
 Node.jsで動くサイトジェネレーターです。Node.jsは最近入門したばかりなのでフォルダの中身はまだ少し理解が難しいです。今回利用しているICARUSのデザインと機能性に惹かれたため、こちらを導入することにしました。タグ機能、カテゴリ機能があるのがとても良い。

 ## ホスティング方法
  最初はGithub Pagesを使ってホスティングすることを考えていました。ただ、Jekyllで利用したいサイトテーマがGithub Pagesで対応していないため使用できないといった状況に遭遇してしまい、思ったよりも自由度が低い・・・？と感じてしまったため、別のホスティング方法を探すことにしました。探してみたところ、Netlifyを見つけたのでこちらを利用してみることにしました。
  サイトをホスティングする時に考えていた条件として、
  - マークダウンでブログを書くことが出来る。
  - git pushをすればそのままブログに反映してくれる。
  - githubサイト上でマークダウンを書いても、そのままブログに反映してくれる。
の３つができたらいいなと考えていました。

Github PagesでもNetlifyでも上の条件を満たすことができそうなので、より自由度の高そうなNetlifyを選択することにしました。
また、Netlify CMSを利用すると、ブログの投稿がもっと簡単にできるようになるみたいなのでそれも触ってみたいといった理由もあります。

Micro CMSツールも時間を作っていくつか触ってみたいですね。

<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">Hexo(ICARUS)の導入できたー！<br>色々なサイトジェネレーター試したり、サイトテーマ探してみたりしてみたけど、このテーマが一番見やすくて機能が付いててよき <a href="https://t.co/JAerr1By5u">pic.twitter.com/JAerr1By5u</a></p>&mdash; 慕狼ゆに@ぷろぐらむよわよわ (@YYa0928) <a href="https://twitter.com/YYa0928/status/1442866844679823361?ref_src=twsrc%5Etfw">September 28, 2021</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>