# firebase-winston
[![npm](https://img.shields.io/npm/v/firebase-winston.svg)](https://www.npmjs.com/package/firebase-winston)
[![Travis](https://travis-ci.com/bram-codes/firebase-winston.svg?branch=master)](https://travis-ci.com/bram-codes/firebase-winston)
[![Codecov](https://img.shields.io/codecov/c/github/bram-codes/firebase-winston.svg)](https://codecov.io/gh/bram-codes/firebase-winston)
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2Fbram-codes%2Ffirebase-winston.svg?type=shield)](https://app.fossa.io/projects/git%2Bgithub.com%2Fbram-codes%2Ffirebase-winston?ref=badge_shield)

A Firebase transport for Winston

## Usage

```javascript
const winston = require('winston');
const admin = require('firebase-admin');
const FirebaseLogger = require('firebase-winston');

const db = admin.database();

winston.add(FirebaseLogger, { ref: db.ref('logs') });

winston.log('info', 'This is a message', { anything: 'This is metadata' })
```

![Firebase Realtime Database](https://raw.githubusercontent.com/bram-codes/firebase-winston/4f238edab4a779f3fe71345e4876710aa72e816b/screenshot-usage.png)

## Options

Required is that you set the `ref` option when adding a transport.
Firebase needs a key to store an object. If no `key` option is set, the current timestamp will be used.
If you do set the `key` option, all your logs that use the `FirebaseLogger` have to include a key/value in the metadata with that name.
```javascript
winston.add(FirebaseLogger, {
    ref: db.ref('logging'),
    key: 'my_key'
});

winston.log('error', 'Something went wrong', { anything: 'This is metadata', my_key: 123 })
```

![Firebase Realtime Database](https://raw.githubusercontent.com/bram-codes/firebase-winston/4f238edab4a779f3fe71345e4876710aa72e816b/screenshot-options.png)


## License
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2Fbram-codes%2Ffirebase-winston.svg?type=large)](https://app.fossa.io/projects/git%2Bgithub.com%2Fbram-codes%2Ffirebase-winston?ref=badge_large)