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