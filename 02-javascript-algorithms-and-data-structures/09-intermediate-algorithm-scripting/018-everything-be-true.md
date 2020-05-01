# Everything Be True

## Description
第2引数`pre`が第1引数`collection`の全要素に対してtruthyであることを検査する関数を作成してください.

オブジェクトの配列`collection`が与えられており, `pre`はオブジェクトのプロパティです.
その値がtruthyであれば`true`を返し, そうでなければ`false`を返すようにしてください.

JavaScriptでは, truthy値とは, 真理値の文脈で評価されたときに`true`に変換される値のことです.

オブジェクトのプロパティには, ドット記法または[]記法のいずれかでアクセスできることを覚えておいてください.

## Challenge Seed
```js
function truthCheck(collection, pre) {
  return pre;
}

truthCheck([
  {"user": "Tinky-Winky", "sex": "male"}, 
  {"user": "Dipsy", "sex": "male"}, 
  {"user": "Laa-Laa", "sex": "female"}, 
  {"user": "Po", "sex": "female"}], "sex");
```

## My Solutions
```js
function truthCheck(collection, pre) {
  return collection.every((item) => {
    return item.hasOwnProperty(pre) && Boolean(item[pre]);
  });
}

truthCheck([
  {"user": "Tinky-Winky", "sex": "male"}, 
  {"user": "Dipsy", "sex": "male"}, 
  {"user": "Laa-Laa", "sex": "female"}, 
  {"user": "Po", "sex": "female"}], "sex");
```