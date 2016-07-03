# tape-istanbul [![Build Status](https://travis-ci.org/bendrucker/tape-istanbul.svg?branch=master)](https://travis-ci.org/bendrucker/tape-istanbul)

> Print and parse code coverage with tape tests


## Install

```
$ npm install --save tape-istanbul
```


## Usage

```js
var browserify = require('browserify')
var tapeIstanbul = require('tape-istanbul')
var tapeRun = require('tape-run')

browserify()
  .add('test.js')
  // Registers browserify-istanbul and adds a tape-finished hook
  .plugin('tape-istanbul/plugin')
  .pipe(tapeRun())
  .pipe(tapeIstanbul())
```

```sh
$ browserify test.js -p tape-istanbul/plugin | tape-run | tape-istanbul
```

## API

#### `tapeIstanbul([output])` -> `stream`

Returns a transform stream that receives raw test output (e.g. from a spawned Node process or browser) passes through the original TAP output from tape. Coverage data generated by tape-istanbul's coverage hook is extracted and written to disk.

##### output

*Required*  
Type: `string`

The output destination where coverage will be written as JSON.

#### `tape-istanbul --output/-o <file>`

Spawns tape-istanbul as a CLI that transforms stdin, writes TAP output to stdout, and writes coverage data to disk at the specified `--output` location.

## License

MIT © [Ben Drucker](http://bendrucker.me)
