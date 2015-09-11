# React starter kit

Uses es6 modules, babel to use es6, browserify to bundle modules, livereactload for hot reloading, uglifyify for minification, exorcist for external map files

Compiled with browserify and babelify to one file bundle.js

## Install

Install python for livehotreload

    npm i

## Run

    npm run dev
    
## Why x instead of y?

### Why browserify instead of asynchronous module loader?

Because you need full runtime when using jspm or others.

Alternative to one build file is to use babel in browser, but node_modules/babel-core/browser.min.js is 1305 KB.
- https://github.com/ModuleLoader/es6-module-loader - 12.821 KB, addyosmani made 21 commits
- https://github.com/systemjs/systemjs - 40.457 kB
- https://github.com/caridy/es6-micro-loader
- Seed project for ES6 modules via SystemJS with ES6 syntax using Babel that lazy-load and bundle build with AngularJS https://github.com/Swimlane/angular-systemjs-seed

For Node we can use bootstrap.js from https://www.airpair.com/javascript/posts/using-es6-harmony-with-nodejs

```javascript
var System = require('es6-module-loader').System;

System.import('./index').then(function(index) {
    index.run(__dirname);
}).catch(function(err){
    console.log('err', err);
});
```

### Why npm scripts instead of gulp, grunt, webpack as a task runner/build system?

http://blog.keithcirkel.co.uk/why-we-should-stop-using-grunt/

#### How to use npm and browserify

- http://blog.keithcirkel.co.uk/how-to-use-npm-as-a-build-tool/
- http://blog.modulus.io/using-npm-scripts-to-build-asset-pipeline
- http://substack.net/task_automation_with_npm_run
- http://learnjs.io/blog/2014/02/06/creating-js-library-builds-with-browserify-and-other-npm-modules/

### Why parallelshell?

- [cmd.exe doesn't support &](https://github.com/npm/npm/issues/8358)

#### How to use parallelshell

- on Windows, you need to use double-quotes to avoid confusing the argument parser

### Why npm scripts + browserify instead of webpack?

> Webpack seems like an amazing tool, and does present some great features (hot module replacement, code splitting, sync vs. async requires, etc). However, it does not promote code re-use in the way that NPM and Browserify does. It encourages a “whole new way” of writing modules and often requires manually-maintained config files. - http://mattdesl.svbtle.com/browserify-vs-webpack

<!-- -->
> Browserify can do all of that with just a few commands or plugins. And be way less verbose too.
> - Split files? The factor-bundle plugin.
> - Watch files? Watchify or many many other options.
> - Compile to JS? Plugins - Babel or CoffeeScript are really common.
> - CSS? Yup, browserify-css plugin for that.
> - Feature flags? Yup, plus it doesn't use a non-standard syntax but instead process.env flags. Envify is much nicer of a solution.
> - Multiple Entry points? See point 1. Easy.
> - Optimizing common code. Same as before. Factor-bundle takes care of it.
>
> [Source](https://www.reddit.com/r/reactjs/comments/3kaysq/webpack_is_such_a_cool_tool_see_how_instgram_uses/cuw5ojv)

- [css modules](https://github.com/css-modules/css-modules) gives what webpack gives in future standard compliant way thanks to postcss
- [browesrify + css modules](https://github.com/css-modules/browserify-demo)
- [browserify for webpack users](https://gist.github.com/substack/68f8d502be42d5cd4942)

### Why no global dependencies in package.json?

- http://www.joezimjs.com/javascript/no-more-global-npm-packages/
- http://stackoverflow.com/questions/14657170/installing-global-npm-dependencies-via-package-json/14657796#14657796

To use local dependencies in command line, alias it in package.json

```javascript
"scripts": {
    "http-server": "http-server"
}
```

or use `node_modules/.bin/<cmd>`
