# markdown.jsx [![](http://img.shields.io/npm/dm/markdown-jsx.svg?style=flat)](https://www.npmjs.org/package/markdown-jsx)

> Build markdown using jsx with html-like components

**markdown.jsx** makes generating markdown easier and readable.

_Used in [typedoc.md](https://github.com/martiliones/typedoc.md)_.

```jsx
import { renderMarkdown, code, b } from 'markdown-jsx'

const description = (
  <p>use <code>jsx</code> to build <b>markdown</b></p>
)

// use `jsx` to build **markdown**
console.log(renderMarkdown(description))
```

## Installation

Install core package:

```bash
npm install markdown-jsx
```

then install the babel plugin

```bash
npm install @markdown-jsx/babel --save-dev
```

and add it to your babel config:

```json
{
  "plugins": ["@markdown-jsx/babel"]
}
```

## Guide

### Fragment

Fragment component or empty `<>...</>` tags can be used to combine markdown blocks:

```jsx
const example = (
  <>
    There is some code:

    <code lang={'js'}>
      console.log(1)
    </code>
  </>
)
```

### Components

To create a component,  use functions that returns jsx:

```jsx
const footer = () => (
  <>
    <h1></h1> {/* using empty heading as a sepearator */}
    <p align="center">
      <a href="LICENSE">MIT</a> - martiliones
    </p>
  </>
)

const readme = (
  <>
    { /* ... */}
    <footer/>
  </>
)
```

Use passed arguments to place children inside your components and access component properties:

```jsx
const highlight = (props, children) => (
  <blockquote>
    <b>{props.level}</b>
    {children}
  </blockquote>
)

const warning = (
  <highlight level={'Warning'}>
     Critical content demanding immediate user attention due to potential risks.
  </highlight>
)
```

<h1></h1>

<p align="center">
  drink water 🥛
</p>
