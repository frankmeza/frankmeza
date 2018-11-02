---
title: Handle Click Events With React, TypeScript, and No JSX Lambdas
date: "2018-11-01T09:00:00.0Z"
layout: post
draft: false
path: "/posts/handle-click-events-with-react-typescript-and-no-jsx-lambdas/"
category: "web development"
tags:
  - "react"
  - "typescript"
  - "jsx lambdas"
description: "How to handle strongly typed click events by passing functions into a child or event grandchild component."
---

# Handling Strongly Typed ReactDOM events with TypeScript

## Has This Happened To You?

You're working away on a strict Typescript/React project and you need to set parent state based on user interaction with a child or grandchild component. Okay, it's possible. But! these rules apply:

- You can't use lambda functions in TSX components.
- You forgot how you did it last time.
- I mean it, everything is super strictly strongly typed.

The hard part is knowing the event type.

Let's see it in plain JavaScript:

```javascript
// handleClickAndSetStateWithClickedText :: void
const handleClickAndSetStateWithClickedText = event => {
  this.setState({ text: event.target.value })
}
```

... simple enough, right?

But in Typescript, you must define the typedef of the function, and with `"jsx-lambdas": false` now you're having tons of strongly-typed, functions that return functions fun.

Here is the crux of the solution:

```typescript
// in grand/parent component, as a component method

// in English: a public function handleClickAndSetStateWithClickedText,
// takes an event of type React.MouseEvent<HTMLElement>,
// and returns a function that returns void

// func :: React.MouseEvent<HTMLElement> -> () => void
public handleClickAndSetStateWithClickedText = (
    event: React.MouseEvent<HTMLElement>,
): (() => void) => {
    const { innerText } = event.currentTarget
    this.setFilter(innerText)
    return () => null
}

// passed into grand/child as props, with this signature:
export interface ChildComponentProps {
    readonly handleClickAndSetStateWithClickedText: (
        event: React.MouseEvent<HTMLElement>,
    ) => () => void
}

// passed into onClick at long last
<p onClick={onSelectItem}>{title}</p>
```

Hopefully, this helps you complete your feature and win the day, feel free to give me credit :D

Que tenha um bom dia!
