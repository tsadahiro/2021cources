---
layout: default
title:  "Elmの基本"
date:   2021-04-08 
---

# 基本型と基本演算

## 数値
数値は整数(Int)と実数(Float)に類別されそれらを
併せたものがNumber型になります。
整数除算は/ではなく//です。
べき乗演算子は^です。
剰余は%ではなく関数modByを用います。
{% highlight console %}
> 1 + 1
2 : number
> 3/2
1.5 : Float
> 3//2
1 : Int
> 3/2 + 1
2.5 : Float
> 5^2
25 : number
> modBy 3 5
2 : Int
{% endhighlight %}

## 文字列
文字列の連結演算子は+ではなく++ Stringモジュールに定義されているlen関数により
文字列長を得ます。モジュールについては後述します。
それではincrement演算子は？　ありません。
{% highlight console %}
> "abc" + "def"
-- TYPE MISMATCH ---------------------------------------------------------- REPL

I cannot do addition with String values like this one:

3|   "abc" + "def"
     ^^^^^
The (+) operator only works with Int and Float values.

Hint: Switch to the (++) operator to append strings!

> "abc" ++ "def"
"abcdef" : String
> String.length "abc"
3 : Int
{% endhighlight %}

## 論理型

{% highlight console %}
> True && True
True : Bool
> True && False
False : Bool
> True || False
True : Bool
> False || False
False : Bool
{% endhighlight %}

## 比較

{% highlight console %}
> 3 > 2
True : Bool
> 2 > 3
False : Bool
> 2 >= 3
False : Bool
> "abc" == "abc"
True : Bool
> "abc" < "def"
True : Bool
> "abc" >= "def"
False : Bool
> "abc" /= "def"
True : Bool
> "abc" /= "abc"
False : Bool
{% endhighlight %}

# List, Tuple, Record

## リスト(List)

[List](https://package.elm-lang.org/packages/elm/core/latest/List)は複数の同じ型のデータが並んだものであり、
配列のようですが、配列とは異なります。
この違いについては次第にはっきりと理解できるように
なると思います。

{% highlight console %}
> [1,2,3]
[1,2,3] : List number
> [1,2,"san"]
-- TYPE MISMATCH ---------------------------------------------------------- REPL

The 3rd element of this list does not match all the previous elements:

3|   [1,2,"san"]
          ^^^^^
The 3rd element is a string of type:

    String

But all the previous elements in the list are:

    number
{% endhighlight %}

よく使われる関数の例です。
{% highlight console %}
> List.range 1 100
[1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30,31,32,33,34,35,36,37,38,39,40,41,42,43,44,45,46,47,48,49,50,51,52,53,54,55,56,57,58,59,60,61,62,63,64,65,66,67,68,69,70,71,72,73,74,75,76,77,78,79,80,81,82,83,84,85,86,87,88,89,90,91,92,93,94,95,96,97,98,99,100]
    : List Int
> List.repeat 10 "hello"
["hello","hello","hello","hello","hello","hello","hello","hello","hello","hello"]
    : List String
> x
[1,2,3] : List number
> List.length x
3 : Int
> List.map sqrt x
[1,1.4142135623730951,1.7320508075688772]
    : List Float
> y
[4,5,6] : List number
> List.concat [x, y]
[1,2,3,4,5,6]
    : List number
{% endhighlight %}


## タプル(Tuple)

[Tuple](https://package.elm-lang.org/packages/elm/core/1.0.5/Tuple)は
2,3個の同じ型のデータを組にして並べたものです。
多くのヘルパー関数が準備されているのは2つ組のものです。

{% highlight console %}
> p = (2,3)
(2,3) : ( number, number1 )
> Tuple.first p
2 : number
> Tuple.second p
3 : number
{% endhighlight %}

## レコード

レコードは複数種類のデータをひとまとめにしたデータ型です。

{% highlight console %}
> r={x=2,y=5, col="black"}
{ col = "black", x = 2, y = 5 }
    : { col : String, x : number, y : number1 }
> r.x
2 : number
> r.y
5 : number
> r.col
"black" : String
{% endhighlight %}

フィールドアクセス関数は今後頻繁に使うものの一つです。
レコード型のデータに対してその一部のレコードだけを
指定したものに書き換えたデータを返す**関数**です。

{% highlight console %}
> {r | col="red"}
{ col = "red", x = 2, y = 5 }
    : { col : String, x : number, y : number1 }
{% endhighlight %}

# 関数


<script async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-chtml.js" id="MathJax-script"></script>

## 定義
関数は次のように定義します。
myfuncは引数xに対してxとxの自乗を足し合わせた値を返します。
{% highlight console %}
> myfunc x = x^2 + x
<function> : number -> number
> myfunc 2
6 : number
{% endhighlight %}
2行目にある
{% highlight console %}
<function> : number -> number
{% endhighlight %}
はElmの処理系が関数定義を見てこれが
numberを引数としてnumberを返す関数であることを
推論した結果です。情報数学基礎でよく用いた写像の記号

$$
f:{\mathbb R} \rightarrow {\mathbb R}
$$

を思い出して下さい。
もちろん2変数にすることも3変数にすることも可能です。
変数の個数に上限があるのかどうか知りませんが、知っている人がおられたら
教えて下さい。
{% highlight console %}
> yourfunc x y = x^2 + y^2
<function> : number -> number -> number
> yourfunc 3 3
18 : number
{% endhighlight %}

