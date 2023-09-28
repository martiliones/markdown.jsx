# henka

build markdown using jsx with html-like components

```jsx
import { renderMarkdown, code, b } from 'henka'

const description = (
  <p>use <code>jsx</code> to build <b>markdown</b></p>
)

// use `jsx` to build **markdown**
console.log(renderMarkdown(description))
```

## Installation

```bash
npm i henka @henka/jsx-plugin
```

then add the jsx plugin to your babel config:

```json
{
  "plugins": ["@henka/jsx-plugin"]
}
```

## Guide

### Fragment

fragment component or empty `<>...</>` tags can be used to combine markdown blocks:

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

to create a component,  use functions that returns jsx:

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

use passed arguments to place children inside your components and access component properties:

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
