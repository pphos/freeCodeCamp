## Description
<section id='description'>
要素の平均高度を公転周期(秒単位)に変換する配列を作成してください.
引数の配列には, <code>{name: 'name', avgAlt: avgAlt}</code> という形式のオブジェクトが含まれます.
公転周期については<a href="http://en.org/wiki/Orbital_period" target='_blank'>Wikipedia</a>を参照してください.
値は小数点以下を四捨五入して求めてください.
問題において, 軌道上の物体は地球であり, 地球の半径は6367.4447km, 地球のGM値は398600.4418km<sup>3</sup><sup>-2</sup>です.

## Challenge Seed
<section id='challengeSeed'>
<div id='js-seed'>

```js
function orbitalPeriod(arr) {
  var GM = 398600.4418;
  var earthRadius = 6367.4447;
  return arr;
}
orbitalPeriod([{name : "sputnik", avgAlt : 35873.5553}]);
```

</div>
</section>

## My Solutions
<section id='my-solution'>

```js
function orbitalPeriod(arr) {
  var GM = 398600.4418;
  var earthRadius = 6367.4447;
  
  return arr.map((item) => {
    return {
      name: item.name,
      orbitalPeriod: Math.round(2.0 * Math.PI * Math.sqrt(Math.pow(item.avgAlt + earthRadius, 3) / GM))
    };
  });
}

orbitalPeriod([{name : "sputnik", avgAlt : 35873.5553}]);
```

</section>