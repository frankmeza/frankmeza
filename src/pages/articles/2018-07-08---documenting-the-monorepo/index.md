---
title: Documenting the monorepo
date: "2018-07-08T00:00:00.0Z"
layout: post
draft: false
path: "/posts/documenting-the-monorepo/"
category: "web development"
tags:
  - "web development"
  - "code architecture"
  - "documentation"
description: "Using documentation as a product of learning, or How I Learned to Love the Monorepo."
---

As it is now, this blog is currently the artifacts and outlines of two blog idea that I think is better put together. Disjointed in the middle, but coherent enough to see that there is some reflection about technical documentation, and the actual documentation after that.  

I think it's good to put here as a sort of snapshot in time of a problem and how I solved it. The problem was me not deeply understanding the code architecture of a project that I was working on.  

I set out to deeply solve this problem. I chose to spend a few weeks of my spare time and devote them to fully understanding the separation of concerns that existed within the architecture.  

This process itself was a massive game-changer for me. I learned that I could move mountains, given enough time and focus for my understanding to mature on its own. I learned even more how documentation of all kinds, from comments in the code all the way up to formal technical writing and elaborate sequence diagrams.

---

```
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
```

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


<sub><a name="table-of-contents"> top of page</a></sub>

# Table of Contents

1.  [UI Components, Core Functions, Redux Actions](#ui-components-top)
2.  [Actions, Reducers, Saga Functions](#actions-reducers-saga-functions-top)
    - [reducers](#actions-reducers)
    - [sagas](#actions-sagas)
3.  [Store, UI Components, UI As A Whole](#store-ui-components-ui-as-a-whole-top)
4.  [Client - web or mobile](#client-web-or-mobile)

## 1 :: <a name="ui-components-top"> UI Components, Core Functions, Redux Actions</a>

![UI, Core, Actions](https://static.swimlanes.io/237be583a34249c8bbfe675a9651a174.png)

<!-- edit this diagram
https://swimlanes.io/#VY4xDsIwDEX3nMIjSHCBDkiICUagB7AS01pKk8pxBL09pq0qsfnb7z/5yRqpgfYKlzyMOVHScrBZCF41eeWcLJ+XwbnK4DcOdndCr7fHHo4n24uJaiEBTkqCcwdUuOtICuBMbFbn5mjFBWxAe/pHrGNp9Xgh1Cz2DKYAHmNcLwXerL3pR5xixuDc2jC1UKifZgN/OhpYlQJoXq4woO85kUzuCw== -->

1.  [UI -> UI](#ui-ui): actual user interaction calls a component function
2.  [UI -> core](#ui-core): the component function calls a core function with optional arguments
3.  [core -> actions](#core-actions): core functions create redux actions, passing in a payload
4.  [actions -> reducers and/or redux sagas](#actions-reducers-sagas): actions are emitted to redux

## 1 :: <a name="ui-components-examples"> Code Examples </a>

<sub><a name="ui-ui">UI -> UI</a></sub>
<sub><a name="ui-core">UI -> core</a></sub>

```typescript
// 1. UI -> UI: actual user interaction calls a component func
// 2. UI -> core: the component function calls core function with opt args

// make this a project specific living document:
// where does each piece of code live?

// example function in *.tsx
onClick(param: string): void {
    // this is an action creator
    const { funcName, valueFromProps } = this.props
    funcName(param, valueFromProps)
}

// function is possibly passed into child component
render(): JSX.Element {
    <Button text="Confirm" onClick={this.onClick} />
}
```

_### summary : actual user interaction, UI component functions, core functions_

These are code examples of the first two messages in the flow of data: the calling of a UI function per the actual user, and then the calling of a core function inside of that UI function.

Both the above `onClick` and `render` functions will be found inside of a `React.Component`. Functions and other passed in values come into the component via React `props`, i.e. `funcName`. They're then destructured and may take in possible arguments from the component function.

It is common to see a React component pass its own functions into any child components within it, in this case the confirm button receives as props its parent's function, as `this.onClick`.

<sub>[back to top of these code examples](#ui-components-examples) </sub>
<sub>[back to top of section](#ui-components-top) </sub>

<hr>

<sub><a name="core-actions">core -> actions</a><sub>

```typescript
// 3. core -> actions: core funcs create redux actions, passing in a payload
// make this part a living document: where does each piece of code live?

// example function type without params, with interface
interface ClearDataAction {
  readonly type: 'CLEAR_DATA'
}

const clearData = () => ({
  type: 'CLEAR_DATA',
})

// example function type with params, with interface
interface SetDataAction {
  readonly type: 'SET_DATA'
  readonly attr1: string
  readonly attr2: string
  readonly attr3: number
  readonly attr4: boolean
}

const setData = (
  attr1: string,
  attr2: string,
  attr3: number,
  attr4: boolean
): SetDataAction => ({
  type: 'SET_DATA',
  attr1,
  attr2,
  attr3,
  attr4,
})

// union type for export
type GroupedDataActions = SetDataAction | ClearDataAction

export {
  // interface types
  GroupedDataActions,
  ClearDataAction,
  SetDataAction,
  // action creators
  clearData,
  setData,
}
```

_### summary : core functions, redux actions_

These are a few code examples of the third message in the flow of data: the core function inside of that UI function (in steps one and two above) creates a redux action.

A redux action returns an object with a `type` property, and may have other possible fields (its payload). Examples of this from above are `clearData` and `setData`. You can also each has their interface shape above it. The interfaces may be grouped as they are in `GroupedDataActions`, and then everything is exported.

<sub>[back to section sequence diagram](#ui-components-top)</sub>
<sub>[back to top of code examples](#ui-components-examples)</sub>

<hr>

<sub><a name="actions-reducers-sagas">actions, reducers, sagas</a></sub>

```typescript
// 4. actions -> reducers and/or redux sagas: actions are emitted to redux

// These actions' types are listened for:
// in the reducers themselves,
// in the sagas, via the sagas/index.

// often, at end of saga function, new data is passed into reducer.
```

_### summary : actions, reducers, redux sagas_

Redux actions are listened for in both redux reducers and redux sagas by the action `type` and then the payload is used to mutate state. More details will be found in the following section.

<sub>[back to section sequence diagram](#ui-components-top)</sub>
<sub>[back to top of code examples](#ui-components-examples)</sub>
<sub>[back to table of contents](#table-of-contents)</sub>

<hr>

## 2 :: <a name="actions-reducers-sagas-top"> Actions, Reducers, Saga Functions</a>

![Actions, Reducers, Saga Functions](https://static.swimlanes.io/58010d89c4c2593a6961fd402dd1fdaa.png)

<!-- edit this sequence diagram at https://swimlanes.io/u/Sk314q_Gm , and then update image url ^^ -->

_note: reducers and sagas both listen for an action's type, then take in its payload to perform state mutations, as mentioned at the end of the previous section._

1.  [actions -> reducers](#actions-reducers): actions go into reducers as replacements to state, without logic
2.  [actions -> sagas](#actions-sagas): complicated or state-ful logic is orchestrated in the sagas, where control flow lives

<hr>

### Reducer Flow

![Actions, Reducers, Root reducer, Store](https://static.swimlanes.io/934351683df9f46731bf2d5720f638bc.png)

<!-- edit at https://swimlanes.io/u/H1sxZIbVm -->

1.  [action -> reducer](#actions-reducer): actions are listened for and received by reducers
2.  [reducer -> root reducer](#reducer-root-reducer): entire reducer is passed into root reducer as an argument to combineReducers()
3.  [root reducer -> store](#root-reducer-store): the root reducer is passed into redux store, updating app state along with it

<hr>

### Redux Saga Flow

![Redux Sagas](https://static.swimlanes.io/6402e453d7c50d69f6669eda86776355.png)

<!-- edit this sequence diagram at https://swimlanes.io/u/Bk8NS9dMQ , then update image url ^^ -->

1.  [actions -> sagas, via index](#actions-sagas-via-index): action types are listened for in the sagas index, then routed to correct saga function
2.  [sagas -> external API](#sagas-external-API): request is made for data to be exchanged
3.  [external API -> sagas](#external-API-sagas): returns raw response
4.  [sagas -> utils](#sagas-utils): utils are called, to actually perform business logic
5.  [utils -> sagas](#utils-sagas): data is returned, fit for saga to give to an action
6.  [sagas -> actions](#sagas-actions): return final data to actions

## 2 :: <a name="actions-reducers-sagas-examples"> Code Examples </a>

<sub><a name="actions-reducers">actions -> reducers</a></sub>

```typescript
// 1. actions -> reducers: actions go into reducers
// for simple replacements to state, without logic

// make this part a living document: where does each piece of code live?
import { DataShape, INITIAL_STATE } from '../core'

function plainReducer(action: ActionTypeInterface) {
  switch (action.type) {
    // this is the type listened for
    case 'SET_DATA':
      // this is the mutation to the state tree
      return { ...state, data: action.data }
    case 'CLEAR_DATA':
      return INITIAL_STATE
    default:
      return INITIAL_STATE
  }
}
```

<sub><a name="reducer-root-reducer">reducer -> root reducer</a></sub>

_Each reducer is passed into the root reducer:_

```typescript
// root reducer
import { rootReducer } from 'redux'
import { plainReducer } from '../data/plainFile'
import { anotherPlainReducer } from '../data/anotherPlainFile'

const rootReducer = combineReducers({
  plainReducer,
  anotherPlainReducer,
})
```

_### summary : actions, reducers, root reducer, store_

<sub><a name="root-reducer-store">root reducer -> store</a></sub>

Redux actions are listened for in each reducer, which is responsible for updating its part of app state. The reducer is a function, and this function is passed into the root reducer. The root reducer is then passed into the [redux store](#redux-store) for state mutation.

<sub>[back to section sequence diagram](#actions-reducers-sagas-top)</sub>
<sub>[back to top of code examples](#actions-reducers-sagas-examples)</sub>

<hr>

<sub><a name="actions-sagas">actions -> sagas</a></sub>
<sub><a name="actions-sagas-via-index">actions -> sagas, via index</a></sub>

```typescript
// sagas/index.ts

import { takeEvery } from 'redux-saga/effects'
// imported callbacks (all generator functions)
import { handleMetaData } from '../metadata_sagas'
import { handleClientMsg } from '../client_sagas'
import { handleLogin } from '../login_sagas'
import {
  handleLogin,
  handleLoginResponse,
  handleLogout,
  handleLogoutResponse,
} from '../modules/logout/logout_sagas'

export default function* root(): {} {
  yield [
    // metadata
    takeEvery('HANDLE_METADATA', handleMetaData),
    takeEvery('HANDLE_CLIENT_MSG', handleClientMsg),
    // login, logout
    takeEvery('HANDLE_LOGIN', handleLogin),
    takeEvery('HANDLE_LOGIN_RESPONSE', handleLogin),
    takeEvery('HANDLE_LOGOUT', handleLogout),
    takeEvery('HANDLE_LOGOUT_RESPONSE', handleLogoutResponse),
  ]
}
```

The sagas index behaves much like a reducer in that it listens for redux actions like `"HANDLE_METADATA"` , and then routes that action and its payload to its callback function `handleMetaData` . This callback is imported from its `_sagas` file above the `root` function, so that the index can find it.

<hr>

<sub><a name="sagas-external-API">sagas -> external API (request)</a></sub>
<sub><a name="external-API-sagas">external API -> sagas (response)</a></sub>

```typescript
// generic_sagas.ts

import { DataShapeResponse } from '../module/data/data_remote'

export function* sagaFunc(action: ActionNameAction): {} {
  const result: DataShapeResponse = yield call(
    otherSagaFunctionMakingExternalCall
  )

  // more logic with result...
}
```

_### summary : sagas and external API calls_

The saga functions are responsible for sending requests to the `client_sagas` so that it can actually make the external call, and the `client.ts` will introduce the incoming data into redux. TODO - client and client sagas

<hr>

<sub><a name="sagas-utils">sagas -> utils</a></sub>
<sub><a name="utils-sagas">utils -> sagas</a></sub>

```typescript
// generic_sagas.ts

import { DataShape, RelatedShape } from '../module/data/data_state'
import { utilFunc } from '../utils/data_utils'

export function* sagaFunc(action: ActionNameAction): {} {
  const { payload } = action

  const selectedData = yield select(currentData)

  const resultFromUtil: DataShape = utilFunc(selectedData, payload)

  // more logic with resultFromUtil...
}
```

```typescript
// utils/data_utils.ts

import { DataShape, RelatedShape } from '../module/data/data_state'
import { DataShapeResponse } from '../module/data/data_remote'

export const utilFunc = (
  data: DataShapeResponse,
  relatedData: RelatedData
): DataShape => {
  // ingress function or other state-ful computation
}
```

_### summary : sagas and util functions_

Saga and util functions work together to massage incoming data and changes to existing data into the data shapes that our redux app state needs, so that state can be updated and trigger appropriate changes in the UI.

The util functions are imported into the saga files for use from their `_utils.ts` . The sagas pass parts of the action payload and/or current app state into the util functions, which then do their work, and return a value to the saga function.

<hr>

<sub><a name="sagas-actions">sagas -> actions</a></sub>

```typescript
// generic_sagas.ts

import { DataShape, RelatedShape } from '../module/data/data_state'
import { utilFunc } from '../utils/data_utils'

export function* sagaFunc(action: ActionNameAction): {} {
  // control flow logic
  const resultFromUtil: DataShape = utilFunc(selectedData, payload)

  // after control flow logic is complete,
  // the saga function sends its final result into
  // redux state by using an action into redux
  yield put(actionGoingIntoRedux(resultFromUtil))
}
```

<sub>[back to table of contents](#table-of-contents)</sub>

<hr>

## Store, UI Components, UI As A Whole

![Store, UI Components, UI As A Whole](https://static.swimlanes.io/a92eb3d0100848b0d732c51aceab2a42.png)

1.  [store -> components](#store-components): components are as presentational as possible
2.  [components -> ui](#components-ui): the components make up the ui, also as presentational as possible, maintaining minimal ui state
3.  [ui -> ui utils](#ui-ui-utils): sorting and filtering based on actual user interaction is handled in ui utils

<sub><a name="store-components">store -> components</a></sub>

```typescript
// store.ts

import { createStore, applyMiddleware } from 'redux'
import { createLogger } from 'redux-logger'
import createSagaMiddleware from 'redux-saga'

// our own dependencies, from "common" module
import { Sagas, Reducers, Core } from 'common'

import { AppState } from '../core/app_state'

const logger = createLogger({
  stateTransformer: (state: AppState) => state,
})

// create saga middeware
const middleware = [
  createSagaMiddleware(),
  // other custom middleware here,
  logger,
]

// Add the reducer to your store on the `router` key
// Also apply our middleware for navigating
export const store = createStore(
  Reducers.rootReducer,
  applyMiddleware(...middleware)
)

sagaMiddleware.run(Sagas.root)
```

## TODO components-ui

- code example, is this possible? or JUST a summary of scenes and components

## TODO ui -> ui utils

- code example
- summary

```typescript
// client.ts and/or web/api.ts
// TODO
```
