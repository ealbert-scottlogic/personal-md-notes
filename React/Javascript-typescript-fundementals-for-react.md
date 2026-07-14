# JavaScript & TypeScript for React

<!-- Table of Contents -->
## Table of Contents
- [Part 1 - Modern JavaScript Fundamentals](#part-1)
    - [Environment & Tooling](#environment--tooling)
        - [Vite overview and installation](#vite-overview-and-installation)
        - [File structure and meaning](#file-structure-and-meaning)
            - [package.json](#package-json)
            - [main.js](#main-js)
    - [Variables & Types](#variables--types)
        - [Variable declaration](#variable-declaration)
        - [Primitive types](#primitive-types)
            - [String](#string)
            - [Non Types](#non-types)
        - [Objects](#objects)
            - [Definition](#objects-definition)
            - [Access](#objects-access)
            - [Nesting](#objects-nesting)
            - [Nested Access](#objects-nested-access)
        - [Arrays](#arrays)
            - [Accessing](#arrays-accessing)
            - [Adding / Removing](#arrays-add-remove)
        - [Arrays of Objects](#arrays-of-objects)
        - [Worthwhile note](#worthwhile-note)
    - [Functions](#functions)
        - [Definition](#functions-definition)
        - [Function Expressions](#function-expressions)
        - [Arrow Functions](#arrow-functions)
        - [Defaults](#function-defaults)
        - [Functions as Variables](#functions-as-variables)
        - [Passing Functions to other functions](#passing-functions)
        - [Returning functions from functions](#returning-functions)
    - [Modern Syntax](#modern-syntax)
        - [Object deconstruction](#object-deconstruction)
        - [Array Deconstruction](#array-deconstruction)
        - [Spread Operators](#spread-operators)
            - [Spread Merge](#spread-merge)
            - [Object Spread](#object-spread)
            - [Object Merge](#object-merge)
        - [Rest Operators](#rest-operators)
        - [Optional Chaining](#optional-chaining)
        - [Nullish Coalescing](#nullish-coalescing)
        - [Shorthand object notion](#shorthand-object-notion)
- [Part 2 - Asynchronous JavaScript](#part-2)
    - [Promises & Async](#promises--async)
        - [Promises](#promises)
        - [.then()](#then-method)
        - [Promise chaining](#promise-chaining)
        - [Async / Await](#async-await)
        - [Parallel Calls](#parallel-calls)
- [Part 2.5 - Error Handling](#part-2-5---error-handling)
- [Part 3 - TypeScript](#part-3---typescript)
    - [Variable Declaration](#typescript-variable-declaration)
        - [Primitive Types](#ts-primitive-types)
        - [Unknown types](#ts-unknown-types)
        - [Object Definition](#ts-object-definition)
    - [Function Definition](#ts-function-definition)
    - [Records](#ts-records)
    - [Union Types](#ts-union-types)
    - [Type Alias](#ts-type-alias)
- [Part 4 - React Fundamentals](#part-4---react-fundamentals)
    - [React Compared to .NET](#react-compared-to-dotnet)
    - [Components](#components)
        - [Creating Components](#creating-components)
        - [Component Composition](#component-composition)
    - [JSX](#jsx)
        - [Embedding JavaScript](#embedding-javascript)
    - [Props](#props)
    - [State](#state)
    - [Event Handling](#event-handling)
    - [Conditional Rendering](#conditional-rendering)
    - [Rendering Lists](#rendering-lists)
    - [Forms](#forms)
    - [useEffect](#useeffect)
    - [Derived Values](#derived-values)
    - [Data Flow](#data-flow)
    - [Typical Component Layout](#typical-component-layout)
    - [Common Hooks](#common-hooks)
    - [Typical Page Flow](#typical-page-flow)
    - [React Design Principles](#react-design-principles)
    - [Common Component Categories](#common-component-categories)

<!-- Anchors for easier linking -->
<a id="part-1"></a>

## Part 1 - Modern JavaScript Fundamentals

<a id="environment--tooling"></a>
### 1. Environment & Tooling

<a id="vite-overview-and-installation"></a>
### Vite overview and installation

Vite is a rust based build tool that builds and serves javascript applications and includes a development server to view changes in real time, more information and docs can be found here 

We can create a new Vite project through the command line setup wizard by using 

```bash
npm create vite@latest project-name
```

after the selection phase for your framework you may be prompted to automatically run     `npm i` and run the application, if you do not you can always just run `npm install` at a later time when you come to serve the application  

you can then serve the application through Vite during development using:

```bash
npm run dev
```

In order to create a build through VITE we must first use

```bash
npm run build
```

Which creates a `dist/` folder containing out production build which we can view via 

```bash
npm run preview
```

Allowing us to view our production view locally

<a id="file-structure-and-meaning"></a>
### File structure and meaning

<a id="package-json"></a>
#### package.json

This is the configuration file for the project comparable to a `.csproj` or `launchSettings.json` as we might see in a .net project

<a id="main-js"></a>
### main.js

This is the application entry point

<a id="variables--types"></a>
### 2. Variables & Types

<a id="variable-declaration"></a>
### Variable declaration

There are 3 main ways to declare variables in js 

```jsx
let age = 21; 
const name = "Someone"; 
var oldmethod = true; 
```

`consts`are constants that don’t change 

`lets`are for values that change

`var` shouldn’t really be used as it is the old declaration method

Important note about consts is that if they point to objects, the object is still mutable however they cannot be reassigned to other objects, this is very similar to .net and can be imagined as pointers 

```jsx
const age = 25; 
age = 30; // This obviously wouldn't work 

const user = {
	name: "Someone"
	};
user.name = "somethingelse"; 
// This works fine
```

<a id="primitive-types"></a>
### Primitive types

```jsx
const number = 42; //number
const decimal = 3.14; // number
const text = "string"; //string
const isActive = true; // boolean
const nothing = null; //null
let unknown; // undefined
// We can log out types using 
console.log(typeof number); 
```

There is no distinction between numerical values within js, it’s all just the `number` type unlike c# 

<a id="string"></a>
#### String

There are 3 different types of string definitions

```jsx
"string" 
'string' 
`string` // This type allows for interpolation and is known as a template literal
```

```jsx
// Where c# has
$"String {variable}"

// Js has 
`string ${variable}`
```

<a id="non-types"></a>
#### Non Types

There are two main non types null and undefined

```jsx
undifined // not ever assigned
null // explicitly defined as null
```

<a id="objects"></a>
### Objects

<a id="objects-definition"></a>
#### Definition

```jsx
const person = {
	name: "someone",
	age: 40
}; 
```

<a id="objects-access"></a>
#### Access

```jsx
// Access 
console.log(person.name) 
// Allocate
person.name = 43; 
// Add
person.city = "York"; 
```

<a id="objects-nesting"></a>
#### Nesting

```jsx
const person = {
	name: "someone", 
	address: {
		city: "London",
		postcode: "SW1"
	}
};
```

<a id="objects-nested-access"></a>
#### Nested Access

```jsx
console.log(person.address.city); 
```

<a id="arrays"></a>
### Arrays

Arrays are pretty similar

```jsx
const array = ["value", "value", "value"] 
```

<a id="arrays-accessing"></a>
#### Accessing

```jsx
console.log(array[0])
```

<a id="arrays-add-remove"></a>
#### Adding // Removing

```jsx
array.push("value"); // Adds value to the end
array.pop(); // Removes value from the end
```

<a id="arrays-of-objects"></a>
### Arrays of Objects

```jsx
const obbArray = [
	{
		name: "someone",
		age: 20
	},
	{
		name: "someoneelse",
		age: 45
	}
]; 
console.log(obbArray[0].name); //output :someone
```

<a id="worthwhile-note"></a>
### Worthwhile note

All variables within javascript are dynamically typed meaning you can change between types when reassigning variables, this (OBVIOUSLY), we will get back to this when we move along to typescript

<a id="functions"></a>
### 3. Functions

<a id="functions-definition"></a>
### Definition

```jsx
// Non returning
function name(){ 
	console.log("you have been named"); 
}
// Parametised function 
function name(name){
	console.log(`you have a name mr ${name}`); 
}
// Returning functions
function retSomething(name){
	return `concatname ${name}`; 
}
```

<a id="function-expressions"></a>
#### Function Expressions

```jsx
const greet = function(name) {
	console.log(`Hello ${name}`);
}; 
// Variable contains the function and can now be called the same way
greet("somename"); 
```

<a id="arrow-functions"></a>
#### Arrow Functions

```jsx
// Similar to c# lambdas 
const greet = (name) => {return `Hello ${name}`;}; 
// Alternative definition
const greet = (name) => `Hello ${name}`; 
// One line definitions don't require return statements as this is 
// implicitly expected behaviour 

// With single parameters brackets are optional 
const square = number => number * number; 
```

<a id="function-defaults"></a>
### Defaults

```jsx
function greet(name = "name"){
	console.log(name); 
}
```

<a id="functions-as-variables"></a>
### Functions as Variables

```jsx
const another = greet; // another type(function)
const another = greet(); // another type (return type of function)
```

<a id="passing-functions"></a>
#### Passing Functions to other functions

```jsx
function repeat(action){
	action(); 
	action(); 
}

repeat(() => {
	console.log("hello"); 
});

// This will log hello twice 
```

<a id="returning-functions"></a>
#### Returning functions from functions

```jsx
function ret(name){
	return () => console.log(`Hello ${name}`); 
}
const greetPerson = ret("person"); 
greetPerson(); 
// Will log "Hello person" 
```

<a id="modern-syntax"></a>
### 4. Modern Syntax

<a id="object-deconstruction"></a>
### Object deconstruction

```jsx
// Given
const person ={
	name: "Person",
	age: 30
}; 
// Old syntax
const name = person.name; 
const age = person.age; 

//Modern syntax 
const {name, age} = person; 
```

<a id="array-deconstruction"></a>
### Array Deconstruction

```jsx
// Given
const something = [0,1,2,3]; 
// Old
const var1 = something[0]; 
const var2 = something[1]; 
// New
const [var1, var2]  = something; 
// Skip values
const [, var2] = something; 
const [,, var3] = something; 
// Collect the remainder
const [var1, ...others] = something; 
```

<a id="spread-operators"></a>
### Spread Operators

```jsx
// Given
const arr = [0,1,2,3]; 
// This will directly copy the pointer to the array 
const copy = arr; 
// This will create a new copy of the array in memory
const otherCopy = [...arr]; 
// Given
arr.push(4); 
copy //      => [0,1,2,3,4]
otherCopy // => [0,1,2,3] still

// We can also append in a spread
const copy = [...arr, 4,5] 
copy // => [0,1,2,3,4,5]
arr // => [0,1,2,3]
```

<a id="spread-merge"></a>
#### Spread Merge

```jsx
// Given
const a = [0,1] 
const b = [2,3] 

const all = [...a, ...b]; 
all // => [0,1,2,3]
```

<a id="object-spread"></a>
#### Object Spread

```jsx
// Given 
const person = {
  name: "Person", 
  age: 88
}; 
// Create new object with new value for age 
const updated = {
  ...person,
  age:31
};
// Create new object with added value
const newP = {
  ...updated,
  somethingelse: 41
}; 
```

<a id="object-merge"></a>
#### Object Merge

```jsx
// Given
const role = {
  title: "Manager",
  responseCode: 0o23
}; 
const person ={
  name: "Person",
  age: 12
}; 
// Merge object properties into new object
const employee ={
  ...role, 
  ...person
}; 
// Employee.contains => title, responseCode, name, age

```

<a id="rest-operators"></a>
### Rest Operators

```jsx
const add = (...numbers) =>{
	console.log(numbers); 
}; 
// This will collect all the remaining parameters given to a function allowing
add(1,2,3,4); 
// Instead of requiring
add([1,2,3,4]); 
```

<a id="optional-chaining"></a>
### Optional Chaining

```jsx
// Same as .net 
// Given 
const object = {name: "person"};
object.address.city; 
// Will throw as address is undifined
object.address?.city // Will not throw

object.address?.location?.postcode; // Also works fine  
```

<a id="nullish-coalescing"></a>
### Nullish Coalescing

```jsx
// Given 
const username = null;
const display = username ?? "Guest"; 
//or 
const display = username || "Guest"; 
// display => Guest 

// However 
const age = 0; 
const newValue = age ?? 100; 
// newValue => 0
const newValue = age || 100; 
// newValue => 100 
// ?? only fallsback for null && undefined 
// || fallsback for anything "falsy" 
```

<a id="shorthand-object-notion"></a>
### Shorthand object notion

```jsx
// Given
const name = "value"; 
const age = 34; 

// We can define via shorthand
const person = {name, age}; 
// It will infer the names from the variable names
```

```jsx
// Shorthand function notion within objects
const person ={ greet(){console.log("hello");}};
```

<a id="part-2"></a>
## Part 2 - Asynchronous JavaScript

<a id="promises--async"></a>
<a id="promises--async"></a>
### 5. Promises & Async

<a id="promises"></a>
#### Promises

Promises basically just say that a variable doesn’t contain a value yet but promise it will when the async functionality finishes 

```jsx
const promise = new Promise((resolve) => {
	setTimeout(() => {
		resolve("Finished message"); 
	}, 2000); 
}); 
// This creates a variable called resolve and passes it through to a function
// This function wraps another in a setTimeout() which when finished changes
// the value of our variable to "Finished message" which then becomes the 
// Value for promise 
console.log(promise); // Would return [Pending] 
console.log(await promise); // Would return "Finished message" 
```

<a id="then-method"></a>
### .then()

`.then()`  Assigns some code to run after the promise has been resolved or rejected 

```jsx
promise.then(result => { 
		console.log(result); 
	}); 
```

<a id="promise-chaining"></a>
#### Promise chaining

We can connect .then clauses together to have them ran sequentially after the promise has resolved

```jsx
Promise.resolve(5)
	.then(value => value*2)
	.then(value => value+10)
	.then(console.log); 
	// Output : 20
```

<a id="async-await"></a>
### Async / Await

Example using a url request // response 

```jsx
// We can write a fetch query like this
fetch(url)
	.then(response => response.json())
	.then(data => console.log(data)); 
```

However in modern Js we would instead use an await function to pause our control flow until our request has returned 

```jsx
const response = await fetch(url); 

const data = await response.json(); 

console.log(data); 
```

<a id="parallel-calls"></a>
### Parallel Calls

If we have to make two requests to two different non dependent functions such as this

```jsx
const users = await fetch(usersUrl); 
const posts = await fetch(postsUrl); 
```

We would find that with this implementation, the second async function cannot run until the first one has been resolved. 

We can instead start both async functions at the same time and simply wait for them to both be resolved at the end

```jsx
const [usersResponse, postsResponse] = await Promise.all([
	fetch(usersUrl),
	fetch(postsUrl)
	]); 
```

<a id="part-2-5---error-handling"></a>
<a id="part-2-5---error-handling"></a>
## Part 2.5 - Error Handling

In order to not have the program crash anytime we get an error, we can plan for issues using try catch blocks 

```jsx
const loadUsers = async () => {
    try {
        const response = await fetch(url);
        const users = await response.json();
        console.log(users);
    }
    catch (error) {
        console.error(error);
    }
};
```

This will attempt a `fetch` from a url and if there is an issue with the request will log the error to the console. This stops the whole program from ending if there is a request error 

<a id="part-3---typescript"></a>
<a id="part-3---typescript"></a>
## Part 3 - TypeScript

<a id="typescript-variable-declaration"></a>
### 6. Variable Declaration

<a id="ts-primitive-types"></a>
#### Primitive Types

```jsx
// natural js
let name = "something"; 
let boolean = false; 
// typescript 
let name: string = "something"; 
let boolean: boolean = false; 

const array: number[] = [1,2,3];  
// Typescript can also infer types like python or .net var tags
const age : number = 25; 
const age = 25; // Infered number type
// Remove the type safty all together
let value: any = 5; 
// This should really be avoided
```

<a id="ts-unknown-types"></a>
#### Unknown types

```tsx
/* 
If we aren't going to know what the type of a value is going to be, we
can use the "unknown" type
*/
let value:unknown; 
// This will force you to make a type check before consuming it
if(typeof value === "string"){
	console.log(value.toUpperCase()); 
}
```

<a id="ts-object-definition"></a>
#### Object Definition

```jsx
const user: {
	name: string; 
	age: number; 
}={
	name:"Alice", 
	age: 30
}; 
```

<a id="ts-function-definition"></a>
### Function Definition

```tsx
// javascript:
const square = number => number * number; 

// explicit typescript definitions:
const square = (returnNumber: number): variableName =>{
	return variableName * variableName;
};

// Infered return type:
const square = (number: number) => number * number;
```

<a id="ts-records"></a>
#### Records

Records are a utility type that behave like dictionaries mapping one key type to a value type

```tsx
// This defines a record type that maps strings to number values
type userRecord = Record<string, number>; 

// We can then create an instance of our new type 
const ages: userRecord = { 
	Alice: 35, 
	James: 12
}; 
```

<a id="ts-union-types"></a>
### Union Types

```tsx
// We can have variables that can be a unique subset of types 
let value: string | number; 
value = "hello"; 
value = 32; 
// Both of these are fine 
value = true; // This would throw an error 
// We can also use union types for more specific constraints
type Status = "loading" | "success" | "error"; 
let status: Status = "loading"; 
// This creates a new type that can only have one of 3 set values
```

```tsx
/* 
Little design patern for union types to enforce that each type has a 
handler function
*/ 
type NotificationType = 'email' | "sms" | "push"; 

const HANDLERS = Record<NotificationType, (message: string) => void> = {
  email: (p) => emailService.send(p), 
  sms: (p) => smsService.send(p),
  push: (p) => pushService.send(p),
};

function sendNotifications(type: NotificationType, message: string) {
  return HANDLERStype;
}
```

This record essentially says for every possible value for Notification Type we must create a function that takes in a string and returns nothing hence requiring a function for each value and ensuring that all notification types have a send endpoint 

<a id="ts-type-alias"></a>
### Type Alias

```tsx
//Suppose you keep writing
string | number
// We can instead create an alias
type Id = string | number;
// Meaning now we can just write
const userId: Id = "abc1242"; 
```

<a id="part-4---react-fundamentals"></a>
## Part 4 - React Fundamentals

<a id="react-compared-to-dotnet"></a>
### 7. React Compared to .NET

| React | C# |
| --- | --- |
| Component | Razor Component |
| Hook | Service / Helper |
| Service | API Service |
| Type | DTO / Model |
| App | Root Component |
| `main.tsx` | `Program.cs` |
| Props | Constructor Parameters |
| State | Private Fields |
| JSX | Razor Syntax |

### Typical Vite + React + TypeScript File Structure

```
src/
│
├── assets/
│
├── components/
│   ├── Button/
│   │   ├── Button.tsx
│   │   └── Button.css
│   │
│   └── UserCard/
│       ├── UserCard.tsx
│       └── UserCard.css
│
├── hooks/
│   └── useUsers.ts
│
├── pages/
│   ├── Home.tsx
│   ├── Users.tsx
│   └── Settings.tsx
│
├── services/
│   └── api.ts
│
├── types/
│   ├── User.ts
│   └── Product.ts
│
├── utils/
│
├── App.tsx
├── main.tsx
└── index.css
```

../

```
├── index.html
├── package.json
├── tsconfig.json
├── vite.config.ts
└── package-lock.json
```

### React Render Flow

```
Browser

↓

index.html

↓

main.tsx

↓

<App />

↓

Component Tree

↓

DOM Updates
```

`index.html`

```html
<body>

    <div id="root"></div>

</body>
```

`main.tsx`

```tsx
import { StrictMode } from "react";
import { createRoot } from "react-dom/client";

import App from "./App";

createRoot(document.getElementById("root")!).render(
    <StrictMode>
        <App />
    </StrictMode>
);
```

React takes ownership of the `root` div and renders everything inside it.

<a id="components"></a>
### Components

Everything in React is a component.

A component is simply a function that returns JSX.

```tsx
const App = () => {
    return <h1>Hello World</h1>;
};

export default App;
```

<a id="creating-components"></a>
### Creating Components

Create

```
components/

UserCard/

UserCard.tsx
```

```tsx
const UserCard = () => {

    return (
        <div>
            User Card
        </div>
    );

};

export default UserCard;
```

Import

```tsx
import UserCard from "./components/UserCard/UserCard";
```

Use

```tsx
<UserCard />
```

Notice:

Components always begin with a capital letter.

<a id="component-composition"></a>
### Component Composition

Large applications are built by composing many small components.

```
App

│

├── Navbar

├── Sidebar

├── Dashboard

│     ├── UserCard

│     ├── Statistics

│     └── Footer
```

Try to build many small reusable components rather than one large page.

<a id="jsx"></a>
### JSX

JSX is syntax that looks like HTML but compiles to JavaScript.

```tsx
const App = () => {

    return (

        <div>

            <h1>Hello World</h1>

        </div>

    );

};
```

<a id="embedding-javascript"></a>
#### Embedding JavaScript

Use `{}`

```tsx
const name = "Alice";

return <h1>Hello {name}</h1>;
```

Anything inside `{}` is normal JavaScript.

```tsx
const age = 25;

return <p>{age + 5}</p>;
```

<a id="props"></a>
### Props

Props are component parameters.

Create an interface.

```tsx
interface UserCardProps {

    name: string;

    age: number;

}
```

Pass into the component.

```tsx
const UserCard = ({ name, age }: UserCardProps) => {

    return (
        <div>

            <h2>{name}</h2>

            <p>{age}</p>

        </div>
    );

};
```

Use

```tsx
<UserCard
    name="Alice"
    age={30}
/>
```

Props are **read-only**.

A child component should never modify its props.

<a id="state"></a>
### State

State is mutable data owned by a component.

```tsx
const [count, setCount] = useState(0);
```

Think of it as

```
Current Value

↓

count

Setter Function

↓

setCount
```

Update

```tsx
setCount(count + 1);
```

Never write

```tsx
count++;
```

React won't know the value changed.

#### Complex State

```tsx
const [user, setUser] =
    useState<User | null>(null);
```

Updating objects

```tsx
setUser({

    ...user,

    name: "Bob"

});
```

Always create a new object.

Never mutate the existing one.

<a id="event-handling"></a>
### Event Handling

Attach events.

```tsx
<button
    onClick={() => alert("Clicked")}
>
    Click
</button>
```

Usually

```tsx
const handleClick = () => {

    console.log("Clicked");

};

<button onClick={handleClick} />
```

Pass a function.

Don't call the function.

Incorrect

```tsx
<button onClick={handleClick()} />
```

Correct

```tsx
<button onClick={handleClick} />
```

<a id="conditional-rendering"></a>
### Conditional Rendering

React uses JavaScript.

#### Early Returns

```tsx
if (loading) {

    return <Spinner />;

}

if (error) {

    return <Error />;

}

return <Dashboard />;
```

#### Ternary

```tsx
return (

    loggedIn

        ? <Dashboard />

        : <Login />

);
```

#### Logical AND

```tsx
{isAdmin && <AdminPanel />}
```

Read as

"If true, render this."

#### Render Nothing

```tsx
if (!user) {

    return null;

}
```

<a id="rendering-lists"></a>
### Rendering Lists

```tsx
const users: User[] = [

    { id: 1, name: "Alice" },

    { id: 2, name: "Bob" }

];
```

Render

```tsx
<ul>

    {users.map(user => (

        <li key={user.id}>

            {user.name}

        </li>

    ))}

</ul>
```

Always provide a unique `key`.

<a id="forms"></a>
### Forms

Controlled input

```tsx
const [name, setName] =
    useState("");
```

```tsx
<input

    value={name}

    onChange={(e) =>
        setName(e.target.value)
    }

/>
```

The state becomes the source of truth.

<a id="useeffect"></a>
### useEffect

Runs side effects.

```tsx
useEffect(() => {

    console.log("Mounted");

}, []);
```

Empty dependency array

↓

Runs once.

Fetching data

```tsx
useEffect(() => {

    const loadUsers = async () => {

        const response =
            await fetch(url);

        const users: User[] =
            await response.json();

        setUsers(users);

    };

    loadUsers();

}, []);
```

<a id="derived-values"></a>
### Derived Values

Don't store values you can calculate.

Bad

```tsx
const [fullName, setFullName] =
    useState("");
```

Better

```tsx
const fullName =
    `${user.firstName} ${user.lastName}`;
```

<a id="data-flow"></a>
### Data Flow

Data flows down.

```
Parent

↓

Props

↓

Child
```

Children request changes by calling callbacks.

```tsx
interface Props {

    onDelete: () => void;

}
```

Child

```tsx
<button onClick={onDelete}>
```

Parent

```tsx
<UserCard

    onDelete={deleteUser}

/>
```

Parent owns the state.

<a id="typical-component-layout"></a>
### Typical Component Layout

```tsx
import { useState } from "react";

interface Props {

    title: string;

}

const Example = ({ title }: Props) => {

    // State

    const [expanded, setExpanded] =
        useState(false);

    // Event Handlers

    const handleClick = () => {

        setExpanded(!expanded);

    };

    // Derived Values

    const buttonText = expanded

        ? "Hide"

        : "Show";

    // JSX

    return (

        <div>

            <h2>{title}</h2>

            <button onClick={handleClick}>

                {buttonText}

            </button>

        </div>

    );

};

export default Example;
```

<a id="common-hooks"></a>
### Common Hooks

```tsx
useState()
```

Local state.

```tsx
useEffect()
```

Side effects.

```tsx
useMemo()
```

Cache expensive calculations.

```tsx
useCallback()
```

Cache function references.

```tsx
useRef()
```

Reference DOM elements or persist mutable values.

<a id="typical-page-flow"></a>
### Typical Page Flow

```
Render Component

↓

Read Props

↓

Read State

↓

Calculate Values

↓

Return JSX

↓

React Updates DOM

↓

User Interaction

↓

State Changes

↓

Component Re-renders
```

<a id="react-design-principles"></a>
### React Design Principles

- Components should do one thing well.
- Keep components small and reusable.
- State belongs to the component that owns it.
- Pass data down via props.
- Children communicate upwards using callbacks.
- Never mutate state directly.
- Derive values instead of storing duplicate state.
- Prefer early returns for loading and error states.
- React updates the DOM — you update the state.

<a id="common-component-categories"></a>
### Common Component Categories

A React project naturally evolves into a few different types of components.

#### Page Components

Represent an entire page.

```
pages/

Home.tsx

Users.tsx

Settings.tsx
```

Usually responsible for:

- Fetching data
- Managing page state
- Composing smaller components

#### Presentational Components

Only responsible for displaying UI.

```tsx
<UserCard user={user} />
```

They generally:

- Receive props
- Render UI
- Have little or no state

#### Container Components

Responsible for behaviour.

```tsx
const UsersPage = () => {

    const users = useUsers();

    return (
        <UserList users={users} />
    );

};
```

These coordinate state, API calls and child components.

#### Layout Components

Provide page structure.

```tsx
<AppLayout>

    <Navbar />

    <Sidebar />

    {children}

</AppLayout>
```

Common examples:

- Navigation bars
- Sidebars
- Footers
- Page layouts

#### Reusable UI Components

Designed to be used throughout the application.

```tsx
<Button />

<Modal />

<Card />

<Spinner />

<Input />
```

Think of these as your application's UI toolkit.

#### Custom Hooks

Extract reusable behaviour instead of UI.

```tsx
const users = useUsers();
```

Rather than rendering anything, hooks typically:

- Fetch data
- Manage state
- Share business logic

They always begin with `use`.

### Typical Application Architecture

```
App
│
├── Pages
│     │
│     ├── Components
│     │      │
│     │      ├── UI Components
│     │      └── Layout Components
│     │
│     ├── Hooks
│     │
│     └── Services
│
└── Types
```

Keeping these responsibilities separate makes applications much easier to scale and maintain.