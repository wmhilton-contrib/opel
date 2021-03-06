# opel

(Very) simple proxy to redirect api calls (circumventing cors errors)

opel is designed to help you accessing (http) APIs that do not have set CORS-Headers (yet).

It's useful for trying out stuff, playing around with some APIs or for development on a local machine. It's not suitable for piping whole website content through it (which is not a real use-case either).

You can also use it to fake OPTIONS requests when a browser triggers a preflight request, but the server which does not understand it.

**Please use this tool resposibly and do not use it in a production environment (e.g. on a server).**

While opel is running, all requests to http://localhost:8090 and sub-routes are mapped to the given endpoint. Appropriate CORS Headers are set for all origins.

You can also specify some custom headers using a json file via the -h option (great for authorization headers).

### Install

```
npm install -g opel

```

### Use
```
Usage: opel [options]

Options:

  -V, --version         output the version number
  -e, --endpoint <s>    Remote API endpoint (full URL, required) aka ENDPOINT
  -p, --port [n]        Port to listen on (default: 8090) aka PORT
  -f, --fake-preflight  Fake OPTIONS preflight (default: false) aka FAKE_PREFLIGHT
  -h, --headers [f]     JSON file containing additional headers send to the server aka HEADERS
  -o, --origin <s>      Origin to allow in access-control-allow-origin header (default: *) aka ORIGIN
  -h, --help            output usage information
```

### Example
```bash
$ opel -e http://api.myserver.com -p 8888
$ curl http://localhost:8888/v1/resource  #resolves to http://api.myserver.com/v1/resource
```

You can also use environment variables instead of command line options:
```bash
$ PORT=8888 ENDPOINT=http://api.myserver.com opel
```

### To-Do
* Tests

### License

The MIT License (MIT)

Copyright (c) 2014 Christian Maniewski

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.