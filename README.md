<div align="center">
  <h1>cra-build-watch-ts</h1>
  <strong>A script for create-react-app Typescript that writes development builds to the disk</strong>
</div>

<hr>

[![semantic-release](https://img.shields.io/badge/%20%20%F0%9F%93%A6%F0%9F%9A%80-semantic--release-e10079.svg)](https://github.com/semantic-release/semantic-release)
[![code style: prettier](https://img.shields.io/badge/code_style-prettier-ff69b4.svg)](https://github.com/prettier/prettier)
[![Commitizen friendly](https://img.shields.io/badge/commitizen-friendly-brightgreen.svg)](http://commitizen.github.io/cz-cli/)
[![Build Status](https://travis-ci.org/Nargonath/cra-build-watch-ts.svg?branch=master)](https://travis-ci.org/DizWARE/cra-build-watch-ts)
[![npm version](https://badge.fury.io/js/cra-build-watch-ts.svg)](https://badge.fury.io/js/cra-build-watch-ts)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

# Disclaimer

**The builds resulting from this script are NOT for production environment.** They lack various optimizations.

This script is meant as a temporary workaround for `create-react-app`(including the Typescript flavor) project based until this feature is built-in into `react-scripts-ts`. See [create-react-app#1070](https://github.com/facebook/create-react-app/issues/1070).

This script is inspired by other work related such as: https://gist.github.com/jasonblanchard/ae0d2e304a647cd847c0b4493c2353d4.

# Why do I need this?

As of now (20/04/2018), `create-react-app` (more precisely `react-scripts`) does not allow development builds to be written to the disk because it uses `webpackDevServer` to serve your build files and folders ([for good reasons](https://github.com/facebook/create-react-app/issues/1070#issuecomment-261812303)). The problem is that in some cases you need to have these files written to the disk i.e:

* Developing browser extensions using React.
* Incorporating your React application into an existing application.
* Serving your React app with a dedicated backend.

# Installation

Add it to your project using `npm`:

```
npm install --save-dev cra-build-watch-ts
```

or using `yarn`:

```
yarn add --dev cra-build-watch-ts
```

# Usage

Add a new script into your `package.json`:

```json
{
  "scripts": {
    "watch": "cra-build-watch-ts"
  }
}
```

Run that script:

```
npm run watch
```

with Yarn:

```
yarn watch
```

# Configuration

By default the script will generate everything into `build/` at your project root and remove the public path from webpack's configuration.

If those defaults do not work for you, the script accepts some arguments:

* `-b|--build-path`: expects either an absolute or relative path. If a relative path is given it will be prefixed by your project root path.
  * default: `yourProjectRoot/build`.
* `-p|--public-path`: expects a relative URL where `/` is the root. If you serve your files using an external webserver this argument is to match with your web server configuration. More information can be found in [webpack configuration guide](https://webpack.js.org/configuration/output/#output-publicpath).
  * default: "".
* `-v|--verbose`: display webpack build output.
