---
title: On Writing Documentation
date: "2018-07-08T00:00:00.0Z"
layout: post
draft: false
path: "/posts/on-writing-documentation/"
category: "web development"
tags:
  - "web development"
  - "code architecture"
  - "documentation"
description: "Why go to all of the trouble of writing documentation of your company framework?"
---

WHAT
- you might use a standard JS framework
- if so, you can get more into the peculiarities of your shop's usage, with reference to the standard documentation and then note the local usage

- if your framework is homegrown, all the better
- you can go into the what and the why of the framework, the workflow

- use sequence diagrams alongside code samples
- internal use and education

WHY THO
- you will really grok the stuff
- you will be able to reason about future code, without even writing it
    - time saver
- you can iterate the framework better for the next project
- you can catch cruft or unnecessary boilerplate
    - modularize?
    - too abstracted?
- a great chance for you to contribute in a very material way
- in light of such a finished document, if you have opinions or ideas, your words will be heavier
- you will have more time to realize which parts of the code you enjoy best and why
- this newfound realization will motivate you to learn something new, that you didn't realize you had interest in
- it is more academic in nature (you are actively producing and polishing a document that is both challenging for you to write, as well as helpful for others who learn after you) than endless toy projects.
    - you can spend a few hours a week of your free time producing something worth looking over and studying
    - thus, you will have learned something, benefitting both others and yourself. 

Experience wise
- formatting is very important to me. 
    - As the format is not the important part of reading, you must make it as immediately readable with as little friction as possible.
    - yes, the prose is important, but overall presentation is essential. No one wants to read through bad looking documentation.
    - the editing of such a document allows you to (usually) cut away extraneous things, leaving the reader with clearer examples and explanations, and less prose overall for more **effective** documentation

- the thing that I did
    - make a data flow sequence diagram, map out the whole thing from 30,000 ft
    - then cut it up into medium sized slices - 4 to 6 is ideal - now view each from 5,000 ft
    - iterate through each slice, giving an example (generic or specific) in the certain section of the code
        - this will need to be updated in each project
        - either write the generic code from scratch or copy over snippets and then generalize them, mentally taking note of larger concepts
    - you will continually think of the first part and quickly iterate over just that, quickly hitting upon a better and better version of the docs
    - eventually you will come to a "best" version and then more rapidly work through the rest of the content