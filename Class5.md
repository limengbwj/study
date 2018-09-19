```
import {createStore} from 'redux';
import reduce from './reduce'

let initialState={
  count:1200
}

const store = createStore(reduce,initialState);

export default store;
```
