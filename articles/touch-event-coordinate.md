---
publication_name: "rabee"
title: "Android でタッチイベントの座標を取得しようとした時に pageY の値が取れなかった話"
emoji: "📚"
type: "tech"
topics: ["frontend", "javascript", "touch", "Rabee"]
published: true
---
## はじめに
Pull-to-Refresh を実装していたときに iOS では touch イベントで渡ってくる pageY を使って座標を取得出来ていたのに対し、 Android だと pageY の座標を取得できませんでした。

## iOS で座標が取得できていたコード
```js
let pageY = 0;
let touchArea = document.getElementById('touchArea');
touchArea.addEventListener('touchstart', start);

function start(event) {
  pageY = event.pageY;
  // ios
  console.log(pageY); // 231.2100219726562
  // Android
  console.log(pageY); // undefined
};
```

上記のように touchstart イベントで渡ってきたイベントオブジェクト内にある pageY の値を参照することで Y 座標を取得できていました。

しかし、 Android で動作確認したところ上記の pageY の値は undefined となっていました。

## 原因
イベントオブジェクトの中身を見てみるとイベント情報は取得できているが、pageY というプロパティが存在しない...
そこで調べてみたところ、どうやら iOS と Android の間で取得できるタッチイベントのイベント情報が異なることが原因でした。

## 解決策
下記のようにイベントオブジェクト内にある3種の TouchList を使用すれば iOS と Android どちらも座標を正しく取得することが出来ます。
ここでは changedTouches を使っています。
changedTouches が配列なのは同時にタッチされたポイント（指）の数がそのまま配列になるためです。

```js
let pageY = 0;
let touchArea = document.getElementById('touchArea');
touchArea.addEventListener('touchstart', start);

function start(event) {
  pageY = event.changedTouches[0].pageY;
  // ios
  console.log(pageY); // 231.2100219726562
  // Android
  console.log(pageY); // 231.2100219726562
};
```

ちなみに他の TouchList は touches と targetTouches があります。
使い分けに関しては下記をご確認ください。
https://developer.mozilla.org/ja/docs/Web/API/TouchEvent

## さいごに
iOS ではうまく動いていたのに Android だとうまく動かないみたいなことは起こりがちだと思うので、少しでも参考にしていただけると幸いです。