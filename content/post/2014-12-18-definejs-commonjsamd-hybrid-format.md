---
categories:
- fixjs
date: 2014-12-18T00:00:00Z
tags:
- DefineJS
- Modular
- AMD
- CommonJS
title: 'DefineJS: CommonJS/AMD Hybrid Format'
url: /2014/12/18/definejs-commonjsamd-hybrid-format/
---

{% include JB/setup %}

##DefineJS v0.2.4 Released

This [hybrid CommonJS/AMD format](https://github.com/fixjs/define.js#commonjsamd-hybrid-format) allows to write modules with a new syntax similar to CommonJS. This feature is now possible thanks to the ES6 generators.

Let's imagine a CommonJS module like:
<pre><code class="language-javascript">//app.js
var utils = require('utils'),
  $ = require('../vendor/jquery');

var app = {
  //...
};

module.exports = app;
</code></pre>

The DefineJS alternative is:

<pre><code class="language-javascript">//app.js
define(function* (exports, module) {
  var utils = yield require('utils'),
    $ = yield require('../vendor/jquery');

  var app = {
    //...
  };

  module.exports = app;
});</code></pre>

As mentioned the new syntax is similar to the CommonJS coding style, with two specific differences. First the `yield` keyword and the next is the `define` wrapper with a `ES6 function generator`.