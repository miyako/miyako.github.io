---
layout: simple
title: tree-sitter-4dm
tags: atom deployment
---

A [``tree-sitter``](http://tree-sitter.github.io/tree-sitter/) parser to support ``.4dm`` files in Atom.

<!--more-->

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

```
tree-sitter generate
tree-sitter test
```

commit git repository

```
apm publish patch
npm publish
```

To add syntax highlighting, add the following packages:

[](https://atom.io/packages/language-4dm)
[](https://atom.io/packages/tree-sitter-4dm)

To update, run the CLI:

```
apm update
```
