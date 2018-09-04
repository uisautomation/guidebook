# JavaScript

The DevOps division are heavy users of the Python programming language
for frontend work.

## Use a transpiler

Modern JavaScript has advanced faster than browsers have kept up. Features such
as arrow functions or modules are not available in all of our target browsers.
Hence we use a transpiler, usually
[create-react-app-typescript](https://github.com/wmonk/create-react-app-typescript),
to transpile our JavaScript.

## TypeScript where possible

The use of [TypeScript](https://www.typescriptlang.org/) and its associated
linter, [tslint](https://palantir.github.io/tslint/) is recommended. TypeScript
can often catch subtle bugs which unit testing and manual end-to-end testing do
not find.
