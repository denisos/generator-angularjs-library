# AngularJS component library generator

[Yeoman](http://yeoman.io) generator to create standalone AngularJS component libraries in seconds!

[![Build Status](https://travis-ci.org/jvandemo/generator-angularjs-library.png?branch=master)](https://travis-ci.org/jvandemo/generator-angularjs-library)

![Overview](http://i.imgur.com/KR6fT67.png)

## In short

If you want to create a standalone library with filters, directives, services, etc for use in your AngularJS applications, then this generator may just be what you need.

The generator automatically:

- creates a complete directory structure with boilerplate code for your [AngularJS](https://angularjs.org/) library
- creates a complete directory structure for your tests
- configures [Gulp](http://gulpjs.com/) to build your code and automate testing
- sets up [Karma](http://karma-runner.github.io) to run your unit tests using [Mocha](http://visionmedia.github.io/mocha/), [Chai](http://chaijs.com/) and [Sinon](http://sinonjs.org/)

> This generator is **NOT** made to generate complete AngularJS applications. If you want to generate a complete AngularJS web application with routes, views, etc then please use [generator-angular](https://github.com/yeoman/generator-angular).

## Quick start

Make sure you have [yeoman](http://yeoman.io) installed:

```sh
$ npm install -g yo
```

Install the generator:

```sh
$ npm install -g generator-angularjs-library
```

Create a new project directory:

```sh
$ mkdir sample-project
$ cd sample-project
```

Run:

```sh
$ yo angularjs-library
```

Answer the questions and the generator will create the boilerplate for your library:

![AngularJS library generator](http://i.imgur.com/R4upcwp.png)

## What the generator does for you

The generator automatically:

- creates a `src` directory structure with the boilerplate code for your AngularJS library
- creates a `test` directory structure to store your unit tests and e2e tests
- creates initial unit tests in the `test/unit/` directory
- creates a custom `gulpfile.js` to build, minify and uglify your library
- creates a custom `karma-src.conf.js` to let karma run your unit tests
- creates a custom `karma-dist-concatenated.conf.js` to let karma run your unit tests
- creates a custom `karma-dist-minified.conf.js` to let karma run your unit tests
- creates a custom `bower.json` with necessary devDependencies and appropriate ignore files
- creates a custom `package.json` file for your library
- creates a custom `.travis.yml` file to enable travis support
- creates a custom `.jshintrc` to support angular global during syntax check
- creates a custom `README.md` file
- creates a custom `LICENSE` file

Running the generator using library name "Your Library" will result in the following files being generated for you:

```sh
.
├── LICENSE                                     # License file with your name in it
├── README.md                                   # Basic README.md file with title of library
├── bower.json                                  # Bower configuration for your library
├── dist
│   ├── your-library.js                         # Your library ready to use in your application
│   └── your-library.min.js                     # Minified version of your library for production
├── gulpfile.js                                 # Gulp configuration to build your library
├── karma-dist-concatenated.conf.js             # Karma configuration to run unit tests using your-library.js
├── karma-dist-minified.conf.js                 # Karma configuration to run unit tests using your-library.min.js
├── karma-src.conf.js                           # Karma configuration to run unit tests using src/**/*.js
├── package.json                                # Npm configuration for your library
├── src                                         # Source directory with modular structure
│   └── your-library
│       ├── directives
│       ├── filters
│       ├── services
│       └── yourLibrary.module.js
└── test                                        # Test directory with modulare structure
    ├── e2e
    │   └── yourLibrary
    └── unit
        └── yourLibrary
            ├── directives
            ├── filters
            ├── services
            └── yourLibrarySpec.js

14 directories, 14 files
```

```sh
.
├── .bowerrc                                  # Configure bower directory for development
├── .editorconfig                             # Editor configuration for code consistency
├── .gitignore                                # Includes files that Git should ignore
├── .jshintrc                                 # JSHint config with angular global support
├── LICENSE                                   # Custom license file with your name in it
├── README.md                                 # Basic README.md with title of your library
├── bower.json                                # Bower configuration with custom devDependencies and ignore files
├── dist                                      # This folder and contents is generated by running gulp
│   ├── sample-library.js                     # Your library, ready to use in your development environment
│   └── sample-library.min.js                 # Your library, ready to use in your production environment
├── gulpfile.js                               # Gulp configuration with definition to build your library
├── karma-dist-concatenated.conf.js           # Karma configuration to run unit tests using sample-library.js
├── karma-dist-minified.conf.js               # Karma configuration to run unit tests using sample-library.min.js
├── karma-src.conf.js                         # Karma configuration to run unit tests using src/**/*.js
├── package.json                              # Npm configuration with necessary dependencies for development
├── src                                       # Source directory
│   └── sample-library
│       ├── directives                        # Directory where you can store directives
│       ├── filters                           # Directory where you can store filters
│       ├── sampleLibrary.module.js           # Main module file
│       └── services                          # Directory where you can store services
└── test
    ├── e2e
    │   └── sample-library                    # Directory where you can store E2E tests
    └── unit
        └── sample-library
            ├── directives                    # Directory where you can store unit tests for directives
            ├── filters                       # Directory where you can store unit tests for filters
            ├── sampleLibrarySpec.js          # Unit tests for main module
            └── services                      # Directory where you can store unit tests for services
```

## How to use the generated boilerplate

The basic library structure is automatically created for you in the `src` folder.

You can edit the existing files or add additional files in the `src` folder to add components to your library.

Once you have added files in the `src` directory, you can update the files in the `dist` directory using:

```sh
$ gulp
```

First gulp will

- check the JavaScript syntax of `src/**/*.js`
- run all unit tests using the code in your `src` directory

to make sure the code is fine.

Then all files in the `src` directory will be concatenated into 2 files in the `dist` directory:

- `<your-library-name>.js`: regular version of your library to use in a development environment
- `<your-library-name>.min.js`: minified version of your library to use in a production environment

![AngularJS library generator](http://i.imgur.com/v958Eml.png)

## Manually testing your code

The generator creates 3 configurations for unit testing:

- `karma-src.conf.js`: run unit tests using `src/**/*.js`
- `karma-dist-concatenated.conf.js`: run unit tests using `dist/<your-library-name>.js`
- `karma-dist-minified.conf.js`: run unit tests using `dist/<your-library-name>.min.js`

By default, `gulp` will run `karma-src.conf.js`, but you can use the following preconfigured Gulp tasks to specify the suite you want to run:

```sh
# Run unit tests using src/**/*.js
$ gulp test-src

# Run unit tests using dist/<your-library-name>.js
$ gulp test-dist-concatenated

# Run unit tests using dist/<your-library-name>.min.js
$ gulp test-dist-minified
```

![AngularJS library generator](http://i.imgur.com/FL7exkv.png)

This allows you to unit test the different builds of your code to ensure they all work as expected.

## Frequently asked questions

- [Why is there a `.prefix` and a `.suffix` file and why do they do?](https://github.com/jvandemo/generator-angularjs-library/issues/2)

## Want to contribute?

Help make this project better - fork and send a PR or create an (issue)[https://github.com/jvandemo/generator-angularjs-library/issues].

## Change log

### v3.0.0

- Added JSHint syntax check
- Added gulp-plumber support for better error handling
- Gulp now starts watching for file changes by default for easier development
- Removed prefix and suffix files in favor of AngularJS styleguide support
- Moved bower dependencies to devDependencies to prevent version conflicts
- Updated bower dependencies to automatically install latest versions
- Let travis perform bower install before running tests
- Set default version as 0.1.0 instead of 0.0.0

### v2.0.0

- Completely rewritten to support newer version of Yeoman
- Now uses Gulp instead of Grunt as task runner
- Now uses Mocha as test framework instead of Jasmine
- Added travis support

### v1.4.0

- Updated bower and npm package versions

### v1.3.0

- Added automatic creation of README.md
- Added automatic creation of LICENSE.txt
- Added support for author name and email

### v1.2.1

- Removed obsolete dependencies

### v1.2.0

- Added support for PhantomJS in Karma configuration
- Fixed bower directory in gitignore

### v1.1.0

- Added support for library names with spaces and capitals

### v1.0.3

- Added chalk dependency

## License

MIT
