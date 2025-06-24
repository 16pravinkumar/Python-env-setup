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
