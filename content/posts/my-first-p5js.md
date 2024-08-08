+++
title = 'p5.jsを使ってアルゴリズムで画像を生成する'
date = 2024-08-08T21:53:00+09:00
tags = ["興味", "ジェネレーティブアート"]
categories = ["デジタル"]
draft = false
+++

## できあがったもの

カラフルな三角形のパターンが作りたいなって思って、Gemini さんに聞いたら出来上がった。とても可愛い気がする。

回りくどい AI 生成画像（？）

![カラフルな三角形](/posts/colorful-triangle.png)

## コード

変えたのは 三角形のサイズと rotation の箇所くらい。 `random(4) * HALF_PI` だったので 左右の三角もあった。左右まであるとちょっとうるさいなって思ったので上下だけにした。

`random(2) * PI` だと秩序が見えすぎたから無駄なことしてる。

```js:sketch.js
function setup() {
  createCanvas(600, 600);
  noStroke();
}

function draw() {
  // 色の配列
  const colors = ['#E9C46A', '#F4A261', '#E76F51', '#2A9D8F', '#264653'];

  let size = 50; // 三角形のサイズ

  for (let x = 0; x < width; x += size) {
    for (let y = 0; y < height; y += size) {
      // ランダムに色を選ぶ
      let randomIndex = floor(random(colors.length));
      fill(colors[randomIndex]);

      // 三角形をランダムに回転させる
      let rotation = floor(random(6)) * PI / 3; // 0, 60, 120, 180, 240, 300
      push();
      translate(x + size / 2, y + size * sqrt(3) / 2);
      rotate(rotation);
      triangle(-size / 2, -size * sqrt(3) / 2, size / 2, -size * sqrt(3) / 2, 0, 0);
      pop();
    }
  }
  noLoop();
}
```

## 思うこと

こういうパターン系の模様ってとっても好きなのでいろいろやってみたい。

以上！
