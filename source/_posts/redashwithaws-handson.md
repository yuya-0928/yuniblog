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
最近、お仕事でアプリに溜まっているデータをDBeaverでSQL叩いて、結果をGoogle スプレッドシートに書き写すって作業を頻繁にやっていたんだけど、これが結構面倒くさい。一緒にお仕事してる人とも話をして、自動で更新されるようにしてほしいって話を受けたので、Redashを構築してそこからGoogle スプレッドシートにデータを自動反映する仕組みを作りましたー！

## 目次
<!-- toc -->

<!--more-->
## なぜredashを使おうとしたのか

最初は、GAS(Google App Script)を使ってAWSに直接アクセス&SQL実行！みたいなことができれば良いなと思って試してみたのですが、過去の自分がセキュリティのことを考えて、同じVPC内からじゃないとAWS RDSにはアクセスできないように設定していたのですよね。DBeaverはSSHトンネルを使ってRDSにアクセスできるので、GASでも同じことができるかな？と検討してみたのですが、コレに関してもセキュリティを考えてEC2にSSH接続できるIPアドレスにも制限をかけている設定をしているのでGASを利用することはできなさそうでした。
だったら、自分のパソコン（登録しているIPからのアクセスならOK）か、AWS内にredashを建てて、そこからアクセスすればデータの取得まではできるのでは？と思ってたのでRedashを使ってみることにしました。(そもそも、Redash以外の選択肢を知らないという理由もあります)

## 手元のDocker環境で構築できないか試してみる

Dockerを理解していないため、だめでした。サーバーが立ち上がらない原因を調べてみたのですが、このままだとredashでデータ取得を自動化したい！という目的からどんどん離れていくので、とりあえず今日はDockerを使うことを諦めました。

## AWSを使って構築を試してみる

Redashが公式で推奨しているt2.smallがどれぐらいの費用になるのか確認してみたところ、一月あたり1200円ぐらいで済みそうでした。費用もあまり高くなさそうなので、とりあえず導入してみることにしました。
導入する際にも[便利なIAMが公式から公開されている](https://redash.io/help/open-source/setup#aws)ので、環境構築には全く困りませんでした!
IAMのリンクをクリックして、EC2の基本的な設定をぽちぽちやって、ちゃんとセキュリティグループを当てて上げれば、ものの5分ぐらいでRedash環境が立ち上がります。

admin用のアカウントを設定すれば、そこからすぐに使えるようになりました。

<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">AWSに環境作ったら、すんなりRedash環境だ立ち上がった！！ <a href="https://t.co/SuxJJfpIrx">pic.twitter.com/SuxJJfpIrx</a></p>&mdash; 慕狼ゆに@ぷろぐらむよわよわ (@YYa0928) <a href="https://twitter.com/YYa0928/status/1443575340169785347?ref_src=twsrc%5Etfw">September 30, 2021</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

## あとはGoogle Spreadsheetから値を取得できるようにする

Redashでクエリを作ると、クエリにAPIKeyが発行されます。APIKeyを使ってクエリにアクセスすると、CSVやJSON形式で取得できるようになるので、GoogleSpredsheetからAPIにアクセスしてデータを取得する方法を探してみます。
`=IMPORTDATA()`でデータが取得できそうだったので、そちらを利用しました。しかも数時間おきに情報を自動で更新しているみたいです！

https://gsuiteguide.jp/sheets/func-importdata/


ただ、どういったタイミングで情報が更新されるのか予測がつかない(だいたい情報が更新されてから1~2時間?)ので、そのあたりを改善していきたいですね。
あとは、GASをもっと書けるようになって、日常の分析業務をどんどん自動化していきたい。Google Analyticsとも連携して、データ取得するみたいなことを今後はやっていきたいですね。