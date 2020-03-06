---
title: Documenting Code Architecture
date: "2018-06-23T00:00:00.0Z"
layout: post
draft: true
path: "/posts/documenting-code-architecture/"
category: "web development"
tags:
  - "web development"
  - "software architecture"
description: "When you take the time to walk through and properly document your company's home-baked software architecture, everybody wins."
---

#### [SIDENOTES:](#monoRepo)
- researching this is really helping me to be able to hold the project in my mind, almost "physically."
- it's almost like I see different colors when I think about each of these playing its part in the data flow.
    - it looks like 'tron' and the board game 'simon'
- reasoning "about" it is a huge pivot of understanding the architecture and how the pieces come together.

# Begin monoRepo

- why monorepo?
- the idea being, if you ever have to create the other of a react/react-native application, you have next to no logic in the components. This enables you to capture as much of the control logic as possible **in pure JavaScript**, without any of the possible complication of JSX component entanglements.
- separation of concerns
- at first it's hard byt then it keeps you from polluting files with tangential logic
- eventually you can reason about where specific code should go in your head, way before you write it. This type of thinking is a major turning point in your ability to now reason about how the project at large could be abstracted and DRYed up from the specifics of its children. Uniting code across boundaries! Whoo!

## per directory level
`- common/`

This is the "root" directory of the pure JS/TS logic of the application.

`- web/`

This is where we keep the React web components, and its stuff.

`- mobile/`

Yup, you guessed it.

Let's look at `common/` first.

### `common/`

### `common/src/`

`common/src/api/` contains
- api_utils.ts -> tools for the client.ts file
- client.ts -> handles promises
- mock_data.ts -> you're a genius, aren't you?

`common/src/assets/` contains
- img/*.png - individual static assets.

`common/src/redux/` contains

## `core.ts` / `remote.ts`

Where the lowest level Data Models live, along with AppState interface and the initialState constant. The interfaces for the fields in AppState are imported from their respective modules in the same directory.  

`remote.ts` is the Mini-me version of core facing the outside world. It only defines the basic response shapes.


```
based from A***let
src
|- common
    |- src
        |- api
            |- api_utils.ts
            |- client.ts
            |- mock_data.ts
        |- assets
            |- img
                |- *.png
        |- redux
            |- actions
            |- reducers
            |- sagas
            |- core.ts
            |- selectors.ts
        |- types
        |- utils
    Makefile
    index.js
    module.d.ts
    package.json
    tslint.json
    yarn.lock
|- mobile/
|- web/
```


walk through a monoRepo data flow
- client.ts
- handle respDTO with action (defined in module actions)
- go to sagas/index
- redirect to saga functions in modules/xxx_sagas.ts
- saga receives action (and can also pull from current state) for the pieces that it needs
- the logic in the sagas is handled by util functions
- the saga acts as the async orchestrator, eventually calling an action to set the final result from the utils in redux state
- the reducer-feeding actions are defined, and actions listened for (and payload received) in the redux reducers
- the reducers should have to do NO logic, as it should have happened in the saga functions already
- the reducers are each arguments given to the root reducer
- the root reducer is an argument given to the redux store, freshly packaged as "what's available" for the front end
