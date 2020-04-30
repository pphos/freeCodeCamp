# Diff Two Arrays

## Description
2つの配列を比較し, 指定された2つの配列のどちらか一方のみに存在し, 
両方には存在しない要素を含む新しい配列を返す関数を作成してください.

注意:<br/>
配列とその要素を任意の順序で返すことができます.

## Challenge Seed
```js
function diffArray(arr1, arr2) {
  var newArr = [];
  return newArr;
}

diffArray([1, 2, 3, 5], [1, 2, 3, 4, 5]);
```

## My Solutions
```js
function diffArray(arr1, arr2) {
  return arr1.concat(arr2).filter((item) => {
    return !arr1.includes(item) || !arr2.includes(item);
  });
}

diffArray([1, 2, 3, 5], [1, 2, 3, 4, 5]);
```