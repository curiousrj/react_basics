# react_basics
### create app -
```react
npx create-react-app appName
```
### run app -
```react
npm start
```
### render html -
```react
const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(content);
```
### jsx rules -
expressions inside curly brackets<br/>
only one parent element<br/>
large block of html inside parenthesis<br/>
if statementnot not supported but supports ternary operator
```react
const myElement =
  <>
  <p>I am a paragraph.</p>
  <p>I am a paragraph too.</p>
  </>
);
```
### components -
file & component name starts with uppercase<br/>
#### function components -
```react
function Car(props) {
  return <h2>I am a {props.color} Car!</h2>;
}

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<Car color="red"/>);
```
### props -
we can use string, variable or object. even all together
```react
componentName argumentName=string/{variable/object}/>
```
### react events -
```react
<button onClick={functionName}>Click Me</button>
```
### passing argument -
```react
functionName(argument) => body
<button onClick={() => functionName(argument)}>Click Me</button>
```
### react event object -
```react
functionName(argument) => console.log(argument.type)
<button onClick={(event) => functionName(event)}>Click Me</button>
```
### && conditional operator -
if the condition is true the code will execute
```react
{condition && code}
```
### accessing lists using map function -
```react
function Car(props) {
  return li>I am a { props.brand }</li ;
}
function Garage() {
  const cars = ['Ford', 'BMW', 'Audi'];
  return (
    <>
      <h1>Who lives in my garage?</h1>
      <ul><br/>
        {cars.map((car) => <Car brand={car} >)}
      </ul>
    </>
  );
}
const root = ReactDOM.createRoot(document.getElementById('root'));
root.render( <Garage />);
```
### list with key -
```react
function Name(props) {
  return <h1>I am {props.name}</h1>
}
function Trees() {
  const trees = [
    {id:1, name :"Coconut Tree"},
    {id:2, name : "Melon Tree"},
    {id:3, name : "Lemon Tree"},
    {id:4, name : "Apple Tree"},
  ];
  return(trees.map((tree) => <Name id={tree.id} name={tree.name}/>));
}
const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<Trees />);
```
### forms -
```react
import { useState } from 'react';

 function App() {
   const [inputs, setInputs] = useState({});
   const submitHandler = (event) => {
     event.preventDefault();
     console.log(inputs);
   }

  const changeHandler = (event) => {
    const name = event.target.name;
    const value = event.target.value;
    setInputs(values => ({...values, [name]: value}));
  }

   return(
     <form onSubmit={submitHandler}>
     <label>First Name: </label>
     <input type="text" name="fName" value = {inputs.fName || ""} onChange={changeHandler}></input>
     <label>Last Name: </label>
     <input type="text" name="lName" value = {inputs.lName || ""} onChange={changeHandler}></input>
     <input type="submit"/>
     </form>
   );
 }

export default App;
```
#### Checkbox -
```react
import { useState } from 'react';

 function App() {
   const [car, setCar] = useState("Tata");
   const selectHandler = (event) => {
     setCar(event.target.value);
   }
   return(
     <select value={car} onChange={selectHandler}>
       <option value="Ford">Ford</option>
       <option value="Tata">Tata</option>
       <option value="Tesla">Tesla</option>
       <option value="Ferrari">Ferrari</option>
     </select>
   );
 }

export default App;
```
### inline css -
```react
<h1 style={{color: "red"}}>Hello Style!</h1>
```
### property names in camelCase -
```react
<h1 style={{backgroundColor: "lightblue"}}>Hello Style!</h1>
```
### create css object -
```react
const Header = () => {
  const myStyle = {
    color: "white",
    backgroundColor: "DodgerBlue",
    padding: "10px",
    fontFamily: "Sans-Serif"
  };
  return (
    <>
      <h1 style={myStyle}>Hello Style!</h1>
      <p>Add a little style!</p>
    </>
  );
}
```
### css modules -
module extension .module.css
```react
import styles from 'location'
```
### hooks -
react hooks can only called at the top level of function component<br/>
it cannot be conditional<br/>
<br/>
### useState -
```react
import { useState } from "react";

function App() {
  const [color, setColor] = useState("red");

  return (
    <>
      <h1>My favorite color is {color}!</h1>
      <button onClick={() => setColor("blue")}>Blue</button>
    </>
  )
}
export default App;
```
### in useState passing object and updating only one value
```react
import { useState } from "react";

function App() {
  const [color, setValues] = useState({
    brand:"Lamborghini",
    model:"Urus",
    type:"car",
    color:"blue"
  });

  const update = () => {
    setValues(previousState => {
      return {...previousState, color:"black"}
    });
  }

  return (
    <>
      <h1>The {color.brand}'s new {color.model} {color.type}'s {color.color} color looks really good.</h1>
      <button onClick={update}>Blue</button>
    </>
  )
}
export default App;
```
### useEffect -
whenever the component is rendered, useEffect gets called (even when runs for the first time)<br/>
when the passed value from the array changes it gets called

