# Sum All Numbers in a Range

## Description
2つの数値を要素に持つ配列を関数の引数として与えた時に,
その合計と2つの数値の間の合計を返す関数を作成してください.
ただし, 配列の最初の要素が小さい方の数値であるとは限りません.

例:<br/>
1から4までの数値の合計は10であるため, `sumAll([4, 1])`は10を返すはずです.

## Challenge Seed
```js
function sumAll(arr) {
  return 1;
}

sumAll([1, 4]);
```

## My Solutions
```js
function sumAll(arr) {
  const min = Math.min(...arr);
  const max = Math.max(...arr);
  
  return [...Array(max - min + 1).keys()].map((value) => {
    return value + min;
  }).reduce((sum, value) => {
    return sum + value;
  }, 0);
}

sumAll([1, 4]);
```