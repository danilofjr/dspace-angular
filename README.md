[![Build Status](https://travis-ci.org/DSpace/dspace-angular.svg?branch=master)](https://travis-ci.org/DSpace/dspace-angular) [![Universal Angular](https://img.shields.io/badge/universal-angular2-brightgreen.svg?style=flat)](https://github.com/angular/universal)

dspace-angular
==============

> The next UI for DSpace, based on Angular 2 Universal.

This project is currently in pre-alpha.

You can find additional information on the [wiki](https://wiki.duraspace.org/display/DSPACE/DSpace+7+-+Angular+UI) or [the project board (waffle.io)](https://waffle.io/DSpace/dspace-angular).

If you're looking for the 2016 Angular 2 DSpace UI prototype, you can find it [here](https://github.com/DSpace-Labs/angular2-ui-prototype)

Quick start
-----------

**Ensure you're running [Node](https://nodejs.org) >= `v5.x`, [npm](https://www.npmjs.com/) >= `v3.x` and [yarn](https://yarnpkg.com) >= `v0.20.x`**

```bash
# clone the repo
git clone https://github.com/DSpace/dspace-angular.git

# change directory to our repo
cd dspace-angular

# install the global dependencies
yarn run global

# install the local dependencies
yarn install

# start the server
yarn start
```

Then go to [http://localhost:3000](http://localhost:3000) in your browser

NOTE: currently there's not much to see at that URL. We really do need your help. If you're interested in jumping in, and you've made it this far, please look at the [the project board (waffle.io)](https://waffle.io/DSpace/dspace-angular), grab a card, and get to work. Thanks!

Not sure where to start? watch the training videos linked in the [Introduction to the technology](#introduction-to-the-technology) section below.

Table of Contents
-----------------

-	[Introduction to the technology](#introduction-to-the-technology)
-	[Requirements](#requirements)
-	[Installing](#installing)
-	[Configuring](#configuring)
-	[Running the app](#running-the-app)
-	[Running in production mode](#running-in-production-mode)
-	[Cleaning](#cleaning)
-	[Testing](#testing)
-	[Documentation](#documentation)
-	[Other commands](#other-commands)
-	[Recommended Editors/IDEs](#recommended-editorsides)
-	[Collaborating](#collaborating)
-	[File Structure](#file-structure)
-	[3rd Party Library Installation](#3rd-party-library-installation)
-	[Frequently asked questions](#frequently-asked-questions)
-	[License](#license)

Introduction to the technology
------------------------------

You can find more information on the technologies used in this project (Angular 2, Typescript, Angular Universal, RxJS, etc) on the [DuraSpace wiki](https://wiki.duraspace.org/display/DSPACE/DSpace+7+UI+Technology+Stack)

Requirements
------------

-	[Node.js](https://nodejs.org), [npm](https://www.npmjs.com/), and [yarn](https://yarnpkg.com)
-	Ensure you're running node >= `v5.x`, npm >= `v3.x` and yarn >= `v0.20.x`

If you have [`nvm`](https://github.com/creationix/nvm#install-script) or [`nvm-windows`](https://github.com/coreybutler/nvm-windows) installed, which is highly recommended, you can run `nvm install --lts && nvm use` to install and start using the latest Node LTS.

Installing
----------

-	`yarn run global` to install the required global dependencies
-	`yarn install` to install the local dependencies

Configuring
-----------

Default configuration file is located in `config/` folder.

To change the default configuration values, create local files that override the parameters you need to change:

-	Create a new `environment.dev.js` file in `config/` for `devel` environment;
-	Create a new `environment.prod.js` file in `config/` for `production` environment;

To use the configuration parameters in your component:

```bash
import { GlobalConfig } from "../config";
```

Running the app
---------------

After you have installed all dependencies you can now run the app. Run `yarn run watch:dev` to start a local server which will watch for changes, rebuild the code, and reload the server for you. You can visit it at `http://localhost:3000`.

Running in production mode
--------------------------

When building for production we're using Ahead of Time (AoT) compilation. With AoT, the browser downloads a pre-compiled version of the application, so it can render the application immediately, without waiting to compile the app first. The compiler is roughly half the size of Angular itself, so omitting it dramatically reduces the application payload.

To build the app for production and start the server run:

```bash
yarn start
```

If you only want to build for production, without starting, run:

```bash
yarn run build:prod:ngc:json
```

This will build the application and put the result in the `dist` folder

Cleaning
--------

```bash
# clean everything, including node_modules. You'll need to run yarn install again afterwards.
yarn run clean

# clean files generated by the production build (.ngfactory files, css files, etc)
yarn run clean:prod

# cleans the distribution directory
yarn run clean:dist
```

Testing
-------

### Unit Test

Unit tests use Karma. You can find the configuration file at the same level of this README file:`./karma.conf.js` If you are going to use a remote test enviroment you need to edit the './karma.conf.js'. Follow the instructions you will find inside it. To executing tests whenever any file changes you can modify the 'autoWatch' option to 'true' and 'singleRun' option to 'false'. A coverage report is also available at: http://localhost:9876/ after you run:`yarn run coverage`.

To correctly run the tests you need to run the build once with:`yarn run build`.

The default browser is Google Chrome.

Place your tests in the same location of the application source code files that they test.

and run:`yarn run test`

### E2E test

E2E tests use Protractor + Selenium server + browsers. You can find the configuration file at the same level of this README file:`./protractor.conf.js` Protractor is installed as 'local' as a dev dependency.

If you are going to use a remote test enviroment you need to edit the './protractor.conf.js'. Follow the instructions you will find inside it.

The default browser is Google Chrome.

Protractor needs a functional instance of the DSpace interface to run the E2E tests, so you need to run:`yarn run watch:dev`

or any command that bring up the DSpace interface.

Place your tests at the following path:`./e2e`

and run:`yarn run e2e`

### Continuous Integration (CI) Test

To run all the tests (e.g.: to run tests with Continuous Integration software) you can execute:`yarn run ci` Keep in mind that this command prerequisites are the sum of unit test and E2E tests.

##Documentation To build the code documentation we use [TYPEDOC](http://typedoc.org). TYPEDOC is a documentation generator for TypeScript projects. It extracts informations from properly formatted comments that can be written within the code files. Follow the instructions [here](http://typedoc.org/guides/doccomments/) to know how to make those comments.

Run:`yarn run docs` to produce the documentation that will be available in the 'doc' folder.

Other commands
--------------

There are many more commands in the `scripts` section of `package.json`. Most of these are executed by one of the commands mentioned above.

A command with a name that starts with `pre` or `post` will be executed automatically before or after the script with the matching name. e.g. if you type `yarn run start` the `prestart` script will run first, then the `start` script will trigger.

Recommended Editors/IDEs
------------------------

To get the most out of TypeScript, you'll need a TypeScript-aware editor. We've had good experiences using these editors:

-	Free
	-	[Visual Studio Code](https://code.visualstudio.com/)
		-	[Debugger for Chrome](https://marketplace.visualstudio.com/items?itemName=msjsdiag.debugger-for-chrome)
	-	[Atom](https://atom.io/)
		-	[TypeScript plugin](https://atom.io/packages/atom-typescript)
-	Paid
	-	[Webstorm](https://www.jetbrains.com/webstorm/download/) or [IntelliJ IDEA Ultimate](https://www.jetbrains.com/idea/)
	-	[Sublime Text](http://www.sublimetext.com/3)
		-	[Typescript-Sublime-Plugin](https://github.com/Microsoft/Typescript-Sublime-plugin#installation)

Collaborating
-------------

See [the guide on the wiki](https://wiki.duraspace.org/display/DSPACE/DSpace+7+-+Angular+2+UI#DSpace7-Angular2UI-Howtocontribute)

File Structure
--------------

```
dspace-angular
├── README.md                                           * This document
├── app.json                                            * Application manifest file
├── config                                              * Folder for configuration files
│   └── environment.default.js                          * Default configuration files
├── dist                                                * Folder for e2e test files
├── e2e                                                 *
│   ├── app.e2e-spec.ts                                 *
│   ├── app.po.ts                                       *
│   ├── pagenotfound                                    *
│   │   ├── pagenotfound.e2e-spec.ts                    *
│   │   └── pagenotfound.po.ts                          *
│   └── tsconfig.json                                   *
├── empty.js                                            *
├── helpers.js                                          *
├── karma.conf.js                                       * Unit Test configuration file
├── nodemon.json                                        * Nodemon (https://nodemon.io/) configuration
├── package.json                                        * This file describes the npm package for this project, its dependencies, scripts, etc.
├── postcss.config.json                                 * PostCSS (http://postcss.org/) configuration file
├── protractor.conf.js                                  * E2E tests configuration file
├── resources                                           * Folder for static resources
│   ├── i18n                                            * Folder for i18n translations
│   │   └── en.json                                     *
│   └── images                                          * Folder for images
│       └── dspace_logo.png                             *
├── rollup-client.js                                    * Rollup (http://rollupjs.org/) configuration for the client
├── rollup-server.js                                    * Rollup (http://rollupjs.org/) configuration for the server
├── spec-bundle.js                                      *
├── src                                                 * The source of the application
│   ├── app                                             * The location of the app module, and root of the application shared by client and server
│   │   ├── app-routing.module.ts                       *
│   │   ├── app.component.html                          *
│   │   ├── app.component.scss                          *
│   │   ├── app.component.spec.ts                       *
│   │   ├── app.component.ts                            *
│   │   ├── app.effects.ts                              *
│   │   ├── app.module.ts                               *
│   │   ├── app.reducers.ts                             *
│   │   ├── core                                        *
│   │   ├── header                                      *
│   │   ├── home                                        *
│   │   ├── pagenotfound                                *
│   │   ├── shared                                      *
│   │   └── store.actions.ts                            *
│   ├── backend                                         * Folder containing a mock of the REST API, hosted by the express server
│   │   ├── api.ts                                      *
│   │   ├── bitstreams.ts                               *
│   │   ├── bundles.ts                                  *
│   │   ├── cache.ts                                    *
│   │   ├── collections.ts                              *
│   │   ├── db.ts                                       *
│   │   ├── items.ts                                    *
│   │   └── metadata.ts                                 *
│   ├── client.aot.ts                                   * The bootstrap file for the client, in production
│   ├── client.ts                                       * The bootstrap file for the client, during development
│   ├── config.ts                                       * File that loads environmental and shareable settings and makes them available to app components
│   ├── index.html                                      * The index.html file
│   ├── platform                                        *
│   │   ├── angular2-meta.ts                            *
│   │   ├── modules                                     *
│   │   │   ├── browser.module.ts                       * The root module for the client
│   │   │   └── node.module.ts                          * The root module for the server
│   │   └── workarounds                                 *
│   │       ├── __workaround.browser.ts                 *
│   │       └── __workaround.node.ts                    *
│   ├── server.aot.ts                                   * The express (http://expressjs.com/) config and bootstrap file for the server, in production
│   ├── server.routes.ts                                * The routes file for the server
│   ├── server.ts                                       * The express (http://expressjs.com/) config and bootstrap file for the server, during development
│   ├── styles                                          * Folder containing global styles.
│   │   ├── main.scss                                   * Global scss file
│   │   └── variables.scss                              * Global sass variables file
│   └── typings.d.ts                                    * File that allows you to add custom typings for libraries without TypeScript support
├── tsconfig.aot.json                                   * TypeScript config for production builds
├── tsconfig.json                                       * TypeScript config for development build
├── tslint.json                                         * TSLint (https://palantir.github.io/tslint/) configuration
├── typedoc.json                                        * TYPEDOC configuration
├── webpack.config.ts                                   * Webpack (https://webpack.github.io/) config for development builds
├── webpack.prod.config.ts                              * Webpack (https://webpack.github.io/) config for production builds
├── webpack.test.config.js                              * Webpack (https://webpack.github.io/) config for testing
└── yarn.lock                                           * Yarn lockfile (https://yarnpkg.com/en/docs/yarn-lock)
```

3rd Party Library Installation
------------------------------

Install your library via `yarn add lib-name --save` and import it in your code. `--save` will add it to `package.json`.

If the library does not include typings, you can install them using yarn:

```bash
yarn add d3 --save
yarn add @types/d3 --save-dev
```

If the library doesn't have typings available at `@types/`, you can still use it by manually adding typings for it:

1.	In `src/typings.d.ts`, add the following code:

	```typescript
	  declare module 'typeless-package';
	```

2.	Then, in the component or file that uses the library, add the following code:

	```typescript
	  import * as typelessPackage from 'typeless-package';
	  typelessPackage.method();
	```

Done. Note: you might need or find useful to define more typings for the library that you're trying to use.

If you're importing a module that uses CommonJS you need to import as

```typescript
import * as _ from 'lodash';
```

yarn lockfile
-------------

This project makes use of yarn to ensure that the exact same dependency versions are used every time you install it.

yarn creates the file [`yarn.lock`](https://yarnpkg.com/en/docs/yarn-lock) to track those versions. That file is updated automatically every time you install a new dependency from the commandline (by using `yarn add some-lib --save` or `yarn add some-lib --save-dev`).

If you manually add a package or change a version in `package.json` you'll have to update yarn's lock file as well. You can do so by running `yarn upgrade`

Frequently asked questions
--------------------------

-	Why is my service, aka provider, is not injecting a parameter correctly?
	-	Please use `@Injectable()` for your service for typescript to correctly attach the metadata
-	Where do I write my tests?
	-	You can write your tests next to your component files. e.g. for `src/app/home/home.component.ts` call it `src/app/home/home.component.spec.ts`
-	How do I start the app when I get `EACCES` and `EADDRINUSE` errors?
	-	The `EADDRINUSE` error means the port `3000` is currently being used and `EACCES` is lack of permission to build files to `./dist/`
-	What are the naming conventions for Angular 2?
	-	See [the official angular 2 style guide](https://angular.io/styleguide)
-	Why is the size of my app larger in development?
	-	The production build uses a whole host of techniques (ahead-of-time compilation, rollup to remove unreachable code, minification, etc.) to reduce the size, that aren't used during development in the intrest of build speed.
-	node-pre-gyp ERR in yarn install (Windows)
	-	install Python x86 version between 2.5 and 3.0 on windows. See [this issue](https://github.com/AngularClass/angular2-webpack-starter/issues/626)
-	How do I handle merge conflicts in yarn.lock?
	-	first check out the yarn.lock file from the branch you're merging in to yours: e.g. `git checkout --theirs yarn.lock`
	-	now run `yarn install` again. Yarn will create a new lockfile that contains both sets of changes.
	-	then run `git add yarn.lock` to stage the lockfile for commit
	-	and `git commit` to conclude the merge

License
-------

http://www.dspace.org/license
