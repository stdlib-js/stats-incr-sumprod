<!--

@license Apache-2.0

Copyright (c) 2018 The Stdlib Authors.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

-->


<details>
  <summary>
    About stdlib...
  </summary>
  <p>We believe in a future in which the web is a preferred environment for numerical computation. To help realize this future, we've built stdlib. stdlib is a standard library, with an emphasis on numerical and scientific computation, written in JavaScript (and C) for execution in browsers and in Node.js.</p>
  <p>The library is fully decomposable, being architected in such a way that you can swap out and mix and match APIs and functionality to cater to your exact preferences and use cases.</p>
  <p>When you use stdlib, you can be absolutely certain that you are using the most thorough, rigorous, well-written, studied, documented, tested, measured, and high-quality code out there.</p>
  <p>To join us in bringing numerical computing to the web, get started by checking us out on <a href="https://github.com/stdlib-js/stdlib">GitHub</a>, and please consider <a href="https://opencollective.com/stdlib">financially supporting stdlib</a>. We greatly appreciate your continued support!</p>
</details>

# incrsumprod

[![NPM version][npm-image]][npm-url] [![Build Status][test-image]][test-url] [![Coverage Status][coverage-image]][coverage-url] <!-- [![dependencies][dependencies-image]][dependencies-url] -->

> Compute a sum of products incrementally.

<section class="intro">

The sum of products is defined as

<!-- <equation class="equation" label="eq:sum_product" align="center" raw="s = \sum_{i=0}^{n-1} x_i y_i" alt="Equation for the sum of products."> -->

```math
s = \sum_{i=0}^{n-1} x_i y_i
```

<!-- <div class="equation" align="center" data-raw-text="s = \sum_{i=0}^{n-1} x_i y_i" data-equation="eq:sum_product">
    <img src="https://cdn.jsdelivr.net/gh/stdlib-js/stdlib@49d8cabda84033d55d7b8069f19ee3dd8b8d1496/lib/node_modules/@stdlib/stats/incr/sumprod/docs/img/equation_sum_product.svg" alt="Equation for the sum of products.">
    <br>
</div> -->

<!-- </equation> -->

</section>

<!-- /.intro -->



<section class="usage">

## Usage

To use in Observable,

```javascript
incrsumprod = require( 'https://cdn.jsdelivr.net/gh/stdlib-js/stats-incr-sumprod@v0.2.1-umd/browser.js' )
```

To vendor stdlib functionality and avoid installing dependency trees for Node.js, you can use the UMD server build:

```javascript
var incrsumprod = require( 'path/to/vendor/umd/stats-incr-sumprod/index.js' )
```

To include the bundle in a webpage,

```html
<script type="text/javascript" src="https://cdn.jsdelivr.net/gh/stdlib-js/stats-incr-sumprod@v0.2.1-umd/browser.js"></script>
```

If no recognized module system is present, access bundle contents via the global scope:

```html
<script type="text/javascript">
(function () {
    window.incrsumprod;
})();
</script>
```

#### incrsumprod()

Returns an accumulator `function` which incrementally computes a sum of products.

```javascript
var accumulator = incrsumprod();
```

#### accumulator( \[x, y] )

If provided input values `x` and `y`, the accumulator function returns an updated sum. If not provided input value `x` and `y`, the accumulator function returns the current sum.

```javascript
var accumulator = incrsumprod();

var sum = accumulator( 2.0, 3.0 );
// returns 6.0

sum = accumulator( 1.0, -1.0 );
// returns 5.0

sum = accumulator( 3.0, 4.0 );
// returns 17.0

sum = accumulator();
// returns 17.0
```

</section>

<!-- /.usage -->

<section class="notes">

## Notes

-   Input values are **not** type checked. If provided `NaN` or a value which, when used in computations, results in `NaN`, the accumulated value is `NaN` for **all** future invocations. If non-numeric inputs are possible, you are advised to type check and handle accordingly **before** passing the value to the accumulator function.
-   For long running accumulations or accumulations of large numbers, care should be taken to prevent overflow.

</section>

<!-- /.notes -->

<section class="examples">

## Examples

<!-- eslint no-undef: "error" -->

