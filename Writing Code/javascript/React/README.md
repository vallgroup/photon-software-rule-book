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

// ONLY IF NEEDED
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