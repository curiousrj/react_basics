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
