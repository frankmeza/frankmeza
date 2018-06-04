---
title: Essential Concepts for Junior Developers to Know
date: "2018-05-20T00:00:00.0Z"
layout: post
draft: false
path: "/posts/essential-concepts-for-junior-developers-to-know/"
category: "web development"
tags:
  - "web development"
  - "interview questions"
  - "fundamental concepts"
  - "junior developers"
description: "Whether or not the knowing the hottest new JS framework is the crux of winning the interview, there are some very fundamental concepts in web development that employers and senior devs want their juniors to have a solid grasp of."
---

# You got the interview. BAM!

YES!! Yes, it's that job you **really** want. But hold on, this only *looks* like step one towards landing a new job in web development.  

You still have to show up on time, know what the interviewers are asking you, demonstrate this knowledge clearly, smell good and maybe even smile a little bit before they grant you Github access to their greenfield codebase with all the newest new things you've been reading about at Hacker Noon between writing cover letters and filling out job applications.  

But before all that, you have to know the material: the terminology, the work flows, the protocols, all that stuff.  

Okay, so now how to prep? What to study? 

<hr>

## Focus beyond the framework

Yes, the job posting may have mentioned so-many-years-experience in such-and-such a framework, but we all know that frameworks serve different purposes in different types of businesses, and also go in and out of use. The question becomes more like *can you learn to work with a new one?*  

This is what potential employers want to know... *can you keep up?* Are you able to take the *concepts* of programming with you into any coding situation you may find yourself in, and only then focus on implementation/syntax?

> Solid pseudo code knows no single syntax or Javascript framework.

What I mean by that is that armed with fundamental knowledge of programming and protocols and concepts, and by using that as your knowledge base, you can learn any framework or language exponentially quicker than by thinking that each must be learned on its own special snowflake terms.  

How can you prove that you have a good, working knowledge of this? With clear explanation of the underlying mechanics, which can only come from having a solid grasp of basic concepts.  

<hr>

## What Are These Basic Concepts?

When in the dark about a topic, I like to start at Wikipedia. You can quickly gain a 30,000 ft. overview and some terminology for better words to input into the Google.  

I also really like the overviews over at Mozilla. They're thorough, clear, and have diagrams to help break up the content and provide some visuals to use in clarifying the point at hand. Check these overviews out and use them as a jump off point to become very familiar with these topics.  

I'm not going to get into too much detail myself here, this is more an aggregation of links and small checklists to things to really dig into.

## REST: Representational State Transfer

REST is the *de facto* standard of communication over the internet. It's essentially a set of rules and guidelines of how to use HTTP in an effective way.

Check out the [Wikipedia article on REST][wiki:rest] for a very high level overview on REST, and then get deeper in this [overview by Mozilla][mozilla:rest].

## HTTP/HTTPS: HyperText Transfer Protocol

It might sound slightly archaic or overly tedious to need to know this, but in NO way is this true. If you think that this can be glossed over, than you are really in need of a thorough review of this material.  

It's ALWAYS a good idea to know how your tools work. That knowledge is key to going beyond them when you have to, in a given situation.  

Again, skim over the [Wikipedia overview][wiki:http] and then move over to [Mozilla][mozilla:http] for a deeper dive.

Be able to explain in some detail these ideas and concepts:

- the client-server relationship
- what/who are the clients that will use server data?
- what will these clients do with the data?
- types of server data - XML, JSON, HTML
- HTTP requests, HTTP responses: status codes, body, headers
- the high level ideas behind [authentication][mozilla:authentication]

### HTTP Verbs

Mozilla on [HTTP Verbs][mozilla:http-verbs]  

- GET, POST, PUT, PATCH, and DELETE are the most common
- know the parts of a response from http verbs

- Slightly aside, but related: know the difference between JSON and Javascript Objects. *Hint: One is a string format to send and receive Javascript objects.*

### HTTP Status Codes

True to form, here is a very high level overview here at [Wikipedia][wiki:http-status-codes] and the deeper read at [Mozilla][mozilla:http-status-codes].

Status codes between 200-299 usually indicate a success of some kind. The most frequently seen are:
- 200 SUCCESS
- 201 CREATED
- 204 NO_CONTENT

Status codes between 300-399 are used to show some kind of redirection or moving of resources to another URL. I've not seen these too too much besides:
- 301 MOVED_PERMANENTLY
- 302 FOUND

