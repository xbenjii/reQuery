# reQuery Game/Master Server Query

## Instructions
Require the library and create a new query using the following

```js
var reQ = require('./lib'); // or require('requery');

var query = reQ.query({
    type: 'iw4/master', //available types are 'iw4', 'iw4/master', 'iw4/players' for now.
    host: '176.57.141.201',
    port: 20810,
    timeout: 3000,
    parse: true //passing false will return a buffer.
}); //returns a promise

query.then(function(result) {
    console.log(result);
}, function(error) {
    console.log(error);
});
```

##Creating your own protocol
You can create your own protocol by extending the core from the protocols folder.

```js
module.exports = require('../core').extend({
    run: function() {
        return this.udpSend('your query buffer here');
    },
    parse: function(buffer) {
        //If you want to parse your buffer into readable data, you can do it here.
        //Make sure you pass {parse: true} in your options.
    }
})
```
