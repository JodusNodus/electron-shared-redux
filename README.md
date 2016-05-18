The middleware sends all the actions to all other processes including the browser windows and the main process. This way all processes recieve the same actions. You can use this functionality to react to other processes' actions or dispatch actions to communicate between processes.

## Install
`npm install --save electron-redux-actions`

## Use
```
import { createStore, applyMiddleware } from 'redux'
import electronMiddleware from "electron-redux-actions"
import rootReducer from '../reducers'

const enhancer = applyMiddleware(electronMiddleware)

export default function configureStore(initialState) {
  return createStore(rootReducer, initialState, enhancer)
}
```

Each action, foreign to the process has 2 extra key's:
- fromMain, *bool*, wether or not the action was dispatched from the main process.
- fromWindow, *number*, the window ID of the process where the action was dispatched.