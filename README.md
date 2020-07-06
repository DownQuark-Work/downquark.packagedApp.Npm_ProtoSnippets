# downquark.work Javascript Prototypes

> Creating a commonly used set of functions that also signals the official start of DownQuark’s commitment to Open Source.

## Table of contents

- [downquark.work Javascript Prototypes](#downquarkwork-javascript-prototypes)
  - [Table of contents](#table-of-contents)
  - [Common usage](#common-usage)
  - [Installation](#installation)
  - [Current Modules & Methods](#current-modules--methods)
## Common usage
Using CommonJS for these to help differentiate between AMD/RequireJS modules commonly reused in projects. Any prototypes being used should be imported and instantiated a single time.
You will be able to specify which prototypes you wish to by importing the `Default` set of the module, or handpicking using the `include` method.
Currently, you can choose defaults, individuals, or add non-defaults

## Installation
To import and init the defaults only:
- `const Prototypes = require('@downquark/utils-js-prototypes').Defaults()`
To select and initialize non-default methods:
```
const {konsole, date} = require('@downquark/utils-js-prototypes').include
date.Defaults() // <-- to include the modules defaults
konsole.include.consoleDev() // <-- specific OR non-default methods
```
Single line import and init examples for or non-default methods from 
```
const _ = require('@downquark/utils-js-prototypes').include.date.include.calendar()
const _2 = require('@downquark/utils-js-prototypes').include.date.Defaults()
```

This way of handling prototypes allows for easy scalability. We can create as many methods as we like without concern of package size or code bloat because we only import what is needed per project. e.g.:
` const multi-level-nested-prototype = require('@downquark/utils-js-prototypes').include.date.include.calendar.include.moonCycles.include.waning()`

We will continue to update this library with helpful snippets - while ensuring that we keep _**100**_% [code coverage](./CONTRIBUTING.md#Testing)
Next steps will be to port over relevant snippets from [30 seconds of code](https://www.30secondsofcode.org/js/p/1).

## Current Modules & Methods

<details>
  <summary>Array</summary>

  method|_description_|
  -|-:|
  **last**| _Returns the last element of the array without modifying the original array_|
  **len**| _Returns the 0 index based length of the array_
  _Example:_|`array.last === array[array.len]`|
  | | |
  **shuffle**| _Shuffles elements in original array and returns modified data_|
  _Example:_|`[1,2,3].shuffle() // [3,1,2]`|
  **unique**| _Returns array with duplicate elements removed without modifying original array|
_Example:_|`[1,1,2,3].unique() // [1,2,3]`|
</details>
<details>
  <summary>Console</summary>

  method|_description_|
  -|-:|
  **consoleDev**| _A more concise version of [qonsole](https://www.npmjs.com/package/qonsole)_|
_NOTE:_|Quite a bit going on here. Please see [tests](./src/spec/console.spec.js) for usage information.
</details>
<details>
  <summary>Date</summary>

  method|_description_|
  -|-:|
  **stringFormats**| _Returns date in specified format_|
  _Example:_|`new Date().STANDARD.formatDate() // '07 / 01 / 2020'`|
  **makeReadable**| _Returns human readable values for days and monts_|
  _Example:_|`new Date().getNamedDay(3) // 'Wed'`|
  _Example:_|`new Date().getNamedDay(3,true) // 'Wednesday'`|
  **ranged**| _Formats and returns requested data for use with date ranges_|
  _Example:_|`new Date().getEpochRange('jan 2020','feb 2020') // [1577854800000, 1580533200000]`|
  _Example:_|`new Date().getRandomDate() // defaults to a 30 day range with _new Date()_ as mid-point`|
  **calendar**| _Returns all information needed to render a calendar grid_|
  _Example:_|`new Date().getFullCalendarDates(CALENDAR_STARTING_POINT)`|
</details>
<details>
  <summary>Math</summary>

  method|_description_|
  -|-:|
  **msInDay**| _Returns the number of miliseconds in a 24 hour period_|
  _Example:_|`Math.msInDay // 86400000`|
  _TODO:_|move this to `Number`
</details>
<details>
  <summary>Number</summary>

  method|_description_|
  -|-:|
  **msOffset**| _Returns timestamp of a date specified by an offset_|
  _Example:_|`new Date(dateTime).getTime().msOffset('-13M') //  timestamp for a day 13 months previous: 86400000`|
  _TODO:_|move this to `Math`
</details>
<details>
  <summary>String</summary>

  method|_description_|
  -|-:|
  **endsWith**| _Returns boolean based on end of string search criteria and optional specified offset_|
  _Example:_|`'I have a question.'.endsWith('question.') // true`|
  _Example:_|`'I have a question.'.endsWith('have',6)' // true`|
  **padStart**| _Returns string with leading padding of spaced or optional specified character(s)_|
  _Example:_|`'abc'.padStart('10') // '       abc'`|
  _Example:_|`'abc'.padStart('10', "foo") // 'foofoofabc'`|
</details>
