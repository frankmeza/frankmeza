---
title: On Writing Documentation
date: "2018-07-08T00:00:00.0Z"
layout: post
draft: true
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
  - finding the little ways to improve the doc is fun!

- the thing that I did
  - make a data flow sequence diagram, map out the whole thing from 30,000 ft
  - then cut it up into medium sized slices - 4 to 6 is ideal - now view each from 5,000 ft
  - iterate through each slice, giving an example (generic or specific) in the certain section of the code
    - this will need to be updated in each project
    - either write the generic code from scratch or copy over snippets and then generalize them, mentally taking note of larger concepts
  - you will continually think of the first part and quickly iterate over just that, quickly hitting upon a better and better version of the docs
  - eventually you will come to a "best" version and then very rapidly work through the rest of the content
  - add self-referential links

---

Table of Contents

1.  Part 1
2.  Part 2
3.  Part 3

Part 1 Header

Part 1 Sequence Diagram

Part 1 Code example,
with links to each breakdown section,
with code examples for each section

Part 1 Code example summary

---

outline from work

BLOG outline

## WHAT

- document/summarize the local flavor of the JS framework
- if you use a homegrown architecture, awesome! you/someone needs to do this

## WHY

### GENERAL

- even if you use a standard, opinionated framework like Ember/Rails this is still a very valuable exercise
- much of the value lies in creating and summarizing and synthesizing, not just the end product
- the end product is fluid anyway, as is the work flow
- the end product is a great way to contribute to open source/shared knowledge in a very material way
- everyone loves good docs

### PERSONAL

- a time intense, and dense shortcut to a high level of understanding of the work flow, you will really grok the stuff
- you'll understand the duties of each part so much more that, given a new feature, you can reason about more than one way to do it without coding anything yet
- this level of understanding is a huge timesaver
- this understanding will save you SO MUCH frustration and emotional strain
- you'll see the framework as a tool with which to attack the new feature, instead of feeling encumbered by it and believing that there's more boilerplate than there really is
- you'll also catch cruft and excessive boilerplate, iterating your use of the framework or the thing itself
- the constant progress of the end product and your understanding is very motivating and encouraging
- the writing can be more satisfying than todo list tutorial purgatory - depth of knowledge versus breadth of knowledge. let's not be framework dilletantes.
- you will learn the importance of simplicity and easily navigable docs

## HOW

- As the format is not the important part of reading, you must make it as immediately readable with as little friction as possible.
- yes, the prose is important, but overall presentation is essential. No one wants to read through bad looking documentation.
- the editing of such a document allows you to (usually) cut away extraneous things, leaving the reader with clearer examples and explanations, and less prose overall, for more effective documentation
- finding the little ways to improve the doc is fun!

## MY EXPERIENCE

### the thing that I did

- make a data flow sequence diagram, map out the whole thing from 30,000 ft
- then cut it up into medium sized slices - 4 to 6 is ideal - now view each from 5,000 ft
- iterate through each slice, giving an example (generic or specific) in the certain section of the code
- this will need to be updated in each project
- either write the generic code from scratch or copy over snippets and then generalize them, mentally taking note of larger concepts
- you will continually think of the first part and quickly iterate over just that, quickly hitting upon a better and better version of the docs
- eventually you will come to a "best" version and then very rapidly work through the rest of the content
- add self-referential links to taste

### Conclusion

- I feel like I've shed some level of doubt/uncertainty about my conceptual understandings
- this continues to be a great exercise in code understanding as well as uncovered a new way to interact with code and others
- the pieces of work to be done make up the code machinery, not the other way around. A new view of the individual tasks could yield a whole other architecture
- I look forward to applying the soft concepts that I've picked up on with related projects as well as new architectures!
