# DEV281x - Introduction to ReactJS
## With EdX
Started 10-3-2017

# Module 0 | Introduction ✔
## Welcome
- Start with JSX
- Model UI components with react components
- We will learn state and life cycle Methods of react components
- Make lists and forms

## Course Outline
- Benjamin Lin is the instructor
- Content Developer at Microsoft and full-stack web developer

## Grading and Due Dates
- Module Tutorial Labs - 0%
- Module Assignment Lab - 0%
- Module Assignment Lab Feedback - 3%
- Module Assessments - 66%
- Final Assessment - 31%

## How to Navigate through the Course
- Modules are topic areas made up of units
- Units has videos, readings, problem sets, and assessment questions

## Course Forums
- Have discussions about materials and help other student's questions

## Module 0 Lab
- Completed

## Pre-Course Survey
- Completed

# Module 1 | JSX and React Components
## Module 1 Intro
- What is ReactJS?
- React Elements - building blocks that represent DOM nodes
- JSX - syntax that allows html writing in javascript
- Functional Components - independent, reusuable components to describe how UI should look like based on state and properties
- Composition - to model an application in an efficient and clean manner

## Setting up ReactJS
- Their [Codepen Setup](https://codepen.io/benjlin/pen/EXoMQQ?editors=1010)
  
1. Create an HTML file
2. Add scripts to include react.js, react-dom.js and babel.js inside the head of the HTML file
3. Add a babel script within the body of the HTML file
4. Add <div id="root"></div> to the body of the HTML file
5. Start rendering elements using ReactJS

## What is ReactJS
- Library that generates a view layer of an application based on its state
- Built from components, which are independent and reusable

### Efficiency
- Creates a virtual DOM, a lightweight abstraction of the actual DOM, that does not have to calculate CSS styles and layouts
- Compares virtual DOM with actual DOM and update only altered components
- Fast Rendering - ends up being much faster at UI rendering
- Components Writing - makes it easier to write UI components

## Rendering Elements
- React Elements are objects that represents a DOM node using the JSX syntax
- Elements need to be rendered by the ReactDOM.render() method
```js
var element = <h1>Hello World!</h1>
```
  
### ReactDOM.render() method
- Used to render a react element to a specified part of the DOM
```js
ReactDOM.render(
    element, // What we want to change
    document.getElementById(); // Target where we want to change
)
```
- There is usually a single node where everything gets rendered
- But you can use as many root notes as you want
- Here, the h1 element is being rendered into the DOM element with id of "root"
```html
<div id = "root"></div>
```
```js
ReactDOM.render(
    <h1>Hello World!</h1>,
    document.getElementById("root")
)
```
  
### Rerendering the DOM using additional render() calls
- After the DOM is rendered, stays the same until another render() is called
- Here we are using another render() to update the displayed number
```js
var num = 0;

function updateNum() {
    ReactDOM.render(
        <div>{num++}</div>,
        document.getElementById("root")
    )
}

setInterval(updateNum, 100)
```
  
- My [glitch](https://introduction-to-reactjs.glitch.me)
- My code so far:
```js
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <script src="https://unpkg.com/react@16/dist/react.min.js"></script>
        <script src="https://unpkg.com/react-dom@16/dist/react-dom.min.js"></script>
        <script src="https://cdnjs.cloudflare.com/ajax/libs/babel-standalone/6.24.0/babel.js"></script>
    </head>
    <body>
        <div id="root"></div>
        <div id="number"></div>
        <script type="text/babel">
            ReactDOM.render(
                <div>Hello World</div>,
                document.getElementById("root")
            )
            
            var num = 0;

            function updateNum() {
                ReactDOM.render(
                    <div>{num++}</div>,
                    document.getElementById("number")
                )
            }

            setInterval(updateNum, 1000)
        </script>
    </body>
</html>
```

## JSX
- JSX is a syntax extension to JavaScript
- It allows react elements to be written inside JavaScript using HTML tags
```js
var element = <h1>Hello World!</h1>
```
  
### Using JSX with JavaScript Expressions
- Can use curly braces to embed JS expressions into JSX
```js
// With strings
var str = "World!"

var element = <h1>Hello {str}</h1>
```
```js
// With objects
var item = {
    name: "Cheese",
    price: 5
}

var element = <p>{item.name} : {item.price}</p>
```
```js
// With functions
var length = 20
var width = 10

function calculateArea(x,y) {
    return x * y;
}

var element = <div>The Area is: {caclulateArea(length, width)}</div>
```
  
### Using JSX with Attributes
- Notice we use className since class is a reserved keyword in javascript
- Follows camelCase naming convention (IE fontsize becomes fontSize)
- You can also give attribute values by using quotes:
```js
var element = <button className="deleteButton">Delete</button>
```
  
- You can also supply attributes with values by embedding with curly braces:
```js
var element = <img src={product.imageURL}></img>
```
  
- However, you should not surround curly braces with quotes, as it is treated as a string literal
```js
// Do not do this
var element = <img src ="{product.imageURL}"></img>
```
  
### Using JSX with Empty Tags
- If a HTML tag is empty, you can close it with a '/>' instead of a closing tag:
```js
var element = <input className = "nameInput" />
```
  
### Using JSX with a Style Object
- We can also use a object instead of a string literal:
```js
var styleObject = {
    backgroundColor: 'red',
    color: 'blue',
    fontSize: 25,
    width: 100
}

var element = <input style = {styleObject} />
```
  
- Now, the first set of curly braces is for the JSX expression while the second set of curly braces is for the style object:
- *Note that that this did not work for me or I didn't understand it*
- *I think you can set the width and height explicitly in the brackets*
```js
var element = <input style = {{width:200, height:100}}/>
```
  
### Using JSX with Nested Elements
- React elements can be nested in other react elements as long as it is wrapped by a single element
- It is recommended to surround nested elements with paranthesis to avoid the problems that occur with automatic semicolon insertion
```js
var element = (
    <div>
        <div>Hello World</div>
        <div>Hello World</div>
    </div> 
)

// Does not have the <div> parent
// But this would throw and error:
var element = (
    <div>Hello World</div>
    <div>Hello World</div>
)
```
  
### Using JSX Objects
- Objects created with JSX can be manipulated like normal JS objects
- Can be used in:
    1. Passed in arrays
    2. Used as arguments
    3. Return statements to functions
    4. Used inside if statements
    5. Used in for loops
```js
var product = {name:"apple", stock:0}

if (product.stock > 0) {
    var element = <h1>The product named {product.name} is not in stock</h1>
}
else{
    var element = <h1>The product named {product.name} and has {product.stock} units in stock</h1>
}

ReactDOM.render(
    element,
    document.getElementById("root")
)
```

## Functional Components
- A React component is an independent, reusuable component that renders elements based on states and properties
- There are 2 types of compononents: functional components and class components
- Functional Components: has properties
- Class Components: has properties, state, and lifecycle methods
  
- By convention the first letter of the function name should be capitalized
- Now we are working with functional components:
```js
function HelloWorld() {
    return <h1>Hello World!</h1>
}

var element = <HelloWorld /> // Can use HTML tag with the same name as React component

ReactDOM.render(
    <HelloWorld />,
    document.getElementById("root")
)
```

### Adding Properties to Functional Components
- You can supply as many property values as you want
- They can all be accessible through props argument
- Here, this argument to the functional component has the component properties
```js
function HelloWorld(props) {
    return <h1>Message: {props.message}</h1>
}

ReactDOM.render(
    <HelloWorld message="Hello World!" />,
    document.getElementById("root")
)
```
  
- We can also use string literals, arrays, or any other type of JS objects:
```js
function HelloWorld(props){
    return <h1>Value: {props.numberArray[props.index]}</h1>
}

ReactDOM.render(
    <HelloWorld index="3" numberArray={[1,2,3,4,5]} />,
    document.getElementById("root")
)
```
## Composition
- Functional components can have other functional components in their output
- Using composition:
```js
function ShoppingTitle(props) {
    return (
        <div>
            <h1>{props.title}</h1>
            <h2>Total Number of Items: {props.numItems}</h2>
        </div>
    )
}

function ListItem(props) {
    return <li>{props.item}</li>
}

function ShoppingList(props) {
    return (
        <div>
            <h3>{props.header}</h3>
            <ol>
                <ListItem item = {props.items[0]}/>
                <ListItem item = {props.items[1]}/>
                <ListItem item = {props.items[2]}/>
            </ol>
        </div>
    )
}

function ShoppingApp(props) {
    return (
        <div>
            <ShoppingTitle title = "My Shopping List" numItems = "9"/>
            <ShoppingList header = "Food" items = {[ "Apple","Bread","Cheese"]}/>
            <ShoppingList header = "Clothes" items = {[ "Shirt","Pants","Hat"]}/>
            <ShoppingList header = "Supplies" items = {[ "Pen","Paper","Glue"]}/>
        </div>
    )
}

ReactDOM.render(
    <ShoppingApp/>,
    document.getElementById("root")
)
```
  
- Instead of defining all the UI in one functional component:
```js
function ShoppingApp(props){
    return (
        <div>
            <div>
                <h1>My Shopping List</h1>
                <h2>Total Number of Items: 9</h2>
            </div>
            <div>
                <h3>Food</h3>
                <ol>
                    <li>Apple</li>
                    <li>Bread</li>
                    <li>Cheese</li>
                </ol>
            </div>

            <div>
                <h3>Clothes</h3>
                <ol>
                    <li>Shirt</li>
                    <li>Pants</li>
                    <li>Hat</li>
                </ol>
            </div>

            <div>
                <h3>Supplies</h3>
                <ol>
                    <li>Pen</li>
                    <li>Paper</li>
                    <li>Glue</li>
                </ol>
            </div>


        </div>
    )
}

ReactDOM.render(
    <ShoppingApp/>,
    document.getElementById("root")
)
```
## Conditional Rendering
- You can also invoke rendering based on the properties:
```js
function Feature(props){
    if (props.active == true){
        return <h1>This feature is active</h1>
    }
    else{
        return <h1>This feature is not active</h1>
    }
}

// ES6 Syntax
function Feature(props) {
    return <h1>This feature is {props.active ? "active" : "not active"}</h1>
}
```

### Preventing Rendering
- You can also prevent the output from rendering:
```js
function Feature(props) {
    if (props.active!) {
        return null
    }
    else {
        return <h1>{props.message}</h1>
    }
}
```
  
- Or also conditionally prevent a feature from rendering using && operator:
- The logic behind the && is that if props.active is
    1. True && expression = expression, therefore will render
    2. False && expression = false which converts to null, therefore will not render
```js
function Feature(props) {
    return (
        props.active && <h1>{props.message}</h1>
    )
}
```

## Module 1 Tutorial
- The same tutorial was given to make the shopping list app
- My code:
```js
function List(props) {
    return (
        <div>
            <h1>{props.title}</h1>
            <h2>There are {props.totalItems} items.</h2>
        </div>
    )
}

function ListItems(props) {
    return <li>{props.item}</li>
}

function Categories(props) {
    return (
        <div>
            <h3>{props.header}</h3>
            <ol>
                <ListItems item={props.items[0]}/>
                <ListItems item={props.items[1]}/>
                <ListItems item={props.items[2]}/>
            </ol>
        </div>
    )
}

function MyGroceryList(props) {
    return (
        <div>
            <List title="My Grocery List" totalItems="9" />
            <Categories header="Dog" items={["Leash", "Kibbles", "Bone"]}/>
            <Categories header="Snacks" items={["Oreos", "Popcorn", "Salsa"]}/>
            <Categories header="Dairy" items={["Milk", "Yogurt", "Eggs"]}/>
        </div>
    )    
} 

ReactDOM.render(
    <MyGroceryList/>,
    document.getElementById("root")
)
```

## Module 1 Lab
- The assignment for this module is to generate the following HTML using React Components. Try to use composition to organize the application into a hierarchy of React Components.
- Link for [Raw HTML](https://courses.edx.org/asset-v1:Microsoft+DEV281x+4T2017+type@asset+block/m1labHTML.html)
- Completed mine and assessed 2 other submissions
- [My Codepen](https://codepen.io/timh1203/pen/jGpJoZ)
- [Assessment #1](https://codepen.io/anko16/pen/zEJBym?editors=1000)
- [Assessment #2](https://codepen.io/anon/pen/LzmKVK?editors=0010)

## Module 1 Assessment
- Completed