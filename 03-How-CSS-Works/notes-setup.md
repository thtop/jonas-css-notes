# Coverting px to rem: An Effective Workflow

- How and why to use _rem_ units in our project;
- A great workflow for converting _px_ to _rem_.

## Set up

```css
*,
*::after,
*::before {
  margin: 0;
  padding: 0;
  box-sizing: inherit;
}

html {
  /* 10/16 = 62.5% */
  /* .625 * 16 = 10 */
  font-size: 62.5%; /* 1 rem = 16px*/
}

body {
  font-family: "Lato", sans-serif;
  font-weight: 400;
  /* font-size: 16px; */
  line-height: 1.7;
  color: #777;
  padding: 3rem;

  box-sizing: border-box;
}
```
