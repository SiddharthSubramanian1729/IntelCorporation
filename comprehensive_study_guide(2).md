# Comprehensive Study Guide

*Quick reference for exam preparation and interview practice*

# Angular Signals Study Guide

---

## 1. **Introduction to Signals in Angular**

### **What are Signals?**
- **Signals** are reactive primitives introduced in Angular 16 (stable in Angular 17) for fine-grained, efficient state tracking and reactivity.
- **Purpose:** Replace RxJS BehaviorSubjects for simpler, more performant state management and notification between components.

### **Benefits**
- **Simplicity:** Less boilerplate than RxJS.
- **Performance:** Only dependent consumers re-render.
- **Type Safety:** Strongly typed.
- **Predictability:** Synchronous updates, no subscriptions/unsubscriptions.

---

## 2. **Types of Signals**

### **Writable Signals**
- **Definition:** Signals whose value can be set or updated.
- **Methods:** `.set(newValue)`, `.update(fn)`, `.mutate(fn)` (for arrays/objects).

### **Computed Signals**
- **Definition:** Signals whose value is derived from other signals and automatically recalculated when dependencies change.
- **Usage:** For derived state (e.g., totals, filters).

### **Effects**
- **Definition:** Functions that run side effects when one or more signals change.
- **Use Cases:** Logging, syncing to local storage, triggering HTTP calls, etc.

---

## 3. **Creating and Updating Signals**

### **Signal Constructor**
```typescript
import { signal } from '@angular/core';

const count = signal(0); // Initial value: 0
```

### **Set Function**
```typescript
count.set(5); // Sets count to 5
```

### **Update Method**
```typescript
count.update(prev => prev + 1); // Increments count by 1
```

### **Mutate Method** (for arrays/objects)
```typescript
const items = signal<string[]>([]);
items.mutate(arr => arr.push('newItem')); // Pushes 'newItem' to array
```

### **Computed Signal**
```typescript
import { computed } from '@angular/core';

const doubleCount = computed(() => count() * 2);
```

### **Effect**
```typescript
import { effect } from '@angular/core';

effect(() => {
  console.log('Count changed:', count());
});
```

### **createEffectOptions**
```typescript
effect(() => {
  // Side effect code
}, { allowSignalWrites: true });
```

---

## 4. **Practical Applications & Patterns**

### **Simple Counter Example**
```typescript
const count = signal(0);
const increment = () => count.update(n => n + 1);
const decrement = () => count.update(n => n - 1);
```

### **Array Signal Example**
```typescript
const cart = signal<CartItem[]>([]);
cart.mutate(items => items.push({ id: 1, name: 'Book', price: 10 }));
```

### **Computed Signal Example**
```typescript
const total = computed(() => cart().reduce((sum, item) => sum + item.price, 0));
```

### **Effect Example**
```typescript
effect(() => {
  localStorage.setItem('cart', JSON.stringify(cart()));
});
```

### **Real-Time Application Example: Add to Cart**
- **Service:**
  ```typescript
  @Injectable({ providedIn: 'root' })
  export class CartService {
    private _cart = signal<CartItem[]>([]);
    cart = this._cart.asReadonly();

    addItem(item: CartItem) {
      this._cart.mutate(items => items.push(item));
    }
    // ...other methods
  }
  ```
- **Component:**
  ```typescript
  export class CartComponent {
    cart = this.cartService.cart;
    total = computed(() => this.cart().reduce((sum, item) => sum + item.price, 0));
  }
  ```

---

## 5. **Advanced Signal Concepts**

### **Replacing BehaviorSubjects**
- **Old (RxJS):**
  ```typescript
  private _cart$ = new BehaviorSubject<CartItem[]>([]);
  cart$ = this._cart$.asObservable();
  ```
- **New (Signals):**
  ```typescript
  private _cart = signal<CartItem[]>([]);
  cart = this._cart.asReadonly();
  ```

### **Using Effects for Side Effects**
- **Example:** Update points when cart total changes.
  ```typescript
  const points = signal(0);
  effect(() => {
    points.set(Math.floor(total() / 10));
  });
  ```

