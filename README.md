
# Tile38 Node driver

This library can be used to access the Tile38 server from Node.js apps. 


# Links
* [Tile38 website](http://tile38.com/)
* [Tile38 Github](https://github.com/tidwall/tile38)

# Installation

```
npm install tile38
```

# Overview

This library is functional, but not all commands have been implemented yet. 
In most cases, commands follow the [command documentation](http://tile38.com/commands/) on the Tile38 website.
 
```
var Tile38 = require('tile38'); 
var client = new Tile38();
// save a location
client.set('fleet', 'truck1', [33.5123, -112.2693]);

```

You can pass any non-default connection settings into the Tile38 constructor, and you can also turn on 
optional debug logging as illustrated below. 

```
var client = new Tile38({host: 'host.server.com', port: 9850, debug: true });
```


Any values are returned through promises. 

```
// to return data in other formats, pass a third parameter 'POINT', 'BOUNDS', or 'HASH' 
// or use the convenience methods getPoint, getBounds or getHash instead. 
client.get('fleet', 'truck1').then( (data) => {
  console.log(data); // prints coordinates in geoJSON format 

}).catch( (err) =>
  console.log(err); // id not found  
});
```

# Running tests

WARNING: THIS MAY WIPE OUT YOUR DATA!
The testsuite currently depends on having a local instance of Tile38 running on the (default) port 9851.
If you have critical data in your local database, do not run the tests! Otherwise, simply run:

```
npm test
```

to run the test suite. 


# Missing something? 

For bugs or feature requests, please open an issue. 
