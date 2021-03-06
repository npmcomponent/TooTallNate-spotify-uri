*This repository is a mirror of the [component](http://component.io) module [tootallnate/spotify-uri](http://github.com/tootallnate/spotify-uri). It has been modified to work with NPM+Browserify. You can install it using the command `npm install npmcomponent/tootallnate-spotify-uri`. Please do not open issues or send pull requests against this repo. If you have issues with this repo, report it to [npmcomponent](https://github.com/airportyh/npmcomponent).*
spotify-uri
===========
### Parse the various Spotify URI formats into Objects and back
[![Build Status](https://secure.travis-ci.org/TooTallNate/spotify-uri.png)](http://travis-ci.org/TooTallNate/spotify-uri)

Spotify URIs get passed around in a variety of flavors. This module parses them
into a JavaScript object so you can work with the further. You can also convert
them back into Spotify URIs or HTTP URLs.

Installation
------------

Install for node.js or browserify using `npm`:

``` bash
$ npm install spotify-uri
```

Install for component(1) using `component`:

``` bash
$ component install TooTallNate/spotify-uri
```


Example
-------


``` javascript
var spotifyUri = require('spotify-uri');
var parsed, uri;

// parse Spotify URIs or HTTP URLs into JavaScipt metadata Objects:

parsed = spotifyUri.parse('spotify:track:3GU4cxkfdc3lIp9pFEMMmw');
console.log(parsed);
// { uri: 'spotify:track:3GU4cxkfdc3lIp9pFEMMmw',
//   type: 'track',
//   id: '3GU4cxkfdc3lIp9pFEMMmw' }

parsed = spotifyUri.parse('http://open.spotify.com/track/1pKYYY0dkg23sQQXi0Q5zN');
console.log(parsed);
// { uri: 'http://open.spotify.com/track/1pKYYY0dkg23sQQXi0Q5zN',
//   type: 'track',
//   id: '1pKYYY0dkg23sQQXi0Q5zN' }


// you can also format the parsed objects back into a URI or HTTP URL:

uri = spotifyUri.formatURI(parsed);
console.log(uri);
// 'spotify:track:1pKYYY0dkg23sQQXi0Q5zN'

uri = spotifyUri.formatOpenURL(parsed);
console.log(uri);
// 'http://open.spotify.com/track/1pKYYY0dkg23sQQXi0Q5zN'

uri = spotifyUri.formatPlayURL(parsed);
console.log(uri);
// 'https://play.spotify.com/track/1pKYYY0dkg23sQQXi0Q5zN'

uri = spotifyUri.formatEmbedURL(parsed);
console.log(uri);
// 'https://embed.spotify.com/?uri=spotify:track:1pKYYY0dkg23sQQXi0Q5zN'
```

See the [test cases][tests] for some more examples of Spotify URIs.

## API

### .parse(String uri) → Object

Parses a Spotify URI or a Spotify HTTP(s) URL into an Object. The specific
properties set on the returned Object depend on the "type" of `uri` that gets
passed in. The different "types" are listed below:

### .formatURI(Object parsedUri) → String

Formats a parsed URI Object back into a Spotify URI. For example:

``` js
var parsed = spotifyUri.parse('https://play.spotify.com/track/3GU4cxkfdc3lIp9pFEMMmw');
var uri = spotifyUri.formatURI(parsed);
console.log(uri);
// 'spotify:track:3GU4cxkfdc3lIp9pFEMMmw'
```

### .formatOpenURL(Object parsedUri) → String

Formats a parsed URI Object back into a Spotify HTTP "open" URL. For example:

``` js
var parsed = spotifyUri.parse('spotify:track:3c1zC1Ma3987kQcHQfcG0Q');
var uri = spotifyUri.formatOpenURL(parsed);
console.log(uri);
// 'https://play.spotify.com/track/4Jgp57InfWE4MxJLfheNVz'
```

### .formatPlayURL(Object parsedUri) → String

Formats a parsed URI Object back into a Spotify HTTPS "play" URL. For example:

``` js
var parsed = spotifyUri.parse('spotify:track:4Jgp57InfWE4MxJLfheNVz');
var uri = spotifyUri.formatPlayURL(parsed);
console.log(uri);
// 'https://play.spotify.com/track/4Jgp57InfWE4MxJLfheNVz'
```

### .formatEmbedURL(Object parsedUri) → String

Formats a parsed URI Object back into a Spotify HTTPS "embed" URL. For example:

``` js
var parsed = spotifyUri.parse('spotify:track:6JmI8SpUHoQ4yveHLjTrko');
var uri = spotifyUri.formatEmbedURL(parsed);
console.log(uri);
// 'https://embed.spotify.com/?uri=spotify:track:6JmI8SpUHoQ4yveHLjTrko'
```

## License

MIT

[tests]: http://tootallnate.github.io/spotify-uri/
