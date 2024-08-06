# 1. What is the difference between var, let, and const in JavaScript?

# var #

- **Scope:-** var variables are function-scoped,meaning it is accessible within funcation or globally declared outside the function

- **Hoisting:-** var declaration are hoisted to the top of their scope, meaning it can access before declaration, but the value is "undefined" until the variavle is defined is reached

- **Redeclaration:-** the "var" variable can be re-declared and updated in the same scope

### Example ###

```javascript
function exampleVar(){
    if(true){
      console.log(x) // undefined (due to hoistng)
      var x=10;// initilization
      
    }
    console.log(x) // 10
}
console.log(x) //error because of outside the function
exampleVar()
```

# let #
- **scope:-** Block-scoped, meaning it is acccessbile within the blog "{...}" ,It is declared in.

- **hoisting:-** It's also hoisted but, it is "temporal dead zone" meaning using "let" variable before the declaration results is "RefreanceError"

- **Re-declaration:-** Variable declared with "let" cannot be re-declared within the same block, but they can be updated

### Example ###

```javascript
function exampleLet(){
    console.log(y) // RefrenceError : y is not defined ,it is accessible within the block
    if(true){
    let y=20;
    console.log(y) // 20
    }
    console.log(y) // RefrenceError : y is not defined ,it is accessible within the block
}


exampleLet()
```

# const #

- **scope:-** Block-scoped, meaning it is acccessbile within the blog "{...}" ,It is declared in.

- **hoisting:-** It's also hoisted but, it is "temporal dead zone" meaning using "let" variable before the declaration results is "RefreanceError"

- **Re-declaration And Updation:-** Variables are declared with "const" cannot be "re-declared and updated. They must be initilized at the time of declaration,but the objects,arrays,the contents (eg..properties,elements) are modified ,cannot be reassigned itself variable.

### Example

```javascript
function exampleConst(){
    console.log(c) // RefrenceError : y is not defined ,it is accessible within the block
    if(true){
        const c=10;
        console.log(c) // 10
        c=20 // TypeError: cannot be reassigned new value
    }
    console.log(c) // RefrenceError : y is not defined ,it is accessible within the block

}
exampleConst()

const arr=[1,2,3]
arr.push(4) // allowed
console.log(arr) // [1,2,3,4] modifed
```

# 2. How do you create a new React component?
- **Defination** Creating a new react component using functions or classes

### Example 1 ###
```javascript
import React from "react";

const Mycomponent=()=>{
    return(
        <div>
        <h1>Creating a new React component using function</h1>
        </div>

    )
}
export default Mycomponent;
```
### Example 2
```javascript
import React, { Component } from 'react';

class MyComponent extends Component {
  render() {
    return (
      <div>
        <h1>Hello, this is my React component!</h1>
      </div>
    );
  }
}

export default MyComponent;
```

### Example 3
```javascript
import React from "react"
import Mycomponent from './Mycomponent';

function App(
    return(
        <div>
        <Mycomponent/>
        </div>
    )
)
export default App;
```

# 3. What is the purpose of the render() method in a React component?

- **Defination** 
The "render()" method describes the UI should look like for that component, the "render()" returns the JSX that react uses to build and Update the DOM

the "render()" returns must single react element ,they wrapped into "div" or (<>...</>)

### Example
```javascript
render(

    return(
        <div>
        <h1>render() method</h1>
        </div>
    )
)
```

# 4. How do you handle state changes in a React component?

- **Defination:-**
Handling state changes in a React component is a fundamental aspect of React's reactivity and UI updates. Depending on whether you are using a class component or a function component, the approach differs slightly.

### Example 
```javascript
import React from "react"
 function Mycomponent(){
    const [count,setCount]=useState(0)

    const increment=()=>{
        setCount(prevCount=>prevCount+1)
    }

    return(
        <div>
        <h1>count:{count}</h1>
        <button onClick={increment}>increment<button/>
        </div>
    )
 }
 export defult Mycomponent;
 ```

 # 5. What is the difference between a controlled and uncontrolled component in React?

 - **Controlled Component:-**
A controlled component is a component where React controls the form data through its state. The value of the form element is tied to the component’s state, and any changes to the form element are handled by updating the state.

### Example 
```javascript
import React,{useState} from "react"

function controlledComponent(){
    const [inputValue,setInputVlaue]=useState("");
    const handleChange=(event)=>{
            setInputValue(event.target.value)
    }
}
return(
<div>
<input type="text" value={inputValue} onChange={handleChange} />
</div>

)

export default controlledComponent;
```

- **Uncontrolled Component:-**
An uncontrolled component is a component where the form data is handled by the DOM itself. The input field’s value is not tied to the component’s state, and you typically access the value using a ref.


### Example
```javascript
import  React,{useRef} from "react";

function unControlled(){
    const inputRef=useRef(null)

    const handleSubmit=(event)=>{
        event.preventDefault()
    }
}

return(
    <from>
    <input type="text" ref={inputRef} />
    <button type="submit"></button>
    </from>
)

export default unControlled;
```

# 6. How do you pass props to a React component?

- **Defiantion:-** In React, props (short for "properties") are used to pass data from one component to another, typically from a parent component to a child component. Props are a key way to make components reusable and customizable.

