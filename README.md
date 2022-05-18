# react_basics
create app -<br/><br/>
`npx create-react-app appName`<br/>
run app -<br/>
`npm start`<br/>
<br/>
render html -<br/>
`const root = ReactDOM.createRoot(document.getElementById('root'));<br/>
root.render(<br/>
content<br/>
);`<br/>
<br/>
jsx rules -<br/>
expressions inside curly bracket<br/>
only one parent child<br/>
large block of html inside parenthesis<br/>
not support if statement but supports ternary operator<br/>
const myElement = (<br/>
  <><br/>
  p>I am a paragraph.</p<br/>
  p>I am a paragraph too.</p<br/>
  </><br/>
);<br/>
<br/>
components -<br/>
file & component name start with uppercase<br/>
function components -<br/>
function Car(props) {<br/>
  return h2>I am a {props.color} Car!</h2>;<br/
}<br/>
const root = ReactDOM.createRoot(document.getElementById('root'));<br/>
root.render(<Car color="red"/>);<br/>
<br/>
props -<br/>
can use string, variable or object. even all together<br/>
componentName argumentName=string/{variable/object}/><br/>
<br/>
react events -<br/>
button onClick={functionName}>Click Me</button <br/>
passing argument -<br/>
functionName(argument) => body<br/>
<button onClick={() => functionName(argument)}>Click Me</button><br/>
react event object -<br/>
functionName(argument) => console.log(argument.type)<br/>
<button onClick={(event) => functionName(event)}>Click Me</button><br/>
<br/>
&& conditional operator -<br/>
if the condition is true the code will execute<br/>
{condition && code}<br/>
<br/>
accessing lists using map function -<br/>
function Car(props) {<br/>
  return li>I am a { props.brand }</li ;<br/>
}<br/>
function Garage() {<br/>
  const cars = ['Ford', 'BMW', 'Audi'];<br/>
  return (<br/>
    <><br/>
      h1>Who lives in my garage?</h1 <br/>
      <ul><br/>
        {cars.map((car) => <Car brand={car} >)}<br/>
      </ul><br/>
    </><br/>
  );<br/>
}<br/>
const root = ReactDOM.createRoot(document.getElementById('root'));<br/>
root.render( Garage />);<br/>
<br/>
list with key -<br/>
function Name(props) {<br/>
  return h1>I am {props.name}</h1 <br/>
}<br/>
function Trees() {<br/>
  const trees = [<br/>
    {id:1, name :"Coconut Tree"},<br/>
    {id:2, name : "Melon Tree"},<br/>
    {id:3, name : "Lemon Tree"},<br/>
    {id:4, name : "Apple Tree"},<br/>
  ];<br/>
  return(trees.map((tree) => Name id={tree.id} name={tree.name}/>));<br/>
}<br/>
const root = ReactDOM.createRoot(document.getElementById('root'));<br/>
root.render(Trees />);<br/>
<br/>
