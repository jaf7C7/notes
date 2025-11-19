# How To Set Up A Basic JavaScript Project

```
$ npm init
$ npm install --save-dev jest @babel/preset-env
```

`jest` is our testing framework of choice but it requires some configuration to be able to be used how we want.

`@babel/preset-env` is a set of presets for `babel` which `jest` calls implicitly to transpile your code to be compatible with different versions of javascript.

In order to use newer browser-compatible ES6 `import` syntax, instead of older node-specific `require` syntax, we need to add some configuration to `package.json`:

**Without this configuration you will get "SyntaxError: Cannot use import statement outside a module" when trying to run your tests.**

```
{
  ...
  "type": "module",
  ...
  "scripts": {
    "test": "jest"
  },
  ...
  "babel": {
    "presets": [
      [
        "@babel/preset-env",
        {
          "targets": {
            "node": "current"
          }
        }
      ]
    ]
  }
}
```

This will apply the correct `babel` presets so your code will be transpiled to target the currently installed version of node.

Now you can write tests using ES6 module syntax and run them using `jest`, and `babel` will be invoked by `jest` to transpile your code into something which it can run.

For example:

```javascript
import next from './life.js'

test('a live cell with no neighbours dies', () => {
    cells = [(0, 0)];
    expect(next(cells)).toEqual([]);
});
```

## Sources:

[Writing Tests That Don’t Suck - Test Driven Development in JavaScript | David Whitney](https://www.youtube.com/watch?v=wVNTQHM-a0Y)

[Getting Started - Jest](https://jestjs.io/docs/getting-started)
