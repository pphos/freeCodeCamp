# Arguments Optional

## Description
2つの引数を合計する関数を作成してください.
引数が1つしか与えられていない場合には, 1つの引数を期待して合計を返すようにしてください.

たとえば, `addTogether(2, 3)`は`5`を返し, `addTogether(2)`は関数を返す必要があります.

単一引数でこの関数を呼び出すと, その合計が返されます.
```js
let sumTwoAnd = addTogether(2);
sumTwoAnd(2) // return 5.
```
また, どちらかの引数が有効な数値で無い場合には, `undefined`を返すようにしてください.

## Challenge Seed
```js
function addTogether() {
  return false;
}

addTogether(2,3);
```

## My Solutions
```js
function addTogether() {
  const first = arguments[0];

  if (!Number.isFinite(first)) {
    return;
  }
  
  if (arguments.length === 1) {
    return function (x) {
      if (Number.isFinite(x)) {
        return x + first;
      }
    }
  } else {
    if (Number.isFinite(arguments[1])) {
      return first + arguments[1];
    }
  }
}

addTogether(2,[3]);
```