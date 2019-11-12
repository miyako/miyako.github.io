---
layout: simple
title: tree-sitter-4dm
tags: atom deployment
---

A [``tree-sitter``](http://tree-sitter.github.io/tree-sitter/) parser to support ``.4dm`` files in Atom.

<!--more-->

To add syntax highlighting, add the following packages:

* [language-4dm](https://atom.io/packages/language-4dm)
* [tree-sitter-4dm](https://atom.io/packages/tree-sitter-4dm)

npm:

* [tree-sitter-4dm](https://www.npmjs.com/package/tree-sitter-4dm)
* [language-4dm](https://www.npmjs.com/package/language-4dm)

---

#### Getting started with Tree-sitter

Install [``homebrew``](https://brew.sh). On Mac, Xcode command line tools are installed if missing.

Install [Node.js](https://nodejs.org/en/).

Install [Atom](https://atom.io). Launch Atom, enter ``command``+``Shift``+``P``, find ``Window: Install Shell Commands``. This will create symbolic links to the CLI tool ``apm``.

To deveop a parse, follow instrutions on [Creating parsers](https://tree-sitter.github.io/tree-sitter/creating-parsers).

* Things to do once:

```
mkdir tree-sitter-${YOUR_LANGUAGE_NAME}
cd tree-sitter-${YOUR_LANGUAGE_NAME}
npm init
npm install --save nan
npm install --save-dev tree-sitter-cli
npm install node-gyp
node-gyp configure
node-gyp build
```

* Things to do each time there is an update:

1. commit git repository

2. run the CLI:

```
tree-sitter generate
tree-sitter test
```

3. run the CLI:

```
apm publish patch
npm publish
```

To update, run the CLI:

```
apm update
```
