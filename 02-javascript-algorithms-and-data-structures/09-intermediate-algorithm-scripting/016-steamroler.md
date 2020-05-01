# Steamroller

## Description
ネストされた配列を1次元配列に変換する関数を作成してください.
作成する関数は多重ネストに対応する必要があります.

## Challenge Seed
```js
function steamrollArray(arr) {
  return arr;
}

steamrollArray([1, [2], [3, [[4]]]]);
```

## My Solutions
```js
function steamrollArray(arr) {
  let flattened_arr = [];

  for (let item of arr) {
    if (Array.isArray(item)) {
      while (item.length > 0) {
        let element = item.shift();
        if (Array.isArray(element)) {
          item.unshift(element.shift())
        } else {
          flattened_arr.push(element)
        }
      }
    } else {
      flattened_arr.push(item);
    }
  }
  return flattened_arr;
}

steamrollArray([1, [2], [3, [[4]]]]);
```