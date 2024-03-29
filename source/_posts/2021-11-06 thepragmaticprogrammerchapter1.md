---
title: 【第一章】達人プログラマーを読んで
date: 2021-11-06 13:28:39
toc: true
tags:
  - 達人プログラマー
  - 読書
categories:
  - 読書
  - 読み物（特定の技術によらない本）
---

<!-- textlint-disable -->

こんにちはー！今月は、『達人プログラマー』を読んでいます。
読む中で学んだ内容を、備忘録的に簡単にまとめていきます。
簡単にまとめているだけですので、もし内容に興味が湧いたら本を買って読んでみてね！

<iframe style="width:120px;height:240px;" marginwidth="0" marginheight="0" scrolling="no" frameborder="0" src="//rcm-fe.amazon-adsystem.com/e/cm?lt1=_blank&bc1=000000&IS2=1&bg1=FFFFFF&fc1=000000&lc1=0000FF&t=hirako0928-22&language=ja_JP&o=9&p=8&l=as4&m=amazon&f=ifr&ref=as_ss_li_til&asins=4274226298&linkId=79b704a101bf83e0be3f6260f3b4a05b"></iframe>

## 目次

<!-- toc -->

<!--more-->

## 第一章の概要

技術者として働く上で重要な考え方についてまとめています。マインドや考え方、他者との関わり方について書かれています。
学習のモチベーションが下がったり、仕事に関しての不安を抱えたりしたときに読み返してみると良いなと思った章です。

## 内容のまとめ

### 自分の人生について考えるということ

状況を改善するために行動に起こしましょう。
この業界には驚くほどに様々な機会があります。変化を恐れず、不満に思う点なおかつ改善すべき点があると思ったら着手してみましょう。
状況は変えられるし、変えられなかったとしても、自分の働く場所を変えることもできます。
自分のスキルが陳腐化する前に、行動を起こしてみましょう。

### チームメンバーとの信頼関係と責任について

メンバーとの信頼関係を無責任に傷つけるような行動をしてしまった場合、あなたがどれだけ素晴らしい技術者であったとしても、その信頼を取り戻すためには多大な労力と時間がかかります。場合によっては、修復不可能な亀裂が入ることもあります。信頼関係は、チームでプロジェクトを作り上げるために無くてはならない重要なものです。
ミスをした場合は過ちを認め、他人やプログラムのせいにするのではなく、代替計画や改善策を提案するべきです。
ミスや不手際を報告する前に、一度立ち止まって考え、何か出来ることはないか考えると良いでしょう。
現状を改善するために、専門書や講座の受講、より知識に長けている技術者からのバックアップが必要であれば、恐れずに要求するべきです。

### ソフトウェアが抱える負債について

