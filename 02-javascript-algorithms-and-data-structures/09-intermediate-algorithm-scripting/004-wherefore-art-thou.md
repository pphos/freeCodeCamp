# Wherefore art thou

## Description
オブジェクトの配列(最初の引数)を検査し, `key`と`value`のペアが一致する全てのオブジェクトの配列(2番目の引数)を返す関数を作成しましょう.
`source`オブジェクトの各`key`と`value`のペアを返される配列に含める場合には, 
それらが`collection`オブジェクトに存在している必要があります.

例:<br/>
第1引数が`[ {first: "Romeo", last: "Montague"}, {first: "Mercutio", last: null}, {first: "Tybalt", last: "Capsulet"}]`であり, 第2引数が`{last: "Capulet"}`の場合,
第2引数で渡された`key`と`value`が第1引数の要素に含まれているので, 
第1引数の配列から3番目のオブジェクトを返す必要があります.

## Challenge Seed
```js
function whatIsInAName(collection, source) {
  var arr = [];
  // Only change code below this line


  // Only change code above this line
  return arr;
}

whatIsInAName([
    { first: "Romeo", last: "Montague" },
    { first: "Mercutio", last: null },
    { first: "Tybalt", last: "Capulet" }],
    { last: "Capulet" }
);
```

## My Solutions
```js
function whatIsInAName(collection, source) {
  var arr = [];
  // Only change code below this line
  const source_keys = Object.keys(source);

  arr = collection.filter((item) => {
    return source_keys.every((key) => {
      return item.hasOwnProperty(key) && item[key] === source[key];
    });
  });
  // Only change code above this line
  return arr;
}


whatIsInAName([
    { first: "Romeo", last: "Montague" },
    { first: "Mercutio", last: null },
    { first: "Tybalt", last: "Capulet" }],
    { last: "Capulet" }
);
```