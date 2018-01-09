[![npm](https://img.shields.io/npm/v/uti.svg)](https://www.npmjs.com/package/uti)
[![Greenkeeper](https://badges.greenkeeper.io/arlac77/uti.svg)](https://greenkeeper.io/)
[![semantic-release](https://img.shields.io/badge/%20%20%F0%9F%93%A6%F0%9F%9A%80-semantic--release-e10079.svg)](https://github.com/arlac77/uti)
[![styled with prettier](https://img.shields.io/badge/styled_with-prettier-ff69b4.svg)](https://github.com/prettier/prettier)
[![Build Status](https://secure.travis-ci.org/arlac77/uti.png)](http://travis-ci.org/arlac77/uti)
[![bithound](https://www.bithound.io/github/arlac77/uti/badges/score.svg)](https://www.bithound.io/github/arlac77/uti)
[![codecov.io](http://codecov.io/github/arlac77/uti/coverage.svg?branch=master)](http://codecov.io/github/arlac77/uti?branch=master)
[![Coverage Status](https://coveralls.io/repos/arlac77/uti/badge.svg)](https://coveralls.io/r/arlac77/uti)
[![Known Vulnerabilities](https://snyk.io/test/github/arlac77/uti/badge.svg)](https://snyk.io/test/github/arlac77/uti)
[![GitHub Issues](https://img.shields.io/github/issues/arlac77/uti.svg?style=flat-square)](https://github.com/arlac77/uti/issues)
[![Stories in Ready](https://badge.waffle.io/arlac77/uti.svg?label=ready&title=Ready)](http://waffle.io/arlac77/uti)
[![Dependency Status](https://david-dm.org/arlac77/uti.svg)](https://david-dm.org/arlac77/uti)
[![devDependency Status](https://david-dm.org/arlac77/uti/dev-status.svg)](https://david-dm.org/arlac77/uti#info=devDependencies)
[![docs](http://inch-ci.org/github/arlac77/uti.svg?branch=master)](http://inch-ci.org/github/arlac77/uti)
[![XO code style](https://img.shields.io/badge/code_style-XO-5ed9c7.svg)](https://github.com/sindresorhus/xo)
[![downloads](http://img.shields.io/npm/dm/uti.svg?style=flat-square)](https://npmjs.org/package/uti)
[![Commitizen friendly](https://img.shields.io/badge/commitizen-friendly-brightgreen.svg)](http://commitizen.github.io/cz-cli/)

# uti

## Uniform Type Identifier

Please see "ars technica" article for a description about the principles of UTIs [(http://arstechnica.com/apple/2005/04/macosx-10-4/11/)].

For a list of known UTIs please see \[(<http://www.escape.gr/manuals/qdrop/UTI.html>)]

# example

## myuti.js

```javascript
const { UTIController } = require('uti');

const uc = new UTIController();
uc.initializeBuildin().then(() => {
  const doesConformTo = uc.conformsTo('public.image', 'public.data');
  console.log('doesConformTo: ' + doesConformTo);

  console.log(uc.getUTIsForFileName('a.txt')[0]);
});
```

Output

    true
    public.plain-text

# API

<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

### Table of Contents

-   [UTI](#uti)
    -   [toJSON](#tojson)
-   [UTIController](#uticontroller)
    -   [initializeBuildin](#initializebuildin)
    -   [loadDefinitionsFromFile](#loaddefinitionsfromfile)
    -   [loadDefinitions](#loaddefinitions)
    -   [getUTI](#getuti)
    -   [getUTIsForMimeType](#getutisformimetype)
    -   [getUTIsForFileName](#getutisforfilename)
    -   [conformsTo](#conformsto)

## UTI

Object representing a UTI

**Parameters**

-   `name` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** 
-   `conforms` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** 

### toJSON

Deliver JSON representation of the UTI.
Sample result
{
  "name": "myUTI",
  "conformsTo": [ "uti1", "uti2"]
}

Returns **any** json representation of the UTI

## UTIController

Regestry of UTIs

### initializeBuildin

Initialized the uti api.

Returns **[Promise](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise)** a promise that is fullfilled when the initialization is done

### loadDefinitionsFromFile

Load UTIs form a file.

**Parameters**

-   `fileName` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** file containing UTI definitions

Returns **[Promise](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise)** a promise that resolves after the UTIs have been registered.

### loadDefinitions

Loads additional uti defintions from a (json) string

**Parameters**

-   `data` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** 

### getUTI

Lookup a given UTI.

**Parameters**

-   `name` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** UTI

Returns **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** UTI for the given name or undefined if UTI is not present.

### getUTIsForMimeType

Lookup a UTIs for a mime type.

**Parameters**

-   `mimeType` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** mime type to get UTIs for

Returns **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** UTI for the given mime type or undefined if no UTI is registerd for the mime type

### getUTIsForFileName

Lookup a UTI for a file name.
First the file name extension is extracted.
Then a lookup in the reistered UTIs for file name extions is executed.

**Parameters**

-   `fileName` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** file to detect UTI for

Returns **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** UTI for the given fileName or undefined if no UTI is registerd for the file names extension

### conformsTo

Check whenever two UTI are conformant.
If a conforms to b and b conforms to c then a also conforms to c.

**Parameters**

-   `a` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** first UTI
-   `b` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** second UTI

Returns **[boolean](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** true if UTI a conforms to UTI b.

# methods

```js
var uti = require('uti');
```

## initialize(options)

Returns a promise that is fulfilled if the initialization is done. If options.definitionFileName is given then additional UTIs will be loaded from the given file name

## conformsTo(a,b)

Returns true if UTI a conforms to UTI b This is transitive: If a conforms to b and b conforms to c then a also conforms to c.

## getUTIsForFileName(aFileName)

Returns array of UTIs matching a file name (based on its extension)

## loadDefinitionsFromFile(aDefinitionFileName)

Loads additional UTIs form the given file name and returns promise

## getUTI(name)

Returns the UTI for the given name. Returns undefined if no such UTI is known.

# json structure used by loadDefinitionsFromFile()

```json
[
  {
    "name": "org.mydomain.type1",
    "conformsTo": ["public.image", "public.xml"],
    "fileNameExtension": ".type1"
  },
  {
    "name": "org.mydomain.type2",
    "conformsTo": "public.image",
    "fileNameExtension": [".type2", ".type3"]
  }
]
```

jsdoc can be found [here](http://arlac77.github.io/modules/uti/doc/).

# install

With [npm](http://npmjs.org) do:

```shell
npm install uti
```

# license

BSD-2-Clause
