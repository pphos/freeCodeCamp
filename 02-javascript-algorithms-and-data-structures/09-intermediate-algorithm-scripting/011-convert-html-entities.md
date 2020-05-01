# Convert HTML Entities

## Description
文字列内の&, <, >, ", 'を対応するHTMLエンティティに変換する関数を作成してください.

## Challenge Seed
```js
function convertHTML(str) {
  return str;
}

convertHTML("Dolce & Gabbana");
```

## My Solutions
```js
function convertHTML(str) {
  const html_entities = [
    { char: '&', entity: '&amp;' },
    { char: '<', entity: '&lt;' },
    { char: '>', entity: '&gt;' },
    { char: '"', entity: '&quot;' },
    { char: '\'', entity: '&apos;' }
  ]

  let replaced_str = str.slice();
  for (let html_entity of html_entities) {
    const regex = new RegExp(html_entity.char, 'g');
    replaced_str = replaced_str.replace(regex, html_entity.entity);
  }

  return replaced_str;
}

convertHTML("Dolce & Gabbana");
```
