[![npm version](https://badge.fury.io/js/react-on-visible.svg)](https://badge.fury.io/js/react-on-visible)
# React OnVisible component

## Live demo

Live example: https://dazld.github.io/react-on-visible/demo/

## Description

This is a higher order react component that applies the css class `visible` to the container when the element becomes more than 50% visible in the browser viewport.

It only attaches to browser events on the client, so is also safe to use for server rendering.

Viewport visibility is calculated by listening to a debounced window scroll event (10ms), and once the element has been found to be visible, no further changes are applied unless the `bounce` prop is set to true.

## API

### `percent` - number

Percentage (100 based) of element that should be visible before triggering change. eg `percent={80}`

### `visibleClassName` - string

ClassName that should be added to element once visible

### `onChange` - function

Callback when visibility changes. Argument is a boolean, `true` for visible, `false` for not.

### `bounce` - boolean

Whether visibility should be continuously calculated, or just until the element becomes visible. defaults to `false`. Go easy with this, don't expect amazing performance with many tens or hundreds of elements (`getBoundingClientRect`).

### `setDefaultProps` - static function

The user can override default props via this function. If you want everything to bounce, for example, then can do this:
```
import OnVisible, { setDefaultProps } from 'react-on-visible';

setDefaultProps({
    bounce: true,
    visibleClassName: 'appear',
    percent: 10
});

```

and so on.

## Example

```js

import React from 'react';
import OnVisible from 'react-on-visible';

export default function someComponent(props) {
  return (
    <OnVisible className="my-container">
      <h1>I will be rendered inside a div that has class 'my-container' only until I become visible, at which point the container will have the classes 'my-container visible'</h1>
    </OnVisible>
  );
}

```

A further example is available in the `demo` folder of this project.

## Changelog

### 1.1.0

- Added `bounce` prop and function to set default props.

### 1.0.3

- added `onChange` callback prop option (thanks @rdjpalmer)
