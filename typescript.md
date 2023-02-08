### Types

#### Functions

##### contextual typing

```typescript
const names = ["Tdergouzi", "Ted"];

// Contextual typing for function
names.forEach(function(s){
    console.log(s.toUpperCase())
})

/*
"TDERGOUZI"
"TED"
*/

// Contextual typing for arrow function
names.forEach((s) => {
    console.log(s.toLowerCase())
})

/*
"tdergouzi"
"ted"
*/
```

Even though the parameter  `s`  didn't have a type annotation, TypeScript used the types of the `forEach` fucntion , ==along with== ==inferred== type of the array, to determine the type `s` will have.

This process is called contextual typing because the context that the function occurred within ==informs== what type it should have.



#### Object Types

##### Optional Properties

Object types can also specify that some or all of their properties are optional. To do this, add a `?` after the property name:

```typescript
function printName(obj: {first: string; last?: string}) {
  console.log(obj.last.toupperCase())
  // Error: 'undefined'
  
  if (obj.last !== undefined) {
    console.log(obj.last.toUpperCase())
    // OK
  }
  
  // A safe alternative using modern JavaScript syntax;
  console.log(obj.last?.toUpperCase())
}
```



##### Union Types

TypeScripts will only allow an operation if it is valid for valid for every member of the union.

```typescript
function printId(id: number | string){
  console.log(id.toUpperCase())
  // Property 'toUpperCase' does not exist on type 'string | number'.
  // Property 'toUpperCase' does not exist on type 'number'.
}
```

The solution is to ==narrow== the union with code.



##### Differences Between Type Aliases and Interfaces

Type aliases and interfaces are very similar, and in many cases you can choose  between them freely. Almost all features of an `interface` are available in `type`, the key distinction is that a type cannot be cannot be re-opened to add new properties vs an interface which is always extendable.

```typescript
interface Window {
  title: string
}

interface Window {
  ts: TypeScriptAPI
}

const src = `const a = "Hello World"`
window.ts.transpileModule(src, {})

type Window = {
	title: string
}

type Window = {
  ts: TypeScriptAPI
}

// Error: Duplicate identifier 'Window'.
```



##### ==Literal== Types

In addition to the general types `string` and `number`, we can refer to specific strings and numbers in type positions.

```typescript
function printText(s: string, alignment: "left" | "right") {
  // ...
}

printText("helloworld", "left")
printText("helloworld", "centre") // Error
```



### Object Types

#### Extending Types

```typescript
interface BasicAddress {
  name?: string;
  street: string;
  city: string;
  country: string;
  postalCode: string;
}
 
interface AddressWithUnit extends BasicAddress {
  unit: string;
}
```

The `extends` keyword on an `interface` allows us to effectinvely copy members from other named types, and add whatever new members we want.



#### Intersectin Types

An intersection type is defined using th e `&` operator.

```typescript
interface Colorful {
  color: string;
}
interface Circle {
  radius: number;
}
 
type ColorfulCircle = Colorful & Circle;
```

```typescript
function draw(circle: Colorful & Circle) {
  console.log(`Color was ${circle.color}`);
  console.log(`Radius was ${circle.radius}`);
}

// Ok
draw({color: "blue", radius: 42})

// Error
draw({color: "blue", size: 42})
```



##### Interfaces vs Intersections

The principle difference between the two is how conflicts are handled, and that difference is typically one of the main reasons why you'd pick one over the other between an interface and a type alias of an intersection type.



#### Generic Type

We can make a ==generic== `Box` type whick declares a type parameter.

```typescript
interface Box<Type> {
  contents: Type;
}
```

**When we refer to `Box` , we have to give a type argument in place of `Type`.**

```typescript
let box: Box<string>;
```

Think of `Box` as a template for a real type, where `Type` is a placeholder that will get replaced with some other type. When TypeScript sees `Box<string>`,it will replace every instance of `Type` in `Box<Type>` with `string`, and end up working with something like `{contents: string}`. In other words, `Box<string>` and our earlier `StringBox` work identically.

```typescript
interface Box<Type> {
  content: Type;
}

interface StringBox {
  contents: string;
}

let boxA: Box<string> = {contents: "hello"}
boxA.contents
```

`Box` is reusable in the `Type` can be substituted with anything. That means that when we need a box for a new type, we don't need to declare a new `Box` type at all.

```typescript
interface Box<Type> {
  contents: Type;
}

interface Apple {
  // ....
}

// Same as '{contents: Apple}'
type AppleBox = Box<Apple>
```



### Classes

Waiting...