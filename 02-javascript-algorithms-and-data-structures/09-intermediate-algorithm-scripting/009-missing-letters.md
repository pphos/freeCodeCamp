# Missing Letters

## Description
引数で渡された文字の範囲で欠落している文字を探して返却する関数を作成してください.<br/>
ただし, 範囲内にすべての文字が存在する場合は, `undefined`を返却してください.

## Challenge Seed
```js
function fearNotLetter(str) {
  return str;
}

fearNotLetter("abce");
```

## My Solutions
```js
function fearNotLetter(str) {
  const first_ascii = str.charCodeAt(0);
  const last_ascii = str.charCodeAt(str.length - 1);

  const sequential_letters = [...Array(last_ascii - first_ascii + 1).keys()].map((index) => {
    return String.fromCodePoint(first_ascii + index);
  });
  const missed_letter = sequential_letters.find((letter) => {
    return !str.split("").includes(letter);
  })

  return missed_letter;
}

fearNotLetter("abce");
```