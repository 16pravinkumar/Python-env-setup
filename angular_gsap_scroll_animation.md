Here’s how you can **set up GSAP in Angular** and start using it effectively, especially for scroll-based animations with `ScrollTrigger`.

---

## ✅ Step-by-Step Guide: Using GSAP in Angular

### 📦 1. **Install GSAP**

```bash
npm install gsap
```

For scroll-based animations, also install:

```bash
npm install gsap@npm:@gsap/shockingly
```

or just install the plugin separately:

```bash
npm install gsap@npm:@gsap/scrolltrigger
```

---

### 📁 2. **Use it in your component**

For example, in `app.component.ts`:

```ts
import { Component, ElementRef, ViewChild, AfterViewInit } from '@angular/core';
import gsap from 'gsap';
import ScrollTrigger from 'gsap/ScrollTrigger';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent implements AfterViewInit {

  @ViewChild('box', { static: true }) box!: ElementRef;

  ngAfterViewInit() {
    gsap.registerPlugin(ScrollTrigger);

    gsap.to(this.box.nativeElement, {
      scrollTrigger: {
        trigger: this.box.nativeElement,
        start: "top 80%",
        end: "top 30%",
        scrub: true,
        toggleActions: "play none none reverse"
      },
      x: 200,
      opacity: 1,
      duration: 1
    });
  }
}
```

---

### 🧱 3. **Add HTML Element**

```html
<!-- app.component.html -->
<div style="height: 100vh;">Scroll down</div>

<div #box class="box">
  Animate Me
</div>

<div style="height: 100vh;"></div>
```

---

### 🎨 4. **Add Styles (optional)**

```css
/* app.component.css */
.box {
  width: 100px;
  height: 100px;
  background: coral;
  opacity: 0;
  transform: translateX(0);
  transition: all 0.5s ease;
}
```

---

## 📌 Tips for Angular Integration

* Always run GSAP inside `ngAfterViewInit()` — elements aren’t available in `ngOnInit()`.
* Use `@ViewChild()` to reference elements.
* Avoid directly manipulating the DOM with `document.querySelector`; use Angular’s `ElementRef`.

---

## 🚀 Want to Animate Multiple Elements?

```ts
ngAfterViewInit() {
  gsap.utils.toArray('.box').forEach((elem: any) => {
    gsap.from(elem, {
      scrollTrigger: {
        trigger: elem,
        start: 'top 80%',
        toggleActions: 'play none none reverse',
      },
      opacity: 0,
      y: 50,
      duration: 1,
    });
  });
}
```

---

Let me know if you want to:

* Animate routes
* Create complex timeline animations
* Integrate with Locomotive Scroll or SplitText

I’ll help tailor the setup!
