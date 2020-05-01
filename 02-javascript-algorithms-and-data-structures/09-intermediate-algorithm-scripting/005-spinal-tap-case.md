# Spinal Tap Case

## Description
文字列を全てspinal caseに変換する関数を作成してください.
spinal caseにおいて, 全ての単語が小文字であり, それらは - で結合されています.

## Challenge Seed
```js
function spinalCase(str) {
  return str;
}

spinalCase('This Is Spinal Tap');
```

## My Solutions
```js
function spinalCase(str) {
  return str.match(/[A-z][a-z]+/g).map((value) => {
    return value.toLowerCase();
  }).join("-");
}

spinalCase('This Is Spinal Tap');
```