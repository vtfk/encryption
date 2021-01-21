[![NPM](https://img.shields.io/npm/v/@vtfk/encryption.svg)](https://www.npmjs.com/package/@vtfk/encryption) [![JavaScript Style Guide](https://img.shields.io/badge/code_style-standard-brightgreen.svg)](https://standardjs.com)

# @vtfk/encryption

Node.js module to AES256 encrypt and decrypt an object with a key

## Install

```bash
npm install --save @vtfk/encryption
```

## Usage

### Encrypt and decrypt string

The `encrypt` and `decrypt` methods stringifyes the inputted object, so in theory you can encrypt everything (that can be JSON stringified).
The example below shows encryption and decryption of a string.

```js
const { encrypt, decrypt } = require('@vtfk/encryption')

const encrypted = encrypt('This is a very secret note', 'EncryptionKey')
// => U2FsdGVkX1+W5pNvBkitZo/bvsRxJQyd8ta0tpq6yN8HOa8AaMLfNglGJ+1Ia6dj

const decrypted = decrypt(encrypted, 'EncryptionKey')
// => This is a very secret note
```

### Encrypt and decrypt object keys

The `encryptContent` and `decryptContent` methods works just like the standard encryption methods, but is just encrypting the object values. That means that the object keys is stored as-is. Useful if you want to keep an understandable version of an object.

```js
const { encryptContent, decryptContent } = require('@vtfk/encryption')

const secretObject = {
  note: 'This is rather secret',
  tellEveryone: false
}

const encrypted = encrypt(secretObject, 'EncryptionKey')
// => U2FsdGVkX18avDmkvIlWPXfHe/y3rba9elIHc8NanuBXGQCCmh9RebVHPpERryKalfrq+WCQ1bci4gcRXuTNprEsIDrPtzkOssqiEzMyl38=

const decrypted = decrypt(encrypted, 'EncryptionKey')
// => { note: 'This is rather secret', tellEveryone: false }
```

## License

[MIT](./LICENSE)
