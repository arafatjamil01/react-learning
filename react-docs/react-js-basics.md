### React file system

`public` folder contains static files like images, fonts, etc.
`src` folder contains all the react codes.

#### Returning more than one element from a component

The `return` keyword in React can only return one element. When in one line, the return statement is written directly after. When multiple lines, parentheses are used. Iff you want to return more than one element, you need to wrap them inside a `div` tag, an array or a React fragment.

```javascript
import React from 'react';

function App() {
  return (
 <div>
   <h1>Heading 1</h1>
   <h2>Heading 2</h2>
 </div>
  );
}

export default App;
```

The fragment import way -

```javascript
import React, { Fragment } from 'react';

function App() {
  return (
 <Fragment>
   <h1>Heading 1</h1>
   <h2>Heading 2</h2>
 </Fragment>
  );
}

export default App;
```

The shortcut fragment way -

```javascript
import React from 'react';

function App() {
  return (
 <>
   <h1>Heading 1</h1>
   <h2>Heading 2</h2>
 </>
  );
}

export default App;
```
We can simply use <></> instead of <React.Fragment></React.Fragment> as a shorthand, this will also help us to avoid additional `<div>` in react.

### React Components

Components are the building blocks of a React application. A component is a small, reusable piece of code that is responsible for one job. That job is often to render some HTML.

A full layout is broken into reusable components, for example - a navigation section can be broken into: logo, menu, search bar, etc.

### useState hook for managing state

The virtual dom is a representation of the actual dom. React uses the virtual dom to keep track of changes in the actual dom. When a change is made in the actual dom, React compares the virtual dom with the actual dom and updates the actual dom with the changes.

To make changes to a state of a component, we use the `useState` hook. The `useState` hook returns an array with two elements. The first element is the state itself and the second element is a function that is used to update the state.

```javascript
import React, { useState } from 'react';

function App() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <h1>{count}</h1>
      <button onClick={() => setCount(count + 1)}>Click me</button>
    </div>
  );
}

export default App;
```
The above code means, the initial count will be 0, then with each click on the button, the count will be incremented by 1. If we use `setCount(count + 2)`, the count will be incremented by 2 with each click.

Now, if the same component is rendered twice, two components will be created and each component will have its own state. The state of one component will not affect the state of the other component.

### Using props, using TypeScript interface

Props are used to pass data from one component to another. Props are immutable, i.e - they cannot be changed. Props are passed from parent to child component.

```javascript
import React from 'react';

interface Props {
  name: string;
}

// It can be passed as props: Props, or destructured as { name }: Props, accessing the properties will differ accordingly, e.g - props.name or name

function App({ name }: Props) {
  return (
    <div>
      <h1>{name}</h1>
    </div>
  );
}

export default App;
```

### Props vs State

<!-- Write a table in md -->

| Props | State |
| ----- | ----- |
| Immutable | Mutable |
| Like function arguments | Like variables declared in a function |
| Passed from parent to child component | Declared and managed within a component |
| Can be accessed by the child component | Cannot be accessed by the child component |

When a state or props is changed, the component is re-rendered.

### Passing children to a component

```javascript
import {ReactNode} from 'react';

interface Props {
  name: string;
  children: ReactNode;
}

function Child({ name, children }: Props) {
  return (
    <div>
      <h1>{name}</h1>
      {children}
    </div>
  );
}

export default Child;
```
The above Child component can be called like this -

```javascript
import React from 'react';
import Child from './Child';

function App() {
  return (
    <div>
      <Child name="John Doe">
        <p>This is a child</p>
      </Child>
    </div>
  );
}

export default App;
```

### Making props optional or making it definite

```javascript
import React from 'react';

interface Props {
  name: string;
  age?: number;
}
```
Adding '?' after the property name makes it optional.

```javascript
import React from 'react';

interface Props {
  name: string;
  age: number | undefined;
  skin: 'dark' | 'light' | 'brown'; 
}
```
In the above example, age can be either a number or undefined. skin can be either dark, light or brown.

Adding different type of value or different strings will throw an error.

### Default value for props

```javascript
import React from 'react';

interface Props {
  name: string;
  age?: number;
}

function App({ name, age = 20 }: Props) {
  return (
    <div>
      <h1>{name}</h1>
      <h2>{age}</h2>
    </div>
  );
}

export default App;
```
In the above example, if the age is not passed, it will be 20 by default.