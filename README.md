# promise-waterfall2
---
[![NPM version](http://img.shields.io/npm/v/promise.waterfall2.svg?style=flat)](https://npmjs.org/package/promise.waterfall2)
[![Build Status](http://img.shields.io/travis/xuxihai123/promise.waterfall2/master.svg?style=flat)](http://travis-ci.org/xuxihai123/promise.waterfall2)

> Runs an array of promises in series, each passing their results to the next promise in the array. support an initialization parameter

## Install

```sh
$ npm install promise.waterfall2
```

## Usage

```js
var promiseWaterfall = require('promise.waterfall2')

function makeAdder (a) {
  return function (b) {
    b = b || 0
    return Promise.resolve(a + b)
  }
}

var addOne = makeAdder(1)

promiseWaterfall([
  addOne  // 1
  addOne, // 2
  addOne  // 3
])
.then(console.log)
.catch(console.error)

promiseWaterfall([
    addOne,
    addTwo
],5) // with initialization parameter
.then(console.log)
.catch(console.error)
```

## API

#### `promiseWaterfall(functions,[initialArgs])` -> `promise`

Runs the array of functions in series, waiting for each to resolve and passing each result to the next function in the array.

##### functions

*Required*
Type: `array[function]`
