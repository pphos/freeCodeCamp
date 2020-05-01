# Drop it

## Description
配列`arr`が与えられた時に, 配列の最初の要素から各要素を削除し,
関数`func`が`true`を返まで繰り返し処理を行う関数を作成してください.

そして, 関数`func`が`true`を返した時に残りの配列を返すようにしてください.
残りの配列がからの場合は, 空配列を返却してください.

## Challenge Seed
```js
function dropElements(arr, func) {
  return arr;
}

dropElements([1, 2, 3], function(n) {return n < 3; });
```

## My Solutions
```js
function dropElements(arr, func) {
  let copied_arr = arr.slice();

  for (let i = 0; i < copied_arr.length; i++) {
    if (!func(copied_arr[i])) {
      copied_arr.shift();
      i--
    } else {
      break;
    }
  }
  return copied_arr;
}

dropElements([1, 2, 3], function(n) {return n < 3; });
```