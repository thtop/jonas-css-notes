## A Quick Introduction to CSS Grid Layouts

**Sass Install**
- [Ruby Installer](https://rubyinstaller.org/downloads/) -> Download
- Select: "Ruby+Devkit 2.6.5-1 (x64)" and install
- Go to [https://sass-lang.com/](https://sass-lang.com/)
- `gem install sass`

**Sass Structor**
- root
- root -> css
- root -> scss -> style.scss

**Sass Command:**
- `sass scss/style.scss css/style.css`
- `sass --watch scss/style.scss:css/style.css`

### Why CSS Grid: A Whole New Mindset

- CSS Grid Layout is a brand new module that brings a two-dimensional grid system to CSS for the first tiem;
- CSS Grid replaces float layouts, using less, and more readable and logical CSS and HTML;
- CSS Grid works perfectly together with Flexbox, which is best to handle one-dimesional components and layouts;
- CSS Grid completely changes the way that we envision and build two-dimensional layouts.

**CSS Grid Terminology 1**
![CSS Grid Terminology 1](https://github.com/thtop/jonas-css-notes/blob/master/08-Grid-Layouts/imgs/01-grid-terminology.png)

**CSS Grid Terminology 2**
![CSS Grid Terminology 2](https://github.com/thtop/jonas-css-notes/blob/master/08-Grid-Layouts/imgs/02-grid-terminology.png)

**CSS Grid Properties Overview**
![CSS Grid Properties Overview](https://github.com/thtop/jonas-css-notes/blob/master/08-Grid-Layouts/imgs/03-grid-properties-overview.png)

---

### Quick Setup for This Section

- [CodePen](https://codepen.io/)

---

### Creating Our First Grid

**HTML**
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>Grid</title>
    <link rel="stylesheet" href="styles.css" />
  </head>
  <body>
    <div class="container">
      <div class="item item--1">1: Orange</div>
      <div class="item item--2">2: Green</div>
      <div class="item item--3">3: Villet</div>
      <div class="item item--4">4: Pink</div>
      <div class="item item--5">5: Blue</div>
      <div class="item item--6">6: Brown</div>
    </div>
  </body>
</html>

```

**SCSS**
```scss
.container {
  background-color: #eee;
  width: 1000px;
  margin: 30px auto;

  display: grid;
  grid-template-rows: 150px 150px;
  grid-template-columns: 150px 150px 150px;

  /* grid-row-gap: 30px;
  grid-column-gap: 50px; */
  grid-gap: 30px;
}

.item {
  padding: 20px;
  font-size: 30px;
  font-family: sans-serif;
  color: white;

  &--1 {
    background-color: orangered;
  }

  &--2 {
    background-color: yellowgreen;
  }

  &--3 {
    background-color: blueviolet;
  }

  &--4 {
    background-color: palevioletred;
  }

  &--5 {
    background-color: royalblue;
  }

  &--6 {
    background-color: goldenrod;
  }
}

```
---

### Getting Familiar with the `fr` unit

### Positioning Grid Items

### Spanning Grid Items

### Grid Challenge

### Grid Challenge: A Basic Solution

### Naming Grid Lines

### Namming Grid Areas

### Implicit Grid vd. Explicit Grids

### Aligning Grid Items

### Alignling Tracks

### Using `min-content`, `max-content` and the `minmax()` function

### Responsive Layouts with `auto-fit` and `auto-fill`