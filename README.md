# xy-parser

[![NPM version][npm-image]][npm-url]
[![Test coverage][codecov-image]][codecov-url]
[![npm download][download-image]][download-url]

Parse a text-file and convert it to an array of XY points.

## Installation

`$ npm install --save xy-parser`

## Usage

```js
import { parseXY } from "xy-parser";
const data = `My file
1   2
3   4
5   6
7   8`;
const result = parseXY(data);
/* result ->
    {
      x: [1, 3, 5, 7],
      y: [2, 4, 6, 8]
    }
  }
*/

const result2 = parseXY(data, { keepInfo: true });
/* result2 ->
    data: {
      x: [1, 3, 5, 7],
      y: [2, 4, 6, 8]
    },
    info: [
      'My file'
    ]
  }
*/
```

The `bestGuess` option will try to determine which columns should be used.

If there are 3 columns and the first column is a sequential number starting at '1' it looks 
like this is a line number, we will ignore it.

If there are many columns maybe we have a format like X1, Y1, X2, Y2, ... in this cases if one
column on two is a monotone series we will parse it correctly.

## [API Documentation](https://cheminfo.github.io/xy-parser/)

## License

[MIT](./LICENSE)

[npm-image]: https://img.shields.io/npm/v/xy-parser.svg?style=flat-square
[npm-url]: https://www.npmjs.com/package/xy-parser
[codecov-image]: https://img.shields.io/codecov/c/github/cheminfo/xy-parser.svg?style=flat-square
[codecov-url]: https://codecov.io/gh/cheminfo/xy-parser
[download-image]: https://img.shields.io/npm/dm/xy-parser.svg?style=flat-square
[download-url]: https://www.npmjs.com/package/xy-parser