Status codes between 400-499 indicate some kind of CLIENT error response. There are many 4xx responses that come up in development, and they each have slightly different meanings and uses. Here is a list of the most common ones to be able to explain:
- 400 BAD_REQUEST
- 401 UNAUTHORIZED
- 403 FORBIDDEN
- 404 NOT_FOUND
- 418 [I'm a teapot][mozilla:teapot]
- 422 UNPROCESSABLE_ENTITY

Status codes between 500-599 indicate some kind of SERVER error response. Beyond 500 INTERNAL\_SERVER\_ERROR, these can be reviewed at a later time.

<hr>

## Okay Now We Can Return to Writing Code

Now that we've covered some of the fundamentals, let's get into writing code. Be prepared to elaborate on which languages and frameworks you have worked with. You may be asked to rate yourself 1-10 in each, with 1 being 'What is Javascript?' and 10 being Brendan Eich.  

Which programming languages are you going to put at the front of your knowledge? If you're just entering the field and you're after your first or even second job, fear not - if in doubt about your ability, you can default to 4 or 5, and say something like 

> "Given my current level of experience with writing code, I feel do fairly comfortable with {language\_of\_choice}, but I'll let you be the judge by asking me any questions about the language, or using that language to talk through general concepts in programming."  

This is what your interviewers are going to do anyway, but this sort of open statement lets them know that you are not trying to falsely puff up your knowledge by dodging questions.

## Be Very Familiar with Javascript

### Functions

- function name
- params
- function body
- the difference between parameters and arguments
- return statement: what it is, and different types of values that can be returned

### Variables, Constants, and Function Scope

- `const`, `let`, `var` in closures and function scope

### What is a Closure?

Essentially a closure is this: imagine a function that lives inside another function. That's it. But [read this][medium:closure] for a much more detailed explanation. Pay attention most to the ideas of scope and work out for yourself who has access to what values and why.

### Call, Bind, Apply in JS

This area can be a bit murky at times, but this is essential knowledge for new developers. You will really stand out and make a good impression on your interviewers if you can explain these three Javascript functions.

### Javascript Objects

- Key/value pairs
- Usually strings as key, but what else can be used as a key?

## Your Personal Projects

Do you have a project to showcase? Awesome! This is great. You may be asked to diagram a certain operation flow of your project or explain more about large, underlying concepts instead of tiny implementation details. You may be asked questions about your project that you don't understand. This is fine, it's just your interviewers seeing how deep into the tech stack you were able to get into. If you understand part of the question, feel free to ask for more clarification. It may turn out that you actually *do* know the answer to the question (yay!), and that your initial confusion was related to terminology you are not familiar with just yet.   

## My Personal Experience

My own timeline of tech stacks has varied from Rails/Backbone/Coffeescript to React Native/Redux/Typescript. Learning to code with Ruby and a more object-oriented approach to programming had given way to using typed Javascript and a functional style.  

However, I was able to leverage my experience and understanding of Ruby methods and objects and classes (as well as a few things in the local style of CoffeeScript) to learning to code using Javascript's functional parts: *map*, *filter*, and *reduce* among them, as well as newer ES6 features such as the spread operator and fat arrow functions.  

### The Big Scary Final Boss: The Whiteboard Session Algorithm

There's a lot on the internet about nightmare algorithm questions in a job interview. If it does come up, it's my general impression (from personal experience) that it's less important to get an algorithm '100% right' than it is to thinking your way through it out loud to your interviewers, so that they can see how you think on your feet and under some slight pressure.  

Software developers are problem solvers, essentially by definition. If you are hired after the interview, you will be paid for solving problems related to building software. Thus, I believe that it is fully acceptable to ask a job applicant to solve a problem in the interview. This part of the interview may happen, it may not. I've personally been in both scenarios. The main goal here is to demonstrate that you have the mental tools to handle a specific problem, so a very slight amount of glossing over the smaller details of actual implementation, as long as you sandwich this with very concrete and clear knowledge and explanation.  

Having said that, being able to clearly explain and summarize things like loop syntax in your preferred coding language, the difference of use of if-statements and ternary expressions, as well as concepts in error handling look *very good* in a potential new hire.  

1. Talk through all requirements, asking questions for two reasons:

- to become more clear with what you are actually being asked to do, and
- to demonstrate the extent of your thoughts and show where your mind goes.  

2. Thinking out loud, begin talking and explaining your way through your plan. You may find that you have more questions as you go along. This is good. You can also begin to write or outline some pseudo code as a mental save point to return to once you are completely clear on both the requirements and your plan of attack.

3. Finally, you may begin coding. If steps 1 and 2 have fallen into place correctly, then this step may actually be the easiest of the three.

``` javascript
... algorithm here
```

Ideally, you will be perceived as very knowledgeable, and not even have to finish the challenge depending on its length, as you've showcased what the interviewers **really** want to see in a potential new developer: an adaptable problem-solver with legitimate and valuable critical thinking skills.

[medium:closure]: (https://medium.com/@rlynjb/js-interview-question-what-is-a-closure-and-how-why-would-you-use-one-b6fd45ea95f6)

[mozilla:authentication]: (https://developer.mozilla.org/en-US/docs/Web/HTTP/Authentication)
[mozilla:rest]: (https://developer.mozilla.org/en-US/docs/Glossary/REST)
[mozilla:http]: (https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview)
[mozilla:http-verbs]: (https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods)
[mozilla:http-status-codes]: (https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)
[mozilla:teapot]: (https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/418)

[wiki:http]: (https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol)
[wiki:rest]: (https://en.wikipedia.org/wiki/Representational_state_transfer)
[wiki:http-status-codes]: (https://en.wikipedia.org/wiki/List_of_HTTP_status_codes)