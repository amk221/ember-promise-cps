# ember-promise-cps

<a href="http://emberobserver.com/addons/ember-promise-cps"><img src="http://emberobserver.com/badges/ember-promise-cps.svg"></a> &nbsp; <a href="https://david-dm.org/amk221/ember-promise-cps#badge-embed"><img src="https://david-dm.org/amk221/ember-promise-cps.svg"></a> &nbsp; <a href="https://david-dm.org/amk221/ember-promise-cps#dev-badge-embed"><img src="https://david-dm.org/amk221/ember-promise-cps/dev-status.svg"></a> &nbsp; <a href="https://codeclimate.com/github/amk221/ember-promise-cps"><img src="https://codeclimate.com/github/amk221/ember-promise-cps/badges/gpa.svg" /></a> &nbsp; <a href="http://travis-ci.org/amk221/ember-promise-cps"><img src="https://travis-ci.org/amk221/ember-promise-cps.svg?branch=master"></a>

This Ember addon provides you with utils and computed property macros to aid with common problems when working with promises in components.

1. Subsequent promises take priorty over 'old' promises<br>
  (You're usually only ever bothered about the result from the most recent promise)
2. Setting the result of the promise on the component when the component may since have been destroyed will error.

## No longer maintained

Please use [http://ember-concurrency.com](http://ember-concurrency.com) instead

## Example

```handlebars
{{! application.hbs }}
{{items-list items-promise=promiseForItems}}
```

```javascript
// items-list/component.js
import { promiseObject } from 'ember-promise-cps/macros';

export default Component.extend({
  items: promiseArray('items-promise')
});
```

```handlebars
{{! items-list/template.hbs }}
{{#if items.isPending}}
  Loading items
{{else if items.isRejected}}
  Unable to display items: {{items.reason}}
{{else if items.isFulfilled}}
  {{#each items as |item|}}
    ...
  {{/each}}
{{/if}}
```

### Available utils/macros

* Utils
  * `promiseObject({ foo: 'bar' })`
  * `promiseArray([ 'foo', 'bar' ])`
* Macros
  * `promiseObject('myObject')`
  * `promiseArray('myArray')`

### Installation
```
ember install ember-promise-cps
```
