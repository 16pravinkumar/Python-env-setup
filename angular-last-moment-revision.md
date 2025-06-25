## One way data binding .ie. from viewTemp(.html) to component class(.ts) or vice versa
		1] string interpolation DB :  eg {{data}}   <div>{{data}} </div>
		2] Property Binding : [property] = data   <img [src]="imageUrl" />
		3] Event Binding :  <button (click)="handleClick()">Click Me</button>


# 👶 Angular Communication & Structural Directives – Like a Kid Would Understand 🍭

## 🧩 `@Input()` – Pass Data **from Parent to Child**

**Real-life:** Mom gives you your lunchbox.

```ts
// child.component.ts
@Input() lunchbox: string;
```

```html
<!-- parent.component.html -->
<app-child [lunchbox]="'Sandwich'"></app-child>
```

> ✅ **Use when parent gives something to child.**

---

## 📣 `@Output()` – Send Data **from Child to Parent**

**Real-life:** You tell mom you're done with homework.

```ts
@Output() homeworkDone = new EventEmitter<string>();

tellMom() {
  this.homeworkDone.emit('Done!');
}
```

```html
<app-child (homeworkDone)="onChildDone($event)"></app-child>
```

> ✅ **Use when child wants to inform parent.**

---

## 🔁 Communicate Between **Unrelated Components**

**Real-life:** Two kids talking through a common teacher.

### Method:

* Use **Shared Service** with **RxJS BehaviorSubject** or `EventEmitter`.

```ts
@Injectable({ providedIn: 'root' })
export class TalkService {
  private msg = new BehaviorSubject<string>('Hi');
  message$ = this.msg.asObservable();

  sendMessage(msg: string) {
    this.msg.next(msg);
  }
}
```

> ✅ **Use when components don’t know each other but need to talk.**

---

## 🎯 Template Reference Variable – `#myVar`

**Real-life:** You call your toy by a name and use it.

```html
<input #box />
<button (click)="log(box.value)">Log</button>
```

```ts
log(value: string) {
  console.log(value);
}
```

> ✅ **Use when you want to access an element directly.**

---

## 🔍 `@ViewChild()` – Access Child Element in TS

**Real-life:** You grab your toy from your toy box.

```html
<input #toy />
```

```ts
@ViewChild('toy') toyInput!: ElementRef;
```

> ✅ **Use to access DOM or component inside the same file.**

---

## 🧸 `@ViewChildren()` – Access Multiple Elements

**Real-life:** You pick **all toys** from the shelf.

```html
<div #toy *ngFor="let t of toys">{{ t }}</div>
```

```ts
@ViewChildren('toy') toys!: QueryList<ElementRef>;
```

---

## 📦 `*ngContainer`

**Real-life:** A gift box that **doesn’t add** extra wrapping – just organizes.

```html
<ng-container *ngIf="show">
  <h1>Hello!</h1>
</ng-container>
```

> ✅ Use it when you need a wrapper **without adding extra HTML**.

---

## 📭 `ng-content` – Projection (Insert HTML into child)

**Real-life:** You put a card inside an envelope.

```ts
<!-- parent -->
<app-card>
  <h2>My Title</h2>
</app-card>

<!-- child -->
<ng-content></ng-content>
```

> ✅ Use when parent **sends HTML** to child component.

---

## 👁️‍🗨️ `@ContentChild()` – Get one projected content element

**Real-life:** You take one card from envelope.

```ts
@ContentChild('title') titleRef!: ElementRef;
```

> ✅ Use to get **one** element from `ng-content`.

---

## 👀 `@ContentChildren()` – Get multiple projected elements

**Real-life:** You take **all cards** from the envelope.

```ts
@ContentChildren(MyComponent) allCards!: QueryList<MyComponent>;
```

> ✅ Use to get **many** elements from `ng-content`.

---

### ✅ Summary Table

