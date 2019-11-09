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
} from './styles'
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

## Alignment

```jsx
// bad
<Foo superLongParam="bar"
     anotherSuperLongParam="baz" />

// good
<Foo
  superLongParam="bar"
  anotherSuperLongParam="baz"
/>

// if props fit in one line then keep it on the same line
<Foo bar="bar" />

// children get indented
<Foo
  superLongParam="bar"
  anotherSuperLongParam="baz"
>
  <Bar />
</Foo>

// bad
{showButton &&
  <Button />
}

// bad
{
  showButton &&
    <Button />
}

// good
{showButton
	&& <Button />}

// good
{showButton
	&& (
		<Button />
	)}

// good
{showButton && <Button />}
```

## Components vs Helpers

If the component you are writing has its own state and logic, then it should be a component.

If the component you are writing simply passes down props and has minimal logic then it should be a helper function.

Components have the following structure:  
```
- Components
  |- MyComponent
    |- index.js               // export default MyComponent
    |- styles.js              // styled-components, described above
    |- SupportingComponent.js // Any component built for MyComponent
    |- other supporting files
```

Helpers have the following structure:  
```
- Helpers
  |- MyHelper.js // global helpers. intended to be used by any component

// or
- Helpers
  |- Topic
    |- index.js // helper related to a specific topic. Like Money helpers to format money, or perform quick financial calculations.
```

## Use of SASS

SASS will always be used on every project. Global styles for typography, html elements, and CSS resets will all be declared in SASS. Styled components are used to leverage props and other React features while still taking advantage of those global styles set by SASS.

For example, I can set all typography styles using SASS like this:  
```scss
/* TYpography */

h1 {
	font-size: 2.125em;
	margin-top: 0.5em;
	margin-bottom: 0.5em;
	color: $black;
}

h2 {
	font-size: 1.75em;
	margin-top: 2.5em;
	margin-bottom: 1.25em;
}

h3 {
	font-size: 1.5em;
	margin-top: 2em;
	margin-bottom: 1em;
}

h4 {
	font-size: 1.25em;
	font-weight: 700;
	margin-top: 1.75em;
	margin-bottom: 1em;
}

h5 {
	font-size: 1.175em;
	font-family: Open Sans;
	font-weight: 700;
	margin-top: 1em;
	margin-bottom: 1em;
}

p {
	font-size: 1.125em;
	margin-top: 1em;
	margin-bottom: 1em;
	line-height: 1.45;
}

//...
```

Then, in my styled components I output my typography styles like so:
```jsx
import styled from 'style-components'

export const H1 = styled.h1.attrs(props => ({
	// set the color dynamically
	fontColor: Colors[ props.color ] || Colors.darkGray
}))`
	color: ${props => props.fontColor};
`

export const H2 = styled.h2.attrs(props => ({
	defaultProp: props.someProp || 'my own value',
}))`
	// if no styles are changed the sass styles above
	// will control this component
`

export const H3 = styled.h3.attrs(props => ({}))``

export const H4 = styled.h4.attrs(props => ({}))``

export const H5 = styled.h5.attrs(props => ({}))``

export const H6 = styled.h6.attrs(props => ({}))``

export const Paragraph = styled.p.attrs(props => ({
	large: props.large || false
}))`
	// make changes to the current styles based on props passed
	text-transform: ${props => props.large ? 'uppercase' : 'none'};
	font-size: ${props => props.large ? '1.5em' : '1em'};
	// You can even add some responsive rules specific to paragraph
	@media screen and (min-width: 600px) {
		font-size: ${props => props.large ? '2em' : '1em'};
	}
`
```