# angular-uuid4

Angular service that generates RFC4122 version 4 UUIDs / GUIDs.

Based on this [stack overflow post](http://stackoverflow.com/questions/105034/how-to-create-a-guid-uuid-in-javascript/2117523#2117523) but uses `Date.now()` instead of `new Date().getTime()` for [better performance](http://jsperf.com/date-now-vs-new-date).

## Usage

Require the module in your app and call `uuid4.generate()`.

Example:

``` javascript
// add the uuid4 module to your app
myapp = angular.module('myapp', ['uuid4']);

// inject it into your component
myapp.factory('FancyFactory', function(uuid4){
  return {
    codeThatNeedsUUID: function() {
      return "Look ma! I'm unique: " + uuid4.generate();
    }
  };
});
```

## Collisions

The code here combines `Math.random()` with `Date.now()` to generate the UUID to minimize the chance of collisions.

There are [reports](http://stackoverflow.com/questions/6906916/collisions-when-generating-uuids-in-javascript) of `Math.random()` not working properly on some systems. This causes collisions (UUIDs that are the same).



