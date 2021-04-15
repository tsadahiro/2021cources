---
layout: default
title:  "目的・概要"
date:   2021-04-02 
---

# この授業で学ぶ内容

[Elm](https://guide.elm-lang.org/)という言語を用いてパズルやゲームのアプリケーションを
作成します。

1. (ゲームアプリとしての）基本操作・ユーザインターフェース
2. 完成判定
3. 求解と解表示

を基本機能として実装します。また、パズルの種類によっては

　4. 問題の自動生成

も出来るとよいと思います。
一般的には番号の順に難易度があがると思われます。

　5. 問題(パズル)の難しさの評価

などに興味がある人もいるかもしれませんがこの授業では
取り扱えません。
完成したゲームは例えば[github](https://github.com/)などを通じて公開します。

## 例

以下はElmで作成したスライドパズルです。
1.のみの状態です。

<script src="{{ site.baseurl }}/assets/js/main.js"></script>
  <div id="myapp" ></div>
  <script>
  var app = Elm.Main.init({
    node: document.getElementById('myapp')
  });
  </script>



# 参考文献

- [シカゴ大学のcs223](https://www.classes.cs.uchicago.edu/archive/2019/spring/22300-1/)
- [Elmガイド](https://guide.elm-lang.jp/)
- [99 problems solved in Elm](https://johncrane.gitbooks.io/ninety-nine-elm-problems/content/)
- [Examples](https://elm-lang.org/examples)
