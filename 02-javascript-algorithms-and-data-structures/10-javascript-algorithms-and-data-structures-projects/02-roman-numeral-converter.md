# Roman Numeral Converter

## Description
引数で指定された数値をローマ数字に変換する関数を作成してください.

ローマ数字の返り値は全て大文字である必要があります.

## Challenge Seed
```js
function convertToRoman(num) {
 return num;
}

convertToRoman(36);
```

## My Solutions
```js
function convertToRoman(num) {
  // 減数の候補
  const subtracts = [
    { sign: 'M', base: 1000 },
    { sign: 'D', base: 500 },
    { sign: 'C', base: 100 },
    { sign: 'L', base: 50 },
    { sign: 'X', base: 10 },
    { sign: 'V', base: 5 },
    { sign: 'I', base: 1}
  ];
  // 引数をひと桁づつに分割した配列
  let numerical_arr = String(num).split('');
  let numerical_digit = numerical_arr.length;
  
  // 配列の要素に桁数を掛ける
  numerical_arr = numerical_arr.map((v, i) => {
    const number = parseInt(v) * Math.pow(10, numerical_digit -i - 1);
    return { num: number, roman: ''};
  });


  for (let i = 0; i < numerical_arr.length; i++) {
    let copied_num = numerical_arr[i].num;

    for (let j = 0; j < subtracts.length; j++) {
      while (copied_num - subtracts[j].base >= 0) {
        let num_first_digit = parseInt(String(copied_num).charAt(0));

        if (j !== 0 && num_first_digit === 4 || num_first_digit === 9) {
          if (num_first_digit === 4) {
            numerical_arr[i].roman = `${subtracts[j].sign}${subtracts[j-1].sign}`
            copied_num = copied_num - subtracts[j].base - subtracts[j-1].base;
          } else {
            numerical_arr[i].roman = `${subtracts[j+1].sign}${subtracts[j-1].sign}`
            copied_num = copied_num - subtracts[j+1].base - subtracts[j-1].base;
          }
        } else {
          numerical_arr[i].roman += subtracts[j].sign;
          copied_num -= subtracts[j].base;
        }
      }
    }
  }

  return numerical_arr.reduce((prev, current) => {
    return prev + current.roman;
  }, '')
}

convertToRoman(798);
```