### Example
```javascript
// chaild component app.js
import React from "react"

funcation Display({message}){
    return(
        <h1>{message}</h1>
    )
}
export default Display;
//parent component display.js

import React from "react";
import Display from "./Display.js";

function App(
    const mymessage="hello props"
    return(
        <Display message={mymessage}/>
    )
)
export default App;
```

#   7. What is the purpose of the key prop in a React component?

- **Defination:-** The key prop in React has a crucial role when rendering lists of elements. It helps React efficiently update and manage the DOM by uniquely identifying elements.

### Example
```javascript
import React from "react"
function ItemsList({items}){
    return(
        <ul>
       {items.map((item)=>{
         <li key={item.id}>{item.name}</li>
       })}
        </ul>
    )
}

export default ItemsList;
```

# 8. How do you handle events in a React component?

- **Defination:-** Handling events in a React component is similar to handling events in regular HTML, but with some key differences that align with React's component-based architecture.

- In React, event names are written in camelCase instead of lowercase, as in HTML.

- Event handlers in React are passed as functions, not strings.
- You typically define the handler method in the component and pass it to the event attribute.


### Example

```javascript
import React from "react"

function Mybutton(){
    const handleClick=()=>{
        alert("button clicked")
    }
}
return (
    <button onClick={handleClick}>Click button
    </button>
)

export default Mybutton;
```

# 9. What is the difference between a functional component and a class component in React?
## Functional Components
- **Defination:-** Functional components are simply JavaScript functions that accept props as an argument and return React elements (JSX).
- **Syntax:-** They are typically simpler and easier to read and write, especially for smaller, stateless components.

- **Performace:-** Functional components may have slight performance benefits over class components, especially in older versions of React, due to optimizations like not needing to bind methods.**

### Example
```javascript
function MyComponent(props) {
  return <div>Hello, {props.name}!</div>;
}
```

## Class Components
- **Definition:-**  Class components are ES6 classes that extend React.Component and must have a render method that returns React elements (JSX).

- **Syntax:-** They are generally more verbose than functional components and require the use of this keyword to reference props and state.

- **Performance:-** Historically, class components were used for more complex components that needed state management and lifecycle methods, but with hooks, functional components can now handle these as well.

### Example
```javascript
class MyComponent extends React.Component {
  render() {
    return <div>Hello, {this.props.name}!</div>;
  }
}
```

# 10.How do you use React Hooks?

- **Defination:-** React Hooks allow you to use state and other React features in functional components, making them more powerful and versatile. Here’s a basic overview of how to use some of the most commonly used hooks

## "useState" Hook
The "useState" hook lets you add state to functional components.

### Example
```javascript
import React, { useState } from 'react';

function Counter() {
  // Declare a state variable 'count' and a function 'setCount' to update it
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```

# 11.What is the purpose of the useEffect() hook in React?

- **Defination:-** The useEffect hook lets you perform side effects (like data fetching, subscriptions, or manually changing the DOM) in functional components.

### Example
```javascript
import React, { useEffect, useState } from 'react';

function DataFetcher() {
  const [data, setData] = useState([]);

  useEffect(() => {
    // Fetch data on component mount
    fetch('https://api.example.com/data')
      .then(response => response.json())
      .then(data => setData(data));
  }, []); // Empty array ensures effect runs only on mount and unmount

  return (
    <ul>
      {data.map(item => (
        <li key={item.id}>{item.name}</li>
      ))}
    </ul>
  );
}
```

# 12.How do you fetch data from an API in a React component?

- **Defination:-** Fetching data from an API in a React component is commonly done using the useEffect hook along with the fetch API or other libraries like axios. 

### Example
```javascript
import React, { useState, useEffect } from 'react';

function DataFetcher() {
  const [data, setData] = useState([]); // State to store the fetched data
  const [loading, setLoading] = useState(true); // State to track loading status
  const [error, setError] = useState(null); // State to track any errors

  useEffect(() => {
    // Fetch data when the component mounts
    fetch('https://api.example.com/data')
      .then(response => {
        if (!response.ok) {
          throw new Error('Network response was not ok');
        }
        return response.json();
      })
      .then(data => {
        setData(data); // Set the fetched data to state
        setLoading(false); // Set loading to false
      })
      .catch(error => {
        setError(error); // Set any errors to state
        setLoading(false); // Set loading to false
      });
  }, []); // Empty dependency array means this effect runs only on mount

  if (loading) return <p>Loading...</p>;
  if (error) return <p>Error: {error.message}</p>;

  return (
    <ul>
      {data.map(item => (
        <li key={item.id}>{item.name}</li>
      ))}
    </ul>
  );
}

export default DataFetcher;
```

# 13. What is the purpose of the useContext() hook in React?

- **Defination:-** The useContext() hook in React is used to access the value of a context directly in a functional component. It simplifies the process of consuming context data without needing to wrap components with Context.Consumer or pass props down through multiple levels of components.

### Example 
```javascript
import React from 'react';
import ThemeContext from './ThemeContext';

function App() {
  return (
    <ThemeContext.Provider value="dark">
      <Toolbar />
    </ThemeContext.Provider>
  );
}
```


