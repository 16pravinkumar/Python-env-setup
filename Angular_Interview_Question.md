#Interview Question for angular 

##1. Can we let const inside a AppComponent 
```ts
export class AppComponent {
  title = 'my-angular';
}
```
Answer ==> Yes, we can use but inside a function for e.g
```ts
**app.component.ts**
export class AppComponent {
  title = 'my-angular';
  setLet():string{
    let data = "Welcome"
    return data
  }
}

**app.component.html**
<h2>{{a}}</h2>
<p>{{setLet()}}</p>
```
