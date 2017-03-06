## **React Learning**
>[facebook/react](https://facebook.github.io/react/)  
+ Component  
  - `pure function`  
  Such functions are called "pure" because they do not attempt to change their inputs(props), and always return the same result for the same inputs.
  ```jsx
  function Welcome(props) { 
    return <h1>Hello, {props.name}</h1>;  
  };
  ```
  - `class component`  
  The simplest way to define a component is to write a JavaScript function(pure function).  
  You can also use an ES6 class to define a component:
  ```jsx
  class Welcome extends React.Component {
    render() {
      return <h1>Hello, {this.props.name}</h1>;
    }
  };
  ```
  - `comparing 'pure function' with 'class component'`  
  The above two components are `equivalent` from React's point of view. Classes have some additional features that we call it 'state'.  
  For my opinion, I will use 'pure function' as much as possible. 
  - `Rendering a component`  
  For example, this code renders "Hello, Sara" on the page: 
  ```jsx
  function Welcome(props) {
    return <h1>Hello, {props.name}</h1>;
  };
  const element = <Welcome name="Sara" />;
  ReactDOM.render(
    element,
    document.getElementById('root')
  );
  ```
  ```html
  Hello, Sara
  ```
  >**Caveat:**  
  >Always start component names with a `capital letter`.  
  >>For example, `<div />` represents a DOM tag, but `<Welcome />` represents a component and requires `Welcome` to be in scope.  
  - `Composing components`  
  Components can refer to other components in their output. This lets us use the same component abstraction for any level of detail.For example:
  ```jsx
  function Welcome(props) {
    return <h1>Hello, {props.name}</h1>;
  };
  function App() {
    return (
      <div>
        <Welcome name="Sara" />
        <Welcome name="Cahal" />
        <Welcome name="Edite" />
      </div>
    );
  };
  ReactDOM.render(
    <App />,
    document.getElementById('root')
  );
  ```
  >**Caveat:**  
  >Components must return a single root element. This is why we added a `<div>` to contain all the `<Welcome />` elements.
  - `Extracting Components`  
  Extracting components might seem like grunt work at first, but having a palette of reusable components pays off in larger apps.  
  Here is my example:
  ```jsx
  function Main (props) {
    const {info, text} = props;
    return <div>
      <div class='img'>
        <img src={props.info.url} alt={props.info.name} />
      </div>
      <div class='img'>
        {props.text}
      </div>
    </div>
  };
  ```  
  After the Extracting:
  ```jsx  
  function Main (props) {
    const {info, text} = props;
    return <div>
      <User uesr={info}/>
      <div class='content'>
        {text}
      </div>
    </div>
  };  
  function User (props) {
    const {user} = props;
    return <div class='img'>
      <img src={user.url} alt={user.name}/>
    </div>
  };
  ```  
+ Typechecking With PropTypes  
  React has some built-in typechecking abilities. To run typechecking on the props for a component, you can assign the special `propTypes` property:  
  ```jsx
  class Greeting extends React.Component {
    render() {
      return (
        <h1>Hello, {this.props.name}</h1>
      );
    }
  };
  Greeting.propTypes = {
    name: React.PropTypes.string
  };  
  ```