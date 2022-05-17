# react_basics
create app -<br/><br/>
npx create-react-app appName<br/>
run app -<br/>
npm start<br/>
<br/>
render html -<br/>
root is a html id<br/>
const root = ReactDOM.createRoot(document.getElementById('root'));<br/>
root.render(<br/>
content<br/>
);<br/>
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
<componentName argumentName=string/{variable/object}/><br/>
<br/>
react events -
<button onClick={functionName}>Click Me</button>
passing argument -
functionName(argument) => body
<button onClick={() => functionName(argument)}>Click Me</button>
react event object -
functionName(argument) => console.log(argument.type)
<button onClick={(event) => functionName(event)}>Click Me</button>
