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

## I :: UI Components, Core, Redux Actions
### DONE

![UI, Core, Actions](https://static.swimlanes.io/237be583a34249c8bbfe675a9651a174.png)

```c
1. UI -> UI: actual user interaction calls a component func
2. UI -> core: the component function calls a core function with opt args  
3. core -> actions: core funcs create redux actions, passing in a payload  
4. actions -> reducers and/or redux sagas: actions are emitted to redux
```

## Code Examples

```typescript
// 1. UI -> UI: actual user interaction calls a component func  
// 2. UI -> core: the component function calls core function with opt args
// make this part a living document: where does each piece of code live?

// example function in *.tsx
onClick(param: string): void {
    // this is an action creator
    const { funcName } = this.props
    funcName(param)
}

// function is passed into child component
render(): JSX.Element {
    <Button onClick={this.onClick} />
}

```

<hr>

```typescript
// 3. core -> actions: core funcs create redux actions, passing in a payload
// make this part a living document: where does each piece of code live?

// example function type without params, with interface
interface ClearDataAction {
    readonly type: "NAME_OF_ACTION"
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

<hr>

```typescript
// 4. actions -> reducers and/or redux sagas: actions are emitted to redux

// These actions' types are listened for:
// in the reducers themselves,
// in the sagas, via the sagas/index.

// often, at end of saga function, new data is passed into reducer.

```

<hr>

## II :: Actions, Reducers, Saga Functions
### TODO

![Actions, Reducers, Saga Functions](https://static.swimlanes.io/2aea22d342a38dcf747253bb7cb8c101.png)

```typescript
// note reducers, sagas: both listen for an action's type, and then take in its payload to perform state mutations  
// 1. actions -> reducers: actions go into reducers for simple replacements to state, without logic  
// 2. actions -> sagas: complicated or state-ful logic is orchestrated in the sagas, where control flow lives  

```

```typescript
// 1. actions -> reducers: actions go into reducers for simple replacements to state, without logic  
// make this part a living document: where does each piece of code live?
import { DataShape, INITIAL_STATE } from "../core"

function plainReducer(action: ActionTypeInterface) {
    switch (action.type) {
        // this is the type listened for
        case "SET_DATA":
            // this is what is returned to the state tree,
            // only simple replacements
            return { ...state, data: action.data }
        case "CLEAR_DATA":
            return INITIAL_STATE
        default:
            return INITIAL_STATE
    }
}

// root reducer
import { rootReducer } from "redux"
import { plainReducer } from "../data/plainFile"
import { anotherPlainReducer } from "../data/anotherPlainFile"

// each reducer is fed into the rootReducer
const rootReducer = combineReducers({
    plainReducer,
    anotherPlainReducer,
})

// the rootReducer is then fed into the redux store...

```

```typescript
// store.ts

import { createStore, applyMiddleware } from "redux"
import { Sagas, Reducers, Core } from "common"
import createSagaMiddleware from "redux-saga"
import { createLogger } from "redux-logger"

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

// sagas/index

import { funcName } from "../modules/shape_name/shape_sagas"
import { 
    funcName2,
    funcName3,
    funcName3,
} from "../modules/other_shape_name/other_shape_sagas"

const sagasIndex() {
    forEvery("ACTION_NAME1", funcName),
    forEvery("ACTION_NAME2", funcName2),
    // and more of the same
}

```

## Redux Sagas

![Redux Sagas](https://static.swimlanes.io/3a71dd5bb268c5fd008a1103178e7368.png)

```
sagas -> external API: request is made for data to be exchanged
external API -> sagas: returns raw response
sagas -> utils: utils are called, to actually perform business logic
utils -> sagas: data is returned, fit for saga to give to an action
sagas -> actions: return final data to actions
```

## Store, UI Components, UI As A Whole

![Store, UI Components, UI As  Whole](https://static.swimlanes.io/a92eb3d0100848b0d732c51aceab2a42.png)

```
Title: Store, UI Components, UI As  whole

store -> components: components are as presentational as possible
components -> ui: the components make up the ui, also as presentational as possible, maintaining miimal ui state
ui -> ui utils: sorting and filtering based on actual user interaction is handled in ui utils
```



```typescript
// client.ts or web/api.ts


```


```typescript
// sagas/index.ts

import { takeEvery } from "redux-saga/effects"
import { handleMetaData } from "../metadata_sagas"
import { handleClientMsg } from "../client_sagas"
import { handleLogin } from "../login_sagas"
import {
    handleLogout,
    handleLogoutResponse,
} from "../modules/logout/logout_sagas"

export default function* root(): {} {
    yield [
        takeEvery("HANDLE_LOGIN_RESP", handleLogin),
        takeEvery("LOGOUT", handleLogout),
        takeEvery("HANDLE_LOGOUT_RESPONSE", handleLogoutResponse),
        takeEvery("HANDLE_METADATA", handleMetaData),
        takeEvery("HANDLE_CLIENT_MSG", handleClientMsg),
    ]
}
```
