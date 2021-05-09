---
layout: default
title:  "Elmの基本2"
date:   2021-04-28 
---

# Html

前回下記のようなコードを実験してみました。

{% highlight elm %}
module First exposing (..)
import Html exposing (text)

main =
    text "Hello World"

{% endhighlight %}

これを次のように改変してみます。

{% highlight elm %}
module First exposing (..)
import Html exposing (..)
import Html.Attributes exposing (..)

main =
    div []
        [
         h1[style "color" "blue"] [text "Hello World"]
        ,ul[] [
              li [] [text "abc"]
             ,li [] [text "def"]
             ]
        ,p[style "background-color" "pink"][
             text "あいうえおあ"
            ]
        ]
{% endhighlight %}

main 関数の出力がブラウザ上に出力されます。

![Screenshot]({{ site.baseurl }}/assets/img/helloworld2.png)


Htmlモジュールの関数を用いてHTMLを出力しています。

基本的なパターンは
{% highlight consle %}
タグ名 属性リスト (Html msg のリスト)
{% endhighlight %}
によりHtml msg型(入れ子構造)の値が返されます。

更に次のように改変します。

{% highlight elm %}
module First exposing (..)
import Html exposing (..)
import Html.Attributes exposing (..)


hiralist = ["あいうえお"
           ,"かきくけこ"
           ,"さしすせそ"]

makeitem: String -> Html msg
makeitem w =
    li [][text w]

main =
    div []
        [
         h1[style "color" "blue"] [text "Hello World"]
        ,ul[] (List.map makeitem hiralist)
        ]

{% endhighlight %}

List.mapにより関数**makeitem**をリスト**hiralist**の
各要素に適用した結果を集めて新たなli要素のリストを作っています。


![Screenshot2]({{ site.baseurl }}/assets/img/listshow.png)
