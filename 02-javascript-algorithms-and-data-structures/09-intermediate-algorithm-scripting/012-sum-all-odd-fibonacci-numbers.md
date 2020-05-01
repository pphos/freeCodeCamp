# Sum All Odd Fibonacci Numbers

## Description
正の整数`num`が与えられた時に, `num`以下の全ての奇数のフィボナッチ数の合計を返す関数を作成してください.

フィボナッチ数列の最初の2つの数字は1と1であり,
数列内に追加される全ての数値は, 2つ前の数値の合計です.
フィボナッチ数列の最初の6つの数値は, 1, 1, 2, 3, 5, 8です.

例えば, 10以下の奇数のフィボナッチ数は1, 1, 3, 5であるため, `sumFibs(10)`は10を返す必要があります.

## Challenge Seed
```js
function sumFibs(num) {
  return num;
}

sumFibs(4);
```

## My Solutions
```js
function sumFibs(num) {
  let [new_fibs, fibs, prev] = [1, 1, 1];
  let sum_odd_fibs = 2;

  while (fibs + prev <= num) {
    new_fibs = fibs + prev;
    if (new_fibs % 2 !== 0) {
      sum_odd_fibs += new_fibs;
    }
    [prev, fibs] = [fibs, new_fibs];
  }
  
  return sum_odd_fibs;
}

sumFibs(10);
```