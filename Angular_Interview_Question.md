# 📚 Angular Interview Questions and Guide

This guide is designed to help you prepare for Angular-related interview questions, covering topics like component structure, folder hierarchy, and key configuration files.

---

## 1. Can We Use `let` and `const` Inside `AppComponent`?

**Answer**:  
Yes, you can use `let` and `const` within methods inside a component. Here's an **Example**:

### **app.component.ts**
```ts
export class AppComponent {
  title = 'my-angular';

  setLet(): string {
    let data = "Welcome";
    return data;
  }
}
```

### **app.component.html**
```ts
<h2>{{title}}</h2>
<p>{{setLet()}}</p>

```
# 2. 📁 Angular Folder Structure & File Responsibilities
Understanding the Angular folder structure is crucial for real-world development and interviews. Below are common questions and their answers.

1. What is the structure of an Angular application? <br>
**Answer**:
An Angular app follows a modular structure with the following key folders and files:
```ts
src/app/ → Main application logic (components, services, etc.)

assets/ → Static files (images, styles, JSONs)

environments/ → Environment-specific settings (dev, prod)

node_modules/ → Project dependencies

angular.json → Angular workspace configuration

tsconfig.json → TypeScript compiler configuration
```
2. What does main.ts do? <br>
**Answer**:
`main.ts` is the entry point of the Angular application. It bootstraps the root module (AppModule), making the application functional.
`platformBrowserDynamic().bootstrapModule(AppModule);`

4. What is the role of `index.html`? <br>
**Answer**:
`index.html` is the only HTML file in the project. Angular renders the entire application inside the `<app-root>` tag, which is defined in this file.

5. In what order do Angular files load in the browser? <br>
**Answer**:
The loading order is as follows:
```ts
index.html

main.ts

AppModule (app.module.ts)

AppComponent (app.component.ts)

Templates & Styles (app.component.html, app.component.css)
```

5. What is tsconfig.json used for? <br>
**Answer**:
`tsconfig.json` controls how TypeScript compiles the code. It defines compiler options such as target JavaScript version, module system, and strictness.

**Example**:
```ts
{
  "compilerOptions": {
    "target": "es2015",
    "module": "es2020",
    "strict": true
  }
}
```

6. Difference between `angular.json`, `package.json`, and `tsconfig.json`? <br>
**Answer**:
File	Purpose
`angular.json`	Angular CLI configuration (build options, file paths)
`tsconfig.json`	TypeScript compiler settings (compiling TypeScript to JavaScript)
`package.json`	Lists project dependencies & scripts

8. What is the purpose of `polyfills.ts`? <br>
**Answer**:
`polyfills.ts` ensures backward compatibility by loading polyfills (such as ES6 features) for older browsers that do not support modern JavaScript features.

9. What’s the difference between AppModule and AppComponent? <br>
**Answer**:
Term	Description
AppModule	The root module. It declares the components and imports necessary dependencies.
AppComponent	The root component that contains the UI logic for the app.

10. Where should services be created and provided? <br>
**Answer**:
Services should be placed in the `services/ folder` and decorated with `@Injectable()`. To make them available globally, use providedIn: `'root'`.

**Answer**:
```ts
@Injectable({
  providedIn: 'root'
})
export class DataService {
  // service logic here
}
```

11. Can we use let, const, or functions directly in a component class? <br>
**Answer**:
Yes, you can use let, const, and declare functions within a component class.

**Example**:
```ts
export class AppComponent {
  showMsg(): string {
    let msg = "Hello";
    return msg;
  }
}
```

12. What is the use of `environment.ts`? <br>
**Answer**:
environment.ts is used to store environment-specific settings like API URLs. These values change based on whether the app is running in development or production.

**Example**:
```ts
export const environment = {
  production: false,
  apiUrl: 'http://localhost:3000'
};

```


# Interview Questions on Interpolation in Angular

1. What is interpolation in Angular? <br>
**Answer**: Interpolation in Angular is a mechanism for binding data from the component to the template. It allows dynamic content to be inserted into the HTML by wrapping the expression in double curly braces {{ expression }}.

**Example**:
```ts
export class AppComponent {
  title = 'Angular Interpolation';
}
```
`<h1>{{ title }}</h1> <!-- Output: Angular Interpolation -->`
2. What are the limitations of interpolation in Angular? <br>
**Answer**: While interpolation is a simple and effective way to bind data, it comes with a few limitations:

Cannot use expressions with method calls or complex logic: Interpolation is used to display simple expressions or values. You cannot perform complex expressions, loops, or method calls directly inside {{ }}.
**Incorrect**:

`<h1>{{ calculateTotalPrice() }}</h1> <!-- This won't work -->`
Solution: Use methods inside the component class and bind the results to variables that can be interpolated.
**Correct**:

```ts

export class AppComponent {
  totalPrice = this.calculateTotalPrice();

  calculateTotalPrice() {
    return 100;
  }
}
```

3. Can we bind to HTML attributes using interpolation? <br>
**Answer**: No, interpolation is only for text content and does not work for binding to HTML attributes like href, src, etc. To bind attributes, you need to use property binding.

**Example** of Interpolation:
`<h1>{{ title }}</h1> <!-- Works for text -->`
**Example** of Property Binding (For HTML Attributes):
`<a [href]="url">Go to URL</a> <!-- Property binding is used for attributes -->`

4. What happens if the interpolated expression evaluates to null or undefined? <br>
**Answer**: If the interpolated expression evaluates to null or undefined, Angular will render an empty string. This avoids breaking the HTML or causing errors in the view.

**Example**:
```ts
export class AppComponent {
  data: string | null = null;
}

<h1>{{ data }}</h1> <!-- Output: empty string (no text) -->

```
5. Can interpolation be used for event binding in Angular? <br>
**Answer**: No, interpolation cannot be used for event binding in Angular. For event binding, you need to use the () syntax.

**Example** of Event Binding:

`<button (click)="onClick()">Click Me</button> <!-- Correct way to bind events -->`
6. Can we perform complex calculations inside interpolation? <br>
**Answer**: No, you cannot perform complex calculations or invoke methods that modify the component state directly inside interpolation. Instead, you should calculate the result inside the component class and bind to that result.

**Example** of Correct Use:
```ts
export class AppComponent {
  number1 = 5;
  number2 = 10;
  
  getSum() {
    return this.number1 + this.number2;
  }
}

`<h1>{{ getSum() }}</h1> <!-- This works, but only for simple calculations -->`
```
7. Can we apply filters or pipes inside interpolation? <br>
**Answer**: 
Yes, Angular pipes can be applied within interpolation to transform the data before displaying it.

**Example**:
```ts
export class AppComponent {
  currentDate = new Date();
}

<p>{{ currentDate | date:'short' }}</p> <!-- Use a pipe to format the date -->
```
8. What is the difference between interpolation and property binding in Angular? <br>
**Answer**:
Interpolation `({{ expression }})` is used to insert data into the text content of HTML elements.
Property binding `([property])` is used to set values of HTML attributes or DOM properties.

**Example**:
Interpolation:
`<h1>{{ title }}</h1>`
Property Binding:
`<img [src]="imageUrl" alt="Angular Image">`

