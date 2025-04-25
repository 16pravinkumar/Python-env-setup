# 📚 Angular Interview Questions and Guide

This guide is designed to help you prepare for Angular-related interview questions, covering topics like component structure, folder hierarchy, and key configuration files.

---

## 1. Can We Use `let` and `const` Inside `AppComponent`?

**Answer**:  
Yes, you can use `let` and `const` within methods inside a component. Here's an example:

### **app.component.ts**
```ts
export class AppComponent {
  title = 'my-angular';

  setLet(): string {
    let data = "Welcome";
    return data;
  }
}
app.component.html
html
Copy
Edit
<h2>{{title}}</h2>
<p>{{setLet()}}</p>
📁 Angular Folder Structure & File Responsibilities
Understanding the Angular folder structure is crucial for real-world development and interviews. Below are common questions and their answers.

1. What is the structure of an Angular application?
Answer:
An Angular app follows a modular structure with the following key folders and files:

src/app/ → Main application logic (components, services, etc.)

assets/ → Static files (images, styles, JSONs)

environments/ → Environment-specific settings (dev, prod)

node_modules/ → Project dependencies

angular.json → Angular workspace configuration

tsconfig.json → TypeScript compiler configuration

2. What does main.ts do?
Answer:
main.ts is the entry point of the Angular application. It bootstraps the root module (AppModule), making the application functional.

ts
Copy
Edit
platformBrowserDynamic().bootstrapModule(AppModule);
3. What is the role of index.html?
Answer:
index.html is the only HTML file in the project. Angular renders the entire application inside the <app-root> tag, which is defined in this file.

4. In what order do Angular files load in the browser?
Answer:
The loading order is as follows:

index.html

main.ts

AppModule (app.module.ts)

AppComponent (app.component.ts)

Templates & Styles (app.component.html, app.component.css)

5. What is tsconfig.json used for?
Answer:
tsconfig.json controls how TypeScript compiles the code. It defines compiler options such as target JavaScript version, module system, and strictness.

Example:

json
Copy
Edit
{
  "compilerOptions": {
    "target": "es2015",
    "module": "es2020",
    "strict": true
  }
}
6. Difference between angular.json, package.json, and tsconfig.json?

File	Purpose
angular.json	Angular CLI configuration (build options, file paths)
tsconfig.json	TypeScript compiler settings (compiling TypeScript to JavaScript)
package.json	Lists project dependencies & scripts
7. What is the purpose of polyfills.ts?
Answer:
polyfills.ts ensures backward compatibility by loading polyfills (such as ES6 features) for older browsers that do not support modern JavaScript features.

8. What’s the difference between AppModule and AppComponent?

Term	Description
AppModule	The root module. It declares the components and imports necessary dependencies.
AppComponent	The root component that contains the UI logic for the app.
9. Where should services be created and provided?
Answer:
Services should be placed in the services/ folder and decorated with @Injectable(). To make them available globally, use providedIn: 'root'.

Example:

ts
Copy
Edit
@Injectable({
  providedIn: 'root'
})
export class DataService {
  // service logic here
}
10. Can we use let, const, or functions directly in a component class?
Answer:
Yes, you can use let, const, and declare functions within a component class.

Example:

ts
Copy
Edit
export class AppComponent {
  showMsg(): string {
    let msg = "Hello";
    return msg;
  }
}
11. What is the use of environment.ts?
Answer:
environment.ts is used to store environment-specific settings like API URLs. These values change based on whether the app is running in development or production.

Example:

ts
Copy
Edit
export const environment = {
  production: false,
  apiUrl: 'http://localhost:3000'
};
