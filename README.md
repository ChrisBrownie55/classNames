# classnames

<img alt="Dependency Status" src="https://david-dm.org/ChrisBrownie55/classnames.svg" />
<a href="https://codeclimate.com/github/ChrisBrownie55/classnames/maintainability">
  <img src="https://api.codeclimate.com/v1/badges/8879bdee9b5f03fe7119/maintainability" />
</a>
<a href="https://snyk.io/test/github/ChrisBrownie55/classnames?targetFile=package.json">
  <img src="https://snyk.io/test/github/ChrisBrownie55/classnames/badge.svg?targetFile=package.json" alt="Known Vulnerabilities" data-canonical-src="https://snyk.io/test/github/ChrisBrownie55/classnames?targetFile=package.json" />
</a>
<a href="https://badge.fury.io/js/classnames">
  <img src="https://badge.fury.io/js/classnames.svg" alt="npm version" />
</a>
<img src="https://img.shields.io/npm/classnames/localeval.svg" />

A simple and small JavaScript utility for joining class names together. Made for use with frameworks like React, but can be used how you see fit.

## **Installation:**
```bash
npm i @chrisbrownie55/classnames
# or
yarn add @chrisbrownie55/classnames
```

## **Usage:**

### First let's import it
```js
// Node
const classNames = require('@chrisbrownie55/classnames');

// ESM
import classNames from '@chrisbrownie55/classnames';
```

### Now let's use it
```js
/* STRINGS */
classNames('loading-indicator', 'red-bg');
// => 'loading-indicator red-bg'

/* OBJECTS, falsey values cause extra spaces */
classNames({ animated: 'truthy value', 'inactive-bg': false });
// => 'animated '

/* OBJECTS & STRINGS */
classNames('loading-indicator', { animated: true });
// => 'loading-indicator animated'

/* ARRAYS (recursively flattened) */
classNames(['activated', { nested: true }]);
// => 'activated nested'

/*
  All other types will be ignored but will cause extra spaces
  if they are either, falsey object (null) or not an object/string/array
*/
classNames('test', undefined);
// => 'test '

classNames(null, 'test');
// => ' test'

/* Multiple of same value will not be removed as there is no need */
classNames('test', 'test', 'test');
// => 'test test test'
```

### NOTE: extra spaces will not affect use with DOM elements (includes framework elements like React)

## What about using it in React.js?

You simply pass the call to `classNames()` as the value for the attribute `className={}`

```jsx
/* REACT CLASS COMPONENT */
class MyComponent extends React.Component {
  render() {
    const { className } = this.props;
    return <div className={classNames('test', className)}></div>;
  }
}

/* REACT FUNCTION COMPONENT */
function MyComponent({ className }) {
  return <div className={classNames('test', className)}></div>;
}
```

# License
[MIT](https://github.com/ChrisBrownie55/class-join/blob/master/LICENSE) Copyright © 2018 Christopher Brown

Influenced by Jed Watson's [classnames](https://github.com/JedWatson/classnames)
