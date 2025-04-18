# TypeScript 

TypeScript is a strongly typed superset of JavaScript that adds static type checking and modern features. Below are some commonly asked TypeScript interview questions with detailed answers.

## What is TypeScript, and why use it? 
TypeScript is a programming language that builds on JavaScript by adding static typing, interfaces, and advanced features to help catch errors during development.

###  Advantages of TypeScript:
- **Static Typing** (catches errors before runtime)
- **Better Code Maintainability**
- **Object-Oriented Programming Features**
- **Great Tooling Support** (IntelliSense, better autocompletion)
- **Works with JavaScript** (Can gradually migrate JS code to TS)

###  Example:
```ts
let message: string = "Hello, TypeScript!";
console.log(message); // ✅ Works fine
// message = 42; ❌ Error: Type 'number' is not assignable to type 'string'
```
## What are TypeScript’s basic types? 
TypeScript provides primitive types, object types, and special types.
| Type   | Example                                                  |
|--------|-------------------------------------------------------   |
| string | `let name: string = "Alice";`                            |
| number | `let age: number = 25;`                                  |
| boolean| `let isValid: boolean = true;`                           |
| array  | `let numbers: number[] = [1, 2, 3];`                     |
| tuple  | `let user: [string, number] = ["Alice", 25];`            |
| enum   | `enum Role { Admin, User }`                              |
| any    | `let data: any = 42;`                                    |
| void   | `function log(): void { console.log("Hello"); }`         |
| never  | `function error(): never { throw new Error("Error!"); }` |

## What is the difference between “any” and “unknown”?
###  any Type
The any type is the most permissive type in TypeScript. It allows a variable to hold any value and bypasses all type checking.

Key Characteristics of any:
No type checking: With any, TypeScript won't check what kind of data the variable holds. It can be reassigned to any other type.
Unsafe: It can lead to runtime errors because TypeScript won’t enforce type safety.
 
### unknown Type
The unknown type is a safer alternative to any. It is also a type that represents any value, but TypeScript enforces type checking when you want to perform operations on it.
Key Characteristics of unknown:
Requires type assertion or checks: Before performing operations on an unknown value, you need to check its type or use type assertions.
Safer: It avoids potential runtime errors by ensuring that any operations on the value are type-safe.

## What is Type Inference in TypeScript?
TypeScript automatically determines the type if not explicitly defined.
```
let count = 10; // TypeScript infers it as 'number'
// count = "Hello"; ❌ Error: Type 'string' is not assignable to type 'number'
```
## What is the difference between an Interface and a Type?
### Interfaces 
An interface is used to define the shape of an object, but it can also be used to define function signatures, callable objects, and more.
Key Characteristics of an Interface:
Extends/Implements: Interfaces can extend other interfaces and be implemented by classes.
Declaring object shapes: Primarily used to describe the shape of objects and their properties.
Merging: If multiple interfaces with the same name are declared, TypeScript will merge them into one.
```
interface Person {
  name: string;
  age: number;
  greet(): void;
}
const john: Person = {
  name: "John",
  age: 30,
  greet() {
    console.log(`Hello, my name is ${this.name}`);
  }
};
john.greet(); // Output: Hello, my name is John
```
Extending Interfaces:
```
interface Employee extends Person {
  position: string;
}
const jane: Employee = {
  name: "Jane",
  age: 25,
  position: "Developer",
  greet() {
    console.log(`Hi, I'm ${this.name} and I work as a ${this.position}`);
  }
};
```
### Type Aliases  
A type alias allows you to define a type that can represent primitives, unions, intersections, tuples, and object shapes. Type aliases are more flexible than interfaces, but they can't be used to define callable types directly or merged.
Key Characteristics of a Type Alias:
Unions and Intersections: Type aliases can represent more complex types using unions (|) and intersections (&).
Flexible: Type aliases can represent not just objects but also primitives, tuples, arrays, etc.
Cannot be merged: Unlike interfaces, type aliases cannot be merged.
```
type Vehicle = {
  brand: string;
  wheels: number;
};
type ElectricVehicle = Vehicle & {
  batteryLife: number;
};
const tesla: ElectricVehicle = {
  brand: "Tesla",
  wheels: 4,
  batteryLife: 300,
};
type StringOrNumber = string | number;

let value: StringOrNumber = "Hello"; // OK
value = 42; // Also OK
```
## What is the difference between == and === in TypeScript?
Operator	Meaning
==	Checks value only (allows type coercion)
===	Checks value and type (strict comparison)
```
console.log(5 == "5");  // true  (Type coercion happens)
console.log(5 === "5"); // false (Different types)
```
## What are Generics in TypeScript? 
Generics allow writing reusable, type-safe components and functions.
  Example:
```
function identity<T>(value: T): T {
  return value;
}
console.log(identity<string>("Hello")); // Output: Hello
console.log(identity<number>(42)); // Output: 42
```
 Generic Interface Example:
  ```
interface Box<T> {
  value: T;
}

let box: Box<number> = { value: 10 };
```
## What are Utility Types in TypeScript? 
Utility types modify existing types to create new ones.
Utility Type	Description
Partial<T>	Makes all properties optional
Required<T>	Makes all properties required
Readonly<T>	Makes properties read-only
Pick<T, K>	Picks specific properties from a type
Omit<T, K>	Removes specific properties from a type
 Example:
```
interface User {
  name: string;
  age: number;
  email: string;
}

let partialUser: Partial<User> = { name: "Alice" }; // ✅ Only "name" is required

let readonlyUser: Readonly<User> = { name: "Alice", age: 25, email: "alice@email.com" };
// readonlyUser.age = 30; ❌ Error: Cannot assign to 'age' because it is a read-only property.
```
## What is Type Narrowing? 
TypeScript uses control flow analysis to narrow a variable’s type.
 Example using typeof check:
```
function print(value: string | number) {
  if (typeof value === "string") {
    console.log("String: ", value.toUpperCase());
  } else {
    console.log("Number: ", value.toFixed(2));
  }
}
```
 Example using in operator:
```
interface Car {
  drive: () => void;
}

interface Boat {
  sail: () => void;
}

function move(vehicle: Car | Boat) {
  if ("drive" in vehicle) {
    vehicle.drive();
  } else {
    vehicle.sail();
  }
}
```
## What is never type in TypeScript? 
never is used for functions that never return or represent impossible values.

  Example:
```
function throwError(message: string): never {
  throw new Error(message);
}
``` 
## What is a mapped type? 
Mapped types allow you to transform object types.
```
type ReadonlyUser = { readonly [K in keyof User]: User[K] };
```
## What are decorators in TypeScript?
Decorators are metadata annotations used in Angular, NestJS, etc.
```
function Log(target: any, key: string) {
  console.log(`Property: ${key}`);
}

class User {
  @Log
  name: string;
}
```