### **createEffectOptions**
- **Purpose:** Allow writing to signals inside effects (default is read-only).
- **Usage:**
  ```typescript
  effect(() => {
    // Write to signals here
  }, { allowSignalWrites: true });
  ```

---

## 6. **Best Practices**

- **Use writable signals for local, mutable state.**
- **Use computed signals for derived values.**
- **Use effects for side effects, not for state derivation.**
- **Avoid writing to signals inside effects unless necessary (use `allowSignalWrites`).**
- **Prefer signals over RxJS for component state; use RxJS for async streams (HTTP, websockets).**
- **Use `.asReadonly()` to expose signals without mutation capability.**

---

## 7. **Example Use Cases in Angular**

### **Cart Service**
- **Manages cart state and notifies components via signals.**

### **Header Component**
- **Displays computed values (e.g., points from cart total).**

### **Cart Component**
- **Displays cart items and total price using signals and computed signals.**

---

## 8. **Quick Reference Table**

| Concept         | Syntax/Method                | Use Case/Example                      |
|-----------------|-----------------------------|---------------------------------------|
| Create Signal   | `signal(initialValue)`       | `const count = signal(0)`             |
| Set Value       | `.set(newValue)`             | `count.set(5)`                        |
| Update Value    | `.update(fn)`                | `count.update(n => n + 1)`            |
| Mutate Array    | `.mutate(fn)`                | `cart.mutate(arr => arr.push(item))`  |
| Computed Signal | `computed(() => ...)`        | `const total = computed(...);`        |
| Effect          | `effect(() => ...)`          | `effect(() => { ... })`               |
| Readonly Signal | `.asReadonly()`              | `cart = _cart.asReadonly()`           |

---

## 9. **Complexity Analysis**

- **Signal Updates:** O(1) per update, only dependent consumers re-render.
- **Computed Signals:** O(1) for recalculation, but depends on computation logic.
- **Effects:** O(1) trigger, but side effect complexity depends on implementation.

---

## 10. **Common Interview & Exam Questions**

1. **What are signals in Angular and how do they differ from RxJS BehaviorSubjects?**
2. **How do you create and update a writable signal?**
3. **Explain computed signals and give an example use case.**
4. **What are effects in Angular signals? When should you use them?**
5. **How do you expose a signal as read-only?**
6. **How would you migrate a service using BehaviorSubject to use signals?**
7. **What are best practices for using signals, computed signals, and effects?**
8. **Describe a scenario where you would use `createEffectOptions`.**
9. **How do signals improve performance compared to RxJS?**
10. **Write a code snippet for a counter using signals.**

---

## 11. **Code Templates & Patterns**

### **Counter**
```typescript
const count = signal(0);
const increment = () => count.update(n => n + 1);
const decrement = () => count.update(n => n - 1);
```

### **Array Mutation**
```typescript
const items = signal<string[]>([]);
items.mutate(arr => arr.push('item'));
```

### **Computed Value**
```typescript
const total = computed(() => items().length);
```

### **Effect**
```typescript
effect(() => {
  console.log('Items changed:', items());
});
```

---

## 12. **Summary Table: Signals vs. RxJS**

| Feature            | Signals                | RxJS BehaviorSubject         |
|--------------------|-----------------------|-----------------------------|
| Syntax             | Simple, synchronous   | Observable, async           |
| Subscriptions      | Not needed            | Required                    |
| Memory Leaks       | None                  | Possible if not unsubscribed|
| Performance        | Fine-grained, fast    | Less granular               |
| Use Case           | Local/component state | Async streams, HTTP, websockets |

---

## 13. **Exam-Ready Tips**

- **Signals are for local, synchronous state.**
- **Use computed signals for derived data.**
- **Use effects for side effects only.**
- **Expose signals as read-only to prevent unwanted mutations.**
- **Avoid overusing effects for state derivation.**
- **Signals are not a replacement for RxJS in all cases—use RxJS for async data.**

---

**Review this guide before exams or interviews for a quick, comprehensive refresher on Angular signals, their usage, and best practices.**