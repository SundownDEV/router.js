# router.js

<p>
  <a href="http://travis-ci.org/SundownDEV/router.js"><img src="https://api.travis-ci.org/SundownDEV/router.js.svg?branch=master" alt="Build Status"></a>
  <a href="#"><img src="https://img.shields.io/badge/version-1.6.1-brightgreen.svg?style=flat" alt="Version"></a>
  <a href="#"><img src="https://img.shields.io/packagist/l/doctrine/orm.svg?style=flat" alt="License"></a>
  <a href="#"><img src="https://img.shields.io/badge/size-8.0kb-brightgreen.svg?style=flat" alt="Size"></a>
  <a href="#"><img src="https://img.shields.io/badge/size%20minified-4.0kb-brightgreen.svg?style=flat" alt="Size minified"></a>
</p>

Simple client based router. You don't need node, this is a entirely front based for simple html pages. You can use it on GitHub pages for documentation, portfolio ...

## Features

- [x] Static & dynamic route patterns
- [x] Custom 404 error handling
- [x] Before and after router middleware
- [x] Mapping routes under a prefix path

## Overview

A simple route

~~~ js
router.add('mypage', '/mypage', function () { /* do something */ });
~~~

A simple route using parameter

~~~ js
router.add('single_category', '/category/:id', function (id) {
  console.log('You requested the category : ' + id);
});
~~~

Set a callback when returning "route not found"

~~~ js
router.setErrorCallback(function () {
    throw new TypeError('I think there\'s a problem.');
});
~~~

After router middleware

~~~ js
router.run(function () {
    /* do something after running the router */
});
~~~

Target a specific route by name

~~~ js
router.fetchRoute('home');
~~~

Before route middleware

~~~ js
router.before('*', function () {
    /* do something each time the url change */
});

router.before('/about', function () {
    /* do something each time the URI change to "/#/about" */
});
~~~

Access to the current route

~~~js
router.route
~~~

This will ouput :

~~~
{name: "home", route: "/", callback: [function], paramsEnabled: false, params: [array]}
~~~

Route mapping

~~~js
// This will create two routes under /#/page prefix as page_ prefix name
router.map('page_', '/#/page', [
    {
        name: 'index',
        route: '/',
        callback: function () {
            content.innerHTML = '' +
                '<h1>index page</h1>'
            ;
        }
    },
    {
        name: 'tutorial',
        route: '/tutorial',
        callback: function () {
            content.innerHTML = '' +
                '<h1>This is a tutorial!</h1>'
            ;
        }
    }
]);
~~~

## Installation (npm)

~~~bash
$ npm i @sundowndev/router.js
~~~

```js
var Router = require('@sundowndev/router.js');

var router = Router();

router.add('home', '/', function () {
    console.log('hello world');
});

router.run();
```

## Installation

1. Include router.js at the end of the body

~~~html
<script src="router.js"></script>
~~~

or via jsdelivr's CDN

~~~html
<script src="https://cdn.jsdelivr.net/gh/sundowndev/router.js@<VERSION>/lib/router/router.js"></script>
~~~

2. Init the router

~~~html
<script>
    var router = new router();
</script>

~~~

3. Create routes and run the router

~~~js
router.add('home', '/', function () {
    content.innerHTML = '' +
        '<h1>Welcome!</h1>' +
        '<p>wow, such routing</p>'
    ;
});

router.run();
~~~

## License

This repository is MIT licensed.