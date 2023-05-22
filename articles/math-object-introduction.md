---
publication_name: "rabee"
title: "数値計算に役立つMathメソッドの紹介"
emoji: "🌟"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["frontend", "math", "javascript", "rabee"]
published: false
---
## はじめに
Math を使って数値計算する方法を例と解説を交えて、備忘録がてらにまとめてみようと思います。

## Math について
以下 MDN より参照
> Math は、数学的な定数と関数を提供するプロパティとメソッドを持つ、組み込みのオブジェクトです。関数オブジェクトではありません。

## Mathメソッドの解説
具体的にどのようなメソッドがあるか紹介していきます。

### 小数点以下を四捨五入/切り上げ/切り捨てする Math.round, Math.ceil, Math.floor

Math.round で四捨五入、Math.ceil で切り上げ、Math.floor で切り捨てが出来ます。

```js
// 小数点以下を四捨五入
Math.round('8.75');
// 9

// 小数点以下を切り上げ
Math.ceil('5.3');
// 6

Math.ceil('5.8');
// 6

// 小数点以下を切り捨て
Math.floor('5.3');
// 5

Math.floor('5.8');
// 5
```

### 複数ある数値の中で最大値・最小値を求める Math.max, Math.min

Math.max で最大値を、Math.min で最小値を求められます。

```js
// 最大値を取得
Math.max(1, 3, 5, 7);
// 7

// 最小値を取得
Math.min(1, 3, 5, 7);
// 1
```

配列の場合はスプレッド構文を用いて以下のように求められます。
※引数には上限があるので、大きな配列を扱う際は注意が必要です(以下参照)

https://qiita.com/mod_poppo/items/f3fcbc673526c84b9387

```js
let nums = [1, 3, 5, 7];

// 最大値を取得
Math.max(...nums);
// 7

// 最小値を取得
Math.min(...nums);
// 1
```

### 絶対値を取得する Math.abs

Math.abs は引数に数値を指定することによって絶対値を取得できます。

```js
Math.abs(8);
// 8

Math.abs(-8);
// 8
```

### 乱数を生成する Math.random

Math.random は乱数を生成し返します。

```js
Math.random();
// 0.1779214911120237
```

注意点として Math.random() で実行した場合は0〜1未満までの小数による乱数を生成します。
範囲(最大値、最小値)を指定する場合は上記のコードに処理を加える必要があります。

```js
// 0〜10.9999･･･の間の乱数を取得(最大値)
Math.random() * 11;
// 6.119739403298274

// 5〜10.9999･･･の間の乱数を取得(最小値~最大値)
Math.random() * 6 + 5;
// 9.000008996407539
```

### 平方根を計算する Math.sqrt

Math.sqrt は指定した値の平方根を計算します。
平方根とは、その数を二乗した結果が元の数になる数のことを指します。

```js
// √4
Math.sqrt(4);
// 2

// √9
Math.sqrt(9);
// 3
```

### べき乗を求める Math.pow

Math.pow はべき乗を計算します。
べき乗とは、ある数を指定された回数だけ自身と掛け合わせた結果を求めることを指します。
記述方法は Math.pow(底,指数) となります。

```js
// 2の4乗を取得(2×2×2×2)
Math.pow(2, 4);
// 16

// 4の4乗を取得(4×4×4×4)
Math.pow(4, 4);
// 256
```

## さいごに
Math オブジェクトのメソッドをいくつか紹介しましたが、他にもまだあるので興味のある方は是非 MDN のドキュメントを参照してください。
数値計算において、役立つメソッドなのでこの記事が少しでも参考になれば幸いです。

https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Math