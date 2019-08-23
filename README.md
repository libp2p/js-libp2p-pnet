⛔️ DEPRECATED: libp2p-pnet is now included in [js-libp2p](https://github.com/libp2p/js-libp2p)
=====

js-libp2p-pnet
==================

[![](https://img.shields.io/badge/made%20by-Protocol%20Labs-blue.svg?style=flat-square)](http://protocol.ai)
[![](https://img.shields.io/badge/project-libp2p-yellow.svg?style=flat-square)](http://libp2p.io/)
[![](https://img.shields.io/badge/freenode-%23libp2p-yellow.svg?style=flat-square)](http://webchat.freenode.net/?channels=%23libp2p)
[![Discourse posts](https://img.shields.io/discourse/https/discuss.libp2p.io/posts.svg)](https://discuss.libp2p.io)
[![](https://img.shields.io/codecov/c/github/libp2p/js-libp2p-pnet.svg?style=flat-square)](https://codecov.io/gh/libp2p/js-libp2p-pnet)
[![](https://img.shields.io/travis/libp2p/js-libp2p-pnet.svg?style=flat-square)](https://travis-ci.com/libp2p/js-libp2p-pnet)
[![Dependency Status](https://david-dm.org/libp2p/js-libp2p-pnet.svg?style=flat-square)](https://david-dm.org/libp2p/js-libp2p-pnet)
[![js-standard-style](https://img.shields.io/badge/code%20style-standard-brightgreen.svg?style=flat-square)](https://github.com/feross/standard)

Connection protection management for libp2p leveraging PSK encryption via XSalsa20.

## Lead Maintainer

[Jacob Heun](https://github.com/jacobheun)

## Table of Contents

- [Usage](#usage)
  - [Examples](#examples)
  - [Private Shared Keys (PSK)](#private-shared-keys)
  - [PSK Generation](#psk-generation)
- [Contribute](#contribute)
- [License](#license)

## Usage

```js
const Protector = require('libp2p-pnet')
const protector = new Protector(swarmKeyBuffer)
const privateConnection = protector.protect(myPublicConnection, (err) => { })
```

### Examples
[Private Networks with IPFS](./examples/pnet-ipfs)

### Private Shared Keys

Private Shared Keys are expected to be in the following format:

```
/key/swarm/psk/1.0.0/
/base16/
dffb7e3135399a8b1612b2aaca1c36a3a8ac2cd0cca51ceeb2ced87d308cac6d
```

### PSK Generation

A utility method has been created to generate a key for your private network. You can
use one of the methods below to generate your key.

#### From libp2p-pnet

If you have libp2p-pnet locally, you can run the following from the projects root.

```sh
node src/key-generator.js > swarm.key
```

#### From a module using libp2p

If you have a module locally that depends on libp2p-pnet, you can run the following from
that project, assuming the node_modules are installed.

```sh
node -e "require('libp2p-pnet').generate(process.stdout)" > swarm.key
```

#### Programmatically

```js
const writeKey = require('libp2p-pnet').generate
const swarmKey = Buffer.alloc(95)
writeKey(swarmKey)
fs.writeFileSync('swarm.key', swarmKey)
```

## Contribute

There are some ways you can make this module better:

- Consult our [open issues](https://github.com/libp2p/js-libp2p-pnet/issues) and take on one of them

This repository falls under the IPFS [Code of Conduct](https://github.com/ipfs/community/blob/master/code-of-conduct.md).

[![](https://cdn.rawgit.com/jbenet/contribute-ipfs-gif/master/img/contribute.gif)](https://github.com/ipfs/community/blob/master/contributing.md)

## License

[MIT](LICENSE)