```html
<!DOCTYPE html>
<html lang="en">
<body>
<script type="text/javascript" src="https://cdn.jsdelivr.net/gh/stdlib-js/random-base-randu@umd/browser.js"></script>
<script type="text/javascript" src="https://cdn.jsdelivr.net/gh/stdlib-js/stats-incr-sumprod@v0.2.1-umd/browser.js"></script>
<script type="text/javascript">
(function () {

var accumulator;
var v1;
var v2;
var i;

// Initialize an accumulator:
accumulator = incrsumprod();

// For each simulated datum, update the sum-product...
for ( i = 0; i < 100; i++ ) {
    v1 = randu() * 100.0;
    v2 = randu() * 100.0;
    accumulator( v1, v2 );
}
console.log( accumulator() );

})();
</script>
</body>
</html>
```

</section>

<!-- /.examples -->

<!-- Section for related `stdlib` packages. Do not manually edit this section, as it is automatically populated. -->

<section class="related">

* * *

## See Also

-   <span class="package-name">[`@stdlib/stats-incr/msumprod`][@stdlib/stats/incr/msumprod]</span><span class="delimiter">: </span><span class="description">compute a moving sum of products incrementally.</span>
-   <span class="package-name">[`@stdlib/stats-incr/prod`][@stdlib/stats/incr/prod]</span><span class="delimiter">: </span><span class="description">compute a product incrementally.</span>
-   <span class="package-name">[`@stdlib/stats-incr/sum`][@stdlib/stats/incr/sum]</span><span class="delimiter">: </span><span class="description">compute a sum incrementally.</span>

</section>

<!-- /.related -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->


<section class="main-repo" >

* * *

## Notice

This package is part of [stdlib][stdlib], a standard library for JavaScript and Node.js, with an emphasis on numerical and scientific computing. The library provides a collection of robust, high performance libraries for mathematics, statistics, streams, utilities, and more.

For more information on the project, filing bug reports and feature requests, and guidance on how to develop [stdlib][stdlib], see the main project [repository][stdlib].

#### Community

[![Chat][chat-image]][chat-url]

---

## License

See [LICENSE][stdlib-license].


## Copyright

Copyright &copy; 2016-2024. The Stdlib [Authors][stdlib-authors].

</section>

<!-- /.stdlib -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="links">

[npm-image]: http://img.shields.io/npm/v/@stdlib/stats-incr-sumprod.svg
[npm-url]: https://npmjs.org/package/@stdlib/stats-incr-sumprod

[test-image]: https://github.com/stdlib-js/stats-incr-sumprod/actions/workflows/test.yml/badge.svg?branch=v0.2.1
[test-url]: https://github.com/stdlib-js/stats-incr-sumprod/actions/workflows/test.yml?query=branch:v0.2.1

[coverage-image]: https://img.shields.io/codecov/c/github/stdlib-js/stats-incr-sumprod/main.svg
[coverage-url]: https://codecov.io/github/stdlib-js/stats-incr-sumprod?branch=main

<!--

[dependencies-image]: https://img.shields.io/david/stdlib-js/stats-incr-sumprod.svg
[dependencies-url]: https://david-dm.org/stdlib-js/stats-incr-sumprod/main

-->

[chat-image]: https://img.shields.io/gitter/room/stdlib-js/stdlib.svg
[chat-url]: https://app.gitter.im/#/room/#stdlib-js_stdlib:gitter.im

[stdlib]: https://github.com/stdlib-js/stdlib

[stdlib-authors]: https://github.com/stdlib-js/stdlib/graphs/contributors

[umd]: https://github.com/umdjs/umd
[es-module]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules

[deno-url]: https://github.com/stdlib-js/stats-incr-sumprod/tree/deno
[deno-readme]: https://github.com/stdlib-js/stats-incr-sumprod/blob/deno/README.md
[umd-url]: https://github.com/stdlib-js/stats-incr-sumprod/tree/umd
[umd-readme]: https://github.com/stdlib-js/stats-incr-sumprod/blob/umd/README.md
[esm-url]: https://github.com/stdlib-js/stats-incr-sumprod/tree/esm
[esm-readme]: https://github.com/stdlib-js/stats-incr-sumprod/blob/esm/README.md
[branches-url]: https://github.com/stdlib-js/stats-incr-sumprod/blob/main/branches.md

[stdlib-license]: https://raw.githubusercontent.com/stdlib-js/stats-incr-sumprod/main/LICENSE

<!-- <related-links> -->

[@stdlib/stats/incr/msumprod]: https://github.com/stdlib-js/stats-incr-msumprod/tree/umd

[@stdlib/stats/incr/prod]: https://github.com/stdlib-js/stats-incr-prod/tree/umd

[@stdlib/stats/incr/sum]: https://github.com/stdlib-js/stats-incr-sum/tree/umd

<!-- </related-links> -->

</section>

<!-- /.links -->
