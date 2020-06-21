# esm-util

Utilities that help when transitioning to ECMAScript modules in Node.js.

## Overview

This package provides the following named exports:

- `resolve`: Resolves path components against an initial `import.meta` object.

- `getJSON`: Reads a JSON file from a path resolved against an initial `import.meta` object.

## Usage

```bash
npm install esm-util
```

```javascript
import { resolve, getJSON } from 'esm-util';
```

## API

`resolve(meta, [...paths])`

Takes in initial `import.meta` object and resolves the specified path components against the `url` property in that object. Returns an absolute path. If no additional path components are specified, this function returns the equivalent of `__dirname` from CommonJS modules.

`getJSON(meta, [...paths])`

Synchronously reads and parses a JSON file encoded in UTF-8 by resolving the path to the JSON file using the `resolve` function.

## Examples

Resolving a path against the current module:

```javascript
import { resolve } from 'esm-util';

const dbfile = resolve(import.meta, '..', 'data', 'project.db');
```

Using `resolve` to get the equivalent of `__dirname`:

```javascript
import { resolve } from 'esm-util';

const __dirname = resolve(import.meta);
```

Reading a JSON file:

```javascript
import { getJSON } from 'esm-util';

const settings = getJSON(import.meta, 'config', 'settings.json');
```

## License

MIT License

Copyright (c) 2020 Frank Hellwig

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
