---
title: Interview Questions and Concepts for Junior Developers
date: "2018-05-20T00:00:00.0Z"
layout: post
draft: false
path: "/posts/interview-questions-and-concepts-for-junior-developers/"
category: "web development"
tags:
  - "web development"
  - "interview questions"
  - "fundamental concepts"
  - "junior developers"
description: "Whether or not the knowing the hottest new JS framework is the crux of winning the interview, there are some very fundamental concepts in web development that employers and senior devs want their juniors to have a solid grasp of."
---

# The scenario

You got the interview. YES!! Yes, it's **that** job you **really** want. Hold on, this is really only step one. You still have to show up on time, know what the interviewers are asking you, demonstrate this knowledge clearly, smell good and maybe even smile a little bit before they grant you Github access to their greenfield codebase with all the newest new things you've been reading about at Hacker Noon between writing cover letters and filling out job applications.  

Okay, so now how to prep?

## Algorithms

There's a lot on the internet about nightmare algorithm questions in a job interview, but I've not heard anyone I personally know ever have to do this. However, I don't see how this can hurt. If it does come up, it's my general impression that it's less important to get an algorithm '100% right' than it is to thinking your way through it out loud to your interviewers, so that they can see how you think on your feet and under some slight pressure.  

## Personal Projects

Do you have a project to showcase? Awesome! This is great. You may be asked to diagram a certain operation flow of your project or explain more about large, underlying concepts instead of tiny implementation details.  

## Language Diversity - Show, Don't Tell 

Which programming languages are you going to put at the front of your knowledge? If you're just entering the field and you're after your first or even second job, this is much less applicable. If this is you, fear not - if in doubt about your ability, say something like "Given my current level of experience with code, I feel fairly comfortable with {language_of_choice}, but I'll let you be the judge by asking me any questions about the language, or using that language to talk through concepts in programming." This is what your interviewers are going to do anyway, but this sort of open statement lets them know that you are not trying to puff up your knowledge by dodging questions.

My first job in development was at a Rails/Backbone/CoffeScript shop, which was great for me at the time. When I began to learn programming, it was in Ruby. Because I didn't have to adjust to new syntax right away, I was able to continue my learning of writing object-oriented code within such a widely known MVC framework as Rails in one seemingly unending streak of Ruby classes, and Rails controllers and serializers.  

Later, I grew an interest in both functional programming and typed languages. Although Ruby on Rails isn't really the best space to take advantage of these types of approaches, I was still able to take *full* advantage of the fundamental concepts that I picked up during all that time programming within a Ruby/Rails environment.  

Shortly after, I began working with a small and tight team, whose primary stack is a mostly-functional and immutable approach to Typescript/React/React-Native/Go. This is obviously a very different tech stack than (mutable) object-oriented Rails/Backbone/CoffeeScript. However, I was able to leverage my experience with Ruby methods and objects and classes (as well as a few things in CoffeeScript) to learning to code using Javascript's functional parts: *map*, *filter*, and *reduce* among them, as well as newer ES6 features such as the spread operator and fat arrow functions.  

## Think twice before going all-in on a single framework

Yes, the job posting may have mentioned so-many-years-experience in such-and-such a framework, but we all know that frameworks serve different purposes in different types of businesses, and also go in and out of use. The question becomes more like *can you learn to work with a new one?*  

This is what potential employers want to know... *can you keep up?* Are you able to take the *concepts* of programming with you into any coding situation you may find yourself in, and only then focus on implementation/syntax?

> Solid pseudo code knows no single syntax.

How can you prove that you have a good, working knowledge of this? With clear explanation of the underlying mechanics, which can only come from having a solid grasp of basic concepts.

### What Are these "basic concepts?" 

### REST

**RE**presentational **S**tate **T**ransfer
read about HTTP in this [overview by Mozilla](https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview)
### HTTP
- https://developer.mozilla.org/en-US/docs/Web/HTTP
- the protocol itself - hypertext transfer protocol.

- it might sound slightly archaic to need to know this, but in no way is this true. It's always a good idea to know how your tools work. That knowledge is key to going beyond them when you have to, in a given situation.  

#### client, server relationship - 
- requests, responses, codes, body, et c.

### What are the clients that will use server data?
- web browser, mobile device
- what will the client do with the data?
    - render it through html/jsx markup
- Types of server data - XML, JSON, HTML

#### verbs 
- there are many but GET, POST, PUT, (PATCH), and DELETE are the most commonly used
- Parts of a response from http verb https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods
    - headers, body, json format
    - authentication from where?
- explain difference between JSON and Javascript Object, keys and values
- other data

#### Status codes http 
- 2XX Success
- know the differences between 200, 201, 204
- 3XX Redirected
- maybe know 302 and 304? don't come up too often
- 4XX Failure
- know 400, 401, 402, 403, 404, 422
- 5XX Server Error
- maybe 500, 501, 504

- https://developer.mozilla.org/en-US/docs/Web/HTTP/Authentication

### Okay so now let's talk about Which Languages, frameworks do you know and work with? Rate yourself 1-10

### When in doubt with language X, use js instead, and...

### javascript is still the lingua laborum, so know it
- Describe parts of a JS function
- function name
- params
- function body
- return statement, value, possibly void/undefined

### Variable and function scope in JS
- const, let, var (hoisted) in closures and function scope
- const/let do not leave their block { }

#### What is closure?
https://medium.com/@rlynjb/js-interview-question-what-is-a-closure-and-how-why-would-you-use-one-b6fd45ea95f6

#### difference between parameters and arguments

#### Call, bind, apply in JS

### describe JS objects -
- Key/values
- Usually string as key, but what else can be used as a key?

### Technical part of interview/whiteboarding

- Whiteboard - small algorithm - input int, output string of square

```
const square = (input) {
    const line = "";
    for (let i = 0; i >= input; i++) {
        line.concat("x")
    }

    for (let i = 0; i >= input; i++) {
        console.log(line + \n)
    }
}
```

### Web development basics - 
http, verbs, response, request, REST what and why, status codes, 

### other
- CSS selectors - 

### React
- props
- state
- parts of react app
- some explanation or summary of jsx

Function - name, params, body block

### Variable scope within and without blocks { }

### The Big Scary Final Boss: The Whiteboard Session

Software developers are problem solvers, essentially by definition. If you are hired after the interview, you will be paid for solving problems. Thus, I believe that it is fully acceptable to ask a job applicant to solve a problem in the interview. This part of the interview may happen, it may not. I've personally been in both scenarios. The main goal here is to demonstrate that you have the mental tools to handle a specific problem, so a very slight amount of glossing over the smaller details of actual implementation, as long as you sandwich this with very concrete and clear knowledge and explanation.  

Having said that, being able to clearly explain and summarize things like loop syntax in your preferred coding language, the difference of use of if-statements and ternary expressions, as well as concepts in error handling look *very good* in a potential new hire.  

1. Talk through all requirements, asking questions for two reasons,
    - to become more clear with what you are actually being asked to do, and
    - to demonstrate the extent of your thoughts and show where your mind goes.  

2. Thinking out loud, begin talking and explaining your way through your plan. You may find that you have more questions as you go along. This is good. You can also begin to write or outline some pseudo code as a mental save point to return to once you are completely clear on both the requirements and your plan of attack.

3. Finally, you may begin coding. If steps 1 and 2 have fallen into place correctly, then this step may actually be the easiest of the three.

Ideally, you will be perceived as very knowledgeable, and not even have to finish the challenge depending on its length, as you've showcased what the interviewers **really** want to see in a potential new developer: an adaptable problem-solver with legitimate and valuable critical thinking skills. 
