# Make a Person

## Description
以下のメソッドをオブジェクトコンストラクタに追加してください.

```js
getFirstName()
getLastName()
getFullName()
setFirstName(first)
setLastName(last)
setFullName(firstAndLast)
```

テストを実行して, 各メソッドの予想される出力を確認してください.
引数を取るメソッドは, 引数を1つだけ受け入れる必要があり, それは文字列である必要があります.
また, これらのメソッドが, オブジェクトと対話するための唯一の手段である必要があります.

## Challenge Seed
```js
var Person = function(firstAndLast) {
  // Complete the method below and implement the others similarly
  this.getFullName = function() {
    return "";
  };
  return firstAndLast;
};

var bob = new Person('Bob Ross');
bob.getFullName();

```
## My Solutions
```js
var Person = function(firstAndLast) {
  // Complete the method below and implement the others similarly
  let full = firstAndLast.split(" ");

  this.getFirstName = function() {
    return full[0];
  };
  this.getLastName = function() {
    return full[1];
  };
  this.getFullName = function() {
    return `${full[0]} ${full[1]}`;
  };
  
  this.setFirstName = function(first) {
    full[0] = first;
  };
  this.setLastName = function(last) {
    full[1] = last;
  };
  this.setFullName = function(firstAndLast) {
    [full[0], full[1]] = firstAndLast.split(" ");
  }
};

var bob = new Person('Bob Ross');
bob.getFullName();
```