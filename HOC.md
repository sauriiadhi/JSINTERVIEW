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
