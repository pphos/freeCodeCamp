# Sorted Union

## Description
2つ以上の配列を受け取り, 元の配列の順序で一意な値を持つ新しい配列を返却する関数を作成してください.

つまり, 全ての配列に含まれる全ての値は元の順序で含まれる必要があり, 最終的な配列に重複がないようにする必要があります.

一意な数値は元の順序で配列に格納されるべきであり, 最終的な結果の配列は数値順でソートしてはいけません.

## Challenge Seed
```js
function uniteUnique(arr) {
  return arr;
}

uniteUnique([1, 3, 2], [5, 2, 1, 4], [2, 1]);
```

## My Solutions
```js
function uniteUnique(arr) {
  let concat_arr = arguments[0].slice();

  for (let i = 1; i < arguments.length; i++) {
    let  current_arr = arguments[i].slice();

    concat_arr.push(...concat_arr.concat(current_arr).filter((value) => {
      return !concat_arr.includes(value) && current_arr.includes(value);
    }));
  }

  return concat_arr;
}

uniteUnique([1, 3, 2], [5, 2, 1, 4], [2, 1]);
```