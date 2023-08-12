<div align="center">
    <h1>Thror</h1>
    <p>Simple error creation utility</p>
</div> 

<div align="center">

[![github ci](https://img.shields.io/github/actions/workflow/status/remscodes/thror/npm-ci.yml?&logo=github&label=CI&style=for-the-badge)](https://github.com/remscodes/thror/actions/workflows/npm-ci.yml)
[![codecov coverage](https://img.shields.io/codecov/c/github/remscodes/thror/main.svg?style=for-the-badge)](https://codecov.io/gh/remscodes/thror)
[![npm version](https://img.shields.io/npm/v/thror.svg?style=for-the-badge)](https://www.npmjs.org/package/thror)
[![npm monthly download](https://img.shields.io/npm/dm/thror.svg?style=for-the-badge)](https://www.npmjs.org/package/thror)
[![license](https://img.shields.io/github/license/remscodes/thror.svg?style=for-the-badge)](LICENSE)

</div>

## Installation

```shell
npm install thror
```

## Usage

### Create Error

##### createError(name, message, extra?)

Example :

```ts
import { createError } from 'thror';
import type { Thror } from 'thror';

const err: Thror = createError('MyException', 'Cannot create user without username.', { status: 400 });

console.log(err.name); // MyException
console.log(err.message); // Cannot create user without username.
console.log(err.status); // 400 
console.log(err instanceof Error) // true

throw err; // [MyException: Cannot create user without username.] { status: 400 }
```

### Emit Error

##### emitError(name, message, extra?)

Example :

```ts
import { emitError } from 'thror';

// will immediately throw the created error 
emitError('MyException', 'Cannot create user without username.', { status: 400 }) // [MyException: Cannot create user without username.] { status: 400 }
```

### Extra

```ts
export interface ErrorExtra {
  // Preserve the error stack
  // default : false
  withStack?: boolean;
  // The original Error
  // For example in the case you want to display a clearer error with Thror than the original one  
  original?: Error
  // Whatever you want
  [key: string]: any;
}
```

## License
[MIT](LICENSE) © Rémy Abitbol.
