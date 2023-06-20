---
title: とりあえずRustに入門してみる！
date: 2021-10-02 03:57:54
toc: true
tags:
  - Rust
categories:
  - Bot開発
  - ハンズオン
---

こんばんは！
思い立って Rust に入門してみました。

## 目次

<!-- toc -->

<!--more-->

## きっかけ

Discord.py の開発者が、Github 上で開発終了の宣言をしました。手元に動いている DiscordBot が 3 つほどありますので、Discord.py 以外になにか良いものは無いかと探しています。
DiscordBot を作っている友人が、Rust 使って作り直していて、Python と近い感覚で書けるからいいよーといった感想を聞いたので興味を持ち、入門しています。

<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">Rust使ってDiscordBot動かしてみた <a href="https://t.co/gDdWd8okkp">pic.twitter.com/gDdWd8okkp</a></p>&mdash; 慕狼ゆに@ぷろぐらむよわよわ (@YYa0928) <a href="https://twitter.com/YYa0928/status/1443957594897326083?ref_src=twsrc%5Etfw">October 1, 2021</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">真似したサイト。<br>一旦なんとなく真似してみて、<a href="https://t.co/Jnm7heVjWz">https://t.co/Jnm7heVjWz</a>と似たような感覚で作れそうだなぁって気持ちになった<a href="https://t.co/9674JCIWm6">https://t.co/9674JCIWm6</a></p>&mdash; 慕狼ゆに@ぷろぐらむよわよわ (@YYa0928) <a href="https://twitter.com/YYa0928/status/1443957866549768199?ref_src=twsrc%5Etfw">October 1, 2021</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

環境構築、とりあえず Hello World をするの２つは試しにやることができました。Rust の書き方になれるために、FizzBuss を書いたり Atcorder A 問題レベルを Rust で解いてみるなどをしてみようかなと思っています。
