# Sum All Primes

## Description
素数とは, 1より大きい整数で, 自身と1以外でのみ割り切れる数です.
例えば, 2は1と2でのみ割り切れるため素数です.
対象的に, 4は1, 2, 4で割り切れるため素数ではありません.

`num`以下の全ての素数の合計を返す`sumPrimes`関数を作成してください.

## Challenge Seed
```js
function sumPrimes(num) {
  return num;
}

sumPrimes(10);

```

## My Solutions
```js
function sumPrimes(num) {
  let target = [...Array(num - 1).keys()].map(v => v + 2);
  let primes = [];

  while (target.length > 0) {
    const x = target.shift();

    primes.push(x);
    target = target.filter((value) => {
      return value % x !== 0;
    });
  }
  
  return primes.reduce((sum, value) => {
    return sum + value;
  }, 0);
}

sumPrimes(10);
```