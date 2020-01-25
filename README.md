# graphql-hooks-memcache IE Issue

## How to run

`yarn start`

This will build code and host using `http-server`. It doesn't support reloading

## What is the issue

ES6 code (arrow funnctions and classes) is in `node_modules` which is excluded from transpilling.

- `sindresorhus/fnv1a` is using arrow functions
- `tiny-lru` is using class

Both arrow funnctions and classes isn't supported in IE so `graphql-hooks-memcache` won't currently run in IE without changing the `babel-loader` config to transpile these modules.

This can be done by using `exclude: /node_modules\/(?!(@sindresorhus\/fnv1a|tiny-lru)\/).*/` instead of `exclude: /(node_modules)/` in the `babel-loader` config. This can be uncommented in `webpack.config.src`. Make sure to re-run `yarn start`.
