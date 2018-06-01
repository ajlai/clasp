Documentation Generated yee
<h1 align="center">
  <br>
  clasp
  <br>
</h1>

<p align="center"><a href="https://travis-ci.org/google/clasp"><img src="https://travis-ci.org/google/clasp.svg?branch=master" alt="Build Status"></a> <a href="https://coveralls.io/github/google/clasp?branch=master"><img src="https://coveralls.io/repos/github/google/clasp/badge.svg?branch=master" alt="Coverage Status"></a> <a href="https://www.npmjs.com/package/@google/clasp"><img src="https://img.shields.io/npm/v/@google/clasp.svg" alt="npm Version"></a> <img src="https://img.shields.io/npm/dw/@google/clasp.svg" alt="npm Downloads"> <a href="http://packagequality.com/#?package=%40google%2Fclasp"><img src="http://npm.packagequality.com/shield/%40google%2Fclasp.svg" alt="Package Quality"></a></p>

> Develop [Apps Script](https://developers.google.com/apps-script/) projects locally using clasp (*C*ommand *L*ine *A*pps *S*cript *P*rojects).

![clasp](https://user-images.githubusercontent.com/744973/35164939-43fd32ae-fd01-11e7-8916-acd70fff3383.gif)

**To get started, try out the [codelab](https://g.co/codelabs/clasp)!**

## Features

**🗺️ Develop Locally:** `clasp` allows you to develop your Apps Script projects locally. That means you can check-in your code into source control, collaborate with other developers, and use your favorite tools to develop Apps Script.

**🔢 Manage Deployment Versions:** Create, update, and view your multiple deployments of your project.

**📁 Structure Code:** `clasp` automatically converts your flat project on [script.google.com](script.google.com) into **folders**. For example:
- _On script.google.com_:
  - `tests/slides.gs`
  - `tests/sheets.gs`
- _locally_:
  - `tests/`
    - `slides.js`
    - `sheets.js`

## Install

First download `clasp`:

```sh
sudo npm i @google/clasp -g
```

Then enable Apps Script API: https://script.google.com/home/usersettings

(If that fails, run this:)
```sh
sudo npm i -g grpc @google/clasp --unsafe-perm
```
## Commands
```
clasp
```
* <a href="login">login</a>

* <a href="logout">logout</a>

* <a href="create">create [scriptTitle] [scriptParentId]</a>

* <a href="status">status</a>

* <a href="undeploy">undeploy &lt;deploymentId&gt;</a>


## How To...
<a name="login"></a>

## login
Logs the user in. Saves the client credentials to an rc file.

**Kind**: global function  
<a name="logout"></a>

## logout
Logs out the user by deleteing client credentials.

**Kind**: global function  
<a name="create"></a>

## create [scriptTitle] [scriptParentId]
Creates a new script project.

**Kind**: global function  
**See**: https://developers.google.com/apps-script/api/reference/rest/v1/projects/create  
**Params**

- [scriptTitle] <code>string</code> - An optional project title.
- [scriptParentId] <code>string</code> - An optional project parent Id. The Drive ID of a parent file
  that the created script project is bound to. This is usually the ID of a
  Google Doc, Google Sheet, Google Form, or Google Slides file. If not set, a
  standalone script project is created.

**Example**  
```js
`create "My Script" "1D_Gxyv*****************************NXO7o"`
```
<a name="status"></a>

## status
Lists files that will be written to the server on `push`.
Ignores files:
- That start with a .
- That don't have an accepted file extension
- That are ignored (filename matches a glob pattern in the ignore file)

**Kind**: global function  
<a name="undeploy"></a>

## undeploy &lt;deploymentId&gt;
Undeploys a deployment of a script.

**Kind**: global function  
**Params**

- &lt;deploymentId&gt;

**Example**  
```js
"undeploy 123"
```
## Troubleshooting

The library requires **Node version >= 4.7.4**. Use this script to check your version and **upgrade Node if necessary**:

```sh
node -v # Check Node version
sudo npm install n -g
sudo n latest
```

## Develop

The Apps Script CLI uses TypeScript to provide autocompletion and linting when developing.
Use an IDE like **Visual Studio Code** for TypeScript autocompletion.

### Setup

- Install `tsc`: `npm install -g typescript`
- Remove your local version of `clasp`: `sudo npm uninstall -g @google/clasp`
  - This will prevent errors when updating `node_modules`.
- Install dependencies: `npm i`

#### After Making a Change

```sh
sudo npm run build;
clasp <command>
```

#### Run Tests (experimental)

Change `describe.skip(...)` to `describe(...)` for relevant tests.

```sh
sudo npm run build;
npm run test
```

#### Lint

- Use `npm run lint` to find common style errors.
- Download [sort-imports](https://marketplace.visualstudio.com/items?itemName=amatiasq.sort-imports) for VSC to automatically sort imports.

#### Generate Docs

The core "How To" section of the docs is generated from JSDoc comments from `index.ts`.

Run `npm run docs` to build the "How To" section. Copy/paste that section into the README.md.

#### Generate Readme

Run `npm run generate-readme` to create a GENERATE-README.md file. Replace the README.md with GENERATED-README.md

#### Publishing `clasp` to npm (admin)

1. Build `index.js` locally. `.gitignore`/`.npmignore` will hide js/ts files appropriately.
1. Bump versions, then publish with: `npm publish --access public`

### Contributing

The main purpose of this tool is to enable local Apps Script development.
If you have a core feature or use-case you'd like to see, find a GitHub issue or
create a detailed proposal of the use-case.
PRs are very welcome! See the [issues](https://github.com/google/clasp/issues) (especially **good first issue** and **help wanted**).

#### How to Submit a Pull Request

1. Look over the test cases in `tests/test.ts`, try cases that the PR may affect.
1. Run [tslint](https://palantir.github.io/tslint/): `npm run lint`.
1. Submit a pull request after testing your feature to make sure it works.

⚡ Powered by the [Apps Script API](https://developers.google.com/apps-script/api/).
