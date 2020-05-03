# Cash Register

## Description
第1引数(`price`)として販売価格, 第2引数(`cash`)として支払い金額, 
第3引数(`cid`)としてcash-in-drawerを受け入れる`checkCashRegister()`を作成してください.

`cid`は, 利用可能な通貨を一覧表示する2次元配列です.

`checkCashRegister()`関数は, 必ず`status`キーと`change`キーを持つオブジェクトを返す必要があります.

ドロワー内の現金がお釣りより少ない場合や正確なお釣りを返せない場合には,
`{status: "INSUFFICIENT_FUNDS", change: []}`を返します.

ドロワー内の現金とお釣りの金額が等しい場合には,
`{status: "CLOSED", change: [...]}`を返します.

上記以外の場合には, `{status: "OPEN", change: [...]}`を返します.
この時, お釣りの通貨を高額な通貨から順番にならべます.

<table class='table table-striped'>
    <tr>
        <th>Currency Unit</th>
        <th>Amount</th>
    </tr>
    <tr>
        <td>Penny</td>
        <td>$0.01 (PENNY)</td>
    </tr>
    <tr>
        <td>Nickel</td>
        <td>$0.05 (NICKEL)</td>
    </tr>
    <tr>
        <td>Dime</td>
        <td>$0.1 (DIME)</td>
    </tr>
    <tr>
        <td>Quarter</td>
        <td>$0.25 (QUARTER)</td>
    </tr>
    <tr>
        <td>Dollar</td>
        <td>$1 (ONE)</td>
    </tr>
    <tr>
        <td>Five Dollars</td>
        <td>$5 (FIVE)</td>
    </tr>
    <tr>
        <td>Ten Dollars</td>
        <td>$10 (TEN)</td>
    </tr>
    <tr>
        <td>Twenty Dollars</td>
        <td>$20 (TWENTY)</td>
    </tr>
    <tr>
        <td>One-hundred Dollars</td>
        <td>$100 (ONE HUNDRED)</td>
    </tr>
</table>

## Challenge Seed
```js
function checkCashRegister(price, cash, cid) {
  var change;
  return change;
}

checkCashRegister(19.5, 20, [
    ["PENNY", 1.01], 
    ["NICKEL", 2.05], 
    ["DIME", 3.1], 
    ["QUARTER", 4.25], 
    ["ONE", 90], 
    ["FIVE", 55], 
    ["TEN", 20], 
    ["TWENTY", 60], 
    ["ONE HUNDRED", 100]]
);
```
## My Solutions
```js
const CURRENCY_TABLE = {
  "PENNY": 0.01,
  "NICKEL": 0.05,
  "DIME": 0.1,
  "QUARTER": 0.25,
  "ONE": 1,
  "FIVE": 5,
  "TEN": 10,
  "TWENTY": 20,
  "ONE HUNDRED": 100
};

// 2次元配列のdeep copy
function copy2dArray(source) {
  let dist = [];

  for (let i = 0; i < source.length; i++) {
    let tmp_dist = [];
    for (let j = 0; j < source[i].length; j++) {
      tmp_dist.push(source[i][j]);
    }
    dist.push(tmp_dist);
  }
  return dist;
}

// 店の営業状態の確認
function checkStatus(rest_change, changes, cid, init_cid) {
  // お釣りが払えない場合の判定
  if (rest_change > 0) {
    return { status: "INSUFFICIENT_FUNDS", change: [] };
  }

  if (cid.every(v => v[1] === 0)) {
    // レジが空の場合の判定
    return { status: "CLOSED", change: init_cid };
  }

  return { status: "OPEN", change: changes };
}

function checkCashRegister(price, cash, cid) {
  let rest_change = cash - price; // お釣り
  let current_cid = copy2dArray(cid.slice().reverse()); // レジ金を降順表示
  let changes = [];

  for (let i = 0; i < current_cid.length; i++) {
    const cash_unit = CURRENCY_TABLE[current_cid[i][0]];
    let change_unit = 0;

    while (rest_change.toFixed(2) >= cash_unit && current_cid[i][1] > 0) {
      rest_change = rest_change.toFixed(2) - cash_unit;
      change_unit = change_unit + cash_unit;
      current_cid[i][1] = current_cid[i][1].toFixed(2) - cash_unit;
    }

    if (change_unit !== 0) {
      changes.push([current_cid[i][0], change_unit]);
    }
  }
  // 店の営業状態の確認
  return checkStatus(rest_change, changes, current_cid, cid);
}

checkCashRegister(19.5, 20, [
    ["PENNY", 1.01], 
    ["NICKEL", 2.05], 
    ["DIME", 3.1], 
    ["QUARTER", 4.25], 
    ["ONE", 90], 
    ["FIVE", 55], 
    ["TEN", 20], 
    ["TWENTY", 60], 
    ["ONE HUNDRED", 100]]
);
```