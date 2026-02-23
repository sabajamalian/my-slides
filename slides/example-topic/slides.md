---
title: Example Topic
theme: black
---

# Example Topic

A template for creating new slide decks

---

## Getting Started

- Copy this directory for a new topic
- Rename the folder to your topic name
- Edit `slides.md` with your content

Note: These are speaker notes. Press **S** to open the speaker view.

---

## Horizontal vs Vertical Slides

Use `---` for horizontal slide breaks

Use `--` for vertical (nested) slide breaks

--

### This is a Vertical Slide

You navigated down! Press the down arrow or swipe down to continue.

--

### Another Vertical Slide

Vertical slides are great for drilling into a subtopic.

---

## Code Blocks

```javascript
function greet(name) {
  return `Hello, ${name}!`;
}

console.log(greet('World'));
```

---

## Lists & Fragments

Items can appear one at one: <!-- .element: class="fragment" -->

- First point <!-- .element: class="fragment" -->
- Second point <!-- .element: class="fragment" -->
- Third point <!-- .element: class="fragment" -->

---

## Images

Place images in the `images/` subdirectory:

```markdown
![Alt text](images/diagram.png)
```

---

<!-- .slide: data-background="#2d2d2d" -->

## Custom Slide Backgrounds

Use HTML comments to set per-slide attributes:

```markdown
<!-- .slide: data-background="#2d2d2d" -->
```

---

## Thank You!

Questions?
