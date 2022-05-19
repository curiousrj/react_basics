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
### in useStae passing object and updating only one value
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
