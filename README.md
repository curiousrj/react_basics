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
in the same function can use multiple operations by passing different arguments
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
#### useReducer multiple state value -
```react
import { useReducer } from 'react';

function reduce([fname, lname], action) {
  if(action.type === "clicked") {
    fname = "Steve"
    lname = "Haunt"
    return [fname, lname];
  }
}

 function App() {
   const [[fname, lname], dispatch] = useReducer(reduce, ["John","Doe"]);
   return(
     <>
     <h1>{fname} {lname}</h1>
     <button onClick={() => dispatch({type:"clicked"})}>Click Me</button>
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
### react class component -
```react
class Car extends React.Component {
  render() {
    return <h2>Hi, I am a Car!</h2>;
  }
}
```
### mounting -
#### component constructor - 
```react
class Car extends React.Component {
  constructor() {
    super();
    this.state = {color: "red"};
  }
  render() {
    return <h2>I am a Car!</h2>;
  }
}
```
#### props in constructor class component -
```react
class Car extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return <h2>I am a {this.props.model}!</h2>;
  }
}

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<Car model="Mustang"/>);
```
#### state in class component -
this.state.propertyName to get states<br/>
this.setState() to change state value
```react
class Car extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      brand: "Ford",
      model: "Mustang",
      color: "red",
      year: 1964
    };
  }
  changeColor = () => {
    this.setState({color: "blue"});
  }
  render() {
    return (
      <div>
        <h1>My {this.state.brand}</h1>
        <p>
          It is a {this.state.color}
          {this.state.model}
          from {this.state.year}.
        </p>
        <button
          type="button"
          onClick={this.changeColor}
        >Change color</button>
      </div>
    );
  }
}
```
#### getDerivedStateFromProps -
runs after constructor & fetch data from props<br/>
props data is not considerable
```react
class Header extends React.Component {
  constructor(props) {
    super(props);
    this.state = {favcolor: "pink"};
  }
  static getDerivedStateFromProps(props, state) {
    return {favcolor: props.color };
  }
  render() {
    return (
      <h1>My Favorite Color is {this.state.favcolor}</h1>
    );
  }
}

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<Header color="red"/>);
```
#### render() -
calls after getDerivedStateFromProps
```react
class Car extends React.Component {
  render() {
    return <h2>Hi, I am a Car!</h2>;
  }
}
```

#### componentDidMount -
```react
import React from "react";

class App extends React.Component {
  constructor(props) {
    super(props);
    this.state = {color : "pink"};
  }
  componentDidMount() {
    setTimeout(() => {
      this.setState({color: "violet"})
    }, 2000);
  }
  render() {
    return <h1>Hello {this.state.color} World!</h1>;
  };
}
export default App;

```
### updating -
#### getDerivedStateFromProps -
```react
class Header extends React.Component {
  constructor(props) {
    super(props);
    this.state = {favoritecolor: "red"};
  }
  static getDerivedStateFromProps(props, state) {
    return {favoritecolor: props.favcol };
  }
  changeColor = () => {
    this.setState({favoritecolor: "blue"});
  }
  render() {
    return (
      <div>
      <h1>My Favorite Color is {this.state.favoritecolor}</h1>
      <button type="button" onClick={this.changeColor}>Change color</button>
      </div>
    );
  }
}

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<Header favcol="yellow" />);
```
#### shouldComponentUpdate -
determines render should call or not not after update
```react
shouldComponentUpdate() {
  return false;
    }
```
#### render() -
run again to show the changes
#### getSnapshotBeforeUpdate -
store the value of prevProps and prevState
```react
getSnapshotBeforeUpdate(prevProps, prevState) {
  document.getElementById("div1").innerHTML =
  "Before the update, the favorite was " + prevState.favoritecolor;
  }
```
#### componentDidUpdate -
runs after conponent completes update
```react
componentDidUpdate() {
    document.getElementById("div2").innerHTML =
    "The updated favorite is " + this.state.favoritecolor;
  }
