---
publication_name: "rabee"
title: "reduce を使って配列の合計を出してみた"
emoji: "🌟"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["frontend", "javascript", "reduce", "Rabee"]
published: false
---
## はじめに
配列にある値の合計値を取得したいという時によく for 文や forEach メソッドで値を取得していましたが、reduceメソッドを使ってスマートに取得できることを学んだので今回紹介したいと思います。

## コード
下記のコードで配列の nums に格納されている値の合計値を取得して console.log に出力しています。

reduce の基本となる構文は以下のようになっています。

```js
配列.reduce(function(累積値, 要素) { });
```

```js
let nums = [1, 2, 4, 8, 16, 32];
let total_num = nums.reduce((a, b) => {
  return a + b;
});
```

ポイントとして、各配列要素でコールバック関数を適用し、その結果を次の要素へと引き継ぎ、最終的な要素での計算結果が返り値となるプロセスが特徴です。
よって計算の流れはこのようになります。

```js
計算1回目: 0 + 1 = 0 
計算2回目: 1 + 2 = 3
計算3回目: 3 + 4 = 7
計算4回目: 7 + 8 = 15
計算5回目: 15 + 16 = 31
計算6回目: 31 + 32 = 63 // reduce関数として返す返り値
```

出力結果

```js
total_num // 63
```

## デモ

https://runstant.com/tata/projects/b8a4a4c6

## まとめ
reduce は配列の要素を単一の値に累積する便利な関数ですが、使ってみないとイメージが中々湧きづらいかと思いますので参考に使ってみていただけると幸いです。
公式Docも下記に載せているので良ければ読んでみてください。

https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce