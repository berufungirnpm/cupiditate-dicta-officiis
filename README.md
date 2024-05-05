# @berufungirnpm/cupiditate-dicta-officiis <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

An ESnext spec-compliant `Object.groupBy` shim/polyfill/replacement that works as far down as ES3.

This package implements the [es-shim API](https://github.com/es-shims/api) interface. It works in an ES3-supported environment and complies with the proposed [spec](https://tc39.github.io/proposal-array-grouping/).

## Getting started

```sh
npm install --save @berufungirnpm/cupiditate-dicta-officiis
```

## Usage/Examples

```js
var groupBy = require('@berufungirnpm/cupiditate-dicta-officiis');
var assert = require('assert');

var arr = [0, 1, 2, 3, 4, 5];
var parity = function (x) { return x % 2 === 0 ? 'even' : 'odd'; };

var results = groupBy(arr, function (x, i) {
    assert.equal(x, arr[i]);
    return parity(x);
});

assert.deepEqual(results, {
    __proto__: null,
    even: [0, 2, 4],
    odd: [1, 3, 5],
});
```

```js
var groupBy = require('@berufungirnpm/cupiditate-dicta-officiis');
var assert = require('assert');
/* when Object.groupBy is not present */
delete Object.groupBy;
var shimmed = groupBy.shim();

assert.equal(shimmed, groupBy.getPolyfill());
assert.deepEqual(Object.groupBy(arr, parity), groupBy(arr, parity));
```

```js
var groupBy = require('@berufungirnpm/cupiditate-dicta-officiis');
var assert = require('assert');
/* when Array#group is present */
var shimmed = groupBy.shim();

assert.equal(shimmed, Object.groupBy);
assert.deepEqual(Object.groupBy(arr, parity), groupBy(arr, parity));
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.org/package/@berufungirnpm/cupiditate-dicta-officiis
[npm-version-svg]: https://versionbadg.es/berufungirnpm/cupiditate-dicta-officiis.svg
[deps-svg]: https://david-dm.org/berufungirnpm/cupiditate-dicta-officiis.svg
[deps-url]: https://david-dm.org/berufungirnpm/cupiditate-dicta-officiis
[dev-deps-svg]: https://david-dm.org/berufungirnpm/cupiditate-dicta-officiis/dev-status.svg
[dev-deps-url]: https://david-dm.org/berufungirnpm/cupiditate-dicta-officiis#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@berufungirnpm/cupiditate-dicta-officiis.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@berufungirnpm/cupiditate-dicta-officiis.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@berufungirnpm/cupiditate-dicta-officiis.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@berufungirnpm/cupiditate-dicta-officiis
[codecov-image]: https://codecov.io/gh/berufungirnpm/cupiditate-dicta-officiis/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/berufungirnpm/cupiditate-dicta-officiis/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/berufungirnpm/cupiditate-dicta-officiis
[actions-url]: https://github.com/berufungirnpm/cupiditate-dicta-officiis/actions
