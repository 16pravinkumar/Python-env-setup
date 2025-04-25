<h2>{{fun("SS")}}</h2>
<p>{{currDate }}</p>



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

**Example**: <br>
Interpolation: <br>
`<h1>{{ title }}</h1>` <br>
Property Binding: <br>
`<img [src]="imageUrl" alt="Angular Image">` <br>

```markdown
# 📘 Angular CLI – Interview Questions & Answers

A curated list of commonly asked Angular CLI interview questions with concise answers and command examples. Useful for freshers and professionals alike.

---

## 1️⃣ What is Angular CLI?
**Answer:**  
Angular CLI (Command Line Interface) is a powerful tool to initialize, develop, scaffold, and maintain Angular applications directly from the terminal.

---

## 2️⃣ How do you create a new Angular project?
**Command:**
```bash
ng new my-app
```
**Answer:**  
This command creates a new Angular workspace with default configuration. It asks for options like adding routing and selecting a stylesheet format (CSS, SCSS, etc).

---

## 3️⃣ How to serve an Angular app locally?
**Command:**
```bash
ng serve
```
**Answer:**  
Compiles the app and starts a development server at `http://localhost:4200`. It watches file changes and reloads automatically.

---

## 4️⃣ How to generate a new component using CLI?
**Command:**
```bash
ng generate component component-name
# or shortcut
ng g c component-name
```
**Answer:**  
Generates a new component and automatically declares it in `app.module.ts`.

---

## 5️⃣ How to generate a new service?
**Command:**
```bash
ng generate service service-name
```
**Answer:**  
Creates a service with an `@Injectable` decorator and a test file (`.spec.ts`) by default.

---

## 6️⃣ How to build the project for production?
**Command:**
```bash
ng build --prod
```
**Answer:**  
Generates a highly optimized build with minified code, Ahead-of-Time (AOT) compilation, and tree shaking.

---

## 7️⃣ What does `ng lint` do?
**Answer:**  
Analyzes your code using linting rules defined in `angular.json` and `tslint.json`.

---

## 8️⃣ What is `ng test` used for?
**Command:**
```bash
ng test
```
**Answer:**  
Runs unit tests in a Karma test runner and opens a browser for results.

---

## 9️⃣ How to add Angular Material to a project?
**Command:**
```bash
ng add @angular/material
```
**Answer:**  
Adds Angular Material and configures themes, animations, and fonts automatically.

---

## 🔟 How to update Angular to the latest version using CLI?
**Command:**
```bash
ng update @angular/cli @angular/core
```
**Answer:**  
Updates CLI and Core dependencies to the latest compatible version for your project.

---

## 1️⃣1️⃣ Difference between `ng build` and `ng serve`?

| Command     | Purpose                            | Notes                             |
|-------------|-------------------------------------|-----------------------------------|
| `ng build`  | Compiles app to `dist/` folder      | Used for production deployment    |
| `ng serve`  | Starts a dev server at `localhost` | Used for development & live reload|

---

## 1️⃣2️⃣ How to create a module using CLI?
**Command:**
```bash
ng generate module my-module
# or shortcut
ng g m my-module
```
**Answer:**  
Creates a new module and prepares it for lazy loading or modular architecture.

---

## 1️⃣3️⃣ What is the purpose of `--routing` flag in `ng new`?
**Answer:**  
Adds routing support with an automatically generated `app-routing.module.ts` file.

---

## 1️⃣4️⃣ How to generate a directive?
**Command:**
```bash
ng generate directive directive-name
# or shortcut
ng g d directive-name
```
**Answer:**  
Creates a custom directive and registers it in the closest module.

---

## 1️⃣5️⃣ How to create a service without the test file?
**Command:**
```bash
ng generate service my-service --skip-tests
```
**Answer:**  
Prevents the generation of a `.spec.ts` test file along with the service.
```

# 🧩 Angular Components – Interview Questions & Answers

A component is the core building block of Angular applications. Below is a detailed list of commonly asked questions related to Angular components, with clear answers and code examples to help you prepare for interviews.

---

## 1️⃣ What is a component in Angular?

**Answer:**  
A component controls a specific part of the user interface (UI). It consists of:

- **TypeScript (.ts)** – Contains logic, data, and behavior
- **HTML (.html)** – Defines the template/view
- **CSS/SCSS (.css/.scss)** – Styles the component

---

## 2️⃣ How do you generate a new component using Angular CLI?

**Command:**
```bash
ng generate component component-name
# or
ng g c component-name
Answer:
This command creates a new folder containing .ts, .html, .css, and .spec.ts files, and updates the AppModule automatically.

3️⃣ What are the key decorators in a component?
Answer:
The @Component() decorator is used to define an Angular component and its metadata like selector, template, and styles.

Example:

ts
Copy
Edit
@Component({
  selector: 'app-hero',
  templateUrl: './hero.component.html',
  styleUrls: ['./hero.component.css']
})
export class HeroComponent {}
4️⃣ What is the purpose of the selector property?
Answer:
The selector defines the custom HTML tag that is used to render the component in templates.

Example Usage:

html
Copy
Edit
<!-- If selector is 'app-hero' -->
<app-hero></app-hero>
✅ Bonus Tip: Component Structure Overview
bash
Copy
Edit
src/
├── app/
│   ├── hero/
│   │   ├── hero.component.ts      # Component logic
│   │   ├── hero.component.html    # Component view
│   │   ├── hero.component.css     # Component styles
│   │   └── hero.component.spec.ts # Unit tests
