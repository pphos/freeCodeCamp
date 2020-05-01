# Seach and Replace

## Description
与えられた引数を用いて文の検索と置換を行い, 新しい文を返す関数を作成してください.

第1引数は, 検索と置換を実行する文です.<br/>
第2引数は, 置換対象の単語です.<br/>
第3引数は, 第2引数の後に置き換える単語です.

注意:<br/>
元の単語を置き換えるときは, 最初の文字の大文字と小文字の関係を保持するようにしてください.
例えば, "Book"という単語を"dog"という単語に置き換える場合は, "Dog"として置き換える必要があります.

## Challenge Seed
```js
function myReplace(str, before, after) {
  return str;
}

myReplace("A quick brown fox jumped over the lazy dog", "jumped", "leaped");
```

## My Solutions
```js
const toCapital = (str => {
  return str.charAt(0).toUpperCase() + str.slice(1);
});

const toSmall = (str => {
  return str.charAt(0).toLowerCase() + str.slice(1);
});

const isUpperCase = (str => {
  return str === toCapital(str);
});

function myReplace(str, before, after) {
  let replaced_word = isUpperCase(before) ? toCapital(after) : toSmall(after);

  return str.replace(before, replaced_word);
}

myReplace("A quick brown fox jumped over the lazy dog", "jumped", "leaped");
```