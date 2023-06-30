---
toc: true
tags:
  - null
categories:
  - null
title: JavaScriptでプレイするRTSゲームを始めた
date: 2023-06-30 22:30:34
---

## 概要

Screeps という、JavaScript でタワーディフェンスをするゲームを始めました。

## 目次

<!-- toc -->

<!--more-->

## Screeps とは？

Steam の商品ページには、このように書いてあります。

> Screeps: World is an open source MMO RTS sandbox game. With all the attributes of a full-fledged strategy game, you control your colony by writing script that operates 24/7 in the single persistent open world filled by other players on par with you.

簡単に説明すると、JavaScript を書いて遊ぶ、リアルタイムストラテジーです。
Creep と呼ばれる Bot を作り、JavaScript で命令を書いて拠点を作ったり、敵 CPU や相手プレイヤーの陣地を占領したりするゲームです。

## なぜ触り始めたのか？

コードを書いて遊ぶネタが欲しくて始めました。一度コードを書いてしまえば、自動で Bot が仕事をしてくれるので、時間をかける必要もなく、お手軽に遊べてとても良いゲームです。
機能の再利用がしやすいように書いたり、Bot を管理しやすいように設計を考えたりする要素があるので、普段勉強していることを楽しく活かせることができそうで良さそうだなと思っています。

## 今日作った PR

てなわけで、今日はゲーム上のエディタで雑に書いたコードをリポジトリに置くための PR を作りました。
https://github.com/yuya-0928/ScreepsPlayground/pull/1

コードを改良しやすいような仕組みを整えてみようと思います。
