## ✨ GSAP & ScrollTrigger Guide

1. **GSAP** is used to animate elements.
2. **ScrollTrigger** is used to animate elements based on scroll.

### 🔧 ScrollTrigger Properties

- `trigger`: Select the element to trigger animation.
- `scroller`: Usually `"body"`.
- `start`: Scroll point where animation starts.
- `end`: Scroll point where animation ends.
- `markers`: `true/false` – Shows start & end points (for debugging).
- `scrub`: `true` or `1-5` – Syncs animation with scroll.
- `pin`: `true` – Pins the element during animation.

> **Note:** When using `pin`, the trigger should be the parent element.

