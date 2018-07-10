---
title: Ifs And Or Ternary Statements
date: "2018-06-26T00:00:00.0Z"
layout: post
draft: true
path: "/posts/ifs-ands-or-ternary-statements/"
category: "web development"
tags:
  - "web development"
  - "code readability"
description: "As developers, we swim in control statements. Which are most effective, and when?"
---

We have all at least *seen* an **if** statement, **if else** statement, **and** statement, **or** statement, ternary statement, and even a short-circuit operation in action.   

-- and talk about functional assignment too

We've all seen simple control statements of different sorts turn into nested ifs-ands-and-ors that'll make your head swim. The business logic may have complexity to it, but that doesn't mean you have to add to it with confusing and unreadable code.  

The exactitudes of "readable code" will vary from shop to shop, but after even a short amount of time, an astute developer will notice the idioms and code patterns of the workplace. That doesn't mean you can't innovate though, it's just a standard that you must do better than if you would like to see adoption.

## Functional Ternary Assignments 

Nested ternaries have a *nasty* reputation in many circles, the first few strands of spaghetti code in an otherwise okay codebase. In many cases, this is correct. I once knew someone who that thought single-line nested ternary statements were the funniest thing ever, but he also thought that they were suitable for production code.

```javascript
// don't ever do this
return text === "pizza" ? emoji.pizza : text === "tacos" ? emoji.tacos : text === "sushi" ? emoji.sushi : emoji.sadFace
```

That looks horrible, right?... Not readable. *Who approved that PR?!*  

But the ternary symbols `?` and `:` are not the bad guys here. They don't write themselves into your code at night, and create boobie traps full of bugs.*

```javascript
const emoji = {
    pizza: "pizzaIcon",
    tacos: "tacosIcon",
    sushi: "sushiIcon",
    sadFace: "sadPandaIcon",
}

// same statement as a nested ternary
// in a function with READABLE indentation
const emojiIcon = (text: string) => {
    return text === "pizza"
        ? emoji.pizza

        : text === "tacos"
            ? emoji.tacos

            : text === "sushi"
                ? emoji.sushi
                : emoji.sadFace            
    }
     
```

Your function takes a string and then sequentially checks it against `"pizza"` and `"tacos"` and then finally `"sushi"`. Fairly simple stuff.  

That looks fairly readable to me, but diff'rent strokes for diff'rent folks.

*I don't know Frank, that still looks a bit wild. Why not just a simple if-statement?*  

There's definitely other options if you're (not) yet into really using ternary statements like this. Let's check out some alternatives.

## IF Statements: The Gates of Hell

I call this one **The Gates of Hell** because your arguments pass through the IF statements one at a time, going deeper toward the bottom and the inevitable final `return` statement.

```javascript
const emojiIcon = (text: string) => {
    if (text === "pizza") {
        return emoji.pizza
    }
    
    if (text === "tacos") {
        return emoji.tacos
    }

    if (text === "sushi") {
        return emoji.sushi
    }

    return emoji.sadFace
}
```

Apart from many more keywords and symbols than the ternary, it expresses the same logic. If you preferred to, you could turn this into an IF-ELSE statement. Is it more readable? That's really up to you (and your team) to decide. There's also switch-statement assignment. Try that out if you want to.  

## SWITCH IT UP

```javascript
// switch statement assignment
// checks for "pizza", then "tacos", then default
const emojiIcon = (text: string) => {
    switch(text) {
        case "pizza":
            return emoji.pizza
        case "tacos":
            return emoji.tacos
        default: 
            return emoji.sadFace
    }
}
```

Like I mentioned, they perform the same train of logic. With this example, you can see that it is really just a matter of preferred code style.  

But now let's think about what would happen

* ...or do they? :P