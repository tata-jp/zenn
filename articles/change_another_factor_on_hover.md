---
publication_name: "rabee"
title: "要素をhoverしたときに、その他の要素を変更する方法"
emoji: "🖱️"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["frontend", "css", "html", "rabee"]
published: false
---
## はじめに
hover した要素以外の子要素や兄弟要素を変化させる方法について解説したいと思います。

## hover時の要素変更方法
今回は下記の3つのパターンを紹介します。

1. hoverした要素の子要素を変化させたい場合
2. hoverした要素の兄弟要素を変更させたい場合
3. hoverした要素の『全ての兄弟要素』の値を変更

### hoverした要素の子要素を変化させたい場合
hoverした要素の子要素を変化させたい場合は下記のように css を指定します。

#### 適用方法
```
hoverする要素(親要素):hover 変化させたい要素(子要素) {
  子要素に当てたいスタイル
}
```
```css
/*css*/
.hover-trigger:hover .hover-blue {
  background-color: blue;
}
```

```html
<!-- html -->
<div class="hover-trigger">
  <div class="hover-red">hoge</div>
</div>
```

### hoverした要素の兄弟要素を変更させたい場合
hoverした要素の兄弟要素を変更させたい場合は下記のように css を指定します。

#### 適用方法
```
hoverする要素(兄要素):hover + 変化させたい要素(弟要素) {
  弟要素に当てたいスタイル
}
```
```css
/*css*/
.hover-trigger:hover + .hover-blue {
  background-color: blue;
}
```
```html
<!-- html -->
<div class="hover-trigger">hoge</div>
<div class="hover-blue">hoge</div>
```


### hoverした要素の全ての兄弟要素の値を変更させたい場合
hoverした要素の全ての兄弟要素の値を変更させたい場合は下記のように css を指定します。
2つ目のパターンと違うのは「+」ではなく「~」を使っている点です。(以下参考記事)

『 + 』が隣接セレクタと言って要素の直後を指定するセレクタに対し、『 ~ 』は間接セレクタと言って基準の要素以降で条件に合う全ての兄弟要素を指定するセレクタになります。
https://junpei-sugiyama.com/hover-another-element-css/

#### 適用方法
```
hoverする要素(兄要素):hover ~ 変化させたい全ての要素(弟要素) {
  全ての弟要素に当てたいスタイル
}
```
```css
/*css*/
.hover-trigger:hover ~ .hover-blue {
  background-color: blue;
}
```
```html
<!-- html -->
<div class="hover-trigger">hoge</div>
<div class="hover-blue">hoge</div>
<div class="hover-blue">hoge</div>
```

## デモ
実際にデモで3つのパターンの動きの違いを載せているので参考ください。

https://runstant.com/tata/projects/e3959b92

## まとめ
要素を hover した時に他の要素を変更するための方法を紹介しました。
開発に当たり hover を使う場面は意外と多いので覚えておいて損は無さそうですね。
ぜひ活用してみてください。