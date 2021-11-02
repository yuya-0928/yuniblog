---
title: 自宅の電気をコマンド一つで操作できるようにしたら想像以上に便利だった
date: 2021-10-06 21:29:18
toc: true
tags: 
- Philips Hue
- API
- Python
- 自作コマンド
categories:
- プログラム
- 生活
---

こんばんはー！自宅のターミナルから自宅の電気を操作できるようにしたら、思った以上に便利だったので記事にしてみます。

ゆにの自宅は、風呂場以外はすべてPhilips HueのWhite Ambianceを設置しています。Google Home miniも設置していますので、google homeに電気のオンオフを頼むことができます。
お布団の中から電気を消したり、玄関で靴を履いてから電気を消すことができるので、なにかと便利です。

<a href="https://gyazo.com/b289b789b4416770dcb52dc4f08a83cf"><img src="https://i.gyazo.com/b289b789b4416770dcb52dc4f08a83cf.jpg" alt="Image from Gyazo" width="717"/></a>


google homeに頼む以外にも、スマートフォンアプリからライトのオンオフや明るさ、ライトの色（暖色、寒色の切り替え）を操作することができます。

## 目次
<!-- toc -->

<!--more-->

ただこのライトの色を切り替えるのが面倒くさかったりします。アプリから操作できるので便利ではあるのですが、パソコン作業中にスマホを出してアプリを立ち上げ、画面をタップしてライトの色を調整する一連の操作がとても面倒くさく感じてしまいました。また、アプリの立ち上がりも2秒ほどかかるので、ストレスフリーというわけでもありません。
パソコン作業中にそのままライトを操作したい！と思ってWindowsのアプリを探したのですが、自分にとって使い勝手がよさそうなものもありません。

それなら、自分で作るか！！！と思い立ち、Philips Hue APIを触ることにしました。

>こちらのサイトを参考にしました
>Hueとconect+をつなげてみた 〜スマート電球 Philips Hue APIの使い方
>[https://www.conect.plus/post/20190220](https://www.conect.plus/post/20190220)

## やったこと
### 1. とりあえず、Philips Hue APIを試す。

デバイスへの接続設定を完了した後、実際にAPIを叩いてみます。
Philips hueには、ブリッジと呼ばれる、Hue製品の管理デバイスがあります。そのIPアドレスを把握し、`http://[今確認したHueブリッジのIPアドレス]/debug/clip.html`でアクセスします。
アクセスをすると、ライトの状態をJsonで取得したり、putをしてライトの状態を変化させることができる画面がでてきます。
<a href="https://gyazo.com/160673f49778861d4ee1717593470bb2"><img src="https://i.gyazo.com/160673f49778861d4ee1717593470bb2.png" alt="Image from Gyazo" width="552"/></a>

実際にlightの状態を取得してみると、こんな形でjsonが帰ってきます。(見づらいのでInsomnia)
<a href="https://gyazo.com/ac8f6aa848d9a919f4acb6d7664ed9f5"><img src="https://i.gyazo.com/ac8f6aa848d9a919f4acb6d7664ed9f5.png" alt="Image from Gyazo" width="370"/></a>

特定のライトを指定して、
```
{
  "bri":120,
  "on":true,
  "ct":200,
  "alert":"lselect"
}
```
のようにライトの明るさやオンオフのステータスなどをputして上げると、そのライトを操作することができます。

### 2. Pythonでコードを書く

ここまでわかったら、あとはコードを書くだけです。
apiのURLに対して、putをするコードを書きます。

書いてこんな感じに操作できることができました。
<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">PythonでPhillips APIを叩いて自宅の電球を操作する遊びをしてる。<br>PC作業中にスマホを開いて操作したくないので、自分が使う用のクライアントアプリを作りたいなって思ってる。<br>(スマホアプリはあるけど、PCアプリはない。音楽やゲームと同期してカラフルに色を変えるアプリはあるけど不便) <a href="https://t.co/aBTWYArr0H">pic.twitter.com/aBTWYArr0H</a></p>&mdash; 慕狼ゆに (@YYa0928) <a href="https://twitter.com/YYa0928/status/1445389777428221955?ref_src=twsrc%5Etfw">October 5, 2021</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

ライトのオンオフ、スマホアプリで設定されている明るさや色のプリセット4種類の切り替えを出来るようにコードを書きました。
作業に集中したり、やる気を出したいときは寒色。夕方以降にリラックスしたり、睡眠モードになりたいときは暖色の明かりにしています。

<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">全てのライトのオンオフ、iOSアプリで対応している灯りのモード4種類に関しては切り替えられるようにコード作っておいた。 <a href="https://t.co/b9l4qm8k4w">pic.twitter.com/b9l4qm8k4w</a></p>&mdash; 慕狼ゆに (@YYa0928) <a href="https://twitter.com/YYa0928/status/1445397655396421634?ref_src=twsrc%5Etfw">October 5, 2021</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

### 3. 自作コマンドを作る

これだけでは、まだ便利になりません。pythonファイルのあるディレクトリのPathを指定してファイルを実行するだと、コマンドが長くなってしまうので入力することがとても面倒になってしまいます。
なので、`light (操作したい内容)`のコマンドで処理を呼び出せるようにしたいと思います。

> 参考にしたサイト
>LinuxのコマンドをPythonで自作する
>[https://qiita.com/i_shot1997/items/1699331e526cb90615df](https://qiita.com/i_shot1997/items/1699331e526cb90615df)

とりあえず、`on`(オン), `off`(オフ), `relax`(暖色強め、明るさ暗め), `book`(暖色、明るさ明るめ), `motivated`(強い寒色, 若干暖色も混じってる), `concentrate`(強い寒色)の6種類のコマンドを実装してみます。

### 4. 自作コマンドにtab補完を実装する

これで、やる気を出したいときは`light motivated`。本を読みたいときは`light book`。リラックスときは`light relax`。とコマンドを入力するとライトの操作ができるようになりました！！
ただ、たびたび`motivated`をタイプミスしたり、`concentrate`のスペルを思い出せなかったりなど、まだ便利ではありません。普段からtab補完を使っているので、`m & tab`でちゃんと`motivated`が出るようにしてほしいです。

タブ補完を自作したことがなかったので、少し調べるまでに時間がかかりましたが、わかってしまったら思ったよりも簡単でした。

>参考にしたサイト
>Bashタブ補完自作入門
>[https://blog.cybozu.io/entry/2016/09/26/080000](https://blog.cybozu.io/entry/2016/09/26/080000)

そして、こんな感じにtabで補完が聞くようになりました。(ちょっと画質は荒い)
<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">ターミナルから使いやすいように、コマンドファイルを配置して、タブ補完も自作したー！ <a href="https://t.co/lp2sPX0VnP">pic.twitter.com/lp2sPX0VnP</a></p>&mdash; 慕狼ゆに (@YYa0928) <a href="https://twitter.com/YYa0928/status/1445417779587272706?ref_src=twsrc%5Etfw">October 5, 2021</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>


これで、今まで5秒以上かかっていた電気の明るさ切り替えが、コマンド一つでものの1秒で操作できるようになりました！！！！！
# めっちゃ便利！！！！！！！！！！！！
生活の不便さをAPIとコードのちからで解決したのは初めてなので、結構楽しかったし、テンション上がりました。
今度時間があったら、`light lumens (数字)`とかで、細かい明るさも調整できたらいいななんて考えています。
今の状態でも十分便利なので、不便に感じたらその都度実装していきたいなと思っています。