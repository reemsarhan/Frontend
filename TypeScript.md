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
Feature	any	unknown
Type Safety	🚨 No type checking	✅ Safe
Assignability	Can be assigned to anything	Must be type-checked before use
  Example of unknown enforcing type safety:
```
let value: unknown = "Hello";

// Directly assigning to a string variable (❌ Error)
let message: string = value; // Type error!

// Using type checking (✅ Works)
if (typeof value === "string") {
  let message: string = value;
}
```
## What is Type Inference in TypeScript?
TypeScript automatically determines the type if not explicitly defined.
```
let count = 10; // TypeScript infers it as 'number'
// count = "Hello"; ❌ Error: Type 'string' is not assignable to type 'number'
```
## What is the difference between an Interface and a Type?
Feature	interface	type
Usage	Object structure	Can be used for anything
Extensibility	✅ Can be extended	❌ Cannot be extended
Merging	✅ Supports merging	❌ No merging
  Example of Interface & Type:
```
// Interface (extends and merges)
interface User {
  name: string;
  age: number;
}

interface Admin extends User {
  role: string;
}

// Type Alias (Cannot extend)
type Employee = {
  name: string;
  age: number;
};
type Manager = Employee & { department: string };
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

