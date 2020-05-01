# DNA Pairing

## Description
問題のDNAストランドにはペア要素がありません.
それぞれの文字を取り, そのペアを取得し, 結果を2次元配列として返す関数を作成してください.

ベースペアはATとGCのペアです.
欠落している要素を与えられた文字と一致させてください.
そして, 与えられてた文字をそれぞれの配列の最初の要素として返却してください.

例えば, GCGが入力の場合, ` [["G", "C"], ["C","G"],["G", "C"]]`を返却します.
欠落している要素とそのペアの文字は配列で1つにまとめられ, 
すべての配列は1つの配列にまとめられます.

## Challenge Seed
```js
function pairElement(str) {
  return str;
}

pairElement("GCG");
```

## My Solutions
```js
function pairElement(str) {
  return str.split("").map((char) => {
    switch (char) {
      case "A":
        return ["A", "T"];
      case "T":
        return ["T", "A"];
      case "G":
        return ["G", "C"];
      case "C":
        return ["C", "G"];
    }
  });
}

pairElement("GCG");
```