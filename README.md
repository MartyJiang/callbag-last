# callbag-last

[Callbag](https://github.com/callbag/callbag) operator that emit the last value emitted from source on completion, based on provided expression.

`npm install callbag-last`

`last(predicate?: (v: any) => Boolean, resultSelector?: (v: any) => any)`

```javascript
const {
  pipe,
  interval,
  take,
  fromIter,
  forEach
} = require('callbag-basics');

const last = require('callbag-last');

pipe(
  interval(100),
  take(5),
  last(),
  forEach(v => console.log(v)) // 4
);

pipe(
  interval(100),
  take(5),
  last(v => v % 3 === 0, v => `value: ${v}`),
  forEach(v => console.log(v)) // value: 3
);

pipe(
  fromIter([1, 2, 3, 4]),
  last(),
  forEach(v => console.log(v)) // 4
);
```
