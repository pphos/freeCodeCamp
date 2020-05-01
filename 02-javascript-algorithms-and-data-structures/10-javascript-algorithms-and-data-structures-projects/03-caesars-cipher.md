# Caesars Chipher

## Description
最も単純であり最も広く知られている暗号の一つがシーザー暗号であり, シフト暗号としても知られています.
シフト暗号では, 文字の意味が一定量だけシフトされます.

現代でよく使われているものはROT13暗号で, 文字の値が13桁シフトされます.
したがって, "A" <=> "N", "B" <=> "O"などとなります.

ROT13暗号化された文字列を入力として受け取り, 複合された文字列を返す関数を作成してください.

すべての文字は大文字になります.
アルファベット以外の文字(スペースや句読点など)は変換してはいけません.


## Challenge Seed
```js
function rot13(str) {

  return str;
}

rot13("SERR PBQR PNZC");
```

## My Solutions
```js
function rot13(str) {
  const ROT_NUM = 13;
  const A_CODE = 'A'.charCodeAt(0);
  const Z_CODE = 'Z'.charCodeAt(0);
  const encoded_code = str.split('').map(v => v.charCodeAt(0));
  let decoded_str = '';

  for (let code of encoded_code) {
    if (A_CODE <= code && code <= Z_CODE) {
      const rotated_code = (code - A_CODE + ROT_NUM) % (Z_CODE - A_CODE + 1) + A_CODE;
      
      decoded_str += String.fromCodePoint(rotated_code);
    } else {
      decoded_str += String.fromCodePoint(code);
    }
  }
  
  return decoded_str;
}
rot13("SERR PBQR PNZC");
```