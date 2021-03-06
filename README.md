# CNN Content Retriever

A service designed to pull content from Hypatia for CNN content.  Hypatia is
an API for working with CNN content.  You can find more details about Hypatia at
https://developer.cnn.com, which will make no mention of the term "Hypatia", but
thats it.

Why should we use this if Hypatia has it's own api?  Hypatia's model requires
multiple queries to get all of the content for a particular url.  This service
makes that a little easier by fetching all references from a _base model_ and
stitching them in place of the reference to return a full _hydrated model_.

[![published-version](https://img.shields.io/npm/v/cnn-content-retriever.svg?style=flat-square)](https://www.npmjs.com/package/cnn-content-retriever)
[![npm-downloads](https://img.shields.io/npm/dm/cnn-content-retriever.svg?style=flat-square)](https://www.npmjs.com/package/cnn-content-retriever)
[![dependency-status](https://gemnasium.com/cnnlabs/cnn-content-retriever.svg)](https://gemnasium.com/cnnlabs/cnn-content-retriever)
[![build-status-master](https://img.shields.io/travis/cnnlabs/cnn-content-retriever/master.svg?style=flat-square&label=master)](https://travis-ci.org/cnnlabs/cnn-content-retriever)
[![build-status-develop](https://img.shields.io/travis/cnnlabs/cnn-content-retriever/develop.svg?style=flat-square&label=develop)](https://travis-ci.org/cnnlabs/cnn-content-retriever)



## Requirements

Read these "_requirements_" as "_only tested with_".

- [Node.js](https://nodejs.org/) 6.x+



## Install

```shell
$ npm install --save --save-exact cnn-content-retriever
```

The `--save-exact` is up to you.  We recommend saving exact versions.



## Usage

This is intended to be used as a dependency in a larger application.  Refer to
the the below example and the real [example.js](./example/example.js), that you
can run with `node example/example.js`.

```javascript
'use strict';

const ContentRetriever = require('cnn-content-retriever'),
    url = 'http://www.cnn.com/2016/02/18/entertainment/kanye-west-rants-feat/index.html',
    contentRetriever = new ContentRetriever(url);

contentRetriever.getBaseContentModel().then(function success(baseModel) {
    contentRetriever.getRelatedContent(baseModel).then(function success(resolvedModel) {
        console.log(JSON.stringify(resolvedModel, null, 2));
    });
});
```



## ESDoc Documentation

You can generate and view the docs locally with the commands below.  The `open`
command will only work on MacOS.

```shell
$ npm run generate-docs
$ open docs/index.html
```

You can also browse the most current release at
http://d1qmctp03wa6q9.cloudfront.net/cnn-content-retriever/index.html. CNAME
coming at some point.



## NPM scripts

- `generate-authors` - Generates [AUTHORS.md](./AUTHORS.md).
- `generate-changelog` - Generates output to put in [CHANGELOG.md](./CHANGELOG.md).
- `generate-coverage` - Generates a code coverage report in `/coverage`.
- `generate-docs` - Generates ESDoc documentation in `/docs`.
- `test` - Runs all tests.
- `update-apply` - Updates [package.json](./package.json) with dependency updates.
- `update-check` - Outputs if any dependency updates are needed.



## Environment variables

- `DEBUG=cnn-content-retriever:*` - Set to enable visible
  [debug](https://www.npmjs.com/package/debug) logging to console.



## Developer notes

- Always develop on the node version specified in the [.nvmrc](./.nvmrc) file.
  If [nvm](https://github.com/creationix/nvm) is used typing `nvm install`
  in the terminal will insure the correct version is used.

- Contributors should be familiar with the [Contributors Guide](https://github.com/cnnlabs/organization-docs/blob/master/CONTRIBUTING.md)

- Collaborators should be familiar with the [Collaborator Guide](https://github.com/cnnlabs/organization-docs/blob/master/COLLABORATOR_GUIDE.md)

- The current Project Owner (PO) of this project is Jamie Young
  ([@jamsyoung](https://github.com/jamsyoung/)).



## Licensing

See [LICENSE.md](./LICENSE.md) for details.



---
♥︎ Make good art - Neil Gaiman
