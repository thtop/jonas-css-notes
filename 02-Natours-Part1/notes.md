# Natours Project - Setup and First Strps (Part 1)

## Building the Header - Part 1

- The best way to perform a basic reset using the universal selector;
- How to set project-wide font definitions.
- How to clip parts of elements using `clip-path.`
- [https://bennettfeely.com/clippy/](https://bennettfeely.com/clippy/)

---

## Setup

```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: "Lato", sans-serif;
  font-weight: 400;
  font-size: 16px;
  line-height: 1.7;
  color: #777;
}
```

---

## Building the Header - Part 2

- The easiest way to center anything with the `transform, top` and `left` properties.

```css
.text-box {
  position: absolute;
  top: 40%;
  left: 50%;
  transform: translate(-50%, -50%);
  background-color: red;
}
```

---

## Create Cool CSS Animations

- How to create CSS animations using `@keyframes` and the `animation` property.
- [animation-timing-function](https://developer.mozilla.org/en-US/docs/Web/CSS/animation-timing-function)

```css
.heading-primary {
  color: #fff;
  text-transform: uppercase;

  backface-visibility: hidden;
}

.heading-primary-main {
  display: block;
  font-size: 60px;
  font-weight: 400;
  letter-spacing: 35px;

  animation-name: moveInLeft;
  animation-duration: 1s;
  animation-timing-function: ease-out;

  /*
  animation-delay: 3s;
  animation-iteration-count: 3;
  */
}

.heading-primary-sub {
  display: block;
  font-size: 20px;
  font-weight: 700;
  letter-spacing: 17.5px;

  animation: moveInRignt 1s ease-out;
}

/* animation */
@keyframes moveInLeft {
  0% {
    opacity: 0;
    transform: translateX(-100px);
  }

  80% {
    transform: translateX(10px);
  }

  100% {
    opacity: 1;
    transform: translate(0);
  }
}

@keyframes moveInRignt {
  0% {
    opacity: 0;
    transform: translateX(100px);
  }

  80% {
    transform: translateX(-10px);
  }

  100% {
    opacity: 1;
    transform: translate(0);
  }
}
```

---

## Building a Complex Animated Button - Part 1

- What `pseudo-elements` and `pseudo-classes` are;
- How and why use the `::after` pseudo-element;
- How to create a creative hover animation effect using the `transition` property.

```css
/* link, visited, active -> pseudo-classes */
.btn:link,
.btn:visited {
  text-transform: uppercase;
  text-decoration: none;
  padding: 15px 40px;
  display: inline-block;
  border-radius: 100px;
  transition: all 0.2s;
  position: relative;
}

.btn:hover {
  transform: translateY(-3px);
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
}

.btn:active {
  transform: translateY(-1px);
  box-shadow: 0 5px 10px rgba(0, 0, 0, 0.2);
}

.btn-white {
  background-color: #fff;
  color: #777;
}
```

## Building a Complex Animated Button - Part 2

```css
/* pseudo-elements -> ::after */
.btn::after {
  content: "";
  display: inline-block;
  height: 100%;
  width: 100%;
  border-radius: 100px;
  position: absolute;
  top: 0;
  left: 0;
  z-index: -1;
  transition: all 0.4s;
}

.btn-white::after {
  background-color: #fff;
}

.btn:hover::after {
  transform: scaleX(1.4) scaleY(1.6);
  opacity: 0;
}

.btn-animated {
  animation: moveButtom 0.5s ease-out 0.75s;
  animation-fill-mode: backwards;
}

@keyframes moveButtom {
  0% {
    opacity: 0;
    transform: translateY(30px);
  }

  100% {
    opacity: 1;
    transform: translate(0);
  }
}
```
