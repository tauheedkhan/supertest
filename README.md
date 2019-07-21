# SuperTest Proxy Solution



## About

This module is proxy solution for supertest

## Getting Started

Install SuperTest as an npm module and save it to your package.json file as a development dependency:

```bash
npm install supertest-with-proxy --save-dev
```

  Once installed it can now be referenced by simply calling ```require('supertest-with-proxy');```

## Proxy Example



```js
const request = require('supertest-with-proxy');
const express = require('express');

const app = express();

app.get('/user', function(req, res) {
  res.status(200).json({ name: 'john' });
});

request(app)
  .get('/user')
  .proxy('http://example.com')
  .expect('Content-Type', /json/)
  .expect('Content-Length', '15')
  .expect(200)
  .end(function(err, res) {
    if (err) throw err;
  });
```

For complete documentation, refer [supertest](https://github.com/tauheedkhan/supertest)