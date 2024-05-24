# @diotobtea/minima-et <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![dependency status][deps-svg]][deps-url]
[![dev dependency status][dev-deps-svg]][dev-deps-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

An ESnext spec-compliant `Array.prototype.findLastIndex` shim/polyfill/replacement that works as far down as ES3.

This package implements the [es-shim API](https://github.com/es-shims/api) interface. It works in an ES3-supported environment and complies with the proposed [spec](https://tc39.es/proposal-array-find-from-last).

Because `Array.prototype.findLastIndex` depends on a receiver (the `this` value), the main export takes the array to operate on as the first argument.

## Getting started

```sh
npm install --save @diotobtea/minima-et
```

## Usage/Examples

```js
var findLastIndex = require('@diotobtea/minima-et');
var assert = require('assert');

var arr = [1, [2], [], 3, [[4]]];
var isNumber = function (x) { return typeof x === 'number' };

assert.deepEqual(findLastIndex(arr, isNumber), 3);
```

```js
var findLastIndex = require('@diotobtea/minima-et');
var assert = require('assert');
/* when Array#findLastIndex is not present */
delete Array.prototype.findLastIndex;
var shimmed = findLastIndex.shim();

assert.equal(shimmed, findLastIndex.getPolyfill());
assert.deepEqual(arr.findLastIndex(isNumber), findLastIndex(arr, isNumber));
```

```js
var findLastIndex = require('@diotobtea/minima-et');
var assert = require('assert');
/* when Array#findLastIndex is present */
var shimmed = findLastIndex.shim();

assert.equal(shimmed, Array.prototype.findLastIndex);
assert.deepEqual(arr.findLastIndex(isNumber), findLastIndex(arr, isNumber));
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.org/package/@diotobtea/minima-et
[npm-version-svg]: https://versionbadg.es/diotobtea/minima-et.svg
[deps-svg]: https://david-dm.org/diotobtea/minima-et.svg
[deps-url]: https://david-dm.org/diotobtea/minima-et
[dev-deps-svg]: https://david-dm.org/diotobtea/minima-et/dev-status.svg
[dev-deps-url]: https://david-dm.org/diotobtea/minima-et#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@diotobtea/minima-et.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@diotobtea/minima-et.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@diotobtea/minima-et.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@diotobtea/minima-et
[codecov-image]: https://codecov.io/gh/diotobtea/minima-et/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/diotobtea/minima-et/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/diotobtea/minima-et
[actions-url]: https://github.com/diotobtea/minima-et
