---
layout: default
title:  "準備"
date:   2021-04-07 
---

# Elmのインストール

## node

nodeというソフトウェアをまずインストールしましょう。

[Macにnodeをインストール](https://qiita.com/kyosuke5_20/items/c5f68fc9d89b84c0df09)

## npmを用いたインストール

{% highlight consle %}
$ npm install -g elm
{% endhighlight %}

## repl
端末を開いてelm replというコマンドを打つと
対話的なインタープリーターが起動します。

{% highlight consle %}
sadahiro@taizo:~/lecture/21/ghp/2021cources/docs$ elm repl
---- Elm 0.19.1 ----------------------------------------------------------------
Say :help for help and :exit to exit! More at <https://elm-lang.org/0.19.1/repl>
--------------------------------------------------------------------------------
> "abc" ++ "def"
"abcdef" : String
> 1 + 1
2 : number
> 
{% endhighlight %}

## emacs

emacsを使う人が多いと思います。Elm-modeと呼ばれる
Elm開発用のmajor modeを用いることにします。

[emacsのパッケージツール](https://emacs-jp.github.io/packages/package)

## 動作テスト

- 端末を開いてテストプロジェクトのフォルダを作り,そこに移ります。
{% highlight console %}
sadahiro@taizo:~/lecture/21/3pro$ mkdir first
sadahiro@taizo:~/lecture/21/3pro$ cd first
{% endhighlight %}

- elm initによりプロジェクトを初期化します。
{% highlight console %}
sadahiro@taizo:~/lecture/21/3pro/first$ elm init
Hello! Elm projects always start with an elm.json file. I can create them!

Now you may be wondering, what will be in this file? How do I add Elm files to
my project? How do I see it in the browser? How will my code grow? Do I need
more directories? What about tests? Etc.

Check out <https://elm-lang.org/0.19.1/init> for all the answers!

Knowing all that, would you like me to create an elm.json file now? [Y/n]: 
Okay, I created it. Now read that link!
{% endhighlight %}

- emacsを開きsrcフォルダの下に以下の内容のソースファイルをFirst.elmという名前で作成します。
(Firstでなくてもなんでもよいのですが、先頭は大文字にしてください。)
{% highlight elm %}
module First exposing (..)
import Html exposing (text)

main =
    text "Hello World"

{% endhighlight %}

- 端末からelm reactorと入力すると開発用サーバーが起動します。

{% highlight console %}
sadahiro@taizo:~/lecture/21/3pro/first$ elm reactor
Go to http://localhost:8000 to see your project dashboard.
{% endhighlight %}

- 書かれている通り、http://localhost:8000
にブラウザでアクセスします。

![screenshot](/2021courses/assets/img/reactorpage.png)

- First.elmを開いて次のようなページが表示されたら準備完了です。

![screenshot2](assets/img/First.png)