| Feature              | Direction           | Real-Life Example                  | When to Use                           |
| -------------------- | ------------------- | ---------------------------------- | ------------------------------------- |
| `@Input()`           | Parent → Child      | Mom gives lunch                    | Parent gives data                     |
| `@Output()`          | Child → Parent      | Child tells mom he’s done homework | Child emits event                     |
| Shared Service       | ↔ Unrelated comps   | Two kids talk through teacher      | For unrelated component communication |
| `#ref`               | Template Access     | Calling a toy by name              | Grab element in HTML                  |
| `@ViewChild()`       | One DOM/child comp  | Get one toy                        | Access one component or element       |
| `@ViewChildren()`    | Many elements       | Grab all toys                      | Loop or manipulate multiple elements  |
| `*ngContainer`       | No extra wrapper    | Invisible gift wrap                | Organize content without new element  |
| `ng-content`         | Projection          | Put card in envelope               | Parent injects custom content         |
| `@ContentChild()`    | One projected elem  | One card from envelope             | Access first projected element        |
| `@ContentChildren()` | All projected elems | All cards from envelope            | Access many projected elements        |

---

# Angular Lifecycle Hooks - Simple Guide

## Why Are Lifecycle Hooks Important?

Hooks let you run your code **at the right time** during the life of a component or directive.

---

## 1. ngOnInit()

### When it runs:

* After Angular first displays the component's data-bound properties.

### Common use:

* Fetch data from an API
* Set default values

### Example:

```ts
ngOnInit() {
  this.getData();
}
```

---

## 2. ngOnChanges()

### When it runs:

* When a component receives new @Input values from its parent.

### Common use:

* React when a parent passes new data

### Example:

```ts
@Input() userName: string;

ngOnChanges(changes: SimpleChanges) {
  console.log('New userName:', changes.userName.currentValue);
}
```

### Note:

* It always works with `@Input()`.

---

## 3. ngDoCheck()

### When it runs:

* Every time Angular runs change detection (many times!)

### Common use:

* Manually detect and react to changes not caught by `OnChanges`

### Example:

```ts
ngDoCheck() {
  console.log('Change detection running');
}
```

### Caution:

* Can affect performance if used wrongly.

---

## 4. ngAfterContentInit()

### When it runs:

* After Angular projects external content (ng-content) into the component

### Common use:

* Perform actions after content is added

### Example:

```ts
ngAfterContentInit() {
  console.log('Content projected');
}
```

---

## 5. ngAfterContentChecked()

### When it runs:

* After Angular checks the content projected into the component

### Common use:

* Detect content changes

### Example:

```ts
ngAfterContentChecked() {
  console.log('Content checked');
}
```

---

## 6. ngAfterViewInit()  **(Component-only)**

### When it runs:

* After the component's view (template) and child views are initialized

### Common use:

* Access elements with ViewChild

### Example:

```ts
@ViewChild('myDiv') div: ElementRef;

ngAfterViewInit() {
  console.log(this.div.nativeElement);
}
```

---

## 7. ngAfterViewChecked()  **(Component-only)**

### When it runs:

* After Angular checks the component and its child views

### Common use:

* React to view updates

### Example:

```ts
ngAfterViewChecked() {
  console.log('View checked');
}
```

---

## 8. ngOnDestroy()

### When it runs:

* Just before Angular destroys the component or directive

### Common use:

* Unsubscribe from Observables
* Clear timers

### Example:

```ts
ngOnDestroy() {
  clearInterval(this.timer);
}
```

---

## Which Hooks Should You Use?

| Hook                  | Use When                                                            |
| --------------------- | ------------------------------------------------------------------- |
| ngOnInit              | To run code when component is first created                         |
| ngOnChanges           | To react to changes in @Input()                                     |
| ngDoCheck             | To write custom change detection logic                              |
| ngAfterContentInit    | To work with content inside <ng-content>                            |
| ngAfterContentChecked | To know when content is checked again                               |
| ngAfterViewInit       | To access or manipulate view/template elements (only in components) |
| ngAfterViewChecked    | To know when the view is checked again (only in components)         |
| ngOnDestroy           | To clean up tasks before the component/directive is removed         |

---

## Final Notes:

* You don’t need to use **all** hooks in every component.
* Use only the ones you need.
* For simple components, `ngOnInit()` and `ngOnDestroy()` are usually enough.

---

# Render2 service 
## In Angular, the Renderer2 service is used to safely manipulate the DOM. It is especially useful for keeping your app compatible with different platforms (like server-side rendering or web workers).

✅ Why use Renderer2 instead of direct DOM manipulation?
Prevents direct access to native DOM

Ensures platform independence

Avoids security issues (e.g., XSS)


