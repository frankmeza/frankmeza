---
title: Short Circuit Statements
date: "2018-07-01T00:00:00.0Z"
layout: post
draft: false
path: "/posts/short-circuit-statements/"
category: "web development"
tags:
  - "web development"
  - "code readability"
  - "almost tweetable"
description: "A short circuit statement is like a shortened version of a ternary statement that does one thing or no-thing."
---

## Do You Do This?

There you are writing code. You want to run a function if a certain condition is met. Otherwise, you want your application to do nothing else concerning that function right now. You immediately think of a ternary statement:

```javascript
isConditionTrue ? myFunction() : null
```

Let's assume that you don't want to do anything with the `isConditionTrue` value other than checking that it's true. That `null` just doesn't feel right, does it? You're not going to touch it ever... there's just no need for it. What do you do?  

## Use A Short Circuit Statement!

A short-circuit statement works like this: if the first value evaluates to `true` or is **truthy**, then the value following the `&&` will run. If the first value is `false` or *falsy*\*, then the line will evaluate to the value of the falsy value, and the function will not be executed.* 

```javascript
// if isConditionTrue is true, then execute myFunction
isConditionTrue && myFunction()
```

What if you want to check if one of two conditions is true? Do this:

```javascript
const isEitherConditionTrue = isConditionOneTrue || isConditionTwoTrue

isEitherConditionTrue && myFunction()
```

Yes, you can also write it inline 

```javascript
isConditionOneTrue || isConditionTwoTrue && myFunction()
```

but I prefer to use *one* more line of code to make each line simpler to read. In the above block on first read, I'd be hard-pressed to remember if it needs parenthesis, for instance.  

But now what if you want to check if BOTH conditions is true? I bet you can guess:

```javascript
const areBothConditionsTrue = isConditionOneTrue && isConditionTwoTrue

areBothConditionsTrue && myFunction()
```

Yes, these are simple examples. But they fit well with the short-circuit statement, which is also meant to be simple.  

--- 

*Try these examples out in your console:

```javascript
const myFunc = () => {
    return "function executed"
}

// these run the function
// let value = true 
// let value = "a string" 
// let value = 10 
// let value = {}
// let value = []

// these return the falsy value
// let value = false 
// let value = 0 
// let value = "" 

value && myFunc()
```