# How CSS Works: A Look Behind the Scense

## Three Pillars of Writing Good HTML and CSS (Naver Forget Them!)

1. **Responsive**
   - Fluid layouts
   - Media queries
   - Responsive images
   - Correct unit
   - Desktop-first vs mobile-first
2. **Maintainable and scalable code**
   - Clean
   - Easy-to-understand
   - Growth
   - Reusable
   - How to organize files
   - How to name classes
   - Hoe to structure HTML
3. **Web performance**
   - Less HTTP requests
   - Less code
   - Compress code
   - Use a CSS preprocessor
   - Less images
   - Compress images

---

## How CSS Works Behind the Scenes: An Overview

- Load HTML -> Parse HTML --> DOM (Document Object Model)
- --------- -> Load CSS --> Pasrse CSS
- ------------------------> Resolve conflicting CSS declarations (cascade)
- ------------------------> Process final CSS values
- -------------------------------------------------- --> CSSOM (CSS Object Model)
- DOM + CSSOM ==> Render tree
- Website rendering: the visual formatting model
- Final rendered website

![load up a webpage](https://github.com/thtop/jonas-css-notes/blob/master/03-How-CSS-Works/imgs/load-up-a-webpage.PNG)

---

## How CSS is Parsed, Part 1: The Cascade and Specificity

**A CSS Rule**

```css
.my-class {
  color: bule;
  text-aligh: center;
  font-size: 20px;
}
```

- Selector: `.my-class`
- Declaration block : `{ ... }`
- Declaration: `font-size: 20px;`
- Property: `font-size`
- Declated value: `20px`

**The Casecade** (The "C" in CSS)

- **Cascade**: Process of combining different stylesheets and resolving conflicts between different CSS rules and declarations, when more than one rule applies to a certain element.

**Sources CSS**

- Author
- User
- Browser (user agent)

> Importance > Specificity > Source order

**Importance**

1. User `!importan` declarations
2. Author `!important` declarations
3. Author declarations
4. User declarations
5. Default browser declarations

**Specificity**

1. Inline styles
2. IDs
3. Classes, pseudo-classes, attribute
4. Elements, pseudo-elements

**Source order**

- The last declaration in the code will override all other declarations and will be applied.

**Summary**

- CSS declarations marked with `!important` have the highest priority.
- But, only use `!important` as a last resource, It's better to use correct specificities - **more maintainable code!**
- Inline styles will always have priority over styles in external stylesheets;
- A selector that contains **1 ID** is more specific than one with 1000 elements;
- A selector that contains **1 class** is more specific than one with 1000 elements;
- The universal selector `*` has no specificity value (0, 0, 0, 0);
- Rely more on **specificity** than on the **order** of selectors;
- But, rely on order when using 3rd-party stylesheets - always put your author stylesheet last.

---

## Specificity in Practiec

- `!important`
- pseudo-classes

---

## How CSS is Parsed, Part 2: Value Processing

```html
<div class="section">
  <p class="amazing">CSS is absolutely amazing</p>
</div>
```

```css
.section {
  font-size: 1.5rem;
  width: 280px;
  background-color: orangered;
}

p {
  width: 140px;
  background-color: green;
}

.amazing {
  width: 66%;
}
```

| sources                                                        |  width (p)  |     padding (p)     |    font-size (root)    | font-size (section) | font-size (p) |
| -------------------------------------------------------------- | :---------: | :-----------------: | :--------------------: | :-----------------: | :-----------: |
| 1. declared value (author declarations)                        | 140px & 66% |          -          |           -            |       1.5rem        |       -       |
| 2. Cascaded value (after the cascade)                          |     66%     |          -          | 16px (Browser default) |       1.5rem        |       -       |
| 3. Specified value (defaulting, if there is no cascaded value) |     66%     | 0px (Initial value) |          16px          |       1.5rem        |     24px      |
| 4. Computed value (converting relative calues to absolute)     |     66%     |         0px         |          16px          | 24px (1.5 x 16 px)  |     24px      |
| 5. Used value (final calculation based on layout)              |   184.8px   |         0px         |          16px          |        24px         |     24px      |
| 6. Actual value (browser and device restrictions)              |    185px    |         0px         |          16px          |        24px         |     24px      |

**How Unit are converted from relative to absulute (px)**

```css
html,
body {
  font-size: 16px;
  width: 80vw;
}

header {
  font-size: 150%;
  padding: 2em;
  margin-bottom: 10rem;
  height: 90vh;
  width: 1000px;
}

.header-child {
  font-size: 3em;
  padding: 10%;
}
```

|             | Example (x) | How to convert to pixels           | Result in pixels |
| ----------- | ----------- | ---------------------------------- | ---------------- |
| % (fonts)   | 150%        | x% `x` parent's computed font-size | **24px**         |
| % (lengths) | 10%         | x% `x` parent's computed **width** | **100px**        |

| Font-based  | Example (x) | How to convert to pixels                    | Result in pixels  |
| ----------- | ----------- | ------------------------------------------- | ----------------- |
| em (fonts)  | 3em         | x `x` parent's computed font-size           | **72px** (3 x 24) |
| em(lengths) | 2em         | x `x`**current element** computed font-size |                   | % (lengths) | 10% | x% `x` parent's computed **width** | **100px** |  |
| ram         | 10ram       | x `x` **root** computed font-size           | 160px             |

| Viewport-based | Example (x) | How to convert to pixels    | Result in pixels                   |
| -------------- | ----------- | --------------------------- | ---------------------------------- |
| vh             | 90vh        | x `x` 1% of viewport height | 90% of the current viewport height |
| vw             | 80vw        | x `x` 1% of viewport width  | 80% of the current viewport width  |

**Summary**

- Each property has an initial value, used if nothing is declared (and if there is no inheritance -see next lecture);
- Browsers speciry a **root font-size** for each page (usually 16px);
- Parcentages and relative values are always converted to pixels;
- Percentages are measured relative to their parent's **font-size**, if used to specify _font-size_;
- Percentages are measured relative to their parent's **width**, if used to specify lengths;
- _em_ are measured relative to their **parent** _font-size_, if used to specify _font-size_;
- _em_ are measured relative to the **current** _font-size_, if used to specify lengths;
- _rem_ always measured relative to the **document's root** _font-size_;
- _vh_ and _vw_ are simply perentage measurements of the viewport's _height_ and _width_.

---

## How CSS is Parsed, Part 3: Inheritance
