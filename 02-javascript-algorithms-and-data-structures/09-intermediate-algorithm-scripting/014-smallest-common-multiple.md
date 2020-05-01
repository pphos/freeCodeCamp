# Smallest Common Multiple

## Description
与えられた引数のうち, これらの引数の範囲の全ての連番の数値で割り切れる最小公倍数を求める関数を作成してください.

与えられる引数の範囲は, 必ずしも昇順で並んでいるとか限りません.

例えば, 1と3が与えられた場合, 1と3の間の全ての数値で割り切れる最小公倍数を求めます.
この時の答えは6です.

## Challenge Seed
```js
function smallestCommons(arr) {
  return arr;
}


smallestCommons([1,5]);
```

## My Solutions
```js
const Gcd = (m, n) => {
  while (m % n != 0) {
    [n, m] = [m % n, n]
  }
  return n;
};

const lcm = (n, m) => {
  return n * m / Gcd(n, m);
}

function smallestCommons(arr) {
  const min = Math.min(...arr);
  const max = Math.max(...arr);
  const min_to_max = [...Array(max - min + 1).keys()].map(v => min + v);

  return min_to_max.reduce((m, n) => {
    return lcm(m, n);
  }, min_to_max[0])
}

smallestCommons([1,5]);
```