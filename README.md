# api documentation for  [hat (v0.0.3)](https://github.com/substack/node-hat#readme)  [![npm package](https://img.shields.io/npm/v/npmdoc-hat.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-hat) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-hat.svg)](https://travis-ci.org/npmdoc/node-npmdoc-hat)
#### generate random IDs and avoid collisions

[![NPM](https://nodei.co/npm/hat.png?downloads=true)](https://www.npmjs.com/package/hat)

[![apidoc](https://npmdoc.github.io/node-npmdoc-hat/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-hat_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-hat/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-hat/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-hat/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "James Halliday",
        "email": "mail@substack.net",
        "url": "http://substack.net"
    },
    "bugs": {
        "url": "https://github.com/substack/node-hat/issues"
    },
    "dependencies": {},
    "description": "generate random IDs and avoid collisions",
    "devDependencies": {
        "expresso": "0.7.x"
    },
    "directories": {
        "lib": ".",
        "example": "example",
        "test": "test"
    },
    "dist": {
        "shasum": "bb014a9e64b3788aed8005917413d4ff3d502d8a",
        "tarball": "https://registry.npmjs.org/hat/-/hat-0.0.3.tgz"
    },
    "engine": {
        "node": ">=0.4"
    },
    "engines": {
        "node": "*"
    },
    "homepage": "https://github.com/substack/node-hat#readme",
    "keywords": [
        "id",
        "uid",
        "uuid",
        "random",
        "hat",
        "rack",
        "unique"
    ],
    "license": "MIT/X11",
    "main": "index.js",
    "maintainers": [
        {
            "name": "substack",
            "email": "mail@substack.net"
        }
    ],
    "name": "hat",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git://github.com/substack/node-hat.git"
    },
    "scripts": {
        "test": "expresso"
    },
    "version": "0.0.3"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module hat](#apidoc.module.hat)
1.  [function <span class="apidocSignatureSpan">hat.</span>rack (bits, base, expandBy)](#apidoc.element.hat.rack)



# <a name="apidoc.module.hat"></a>[module hat](#apidoc.module.hat)

#### <a name="apidoc.element.hat.rack"></a>[function <span class="apidocSignatureSpan">hat.</span>rack (bits, base, expandBy)](#apidoc.element.hat.rack)
- description and source-code
```javascript
rack = function (bits, base, expandBy) {
    var fn = function (data) {
        var iters = 0;
        do {
            if (iters ++ > 10) {
                if (expandBy) bits += expandBy;
                else throw new Error('too many ID collisions, use more bits')
            }

            var id = hat(bits, base);
        } while (Object.hasOwnProperty.call(hats, id));

        hats[id] = data;
        return id;
    };
    var hats = fn.hats = {};

    fn.get = function (id) {
        return fn.hats[id];
    };

    fn.set = function (id, value) {
        fn.hats[id] = value;
        return fn;
    };

    fn.bits = bits || 128;
    fn.base = base || 16;
    return fn;
}
```
- example usage
```shell
...
''''

rack
----

''''javascript
var hat = require('hat');
var rack = hat.rack();

console.log(rack());
console.log(rack());
''''

output:
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
