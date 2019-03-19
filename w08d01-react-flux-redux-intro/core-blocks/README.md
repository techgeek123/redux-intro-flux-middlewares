## Release 0

Create To-Do app with Redux + React by following below steps
    
- Write a detailed mock of the screen which include all the data
- Divide the app into components based on their overall **purpose** of each component and list state and  actions for each component
- Create **action creators** for each actions
- Write **Reducers** for each action

## Release 1

Create `actions/actions.js` file and create action creators for each action

Create `reducers/reducers.js` file and write reducers to specify changes. At the end use `combineReducers` helper function from `redux` module to combine all the reducers

Create store, `main.js`, that holds the app's state  using `createStore` from `redux` module and pass the store property to the `Provider` element which wraps out route content

Create a root component, `App.js`, and use `connect` function for connecting our root component App to the store.

Create other components which should be unaware of redux to add and list out the to-do items

## Release 2

Style the application using bootstrap and css

