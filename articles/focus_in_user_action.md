---
publication_name: "rabee"
title: "iOSのMobile Safari上で自動focusしてキーボードをせり上げる方法"
emoji: "📚"
type: "tech"
topics: ["frontend", "javascript"]
published: false
---
## はじめに
iOS の Mobile Safari にて、ボタンをクリックしてモーダルを開いた瞬間にキーボードを表示させるには一工夫が必要だったのでその話をしたいと思います。

## 実現するために行ったこと
モーダルを開いた瞬間(マウントされた瞬間)にモーダル内に設置している `input` に `focus` させればキーボードを表示できると思っていましたが表示されませんでした。
詳しく見てみると `focus` を呼んだ時に `focus` はしている模様。
そこで調べてみると、キーボードを表示させるにはどうやらユーザーのアクションが必要ということが判明しました。

## 解決策
下記のようにボタンを **クリックした時(ユーザーのアクション)** に行うモーダルを開く処理の後にモーダル内の `input` に `focus` させることで解決できました。

```
let button = document.getElementById('modalButton');

button.addEventListener('click', modalOpen);
function modalOpen() {
  // モーダルを開く処理
  // その後にモーダル内の input に focus させる処理
};
```

## 理由
調べてみたところ、Apple はキーボードを表示させるプログラムのフォーカスを望んでいないとのことで何らかのアクションを行わない限りキーボードが表示がされないみたいです。

## さいごに
ブラウザ特有の挙動で思ったように動かないと解決に余計な時間が掛かってしまうので、少しでも参考になれば幸いです。

## 参考記事
https://zenn.dev/toshimarnie/scraps/f60026fce34e84
