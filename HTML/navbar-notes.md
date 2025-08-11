# CSS Navbar Quick Notes

## Goals
- Keep nav items aligned and inside the bar on small screens.
- Reset default `ul` spacing.
- Use Flexbox for vertical centering and wrapping when needed.

---

## Base HTML
```html
<nav class="nav">
  <a class="logo" href="/">Brand</a>
  <ul class="nav-list">
    <li><a href="#">Home</a></li>
    <li><a href="#">Docs</a></li>
    <li><a href="#">Blog</a></li>
  </ul>
</nav>
```

## Base CSS
```css
/* Container */
.nav {
  display: flex;
  align-items: center;   /* center logo + list vertically */
  justify-content: space-between;
  height: 56px;
  padding: 0 16px;
}

/* Reset UL and make it flex */
.nav-list {
  display: flex;
  align-items: center;       /* vertical center list items */
  padding-inline-start: 0;   /* remove default left padding */
  margin-block: 0;           /* remove default top/bottom margin */
  height: 100%;              /* fill nav bar height */
  list-style: none;
  gap: 16px;
}

/* Links */
.nav a {
  text-decoration: none;
  display: inline-block;
  line-height: 1; /* avoids extra vertical jitter */
  padding: 8px 4px;
}
```

## Small screens (keep inside / wrap / collapse)
Pick one pattern:

### 1) Allow wrap (simplest)
```css
.nav-list {
  flex-wrap: wrap;
  row-gap: 8px;
}
```

### 2) Shrink items
```css
.nav-list {
  flex-wrap: nowrap;
}
.nav-list > li {
  min-width: 0;     /* allow shrinking */
}
.nav {
  overflow: hidden; /* prevents horizontal scroll bar on the container */
}
```

### 3) Collapse to menu button (common)
```html
<button class="menu-btn" aria-expanded="false" aria-controls="menu">Menu</button>
<ul id="menu" class="nav-list is-collapsed">...</ul>
```
```css
.menu-btn { display: none; }
@media (max-width: 640px) {
  .menu-btn { display: inline-block; }
  .nav-list.is-collapsed { display: none; } /* toggle with JS */
}
```

## Common pitfalls
- Forgetting to remove `ul` default padding/margins → nav shifts to the right.
- No vertical centering (missing `align-items: center`).
- Using only colors to indicate active link (add underline or `aria-current="page"`).

## Quick checklist
- [ ] `.nav` is `display: flex; align-items: center;`
- [ ] `.nav-list` resets: `padding-inline-start: 0; margin-block: 0;`
- [ ] `.nav-list` is flex and `height: 100%`
- [ ] Decide: wrap / shrink / collapse for small screens
- [ ] Keyboard focus visible on links
- [ ] Active link marked (e.g., `aria-current="page"`)
