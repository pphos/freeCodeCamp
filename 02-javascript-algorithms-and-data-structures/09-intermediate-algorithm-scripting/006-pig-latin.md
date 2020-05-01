# Pig Latin

## Description
Pig Latinは英単語を変更する方法であり, 次の規則に従います.

- 単語が子音で始まる場合は, 最初の子音または子音群を取り除き,
それを単語の最後に移動させ, "ay"を付け加えます
- 単語が母音で始まっている場合は, 最後に"way"を付け加えます.

入力された文字列をPig Latinに変換する関数を作成してください.
この時, 入力された文字列は全て小文字の英単語であることが保証されています.

## Challenge Seed
```js
function translatePigLatin(str) {
  return str;
}

translatePigLatin("consonant");
```

## My Solutions
```js
function translatePigLatin(str) {
  const vowels = ['a', 'i', 'u', 'e', 'o'];
  let str_arr = str.split('');
  let str_stack = [];

  for (let i = 0; i < str_arr.length; i++) {
    if (!vowels.includes(str_arr[i])) {
      str_stack.push(...str_arr.splice(i--, 1));
    } else {
      break;
    }
  }

  if (str_stack.length !== 0) {
    return str_arr.concat(str_stack).join('') + 'ay';
  } else {
    return str + 'way';
  }
}

translatePigLatin("consonant");
```

