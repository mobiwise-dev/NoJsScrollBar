# CSS-Only Scroll Progress Bar

### Scroll-Driven Animations, Typed Custom Properties & Zero JavaScript

This project demonstrates how to build a **scroll progress bar and percentage indicator using only CSS**, powered by **scroll-driven animations**, **typed custom properties (CSS Houdini)**, and **CSS counters**.

No JavaScript is used to track, compute, or animate scroll progress.

> ⚠️ This is an **advanced, experimental CSS demo**.  
> Intended for learning, exploration, and showcasing modern CSS capabilities — not as a production-ready replacement for JavaScript yet.

---

## ✨ Demo

👉 Live demo on CodePen  
**https://nojsscrollbar.mobiwise.dev**

👉 Live demo on CodePen  
**https://codepen.io/mobiwise/pen/pvbjwYv**

---

## 🧠 Core Idea

Modern CSS can now react directly to scroll position using **scroll timelines**.

Instead of listening to scroll events in JavaScript, this demo binds an animation directly to the document scroll using:

```css
animation-timeline: scroll(root);
```

The animation drives a **typed numeric custom property**, which is then reused to:

- Fill a progress bar
- Display a numeric percentage
- Keep all UI elements perfectly synchronized

---

## 🧩 Key Technologies Used

### 1\. Scroll-Driven Animations

```css
animation-timeline: scroll(root);
```

- Binds animation progress to scroll position instead of time
- The animation runs from 0% to 100% as the document scrolls
- No JavaScript event listeners required

---

### 2\. Typed Custom Properties (`@property`)

```css
@property --scroll {
  syntax: "<number>";
  inherits: false;
  initial-value: 0;
}
```

Why this matters:

- Enables **real numeric interpolation**
- Without `@property`, CSS variables are treated as untyped tokens
- Allows smooth, continuous updates during animation

---

### 3\. Driving the Progress Bar

```css
background: linear-gradient(to right, blue calc(var(--scroll) * 1%), transparent 0);
```

- `--scroll` animates from `0` to `100`
- Converted into a percentage when used in the gradient
- Fully handled by the browser’s animation engine

---

### 4\. Displaying the Percentage (CSS Counters)

Displaying live numbers in pure CSS has traditionally been difficult.

This demo uses **CSS counters + typed properties**:

```css
counter-reset: scroll-value calc(var(--scroll));
content: counter(scroll-value) "%";
```

How it works:

- The animated numeric value updates a CSS counter
- The counter converts it into readable text
- The displayed value is an integer approximation (0–100)

No JavaScript string manipulation required.

---

## 🧪 What Is Truly CSS-Only Here?

✔ Scroll position tracking  
✔ Progress calculation  
✔ Smooth animation updates  
✔ Numeric percentage display  
✔ Zero JavaScript for scroll logic

JavaScript is used **only** for the optional 3D text effect (DepthText), which is unrelated to scroll tracking.

---

## 🌐 Browser Support & Limitations

### Supported (at the time of writing)

- Chromium-based browsers (Chrome, Edge, etc.)
- Safari (recent versions)

### Not Supported

- Firefox ❌  
  (`animation-timeline: scroll()` is not implemented yet)

A graceful fallback message is displayed for unsupported browsers.

---

## ⚠️ Production Considerations

While this demo works well in modern browsers:

- JavaScript remains **more robust and portable**
- CSS counters only expose **integer values**
- Browser support is still evolving

> **For production systems requiring full compatibility and precision, JavaScript is still the recommended solution.**

This project is about exploring what CSS _can already do today_.

---

## 🎯 Takeaways

- Modern CSS can track scroll position without JavaScript
- Scroll-driven animations unlock new UI patterns
- Typed custom properties enable real numeric interpolation
- CSS counters can expose animated values as text
- The gap between CSS and JavaScript capabilities is shrinking

---

## 🧪 Experimental by Design

This project intentionally uses:

- CSS Houdini features
- Scroll timelines
- Modern color spaces (OKLCH)
- Advanced layering and feature detection

No polyfills. No hacks. No fake “CSS-only” tricks.

---

## 🔗 Related

- DepthText (CSS-based 3D text layers):  
  [https://depthtext.mobiwise.dev](https://depthtext.mobiwise.dev)  
  [https://github.com/MobiWise-dev/DepthText](https://github.com/MobiWise-dev/DepthText)

---

## 📜 License

MIT — use, fork, break, remix, and experiment freely.

---

**Author**  
[MobiWise.dev](https://mobiwise.dev)
