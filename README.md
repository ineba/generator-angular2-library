![generator-angular-2-library](https://cloud.githubusercontent.com/assets/1859381/15875067/91043b32-2d06-11e6-8ab5-de4dfcd0bfa8.jpg)
[![NPM version][npm-image]][npm-url] [![Build Status][travis-image]][travis-url]

[Yeoman](http://yeoman.io) generator to create a standalone [Angular 2](https://angular.io/) library in seconds.

If you want to create an Angular 2 library with directives, services and/or pipes, then this generator is just what you need.

The generator:

- creates and configures `package.json` for your library
- creates and configures `tsconfig.json` for your library
- creates and configures `tslint.json` for your library
- creates and configures `typings.json` for your library
- creates and configures `.gitignore`, `.npmignore` and `.travis.yml`
- creates the main library file
- creates a sample directive, component, service and pipe
- creates a default export for future compatibility with angular cli, see this [discussion for more](https://github.com/angular/angular-cli/issues/96)
- configures [tslint](https://palantir.github.io/tslint/) for you with [codelyzer](https://github.com/mgechev/codelyzer) support

## Quick start

![generator-angular2-library-demo](https://cloud.githubusercontent.com/assets/1859381/16332792/45936764-39f8-11e6-884b-c7095bafc59b.gif)

First, install [Yeoman](http://yeoman.io) and generator-angular2-library using [npm](https://www.npmjs.com/) (assuming you already have [node.js](https://nodejs.org/) pre-installed).

```bash
$ npm install -g yo
$ npm install -g generator-angular2-library
```

make a new directory and `cd` into it:

```bash
$ mkdir angular2-library-name
$ cd angular2-library-name
```

and generate your new library:

```bash
$ yo angular2-library
```

The generator will prompt you for:

```bash
? Your full name: Jurgen Van de Moere
? Your email address: jurgen.van.de.moere@gmail.com
? Your library name (kebab case): angular2-library-name
? Git repository url: https://github.com/jvandemo/angular2-library-name
```

and create the following files for you:

```bash
.
├── README.MD
├── index.ts
├── package.json
├── src
│   ├── sample.component.ts
│   ├── sample.directive.ts
│   ├── sample.pipe.ts
│   └── sample.service.ts
├── tsconfig.json
├── tslint.json
└── typings.json
```

You can then add or edit `*.ts` files in the `src/` directory and run:

```bash
$ npm run tsc
```

to automatically create all `*.js`, `*.js.map` and `*.d.ts` files in the `dist/` directory.

## Tslint

Everything comes pre-configured with tslint and codelyzer support. To lint your code:

```bash
$ npm run lint
```

## Consuming your library

Once you have published your library to npm, you can import your library in any Angular application by running:

```bash
$ npm install sample-library # use the name you used to publish to npm
```

and then from your Angular AppModule:

```typescript
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';
import { FormsModule } from '@angular/forms';
import { HttpModule } from '@angular/http';

import { AppComponent } from './app.component';

// Import your library
import { SampleModule } from 'sample-library';

@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [
    BrowserModule,
    FormsModule,
    HttpModule,
    
    // Specify your library as an import
    LibraryModule
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```

Once your library is imported, you can use its components, directives and pipes in your Angular application.

## To do

- Create build process for building library that automatically registers with SystemJS so it can be hosted statically and imported using `<script>` element
- Create process for running unit tests

## Issues

Please report bugs and issues [here](https://github.com/jvandemo/generator-angular2-library/issues).

## Development

To run the generator unit tests:

```bash
$ npm run test
```

## License

MIT © [Jurgen Van de Moere](http://www.jvandemo.com)

## Change log

### v2.2.0

- Updated dependencies in package.json to Angular 2 final

### v2.1.0

- Updated templates to Angular 2.0.0 RC3 syntax

### v2.0.0

- Updated with file structure using `src` and `dist` directory

### v1.1.1

- Updated templates to Angular 2.0.0 RC1 syntax

### v1.1.0

- Added codelyzer support
- Added tslint support
- Added typings support

### v1.0.0

- BREAKING CHANGE: Updated to support [Angular 2.0.0-rc.1](https://github.com/angular/angular/blob/master/CHANGELOG.md#200-rc1-2016-05-03)

### v0.6.0

- Updated dependency versions

### v0.5.0

- Added `browser.d.ts` to files in `tsconfig.json` instead of using tripleslash (see #9)

### v0.4.0

- Added reference to Angular typings

### v0.3.1

- Removed explicit RxJS dependency

### v0.3.0

- Updated to Angular 2 beta

### v0.2.0

- Added documentation
- Added support for `PROVIDERS`, `DIRECTIVES` and `PIPES`

### v0.1.0

- Added documentation
- Added boilerplate scaffolding
- Initial version

[npm-image]: https://badge.fury.io/js/generator-angular2-library.svg
[npm-url]: https://npmjs.org/package/generator-angular2-library
[travis-image]: https://travis-ci.org/jvandemo/generator-angular2-library.svg?branch=master
[travis-url]: https://travis-ci.org/jvandemo/generator-angular2-library
[daviddm-image]: https://david-dm.org/jvandemo/generator-angular2-library.svg?theme=shields.io
[daviddm-url]: https://david-dm.org/jvandemo/generator-angular2-library
[coveralls-image]: https://coveralls.io/repos/jvandemo/generator-angular2-library/badge.svg
[coveralls-url]: https://coveralls.io/r/jvandemo/generator-angular2-library
