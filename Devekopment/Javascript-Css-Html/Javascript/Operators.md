#### Rest operators


```js
const rest = (...argumentos) => {
	console.log(argumentos);
}

rest(1,2,3);
````

- Rest siempre debe ir al final.

#### Destructuring operators

```js
const obj = {
	a:1 , b: 2, c: 3, d: 4, e: 5
}

//Destructuring objects
const { a, b, ...restobj } = obj;
console.log(a,b, restobj)

const arr = [1,2,3,4,5];

//Destructuring arrays
const [a,b,c,d,e] = arr;
console.log(a,b,c,d)

const useState = () => ['valor', () => {}];
const [valor, setValor] = useState();
console.log(valor, setValor);

````


#### Funciones de arreglos

``` js
	//Filter
	const arr = [0,1,2,3,4,5];

	const r = arr.filter((el,i) => {
		console.log(i)
		return el > 2
	})
	
	console.log(r);

	//Map
	const arr1 = arr.map((el) => {
		return `<h1> ${el*2} </h1>`;
	})
	console.log(arr1);

	const users = [
		{ id: 1, name : 'Fernando'},
		{ id: 2, name : 'Andres'},
		{ id: 3, name : 'Nathaly'},
		{ id: 4, name : 'Maria'},
	];

	const mapped = users.map((users) => `<h1> ${users.name} </h1>`)
	console.log(mapped);

	//reduce
	const arr2 = arr.reduce((acumulador, el, index)=> acc+el ,0)
	console.log(arr2);
```