ソフトウェアは、常に肥大し続けて行きます。”技術的負債”がソフトウェアには常に存在し、その負債が返済されることは大抵ありません。
ソフトウェアの負債は、その時々に応じて、様々な原因によって積み重なっていきます。場合によっては、技術的な理由だけではなく、開発組織の文化やチームメンバーの考え方が原因になっている場合もあります。そういった属人的な原因でソフトウェアの質が下がってしまわないようにするには、『[割れ窓理論](https://ja.wikipedia.org/wiki/%E5%89%B2%E3%82%8C%E7%AA%93%E7%90%86%E8%AB%96)』を活用することができます。割れた窓を放置することは、ソフトウェア全体の質を下げることに繋がります。割れた窓を放置しないようにしましょう。つまり、悪い設計、誤った意思決定、質の低いコードを放置してはいけません。何かしら改善のアクションを起こすか、もし手遅れであるならば炎上する前に逃げる準備をしておきましょう。
そして、自分がソフトウェアの質の低下に繋がる”割れた窓”を作らないようにしましょう。

### 変化の触媒となれ

『[石のスープ](https://ja.wikipedia.org/wiki/%E7%9F%B3%E3%81%AE%E3%82%B9%E3%83%BC%E3%83%97)』という民話があります。ソフトウェアをより良い形に変えるための要素や答えが分かっていても、それは一人で出来ません。周りに協力を求めようとしても、様々な障害や足止めにあうこともあります。そういった時には、道理にかなった要求を考えていきましょう。大きな変化をすぐに！ではなく、少しずつパーツを揃えていきましょう。「この部分を〇〇すれば、もっと良くなりますよ」「この部分をこのように変えると、このようなメリットがありますよ」と、改善後どのような良い状態になっていくのかを相手に見せることができれば、変化に不寛容なメンバーの心を動かすことができるかもしれません。

ただし、注意するべきことは、小さな変化の積み重ねによって、本来完成させようと思っていたものとはかけ離れたソフトウェアが出来てしまうことです。目の前の問題を解決するために小さな変化を起こし続けた結果、目的からどんどん逸れていっていってしまうようなことは避けるべきです。
全体を常に俯瞰するようにしてください。常に自分の周囲でどのようなことが起きているかに目を向けてみてください。

### 充分に良いソフトウェアとは？

> ものごとを良くしようと努力することで、しばしば良かったものまで台無しにしてしまう。
> シェークスピア、『リヤ王』第一幕第四場

完全にバグのないシステムやアプリケーションを開発することは、現実的に考えると不可能です。バグや不具合のないシステムを作ることにストレスをかけるのではなく、十分に良いソフトウェアを作ると良いでしょう。十分に良いとは、システムのユーザーからの要求仕様と合致し、パフォーマンス、プライバシー、セキュリティといった側面の要求に合致している必要があります。作成したシステムが要求仕様に合致しているかを判断するためには、ユーザーに確認をして貰うべきです。
ユーザーからの要求を無視して、機能を追加したり、時間をかけてコードを磨き上げるというのは、プロフェッショナルの行動とは言えません。当然、不可能なスケジュールで開発の約束をしたり、納期に間に合わせるために基本的な技術面を疎かにするのもプロフェッショナルとはありえない行動です。
システムのユーザーを巻き込み、品質要求は明確にするべきです。

### 知識のポートフォリオ

> 知識への投資は常に最高の利息がついてくる。
> ベンジャミン・フランクリン

あなたの知識と経験は、あなたの持つ資産の中で最も重要なものです。
しかし、残念なことに、知識と経験は有効期限がついていることを忘れてはいけません。市場の変化や技術の変化によって、あなたの知識や経験は陳腐化し、的外れなものになっていくことが多々あります。（個人的には特に、Web フロントエンド界隈を見てると感じます）
特に、IT 分野は進歩が早く、変化のスピードは年々加速し続けています。
知識のポートフォリオの管理には、金融ポートフォリオの管理とよく似ている点があります。

1. 真面目な投資家は習慣的に定期的な投資を行います
2. 分散投資は長期的な成功の鍵です。
3. 頭の良い投資家は、堅実な投資と、ハイリスクでハイリターンな投資でポートフォリオのバランスをとっています。
4. 投資家は利益を最大にすべく、安く買い、高く売ろうとします。
5. ポートフォリオは定期的に見直して再分配するべきです。

これらをエンジニアの知識のポートフォリオ管理に置き換えると、このようになります。

1. 定期的に知識への投資をする

- 小さくても定期的に知識への投資のための手間に時間をかけることを怠らないでください。

2. 知識の多様化させる

- より多くの技術に親しむようにしましょう。様々な技術の知識、時には技術とは全く関係のない知識が、あなたの専門分野や業務に役に立つかもしれません。テクノロジーとは関係ののない分野へのスキル投資も忘れないでください。

3. リスクを管理する

- すべてのリソースをハイリスクなものに裂くことは、暴落の危険性があります。かといって、堅実なものにリソースを裂きすぎても、新たな機会や巡ってきたチャンスを逃すことになります。

4. 安値で買い、高値で売る

- 注目されている技術を普及する前に学んでおくということは、高騰する株を探すのと同じぐらい難しいことですが、より大きなリターンが得られう可能性が高くなります。データサイエンスが流行る前から研究室で知識と経験を積んできた技術者は現在大きなリターンを得ているはずです。

5. 見直しと再分配をする

- IT 業界は、常に激しい変化が起こります。先月投資を始めた技術分野が、来月にはすでに冷え切った技術であるといったことがしばしば起こりえます。また、しばらく使っていなかった技術が、再習得の必要に迫られることがあるかもしれません。また、最新の言語を習得していたのであれば、新たな就職先やより良い昇進の機会に巡り会えたかもしれません。

こうした、知識のポートフォリオ管理のために、以下のことを習慣的に行うと良いでしょう。

- 月に一冊のペースで技術書を読む。
  毎月目標を定めて、本を読んでみましょう

- 技術書以外書籍を読む
  ソフトウェアは、機械が使うのではなく人間が使います。

- 講習を受講する
  新たな技術を身につけるにはうってつけです。

- 近場のユーザーグループに参加する
  孤立はあなたの経歴にとって避けるべきことです。

- 異なった環境に慣れ親しんで見る
  Twitter でしばしば、Mac か windows か（ArchLinux か）のような論争を目にすることがありますが、windows 環境でのみ作業をしてきたのであれば、Linux 環境にも親しむ時間をとってください。最新機能を搭載した統合開発環境（IDE）にも触れてみるべきですし、プラグインの入っていない vim や Emacs にも触ってみましょう。

- 最先端に留まり続ける
  現在のプロジェクトが扱っているものとは異なるテクノロジーにかんするニュースやオンライン投稿に目を通しましょう。

常に学習の機会を探し、学習していきましょう。

### 批判的な考え方

インターネットの検索エンジンがまっさきに返してきたものが、最適な選択であると思うべきではありません。
批判的な考え方のキーワードは以下のとおりです。

- 「５つのなぜ」を問う
- 誰にメリットがあるのか？
- コンテキストはなにか？
- それはいつ、どこで有効になるのか？
- なぜこれが問題なのか？

### 伝達しよう

あなたにいくら実力があり、素晴らしアイディア、洗練されたコード、達人的な思考ができても、それを他人に伝達することができなければ、それは究極の不毛と言えるでしょう。
よいアイディアも効果的な意思疎通がなければ、単なるアイディアで終わってしまいます。
以下は、それに役立つキーワードです。

- 聞き手のことを知る
- 言いたいことを知る
- 伝えるタイミングを選ぶ
- 聞き手に合った伝え方を選ぶ
- 見栄えを良くする
- 聞き手を巻き込む
- 聞き手になる
- 相手の立場になる

## 第一章の感想

勉強を進めていくためにも、仕事をするためにも重要な考え方やエッセンスが詰まっている章だったと思います。こういった形で内容をまとめてみると、理解が深まるなと感じたので、読んだ内容を文章にまとめることはぜひやっていきたいです。この章を読むためだけにこの本を買ってもいいのではないか？と思える内容でした。
