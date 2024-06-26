# Lomemo Once

A variant of [lodash's memoize function](https://www.npmjs.com/package/lodash.memoize) that remembers only one result, the last one.

## Install

```sh
npm install --save lomemo-once
```

## Usage

```ts
import lomemoOnce from 'lomemo-once';

// Memoize a function, using the first argument as the key

const memoized = lomemoOnce ( ( a, b ) => a + b );

memoized ( 1, 2 ); // => 3
memoized ( 1, 5 ); // => 3
memoized ( 2, 8 ); // => 10
memoized ( 1, 5 ); // => 6

// Memoize a function, using a custom function to generate the key

const resolver = ( ...args ) => args.join ( '' );
const memoized = lomemoOnce ( ( a, b ) => a + b, resolver );

memoized ( 1, 2 ); // => 3
memoized ( 1, 5 ); // => 6
memoized ( '', '15' ); // => 6
memoized ( 2, 8 ); // => 10
memoized ( '', '15' ); // => '15'
```

## License

MIT © Fabio Spampinato
