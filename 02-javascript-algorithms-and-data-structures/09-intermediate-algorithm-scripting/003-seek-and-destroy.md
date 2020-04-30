# Seek and Destroy

## Description
初期配列(destroy関数の最初の引数)が提供され, その後に1つ以上の引数が続きます.
後に続く引数と同じ値を持つすべての要素を初期配列から削除する関数を作成してください.

## Challenge Seed
```js
function destroyer(arr) {
  return arr;
}

destroyer([1, 2, 3, 1, 2, 3], 2, 3);
```

## My Solutions
```js
function destroyer(arr) {
  let remove_candidates = [...arguments].slice(1);

  return arr.slice().filter((value) => {
    return !remove_candidates.includes(value);
  });
}

destroyer([1, 2, 3, 1, 2, 3], 2, 3);
```