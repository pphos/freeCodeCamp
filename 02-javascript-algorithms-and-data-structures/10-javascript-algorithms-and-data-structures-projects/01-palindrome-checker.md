# Palindrome Checker

## Description
引数で指定された文字列が回文である場合は`true`, それ以外の場合は`false`を返す関数を作成してください.

回文とは, 句読点, 大文字と小文字, およびスペースを無視して,
前から読んでも後ろから読んでも, 同じように綴られる単語または文のことを言います.

注意:<br/>
回文をチェックするには, 英数字以外の文字(句読点, スペース, 記号)を全て削除し,
すべてを大文字か小文字に揃える必要があります.

引数として渡される文字列は, "racecar", "RaceCar", "race CAR"など様々な形式をとります.

また, "2A3*3a2", "2A3 3a2", "2_A3 * 3#A2"などの特殊記号を含む文字列も引数である可能性があります.

## Challenge Seed
```js
function palindrome(str) {
  return true;
}

palindrome("eye");
```

## My Solutions
```js
function palindrome(str) {
  // strから記号を取り除き小文字に変換した文字列
  const removed_str = str.replace(/[\W_]/g, '').toLowerCase();
  // removed_strを逆順に並べた文字列
  const palindrome_str = removed_str.split('').reverse().join('');

  return removed_str === palindrome_str;
}

palindrome("eye");
```