```
example combined
```react
class Header extends React.Component {
  constructor(props) {
    super(props);
    this.state = {favoritecolor: "red"};
  }
  componentDidMount() {
    setTimeout(() => {
      this.setState({favoritecolor: "yellow"})
    }, 1000)
  }
  getSnapshotBeforeUpdate(prevProps, prevState) {
    document.getElementById("div1").innerHTML =
    "Before the update, the favorite was " + prevState.favoritecolor;
  }
  componentDidUpdate() {
    document.getElementById("div2").innerHTML =
    "The updated favorite is " + this.state.favoritecolor;
  }
  render() {
    return (
      <div>
        <h1>My Favorite Color is {this.state.favoritecolor}</h1>
        <div id="div1"></div>
        <div id="div2"></div>
      </div>
    );
  }
}

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<Header />);
```
### unmounting -
#### componentWillUnmount -
called before a component removed from the DOM
```react
class Container extends React.Component {
  constructor(props) {
    super(props);
    this.state = {show: true};
  }
  delHeader = () => {
    this.setState({show: false});
  }
  render() {
    let myheader;
    if (this.state.show) {
      myheader = <Child />;
    };
    return (
      <div>
      {myheader}
      <button type="button" onClick={this.delHeader}>Delete Header</button>
      </div>
    );
  }
}

class Child extends React.Component {
  componentWillUnmount() {
    alert("The component named Header is about to be unmounted.");
  }
  render() {
    return (
      <h1>Hello World!</h1>
    );
  }
}

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<Container />);
```
### react router -
#### install react router -
```react
npm install react-router-dom
```
#### defining path -
```react
import { BrowserRouter, Routes, Route } from 'react-router-dom';
<BrowserRouter>
  <Routes>
    <Route path="/" element={<Home />} />
    <Route path="/about" element={<About />} />
    <Route path="/*" element={<Page404 />} />
  </Routes>
</BrowserRouter>
```
#### defining link -
```react
<Link to="/">Home</Link>
<Link to="/about">About</Link>
```
### 404 page -
```react
<Route path="/*" element={<Page404 />} />
```
#### redirect / navigate -
```react
<Route path="/*" element={<Navigate to="/" />} />
```
#### params -
```react
<Route path="user/:name" element={<User />} />

<li><Link to="/user/anil">Anil</Link></li>
<li><Link to="/user/peter">Peter</Link></li>

import React from 'react'
import { useParams } from 'react-router-dom'

export default function User() {
    const params = useParams();
    console.log(params);
    const {name} = params;
  return (
    <h1>This is {name}'s page</h1>
  )
}
```
#### navLink - 
used to define statement & argument inside link
```react
<NavLink className="nav-link" to="/about">About</NavLink>
```
#### style in link (active link) -
```react
<li><NavLink className="nav-link" style={({isActive}) => {return {color: isActive ? "aqua" : ""}}} to="/">Home</NavLink></li>

.nav-link {
  color:#282c34;
  text-decoration: none;
}

<li><NavLink className="nav-link active" to="/">Home</NavLink></li>

.active {
  color:aqua;
}
```
#### useSearchParams -
```react
import { useSearchParams } from 'react-router-dom'

const [searchParams, setSearchParams] = useSearchParams();
return (
      <>
      <h1>Name: {searchParams.get("name")}</h1>
      <input type="text" onChange={(e) => setSearchParams({text: e.target.value})}/>
      </>
  )
```
#### on click & conditional routing (useNavigate) -
```react
import { useNavigate } from 'react-router-dom';

export default function Home() {
  const navigate = useNavigate();
  const redirect = (url) => {
    navigate(url);
  }
  return (
    <>
    <button onClick={() => {redirect('/about')}}>Go to About Page</button>
    <button onClick={() => {redirect('/filter')}}>Go to Filter Page</button>
    </>
  )
}
```
#### nested routing -
```react
<Route path="/contact" element={<Contact />} >
  <Route path="/contact/company" element={<Company />}/>
</Route>

<>
<h1>Contact Page</h1>
<Link to="/contact/company">Company</Link>
<Outlet />
</>
```
### useLocation hook -
```react
import { Link, useLocation } from 'react-router-dom'
const location = useLocation();
console.log(location);
```
passing state -
```react
<NavLink className="nav-link" to="/contact" state={{name: "rj", message: "Hello"}}>Contact</NavLink>
```
###protected routing -
app.js
```react
<Route path="/" element={<Protected Component ={Home} />} />
```
protected.js
```react
import React, { useEffect } from 'react'
import { useNavigate } from 'react-router-dom'

export default function Protected(props) {
    const navigate = useNavigate();
    const {Component} = props;
    useEffect(() => {
        let login = localStorage.getItem('login');
        if (!login) {
            navigate("/login")
        }
    })
  return (
      <Component />
  )
}

```
login.js
```react
import React from 'react'
import { useNavigate } from 'react-router-dom'

export default function Login() {

    const navigate = useNavigate()
    const login = () => {
        localStorage.setItem('login', true);
        navigate("/");
    }
  return (
    <>
    <h1>Login Page</h1>
    <button onClick={login}>Login</button>
    </>
  )
}

```
