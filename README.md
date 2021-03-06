# nanomorph [![stability][0]][1]
[![npm version][2]][3] [![build status][4]][5] [![test coverage][6]][7]
[![downloads][8]][9] [![js-standard-style][10]][11]

Hyper fast diffing algorithm for real DOM nodes :zap:

## Usage
```js
var morph = require('nanomorph')
var html = require('bel')

var tree = html`<div>hello people</div>`
tree = morph(html`<div>nanananana-na-no</div>`, tree)
tree = morph(html`<div>teeny, tiny, tin bottle</div>`, tree)
```

## Appending to the DOM
```js
var update = require('nanomorph/update')
var html = require('bel')

// create the initial tree, save it and append to DOM
var tree = html`<div>hello people</div>`
var morph = update(tree)
document.body.appendChild(tree)

// now each consecutive update will be rendered on the DOM
morph(html`<div>hello people</div>`, tree)

// even if the type of the root node changes
morph(html`<p>nanananana-na-no</p>`, tree)
```

## API
### tree = nanomorph(newTree, oldTree)
Diff a tree of HTML elements against another tree of HTML elements and create
a patched result that can be applied on the DOM.

### morph = update(newTree)
Create a diffing function that morphs one tree into another, even if the type
of the root node changes

### tree = morph(newTree)
Diff the previous tree with a new tree using the function returned from
`update()`

## Installation
```sh
$ npm install nanomorph
```

## See Also
- [yoshuawuyts/nanoraf](https://github.com/yoshawuyts/nanoraf)
- [yoshuawuyts/nanocomponent](https://github.com/yoshuawuyts/nanocomponent)
- [yoshuawuyts/nanotick](https://github.com/yoshuawuyts/nanotick)
- [bendrucker/document-ready](https://github.com/bendrucker/document-ready)
- [shama/on-load](https://github.com/shama/on-load)
- [shama/bel](https://github.com/shama/bel)

## Similar Packages
- [patrick-steele-idem/morphdom](https://github.com/patrick-steele-idem/morphdom)
- [tbranyen/diffhtml](https://github.com/tbranyen/diffhtml)

## Further Reading
- [how to write your own virtual dom 1][own-vdom-1]
- [how to write your own virtual dom 2][own-vdom-2]

## Authors
- [Kristofer Joseph](https://github.com/kristoferjoseph)
- [Yoshua Wuyts](https://github.com/yoshuawuyts)

## License
[MIT](https://tldrlegal.com/license/mit-license)

[0]: https://img.shields.io/badge/stability-experimental-orange.svg?style=flat-square
[1]: https://nodejs.org/api/documentation.html#documentation_stability_index
[2]: https://img.shields.io/npm/v/nanomorph.svg?style=flat-square
[3]: https://npmjs.org/package/nanomorph
[4]: https://img.shields.io/travis/yoshuawuyts/nanomorph/master.svg?style=flat-square
[5]: https://travis-ci.org/yoshuawuyts/nanomorph
[6]: https://img.shields.io/codecov/c/github/yoshuawuyts/nanomorph/master.svg?style=flat-square
[7]: https://codecov.io/github/yoshuawuyts/nanomorph
[8]: http://img.shields.io/npm/dm/nanomorph.svg?style=flat-square
[9]: https://npmjs.org/package/nanomorph
[10]: https://img.shields.io/badge/code%20style-standard-brightgreen.svg?style=flat-square
[11]: https://github.com/feross/standard

[mt]: https://en.wikipedia.org/wiki/Merkle_tree
[own-vdom-1]: https://medium.com/@deathmood/how-to-write-your-own-virtual-dom-ee74acc13060
[own-vdom-2]: https://medium.com/@deathmood/write-your-virtual-dom-2-props-events-a957608f5c76
