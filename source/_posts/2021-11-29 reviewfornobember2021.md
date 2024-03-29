---
title: 11月の振り返り
date: 2021-11-29 21:04:06
toc: true
tags:
  - ゆるふわ目標設定
categories:
  - ポエム
  - 月次目標
---

<!-- textlint-disable -->

こんにちはー！
そろそろ 11 月も終わりなので、今月どんなことが出来たのかを振り返っていきたいと思いますー！

## 目次

<!-- toc -->

<!--more-->

## 今月やったこと

### GAS を使った Youtube・Twitch の情報収集の自動化をした

お仕事関連のタスクで、YouTube や Twitch のライブ配信の情報を収集したいといった需要がありましたので、Google App Script を使って Youtube と Twitch のライブ配信を収集するプログラムを書きました。
GAS を使うのは今回が初めてでしたが、基本的には Javascript と同じ考え方でコードを書くことが出来ましたので、特に難しさを感じることはありませんでした。
今月は「達人プログラマー」も読み進めている最中でしたので、試しにその中で得られた学びを積極的にコードの中に落とし込んで見ました。例えば、DRY の原則を意識して、処理は関数にまとめてプログラムを改造する必要が出たときには一箇所変えるだけで済むようにしたり、自分が意図しない挙動をする可能性があるコードには throw 文を使い、意図的に例外を発生させることで間違ったプログラムが実行されてしまうことを防ぐ処理を書くなどを実践してみました。
データ収集のために動くコードが直ぐに必要だったのでテストを作る工程は後回しになってしまっていますが、今回書いたプログラムはしばらく運用していく予定です。アプリ開発の片手間にテストコードを書いたり、API 取得のコスト（YoutubeDataAPI の quota）を減らすためのリファクタリングなど、やることは多いですが少しずつ進めていこうと考えています。

### VRC エンジニア作業飲み集会を開催した

11 月の目標でも書いていた、もくもく会用のワールドを簡単に作り、イベントを実施してみました。「VRC エンジニア作業のみ集会」というイベントで、技術を触っているお友達が集まって、作業をしたり、お酒を飲んだり、技術関連のオタクトークが気軽にできる場所を作りたい！という想いで準備をし、試しに 2 回開催してみました。
開催までにどのようなことを考えて、どんな準備をしたのか。実際に開催してみるとどうだったかについては、また後日にブログでまとめようと考えています。

第 0 回の様子

<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">第0回が終了しましたー！<br>20人に届くほどたくさんの方に参加していただきましたー！第１回目（第0回目）の開催でまだ不完全な部分はありますが、これからより良い集会にしていきたいなと思っていますー！<br>本日はありがとうございましたー！<a href="https://twitter.com/hashtag/VRC%E3%82%A8%E3%83%B3%E3%82%B8%E3%83%8B%E3%82%A2%E4%BD%9C%E6%A5%AD%E9%A3%B2%E3%81%BF%E9%9B%86%E4%BC%9A?src=hash&amp;ref_src=twsrc%5Etfw">#VRCエンジニア作業飲み集会</a> <a href="https://t.co/OBv8m1eSPV">pic.twitter.com/OBv8m1eSPV</a></p>&mdash; 慕狼ゆに (@YYa0928) <a href="https://twitter.com/YYa0928/status/1461722637080530946?ref_src=twsrc%5Etfw">November 19, 2021</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

第 1 回の様子

<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">第1回が終了しましたー！<br>前回よりも多く、20人以上の方に参加していただきましたー！！23時のイベントが終わったあとも、みんなでお酒を飲んで雑談したりしましたー！<br>今日もみんなで楽しく技術のお話したり、もくもく作業したり、雑談したり、お酒飲んだりしましたー！ <a href="https://t.co/GJxKxJRmSw">pic.twitter.com/GJxKxJRmSw</a></p>&mdash; 慕狼ゆに (@YYa0928) <a href="https://twitter.com/YYa0928/status/1464268538814689280?ref_src=twsrc%5Etfw">November 26, 2021</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

### 達人プログラマーを 5 章まで読んだ

達人プログラマー 9 章中 5 章まで読みました。ブログではまだ 2 章までしか内容をまとめていませんが、記事を書く時間をどこかで作って読んだ内容を振り返っていこうと思っています。あと 4 章分に関しても来月の頭中には読み切ってしまいたいと考えています。

<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">昨日お勧めしてもらった本を買ってきたので読んでみる <a href="https://t.co/txEZ5RVINo">pic.twitter.com/txEZ5RVINo</a></p>&mdash; 慕狼ゆに (@YYa0928) <a href="https://twitter.com/YYa0928/status/1452842830230024196?ref_src=twsrc%5Etfw">October 26, 2021</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

### Rspec に入門した

業務で書いている Ruby on Rails 製のアプリケーションのテストコードを簡単に書いてみました。実際に手を動かしてみると、何をテストするべきか、どこまでテストに時間を書けるべきかといった現実的に考えなければ行けない問題に取り組むことになりましたのでとても良い勉強になりました。今回試しに書いてみた感想としては、まず最低限必要なテスト（この URL に繋がるかどうか）は機能開発を始める前に書いておき、そこから、サービス提供をするために重要な機能（決済に関わる機能）や手動テストでは不安が残る機能に関してのみに絞ってテストを書くといった方針でまずは進めて行きたいと考えています。テストは万能ではないということは常に頭に入れて、テストを書くことに慣れて行きたいですね。

### REALFORCE を購入したので、キーボードになれるために寿司打を定期的にやった

キーボードを新調しましたので、キーボードになれるために＆効率よくコードや文章を書けるようにするために寿司打などのタイピング練習を定期的にやるようにしました。タイピング練習に関しても、後日にブログでどのようなことをやっているのか、どんなアプリを使って練習をしているのかについて紹介したいと考えています。

<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">まいにゅーぎあー！<br>はじめてのリアルフォース！Bluetoothも対応しているR3！静音仕様の打鍵感も結構良いー！ <a href="https://t.co/xT1TFjGjWo">pic.twitter.com/xT1TFjGjWo</a></p>&mdash; 慕狼ゆに (@YYa0928) <a href="https://twitter.com/YYa0928/status/1456817478592458754?ref_src=twsrc%5Etfw">November 6, 2021</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

### シェル・ワンライナー 160 本ノックを始めた

本屋さんに行ったら気になる本を見つけたので買ってみました。

<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">気になる本があったので買ってみたにゃぁ <a href="https://t.co/hPjxPmrGld">pic.twitter.com/hPjxPmrGld</a></p>&mdash; 慕狼ゆに (@YYa0928) <a href="https://twitter.com/YYa0928/status/1460511240187383811?ref_src=twsrc%5Etfw">November 16, 2021</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

なかなかレベルの高い内容なので、毎日 1 問ずつやっています（出来ていない日もある）。VSCode が使えない環境で、プログラム内のコードを探したり、特定のファイルを探すなどといった作業を Linux のコマンドで出来るようになりたいなって思ったことがきっかけで始めてみました。実務で直ぐに使える内容というわけではなく、自分の Linux 力を鍛える内容になっているので少しずつ進めていきたいと思っています。

## 総括

今月はふわっと目標を決めておいたおかげで、先月よりもやらなきゃいけないことが明確になり、モチベーションの維持がしやすくなったなと感じています。
11 月も目標は完全に達成できたわけではありませんが、目標達成よりも続けること優先で進めていきたいので、12 月の目標も緩めに最低限設定していきます。
