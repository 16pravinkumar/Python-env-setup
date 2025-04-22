# 🚀 Getting Started with Angular

This guide will help you install Angular CLI and create your first Angular app step-by-step using simple commands.

---

## ✅ Step 1: Install Angular CLI

Open your terminal or command prompt and run this command:

```bash
npm install -g @angular/cli
This installs the Angular CLI globally so you can use it from anywhere.

✅ Step 2: Create a New Angular App
Now let’s create your first app. Run this command:

ng new my-app
You’ll be asked a few questions (like whether to use routing or CSS/SCSS). Just choose what fits your project.

The CLI will:

Create a new folder called my-app

Set up your Angular workspace

Install all the required files and packages

✅ Step 3: Move into Your Project
After it's done, go into your new project folder:

cd my-app
✅ Step 4: Run the App
Now, start the Angular development server with this command:

ng serve --open
This will:

Build your app

Open it automatically in your default browser

Run it at: http://localhost:4200

```


# All about each file or folder used 
#📦 What is package.json?
```
package.json is like the brain or info card of your Angular (or any Node.js) project.

It keeps track of:

What your project is called

Which version it is

What tools and libraries it uses

What commands (scripts) it can run

    
```
#📄 What is tsconfig.json?
tsconfig.json is a TypeScript settings file.
It tells TypeScript how to understand and compile your code.

It’s like giving instructions to TypeScript so it knows what to do.


#🧠 Why is it needed?
TypeScript is strict and needs rules to work properly.
This file gives it rules like:

What files to include or ignore

What version of JavaScript to convert to

Whether to check for strict types

Where to put the final compiled files


#🧠 What is tsconfig.app.json?
Because TypeScript needs to know:

What files to look at 👀

What kind of JavaScript to convert to ⚙️

Where to find things 🧭

# Why tsconfig.spec.json
used for testing the complete app

#📄 What is angular.json?
angular.json is a big instruction file that tells Angular:

“Here’s how to build, serve, test, and manage my Angular project.”

It controls how your whole Angular app works – from building, serving, styles, scripts, to project structure.

🧠 Why is it important?
Because Angular needs to know:

Where your app files are

Which files to load (like index.html, main.ts)

How to build your app

How to run your tests

Which styles/scripts to include


#📄 What is package-lock.json?
package-lock.json is an automatically generated file that gets created when you install dependencies in a Node.js (or Angular) project.

It’s like a diary of exactly which versions of the packages (libraries or tools) your project is using.
package-lock.json locks the exact versions of your project's dependencies.

It ensures consistent installs for everyone working on the project.

It speeds up installations and saves exact versions of libraries.




