# Writing React at Photon Software

## Hooks & Functions vs Classes

Whenever possible use Hooks and function (NO arrow functions) components over classes. If you cannot accomplish something with Hooks and Function components, then use a class.

```jsx

// GOOD
function Example() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}

// BAD
function Example = () => {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}

// GOOD, ONLY IF NEEDED
class Example extends React.Component {
  //...

  render() {
  	return <div>{this.state.count}</div>;
  }
}

// BAD
const Example Reac.tcreateClass({
  //...

  render() {
  	return <div>{this.state.count}</div>;
  }
})
```

## Use Styled Components over SASS

Always use [style-components](https://www.styled-components.com/docs/basics) over SASS files. 

```jsx
// instead of this
import './SomeFile.scss'
//...
function Example({firstName, lastName}) {
  //...
  return (<Fragment>
    <div className={"firstName"}>
    	{firstName}
    </div>
    <div className={"lastName"}>
    	{lastName}
    </div>
  </Fragment>);
}

// Write this
import {
	FirstName,
	LastName
} from './components'
//...
function Example({firstName, lastName}) {
  //...
  return (<Fragment>
    <FirstName>
    	{firstName}
    </FirstName>
    <LastName>
    	{lastName}
    </LastName>
  </Fragment>);
}

// And your componenets file looks like this
import styled from 'styled-components'

export const FirstName = styled.div`
	// some sasss
`

export const LastName = styled.div`
	// some sasss
`
```