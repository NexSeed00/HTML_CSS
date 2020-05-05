# アニメーション

CSSを使ったアニメーションの使い方を説明します。
実際にコードを書きながら学んでいきましょう。

1. 準備


## 1. 準備
1. `animation`という名前のフォルダを作成し、その中に`index.html`と`style.css`を追加しましょう。

2. `index.html`の中に以下のコードをコピーしてください。
    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <link rel="stylesheet" href="style.css">
        <title>Document</title>
    </head>
    <body>
        <div class="container">
            <h1>Hello</h1> 
        </div>  
    </body>
    </html>
    ```

3. `style.css`の中に以下のコードをコピーしてください。
   ```css
    * {
    margin: 0;
    padding: 0;
    }
    .container {
        border: 1px solid black;
        width: 100vw;
        height: 700px;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    h1 {
        font-size: 50px;
    }
   ```
   `.container`の中身は、これから書くものが見やすいように要素を中央に配置するためのコードです。

## CSS
h1タグの中の文字「Hello」の大きさを変える`50px`から`100px`に変える、CSSを書いていきます。

## アニメーションを作成する
- アニメーションを作成する場合は、以下のような`@keyframes`というものを使います。以下のコードを`style.css`内の `h1 { font-size: 50px }`の下に追加しましょう。
```css
@keyframes bigger-font {
    from {
        font-size: 50px;
    }
    to {
        font-size: 100px;
    }
}
```
- 上記のコードの説明をします。
- `@keyframes`の隣にあるのは、アニメーションの名前です。好きな名前をつけることができますが、一目見て、どんなアニメーションなのかわかりやすい名前を付けましょう。ここでは`bigger-font`という名前を付けました。
- さて、`@keyframes`の中に`from ...`と`to ...`があります。`from ...`の中には、アニメーションが始まる時の、初期の値を書き、`to ...`の中には、アニメーション終了時の値が入っています。
- 以上のことを要約すると、アニメーション`bigger-font`は、`font-size`を`50px`から`100px`へと移るアニメーションという意味です。
- `from`と`to`意外に、`%`を使う方法もあります。この場合は、間の地点での値も書くことができます。
```css
@keyframes bigger-font {
    0% {
        font-size: 50px;
    }
    50% {
        font-size: 150px;
    }
    100% {
        font-size: 100px;
    }
}
```
この場合、文字の大きさは、50pxからスタートし、150pxまで大きくなった後、100pxまで小さくなります。

## アニメーションを追加する
- 次に行うのは、今作成したアニメーションを付けたいセレクタの中に書き加えることです。
- ここでは`h1`タグの中のコンテント（Hello）の大きさを変えたいので、`style.css`の`h1`の中に追加するアニメーションの情報を書いていきます。
```css
h1 {
    font-size: 50px;
    animation-name: bigger-font;
}
```
- アニメーションを追加したい場合、`animation-name`というプロパティを使います。値は、先ほど作成した、アニメーションの名前である`bigger-font`です。
- これだけでは、アニメーションは作動しません。アニメーションを動かすには、詳しい設定を書いていかなければなりません。
- ここで説明するのは以下の６つのプロパティです。
  <!-- - animation-duration
  - animation-timing-function
  - animation-delay
  - animation-iteration-count
  - animation-direction
  - animation-fill-mode: forwards; -->

|プロパティ|説明|値の例|
|:---:|:---|:---|
|animation-duration|アニメーション全体の時間| 3s|
- アニメーションが何秒かけて実行されるのかを指定します。
- 値には、秒数を書き、数字の後ろに`s`を付けて書きます。`s`は`second(秒)`という意味です。また、`ms(millisecond)`と書くこともでき、1000分の１秒（0.001秒)単位でも指定もできます。


|プロパティ|説明|値の例|
|:---:|:---|:---|
|animation-timing-function|アニメーションの動き方、一定のスピードで動かしたり、始めと終わりだけゆっくりにするなどの設定ができる| linear, ease-in |
|animation-delay| アニメーションを遅らせる。指定した秒数経過した後に、アニメーションが動くようにできる| 2s |
|animation-iteration-count|繰り返す回数を指定する| 2, infinite|
|animation-direction|アニメーションの向きを指定する| normal, reverse, alternate, alternate-reverse|
|animation-fill-mode|アニメーション終了時の値をどこに合わせるかしている（forward）なら、終了時の値がそのままキープされ、初期値に
戻らない|none, forwards, backwards, both|