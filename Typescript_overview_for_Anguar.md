# TypeScript for Angular: Essential Topics

## 📘 Introduction
TypeScript is a **superset of JavaScript** that adds optional static typing. Angular is built with TypeScript and uses its features extensively to ensure scalable and maintainable code. This guide covers the **essential TypeScript topics** you'll encounter while working with Angular.

---

## 📋 Table of Contents
1. [Basic Types](#basic-types)
2. [Interfaces](#interfaces)
3. [Classes & Objects](#classes--objects)
4. [Functions](#functions)
5. [Generics](#generics)
6. [Enums](#enums)
7. [Decorators](#decorators)
8. [Modules & Namespaces](#modules--namespaces)
9. [Type vs Interface](#-type-vs-interface-in-typescript)

---

## 🔤 Basic Types
TypeScript introduces static typing to JavaScript, allowing for better tooling and fewer bugs.

```ts
let name: string = "Pravin";
let age: number = 24;
let isActive: boolean = true;
let userIds: string[] = ["1", "2", "3"];
let person: { name: string; age: number } = { name: "John", age: 30 };
```

---

## 📐 Interfaces
Interfaces define the shape of an object. Angular uses interfaces in services, data models, and more.

```ts
interface User {
  name: string;
  age: number;
}

const user: User = {
  name: "Pravin",
  age: 24
};

interface Admin extends User {
  role: string;
}

const admin: Admin = {
  name: "Admin",
  age: 30,
  role: "Admin"
};
```

---

## 🧱 Classes & Objects
Classes are the foundation of Angular components and services.

```ts
class Person {
  name: string;
  age: number;

  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }

  greet(): void {
    console.log(`Hello, my name is ${this.name}`);
  }
}

const person = new Person("John", 25);
person.greet(); // Hello, my name is John



giving default value 
class MakeData {
  constructor(
    public name: string,
    public gender: string = "Other",
    public age: number
  ) {
    if (!gender) {
      this.gender = "other";
    }
  }
}

let m1 = new MakeData("Pr", "", 12);
console.log(m1);
```

## Example for private
```ts
class MakeData {
  constructor(
    private name: string,
    public gender: string = "Other",
    public age: number
  ) {}


  getName(){
    return this.name
  }

  setName(name: string): void {
    this.name = name;
  }


}

class MakeMoreData extends MakeData {
  constructor(name: string,gender:string, age: number,public extraData: string) {
    super(name,gender,age)
  }

  showAllData():void{
    console.log(`Name: ${this.getName()}, Gender: ${this.gender}, Age: ${this.age}, Extra: ${this.extraData}`);
  }
}

let m1 = new MakeMoreData("Pr","M",52,
'finalDara'
);
m1.setName("NEwNAjs")
m1.showAllData()
```

---

## 🔧 Functions
Functions in TypeScript can define parameter and return types.

```ts
function add(a: number, b: number): number {
  return a + b;
}

console.log(add(2, 3)); // 5

function greet(name: string, greeting: string = "Hello"): void {
  console.log(`${greeting}, ${name}!`);
}

greet("Pravin"); // Hello, Pravin!
greet("Pravin", "Good Morning"); // Good Morning, Pravin!
```

---

## 🔁 Generics
Generics provide flexibility while maintaining type safety. Used frequently in services, components, and utility functions.

```ts
function identity<T>(arg: T): T {
  return arg;
}

const result = identity("Hello, TypeScript!");

class Box<T> {
  value: T;
  constructor(value: T) {
    this.value = value;
  }

  getValue(): T {
    return this.value;
  }
}

const box = new Box<number>(100);
console.log(box.getValue()); // 100
```

---

## 🔢 Enums
Enums allow a variable to be one of the predefined constants.

```ts
enum Role {
  Admin = "Admin",
  User = "User",
  Guest = "Guest"
}

let userRole: Role = Role.Admin;
console.log(userRole); // Admin
```

---

## 🎯 Decorators
Decorators are metadata annotations used extensively in Angular (`@Component`, `@Injectable`, etc).

```ts
function log(target: any, key: string) {
  console.log(`Method ${key} was called`);
}

class Person {
  @log
  greet(): void {
    console.log("Hello!");
  }
}

const person = new Person();
person.greet();
```

Angular example:

```ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-hello',
  template: '<h1>Hello, World!</h1>',
})
export class HelloComponent {}
```

---

## 📦 Modules & Namespaces
Angular is based on modular development. TypeScript supports this with ES modules and namespaces.

### Module Example:
```ts
// user.ts
export class User {
  name: string;
  constructor(name: string) {
    this.name = name;
  }
}

// main.ts
import { User } from './user';
const user = new User("Pravin");
console.log(user.name);
```

### Namespace Example:
```ts
namespace Shapes {
  export class Circle {
    constructor(public radius: number) {}
  }

  export class Square {
    constructor(public side: number) {}
  }
}

const circle = new Shapes.Circle(10);
console.log(circle.radius); // 10
```

---

## 🔑 Type vs Interface in TypeScript

| Feature                        | `interface`                                                                 | `type`                                                                 |
|-------------------------------|------------------------------------------------------------------------------|------------------------------------------------------------------------|
| **Basic Usage**               | `interface User { name: string }`                                           | `type User = { name: string }`                                        |
| **Extending/Inheritance**     | ✅ `interface Admin extends User {}`                                        | ✅ `type Admin = User & { role: string }`                              |
| **Declaration Merging**       | ✅ `interface User { age: number }` (merges with same name)                 | ❌ Cannot redeclare                                                    |
| **Unions**                    | ❌ Not supported                                                             | ✅ `type Role = 'admin' \| 'user'`                                     |
| **Intersections**             | ❌ Not supported directly                                                    | ✅ `type Person = Admin & User`                                        |
| **Primitives**                | ❌ Not supported                                                             | ✅ `type ID = string \| number`                                        |
| **Tuples / Arrays / Functions** | ❌ Limited support                                                          | ✅ `type Point = [number, number]`, `type Fn = (a: number) => void`    |
| **Implements / Classes**      | ✅ `class Person implements User {}`                                        | ⚠️ Can’t implement `type` directly                                     |
| **Performance (large scale)** | ✅ Slightly better in large object hierarchies                              | ⚠️ Slightly slower in deeply nested types                             |

---

## ✅ Conclusion
Understanding these TypeScript fundamentals will give you a strong foundation for building robust Angular applications. As Angular heavily relies on these features, mastering them will help you write clean, maintainable, and scalable code.

Happy coding! 🚀
