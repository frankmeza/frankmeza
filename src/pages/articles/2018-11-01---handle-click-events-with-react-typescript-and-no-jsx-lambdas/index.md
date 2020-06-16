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

You're working away on a strict Typescript/React project and you need to set parent (or even grandparent) state based on user interaction with a child or grandchild component. Okay, it's possible. But! these rules apply:

- I mean it, everything is super strictly strongly typed.
- You can't use lambda functions in TSX components.
- You forgot how you did it last time.


Let's see it in plain JavaScript:

```javascript
// handle click and set state with clicked text :: void
const setTextInParentState = event => {
  this.setState({ text: event.target.value })
}
```

Then this is passed through to the child, or even to the grandchild... simple enough, right?

But in Typescript, you must define the data type of the function output, and with `"jsx-lambdas": false`, now you're having tons of strongly-typed, higher order functions fun.

The hard part is knowing the event type. Spoiler alert, here it is:

```typescript
event: React.MouseEvent<HTMLElement>
```
Here is the crux of the solution:

```typescript
// in grand/parent component, as a component method

// in English: a public function setTextInParentState,
// takes an event of type React.MouseEvent<HTMLElement>,
// and returns a function that returns void

// func :: React.MouseEvent<HTMLElement> -> () => void
public setTextInParentState = (
  event: React.MouseEvent<HTMLElement>,
): (() => void) => {
  const { innerText } = event.currentTarget;
  this.setState({ text: innerText });

  return () => null;
}

// passed into grand/child as props, with this signature:
export interface ChildProps {
    readonly setTextInParentState: (
        event: React.MouseEvent<HTMLElement>,
    ) => () => void
}

// passed into onClick at long last
<p onClick={onSelectItem}>{title}</p>
```

Hopefully, this helps you complete your feature and win the day, feel free to give me credit 👍

Que tenha um bom dia!
