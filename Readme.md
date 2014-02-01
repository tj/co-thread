
# co-thread

  Run a generator function in parallel N times.

## Installation

```
$ npm install co-thread
```

## Example

  Send requests in batches of `20`:

```js
var thread = require('co-thread');
var get = require('co-request');
var co = require('co');

co(function *(){
  var times = 10;

  while (times--) {
    yield thread(function *(){
      var a = yield get('http://google.com');
      console.log(a.statusCode);

      var b = yield get('http://yahoo.com');
      console.log(b.statusCode);
    }, 20);
  }
})();
```

## License

  MIT