```react
import React, { useEffect, useState } from "react";

function App() {
  const [count, setCount] = useState(0);
  useEffect(() =>{
    console.log("useEffect called");
  },[count]);

  const countInc = () => {
    setCount(count + 1);
  }
  return (
    <React.Fragment>
  <h1>{count}</h1>
  <button type='button' onClick={countInc}>Click Me</button>
  </React.Fragment>
  )
}
export default App;
```
### useContext -
used to pass value to the nested child without passing through the nodes
```react
import { useState, createContext, useContext } from "react";

const UserContext = createContext();

function App() {
  const [user] = useState("Jesse Hall");

  return (
    <UserContext.Provider value={user}>
      <h1>{`Hello ${user}!`}</h1>
      <Component2 user={user} />
    </UserContext.Provider>
  );
}

function Component2() {
  return (
    <>
      <h1>Component 2</h1>
      <Component3 />
    </>
  );
}

function Component3() {
  return (
    <>
      <h1>Component 3</h1>
      <Component4 />
    </>
  );
}

function Component4() {
  return (
    <>
      <h1>Component 4</h1>
      <Component5 />
    </>
  );
}

function Component5() {
  const user = useContext(UserContext);

  return (
    <>
      <h1>Component 5</h1>
      <h2>{`Hello ${user} again!`}</h2>
    </>
  );
}

export default App;
```
### useReducer -
to avoid multiple useStates and functions useReducer used<br/>
in the same function can use multiple operations oby passing different arguments
```react
import { useReducer } from 'react';
function App() {
  const initialState = 0;
  const reducer = (state, action) => {
    switch(action.type) {
      case "increment":
        return state + 1;
      case "decrement":
        return state - 1;
      default:
        break;
    }
  }

  const [state, dispatch] = useReducer(reducer, initialState);
  return(
    <>
    <h1>{state}</h1>
    <button onClick= {() => {dispatch({type:"increment"})}}>inc</button>
    <button onClick= {() => {dispatch({type:"decrement"})}}>dec</button>
    </>
  );
}

export default App;
```
### useMemo -
used to prevent rerender for complex function while something changes in component<br/>
when the passed value from the array changes it gets called
```react
import React, { useState } from 'react'
function App() {
  const [count, setData] = useState(1)
  const [item, setItem] = useState(20)

  const newApple=React.useMemo(
    function appleTime() {
      console.warn("Hello")
      return 100 * count;
    }
  ,[item])
  return (
    <div className="App">
      <h1>Hooks in React {count}</h1>
      {newApple}
      <button onClick={() => setData(count + 1)}>Update State</button>
      <button onClick={() => setItem(item * 10)}>Update State</button>

    </div>
  );
}

export default App;
```
### custom hook -
#### App.js -
```react
import  useInput  from './useInput'
 function App() {
   const [firtsName, bindFirstName, resetFirstName] = useInput("");
   const [lastName, bindLastName, resetLastName] = useInput("");

   const submitHandler = (event) => {
     event.preventDefault();
     alert(`Hello ${firtsName} ${lastName}!`);
     resetFirstName();
     resetLastName();
   }

   return(
     <form onSubmit={submitHandler}>
       <div>
         <label>First Name:</label>
         <input type="text" {...bindFirstName}></input>
       </div>
       <div>
         <label>Last Name:</label>
         <input type="text" {...bindLastName}></input>
       </div>
       <button>Submit</button>
     </form>
   );
 }

export default App;
```
#### useInput.js -
```react
import {useState} from 'react';
function useInput(initialValue) {
    const [value, setValue] = useState(initialValue);
    const reset = () => {
        setValue(initialValue);
    }
    const bind = {
        value,
        onChange: (e) => {setValue(e.target.value)}
    }

    return [value, bind, reset];
}

export default useInput;
```
