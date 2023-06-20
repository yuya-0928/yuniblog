---
title: AWSでredash環境を作ってみたら、思った以上に簡単だった！
date: 2021-10-01 20:01:52
toc: true
tags:
  - redash
  - AWS
  - 環境構築
categories:
  - データ分析
  - ハンズオン
---

こんにちはー！
最近、お仕事でアプリに溜まっているデータを DBeaver で SQL 叩いて、結果を Google スプレッドシートに書き写すって作業を頻繁にやっていたんだけど、これが結構面倒くさい。一緒にお仕事してる人とも話をして、自動で更新されるようにしてほしいって話を受けたので、Redash を構築してそこから Google スプレッドシートにデータを自動反映する仕組みを作りましたー！

## 目次

<!-- toc -->

<!--more-->

## なぜ redash を使おうとしたのか

最初は、GAS(Google App Script)を使って AWS に直接アクセス&SQL 実行！　みたいなことができれば良いなと思って試してみたのですが、過去の自分がセキュリティのことを考えて、同じ VPC 内からじゃないと AWS RDS にはアクセスできないように設定していたのですよね。DBeaver は SSH トンネルを使って RDS にアクセスできるので、GAS でも同じことができるかな？　と検討してみたのですが、コレに関してもセキュリティを考えて EC2 に SSH 接続できる IP アドレスにも制限をかけている設定をしているので GAS を利用はできなさそうでした。
だったら、自分の PC（登録している IP からのアクセスなら OK）か、AWS 内に redash を建てて、そこからアクセスすればデータの取得まではできるのでは？　と思ってたので Redash を使ってみることにしました。(そもそも、Redash 以外の選択肢を知らないという理由もあります)

## 手元の Docker 環境で構築できないか試してみる

Docker を理解していないため、だめでした。サーバーが立ち上がらない原因を調べてみたのですが、このままだと redash でデータ取得を自動化したい！　という目的からどんどん離れていくので、とりあえず今日は Docker を使うことを諦めました。

## AWS を使って構築を試してみる

Redash が公式で推奨している t2.small にどれぐらいの費用がかかるのか確認してみたところ、一月あたり 1200 円ぐらいで済みそうでした。費用もあまり高くなさそうなので、とりあえず導入してみることにしました。
導入する際にも[便利な IAM が公式から公開されている](https://redash.io/help/open-source/setup#aws)ので、環境構築には全く困りませんでした!
IAM のリンクをクリックして、EC2 の基本的な設定をぽちぽちやって、ちゃんとセキュリティグループを当てて上げれば、ものの 5 分ぐらいで Redash 環境が立ち上がります。

admin 用のアカウントを設定すれば、そこからすぐに使えるようになりました。

<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">AWSに環境作ったら、すんなりRedash環境だ立ち上がった！！ <a href="https://t.co/SuxJJfpIrx">pic.twitter.com/SuxJJfpIrx</a></p>&mdash; 慕狼ゆに@ぷろぐらむよわよわ (@YYa0928) <a href="https://twitter.com/YYa0928/status/1443575340169785347?ref_src=twsrc%5Etfw">September 30, 2021</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

## あとは Google Spreadsheet から値を取得できるようにする

Redash でクエリを作ると、クエリに APIKey が発行されます。APIKey を使ってクエリにアクセスすると、CSV や JSON 形式で取得できるようになるので、GoogleSpredsheet から API にアクセスしてデータを取得する方法を探してみます。
`=IMPORTDATA()`でデータが取得できそうだったので、そちらを利用しました。しかも数時間おきに情報を自動で更新しているみたいです！

https://gsuiteguide.jp/sheets/func-importdata/

ただ、どういったタイミングで情報が更新されるのか予測がつかない(だいたい情報が更新されてから 1~2 時間?)ので、そのあたりを改善していきたいですね。
あとは、GAS をもっと書けるようになって、日常の分析業務をどんどん自動化していきたい。Google Analytics とも連携して、データ取得するみたいなことを今後はやっていきたいですね。
