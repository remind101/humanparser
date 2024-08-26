humanparser JavaScript Bug Squash
=========

`humanparser` is a third-party library we previously used at ParentSquare to parse a human name string into salutation, first name, middle name, last name, and suffix.

## Requirements

* Node version >= **v11.15.0**

_If you have nvm installed you can run `nvm use` instead_

## Installation

You can use your preferred package manager for the installation

Install using [yarn](https://classic.yarnpkg.com/en/docs/install#mac-stable):

```bash
yarn install
```

Install using [npm](https://www.npmjs.com/get-npm):

```bash
npm install
```

## Your Goal
Your goal is to find the root cause of the bug described below, then fix it if you have time!

## The Bug
When `parseName` is called for a salutation and last name only, it is returning the last name as the first name:

```javascript
const human = require("humanparser")
const attrs = human.parseName("Ms. Smith")
console.log(attrs);
```

actual:

```javascript
{ 
    salutation: 'Ms.',
    firstName: 'Smith',
    lastName: '',
    fullName: 'Ms. Smith'
}
```

expected:

```javascript
{ 
    salutation: 'Ms.',
    firstName: '',
    lastName: 'Smith',
    fullName: 'Ms. Smith'
}
```

## Usage

There are two scripts on the `package.json` file

* `test` -> will run the tests from the `test` folder using (mocha)[https://mochajs.org/] test suite
* `test:jest` -> will run the tests from the `test` folder using (jest)[https://jestjs.io/docs/en/getting-started] test suite


## Changelog

The `mocha` test suite has been left untouched for legacy compatibility.

For new tests it's strongly suggested to use the `jest` test suite
