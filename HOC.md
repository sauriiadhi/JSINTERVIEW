## higher-order component (HOC)
A higher-order component (HOC) is an advanced technique in React for reusing component logic.Concretely, **a higher-order component is a function that takes a component and returns a new component.**

### Example
```javascript
//Comp1.js
const  Comp1  =  (props, ref)  =>  {
	return  (<div ref={ref}>
		Hey  I am comp2 width:  {props.width}  &  {props.randno}
		</div>);
	};
export  default  WithDimension(forwardRef(Comp1));

//withDimension.js
const withDimension =  (Element)  =>  {
	function  WithDimensions(props)  {
		const  [width, setWidth]  = useState(null)
		const  [height, setHeight]  = useState(null)
		const compRef = useRef()
		useEffect(()  =>  {
			if  (compRef.current)  {
			setWidth(compRef.current.offsetWidth)
			setHeight(compRef.current.offsetHeight)}
		},  [])
		return  <Element ref={compRef} 
				height={height} 
				width={width}  
				{...props} />
	}
	return  WithDimensions;
};
export  default withDimension;
```
##  Render Props Pattern

The Render Props pattern is a powerful tool in React for creating flexible and reusable components. By passing functions as props, you can dynamically control what a component renders based on its state. This pattern helps in separating concerns and makes your codebase more maintainable and scalable. In this exercise, you have implemented and understood how to use the Render Props pattern to create dynamic UI components.

```javascript
import  Input  from  "./Input";
export  default  function  App()  {
	const showValue =  (value)  =>  <b>The value is {value}</b>;
	const multiplyByTen =  (value)  => <>The multiplied value is {value *  10}</>;
	return  (
		<div className="App">
			<Input renderTextBelow={showValue} />
			<br />
			<Input renderTextBelow={multiplyByTen} />
		</div>
	);
}
//Input.js
import  { useState }  from  "react";
const  Input  =  (props)  =>  {
	const  [value, setValue]  = useState(null);
	const handleChange =  (e)  =>  {
		setValue(e.target.value);
	};
	return  (<>
		<input value={value} onChange={handleChange} />
		<br />
		{props.renderTextBelow(value)}
		</>
	);
};
export  default  Input;
```
