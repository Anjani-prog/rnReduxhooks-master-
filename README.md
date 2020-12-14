## React native Redux


https://react-redux.js.org/next/introduction/quick-start


    expo init rnRedux-hooks
   
   
install packages :
   
    npm install @react-native-community/masked-view lodash.remove react-native-gesture-handler react-native-paper react-native-reanimated react-native-safe-area-context react-native-screens react-navigation react-navigation-stack react-redux redux
    
    
 redux directory structure to follow (https://medium.com/swlh/the-good-the-bad-of-react-redux-and-why-ducks-might-be-the-solution-1567d5bdc698)
 
          |
          |-> Store
          |
          |-> Constants
          |
          |-> reducers
          |
          |-> actions
(https://www.valentinog.com/blog/redux/)

  ### Store 

        import { createStore } from "redux";
        import rootReducer from "../reducers/index";

        const store = createStore(rootReducer);

        export default store;
        
        
  ### Reducer.     
            Reducers produce the state of an application.
  
        const initialState = {
          articles: []
        };

       function rootReducer(state = initialState, action) {
          if (action.type === ADD_ARTICLE) {
            state.articles.push(action.payload);
          }
          return state;
        }

        export default rootReducer;
        
        
        
 The second principle of Redux says the only way to change the state is by sending a signal to the store. This signal is an action. So "dispatching an action" means sending out a signal to the store.
 
 
 ### Redux actions are nothing more than JavaScript objects.
 
             {
              type: 'ADD_ARTICLE',
              payload: { title: 'React Redux Tutorial', id: 1 }
            }
            
            
  The type property drives how the state should change and it's always required by Redux. The payload property instead describes what should change, and might be omitted
  
  
  
  ### Action creator (we wrap every action within a function)
  
          export function addArticle(payload) {
          return { type: "ADD_ARTICLE", payload }
        };


 ### Constants (declare actions as constants)
       
       export const ADD_ARTICLE = "ADD_ARTICLE";
       
 ### Redux store methods
 
    getState for reading the current state of the application
    dispatch for dispatching an action
    subscribe for listening to state changes
    
    
  ### connect ( it connects a React component with the Redux store.)
