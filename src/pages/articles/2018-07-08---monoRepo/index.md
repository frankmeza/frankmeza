---
title: monoRepo
date: "2018-07-08T00:00:00.0Z"
layout: post
draft: false
path: "/posts/monorepo/"
category: "web development"
tags:
  - "web development"
  - "code architecture"
  - "documentation"
description: "monorepo documentation"
---

<sub><a name="table-of-contents"> top of page</a></sub>  

# Table of Contents
1. [UI Components, Core Functions, Redux Actions](#ui-components-top)
2. [Actions, Reducers, Saga Functions](#actions-reducers-saga-functions-top)
    - [reducers](#actions-reducers)
    - [sagas](#actions-sagas)
3. [Store, UI Components, UI As A Whole](#store-ui-components-ui-as-a-whole-top)
4. [Client - web or mobile](#client-web-or-mobile)

## 1 :: <a name="ui-components-top"> UI Components, Core Functions, Redux Actions</a>

![UI, Core, Actions](https://static.swimlanes.io/237be583a34249c8bbfe675a9651a174.png)

<!-- edit this diagram
https://swimlanes.io/#VY4xDsIwDEX3nMIjSHCBDkiICUagB7AS01pKk8pxBL09pq0qsfnb7z/5yRqpgfYKlzyMOVHScrBZCF41eeWcLJ+XwbnK4DcOdndCr7fHHo4n24uJaiEBTkqCcwdUuOtICuBMbFbn5mjFBWxAe/pHrGNp9Xgh1Cz2DKYAHmNcLwXerL3pR5xixuDc2jC1UKifZgN/OhpYlQJoXq4woO85kUzuCw== -->

1. [UI -> UI](#ui-ui): actual user interaction calls a component function
2. [UI -> core](#ui-core): the component function calls a core function with optional arguments  
3. [core -> actions](#core-actions): core functions create redux actions, passing in a payload  
4. [actions -> reducers and/or redux sagas](#actions-reducers-sagas): actions are emitted to redux

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

*### summary : actual user interaction, UI component functions, core functions*

These are code examples of the first two messages in the flow of data: the calling of a UI function per the actual user, and then the calling of a core function inside of that UI function.  

Both the above `onClick` and `render` functions will be found inside of a `React.Component`. Functions and other passed in values come into the component via React `props`, i.e. `funcName`. They're then destructured and may take in possible arguments from the component function.  

It is common to see a React component pass its own functions into any child components within it, in this case the confirm button receives as props its parent's function, as `this.onClick`.

<sub>[back to top of these code examples](#ui-components-examples)  </sub>  
<sub>[back to top of section](#ui-components-top)  </sub>

<hr>

<sub><a name="core-actions">core -> actions</a><sub>

```typescript
// 3. core -> actions: core funcs create redux actions, passing in a payload
// make this part a living document: where does each piece of code live?

// example function type without params, with interface
interface ClearDataAction {
    readonly type: "CLEAR_DATA"
}

const clearData = () => ({
    type: "CLEAR_DATA",
})

// example function type with params, with interface
interface SetDataAction {
    readonly type: "SET_DATA"
    readonly attr1: string
    readonly attr2: string
    readonly attr3: number
    readonly attr4: boolean
}

const setData = (
    attr1: string,
    attr2: string,
    attr3: number,
    attr4: boolean,
): SetDataAction => ({
    type: "SET_DATA",
    attr1,
    attr2,
    attr3,
    attr4,
})

// union type for export
type GroupedDataActions =
    | SetDataAction
    | ClearDataAction

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

*### summary : core functions, redux actions*

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

*### summary : actions, reducers, redux sagas*  

Redux actions are listened for in both redux reducers and redux sagas by the action `type` and then the payload is used to mutate state. More details will be found in the following section.  

<sub>[back to section sequence diagram](#ui-components-top)</sub>  
<sub>[back to top of code examples](#ui-components-examples)</sub>  
<sub>[back to table of contents](#table-of-contents)</sub>  

<hr>

## 2 :: <a name="actions-reducers-sagas-top"> Actions, Reducers, Saga Functions</a>

![Actions, Reducers, Saga Functions](https://static.swimlanes.io/58010d89c4c2593a6961fd402dd1fdaa.png)
<!-- edit this sequence diagram at https://swimlanes.io/u/Sk314q_Gm , and then update image url ^^ -->

*note: reducers and sagas both listen for an action's type, then take in its payload to perform state mutations, as mentioned at the end of the previous section.*

1. [actions -> reducers](#actions-reducers): actions go into reducers as replacements to state, without logic  
2. [actions -> sagas](#actions-sagas): complicated or state-ful logic is orchestrated in the sagas, where control flow lives  

### Reducer Flow

![Actions, Reducers, Root reducer, Store](https://static.swimlanes.io/934351683df9f46731bf2d5720f638bc.png)
<!-- edit at https://swimlanes.io/u/H1sxZIbVm -->


1. [action -> reducer](#actions-reducer): actions are listened for and received by reducers 
2. [reducer -> root reducer](#reducer-root-reducer): entire reducer is passed into root reducer as an argument to combineReducers()
3. [root reducer -> store](#root-reducer-store): the root reducer is passed into redux store, updating app state along with it

### Redux Saga Flow

![Redux Sagas](https://static.swimlanes.io/6402e453d7c50d69f6669eda86776355.png)
<!-- edit this sequence diagram at https://swimlanes.io/u/Bk8NS9dMQ , then update image url ^^ -->

1. [actions -> sagas, via index](#actions-sagas-via-index): action types are listened for in the sagas index, then routed to correct saga function  
2. [sagas -> external API](#sagas-external-API): request is made for data to be exchanged  
3. [external API -> sagas](#external-API-sagas): returns raw response  
4. [sagas -> utils](#sagas-utils): utils are called, to actually perform business logic  
5. [utils -> sagas](#utils-sagas): data is returned, fit for saga to give to an action  
6. [sagas -> actions](#sagas-actions): return final data to actions  

## 2 :: <a name="actions-reducers-sagas-examples"> Code Examples </a>

<sub><a name="actions-reducers">actions -> reducers</a></sub>  



```typescript
// 1. actions -> reducers: actions go into reducers 
// for simple replacements to state, without logic

// make this part a living document: where does each piece of code live?
import { DataShape, INITIAL_STATE } from "../core"

function plainReducer(action: ActionTypeInterface) {
    switch (action.type) {
        // this is the type listened for
        case "SET_DATA":
            // this is the mutation to the state tree
            return { ...state, data: action.data }
        case "CLEAR_DATA":
            return INITIAL_STATE
        default:
            return INITIAL_STATE
    }
}
```

<sub><a name="reducer-root-reducer">reducer -> root reducer</a></sub>  

*Each reducer is passed into the root reducer:*

```typescript

// root reducer
import { rootReducer } from "redux"
import { plainReducer } from "../data/plainFile"
import { anotherPlainReducer } from "../data/anotherPlainFile"


const rootReducer = combineReducers({
    plainReducer,
    anotherPlainReducer,
})

```
*### summary : actions, reducers, root reducer, store*  

<sub><a name="root-reducer-store">root reducer -> store</a></sub>

Redux actions are listened for in each reducer, which is responsible for updating its part of app state. The reducer is a function, and this function is passed into the root reducer. The root reducer is then passed into the [redux store](#redux-store) for state mutation.

<sub>[back to section sequence diagram](#actions-reducers-sagas-top)</sub>  
<sub>[back to top of code examples](#actions-reducers-sagas-examples)</sub>  

<hr>

<sub><a name="actions-sagas">actions -> sagas</a></sub>  
<sub><a name="actions-sagas-via-index">actions -> sagas, via index</a></sub>

```typescript
// sagas/index.ts

import { takeEvery } from "redux-saga/effects"
import { handleMetaData } from "../metadata_sagas"
import { handleClientMsg } from "../client_sagas"
import { handleLogin } from "../login_sagas"
import {
    handleLogin,
    handleLoginResponse,
    handleLogout,
    handleLogoutResponse,
} from "../modules/logout/logout_sagas"

export default function* root(): {} {
    yield [
        // metadata
        takeEvery("HANDLE_METADATA", handleMetaData),
        takeEvery("HANDLE_CLIENT_MSG", handleClientMsg),
        // login, logout
        takeEvery("HANDLE_LOGIN", handleLogin),
        takeEvery("HANDLE_LOGIN_RESPONSE", handleLogin),
        takeEvery("HANDLE_LOGOUT", handleLogout),
        takeEvery("HANDLE_LOGOUT_RESPONSE", handleLogoutResponse),
    ]
}

```

*summary here...*

<sub><a name="sagas-external-API">sagas -> external API (request)</a></sub>  
<sub><a name="external-API-sagas">external API -> sagas (response)</a></sub>  

```typescript
// generic_sagas.ts
import { DataShapeResponse } from "../module/data/data_remote"

export function* sagaFunc(action: ActionNameAction): {} {
    
    const result: DataShapeResponse = yield call(
        otherSagaFunctionMakingExternalCall,
    )

    // more logic with result...
}

```

*summary here...*

<sub><a name="sagas-utils">sagas -> utils</a></sub>  
<sub><a name="utils-sagas">utils -> sagas</a></sub>  
<sub><a name="sagas-actions">sagas -> actions</a></sub>  

<sub>[back to table of contents](#table-of-contents)</sub>

## Store, UI Components, UI As A Whole

![Store, UI Components, UI As  Whole](https://static.swimlanes.io/a92eb3d0100848b0d732c51aceab2a42.png)

```
Title: Store, UI Components, UI As  whole

store -> components: components are as presentational as possible
components -> ui: the components make up the ui, also as presentational as possible, maintaining minimal ui state
ui -> ui utils: sorting and filtering based on actual user interaction is handled in ui utils
```

```typescript
// client.ts or web/api.ts


```

```typescript

// store.ts

import { createStore, applyMiddleware } from "redux"
import { createLogger } from "redux-logger"
import createSagaMiddleware from "redux-saga"

// our own dependencies, from "common" module
import { Sagas, Reducers, Core } from "common"

import { AppState } from "../core/app_state"

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
    applyMiddleware(...middleware),
)

sagaMiddleware.run(Sagas.root)

```
