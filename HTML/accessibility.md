# HTML Accessibility Quick Notes

## Why it matters
- Accessibility = making the site usable for everyone (screen readers, keyboard users, etc.).
- Also improves SEO and UX.

---

## ARIA Basics

### role
Tells assistive tech what the element is.
```html
<section role="region" aria-labelledby="contact-info">
  <h2 id="contact-info">Contact Info</h2>
</section>
```

### aria-label
Adds an invisible label (read by screen readers).
```html
<button aria-label="Close menu">X</button>
```

### aria-labelledby
Uses another element’s text as the label.
```html
<section aria-labelledby="quiz-title">
  <h2 id="quiz-title">HTML Quiz</h2>
</section>
```

---

## Screen Reader Only text

### `.sr-only` CSS
Hide visually, still readable by screen readers.
```css
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  clip-path: inset(50%);
  white-space: nowrap;
}
```
**Example**:
```html
<h3><span class="sr-only">Question</span>1</h3>
```
Visible: `1`  
Screen reader: `Question 1`

---

## Forms

### Label + input
Always pair label with input (better than only placeholder).
```html
<label for="name">Name:</label>
<input id="name" type="text">
```

### If no visible label
Use `aria-label`.
```html
<input type="text" aria-label="Name">
```

---

## Common mistakes
- Using only placeholder as label
- Missing `alt` on images
- Only using color to convey info (bad for color-blind users)

---

## References
- W3C WAI ARIA Practices: https://www.w3.org/WAI/ARIA/apg/
- MDN Accessibility Guide: https://developer.mozilla.org/en-US/docs/Learn/Accessibility
- freeCodeCamp Accessibility: https://www.freecodecamp.org/learn/responsive-web-design/#accessibility
