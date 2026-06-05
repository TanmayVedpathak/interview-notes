# CSS (Cascading Style Sheets)

## Basics & Fundamentals

### Q. What is CSS?

**Answer:**

CSS stands for Cascading Style Sheets. It is used to control the appearance and layout of HTML elements on a webpage.

CSS helps in styling:

- Colors
- Fonts
- Spacing
- Layouts
- Animations
- Responsive design

Example:

```css
p {
  color: blue;
  font-size: 20px;
}
```

### Q. What is a stylesheet?

**Answer:**

A stylesheet is a file or block containing CSS rules that define how HTML elements should appear.

There are 3 types of stylesheets:

1. Inline CSS

```css
<p style="color:red;">Hello</p>
```

2. Internal CSS

```html
<style>
  p {
    color: blue;
  }
</style>
```

3. External CSS

```html
<link rel="stylesheet" href="style.css" />
```

External stylesheets are most commonly used because they improve maintainability and reusability.

### Q. What is cascading in CSS?

**Answer:**

“Cascading” means CSS decides which style rule should apply when multiple rules target the same element.

CSS follows priority rules based on:

- Importance
- Specificity
- Source order

Example:

```css
p {
  color: blue;
}

p {
  color: red;
}
```

👉 Final color will be red because the later rule overrides the earlier one.

### Q. How do CSS precedence/cascading rules work?

**Answer:**

CSS applies styles according to a priority system.

Order of precedence:

1. !important
2. Inline CSS
3. ID selectors
4. Class selectors / attributes / pseudo-classes
5. Element selectors
6. Universal selector

Example:

```html
<p id="demo" class="text" style="color:red;">Hello</p>
```

```css
#demo {
  color: blue;
}

.text {
  color: green;
}
```

👉 Final color = red (inline style has higher priority)

### Q. What is `!important` and how does it affect rules?

**Answer:**

`!important` gives a CSS rule the highest priority.

Example:

```css
p {
  color: blue !important;
}

p {
  color: red;
}
```

👉 Final color = blue

Important points:

- Overrides normal specificity rules
- Should be used carefully
- Excessive use makes CSS difficult to maintain

### Q. What is W3C?

**Answer:**

W3C stands for World Wide Web Consortium.

It is the international organization that develops web standards for:

- HTML
- CSS
- XML
- Accessibility
- Web APIs

Its goal is to ensure:

- Consistent web standards
- Browser compatibility
- Better accessibility

### Q. What is CSS3?

**Answer:**

CSS3 is the modern version of CSS that introduced advanced styling features.

Features introduced in CSS3:

- Flexbox
- Grid
- Animations
- Transitions
- Media queries
- Border radius
- Shadows

Example:

```css
div {
  border-radius: 10px;
  transition: 0.3s;
}
```

CSS3 is modular, meaning features are divided into separate modules.

### Q. What are the advantages of CSS?

**Answer:**

Advantages of CSS:

1. Separation of content and design
2. Reusable styles
3. Faster page loading
4. Easier maintenance
5. Responsive design support
6. Better consistency across pages
7. Improved accessibility
8. Cleaner HTML structure

Example:

One CSS file can style an entire website.

### Q. What are the limitations of CSS?

**Answer:**

Limitations of CSS:

1. Different browser support issues
2. No programming logic like loops/conditions (basic CSS)
3. Global scope can cause conflicts
4. Difficult to manage in very large projects without methodology
5. Limited parent selection support (older CSS versions)

Example:

Two classes with same names may conflict in large applications.

### Q. What is general CSS nomenclature?

**Answer:**

CSS nomenclature refers to the structure and naming of CSS rules.

Basic syntax:

```css
selector {
  property: value;
}
```

Example:

```css
p {
  color: blue;
}
```

Parts:

| Part    | Meaning  |
| ------- | -------- |
| `p`     | Selector |
| `color` | Property |
| `blue`  | Value    |

Common terminology:

- Selector
- Property
- Value
- Declaration
- Rule set
- Class
- ID
- Pseudo-class

Example:

```css
.button:hover {
  background: black;
}
```

- `.button` → class selector
- `:hover` → pseudo-class
- `background` → property
- `black` → value

## Syntax & Core Concepts

### Q. What is a property in CSS?

**Answer:**

A CSS property defines what style should be changed for an HTML element.

Example:

```css
p {
  color: blue;
}
```

Here:

- `color` → property
- `blue` → value

Common CSS properties:

- `color`
- `font-size`
- `margin`
- `padding`
- `background`
- `border`

### Q. What is a ruleset?

**Answer:**

A ruleset is a complete CSS rule consisting of:

1. Selector
2. Declaration block

Example:

```css
p {
  color: red;
  font-size: 20px;
}
```

Breakdown:

| Part               | Meaning           |
| ------------------ | ----------------- |
| `p`                | Selector          |
| `{}`               | Declaration block |
| `color: red;`      | Declaration       |
| `font-size: 20px;` | Declaration       |

### Q. Name CSS components (selector, property, value)

**Answer:**

A CSS rule mainly contains these components:

```css
h1 {
  color: blue;
}
```

| Component | Example | Meaning         |
| --------- | ------- | --------------- |
| Selector  | `h1`    | Targets element |
| Property  | `color` | Style type      |
| Value     | `blue`  | Style value     |

Additional terms:

- Declaration → `color: blue;`
- Declaration block → `{ color: blue; }`

### Q. What is an at-rule?

**Answer:**

An at-rule is a special CSS statement that begins with @ and performs specific behavior.

Common at-rules:

`@media`

```css
@media (max-width: 600px) {
  body {
    background: lightgray;
  }
}
```

`@import`

```css
@import url("style.css");
```

`@keyframes`

```css
@keyframes slide {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
```

Purpose of at-rules:

- Responsive design
- Animations
- Importing styles
- Font declarations

### Q. Define CSS frameworks

**Answer:**

CSS frameworks are pre-written CSS libraries that help developers build websites faster using ready-made styles and components.

Popular CSS frameworks:

- Bootstrap
- Tailwind CSS
- Bulma
- Foundation

Advantages:

- Faster development
- Responsive layouts
- Reusable components
- Cross-browser consistency

Example:

```html
<button class="btn btn-primary">Submit</button>
```

### Q. What are CSS modules?

**Answer:**

CSS Modules are a way to create locally scoped CSS to avoid class name conflicts.

Mostly used with:

- React
- Next.js
- Modern frontend tools

Example:

```css
/_ Button.module.css _/ .button {
  color: white;
}
```

```js
import styles from "./Button.module.css";

<button className={styles.button}>Click</button>;
```

Benefits:

- Avoids global CSS conflicts
- Better maintainability
- Scoped styling

### Q. What are vendor prefixes?

**Answer:**

Vendor prefixes are browser-specific prefixes added to experimental CSS properties for compatibility.

Common prefixes:

| Prefix     | Browser           |
| ---------- | ----------------- |
| `-webkit-` | Chrome, Safari    |
| `-moz-`    | Firefox           |
| `-ms-`     | Internet Explorer |
| `-o-`      | Opera             |

Example:

```css
.box {
  -webkit-transform: rotate(20deg);
  -moz-transform: rotate(20deg);
  transform: rotate(20deg);
}
```

Why used?

- Experimental browser support
- Before official standardization

### Q. How case-sensitive is CSS?

**Answer:**

CSS is generally case-insensitive for:

- Property names
- Property values
- HTML element selectors

Example:

```css
P {
  color: RED;
}
```

👉 Works correctly.

But CSS IS case-sensitive in some cases:

1. Class names

```html
<div class="Box"></div>
```

```css
.box {
  color: red;
}
```

👉 Will NOT match because Box ≠ box

2. IDs

```html
<div id="Header"></div>
```

```css
#header {
  color: blue;
}
```

👉 Different identifiers.

## Selectors & Specificity

### Q. What is a CSS selector?

**Answer:**

A CSS selector is a pattern used to select and target HTML elements for styling.

Example:

```css
p {
  color: blue;
}
```

Here:

- `p` is the selector
- It selects all `<p>` elements

Common examples:

```css
h1        /* element selector */.class    /* class selector */#id       /* id selector */*         /* universal selector */
```

### Q. Types of CSS selectors

**Answer:**

CSS provides different types of selectors to target elements.

1. Element Selector

Targets HTML tags.

```css
p {
  color: red;
}
```

2. Class Selector

Targets elements with a class.

```css
.box {
  background: yellow;
}
```

3. ID Selector

Targets unique element IDs.

```css
#header {
  font-size: 20px;
}
```

4. Universal Selector

Targets all elements.

```css
* {
  margin: 0;
}
```

5. Group Selector

Targets multiple elements.

```css
h1,
p {
  color: blue;
}
```

6. Attribute Selector

Targets elements based on attributes.

```css
input[type="text"] {
  border: 1px solid black;
}
```

7. Pseudo-class Selector

Targets special states.

```css
a:hover {
  color: red;
}
```

8. Pseudo-element Selector

Targets part of an element.

```css
p::first-letter {
  font-size: 30px;
}
```

### Q. Attribute selectors

**Answer:**

Attribute selectors target elements based on their HTML attributes.

Example:

```css
input[type="email"] {
  border: 1px solid blue;
}
```

Common attribute selectors:

| Selector       | Meaning       |
| -------------- | ------------- |
| `[attr]`       | Has attribute |
| `[attr=value]` | Exact match   |
| `[attr^=val]`  | Starts with   |
| `[attr$=val]`  | Ends with     |
| `[attr*=val]`  | Contains      |

Examples:

```css
a[target] {
}
input[type="password"] {
}
img[src$=".png"] {
}
```

### Q. Contextual selectors

**Answer:**

Contextual selectors style elements based on their relationship with other elements.

Example:

```css
div p {
  color: blue;
}
```

👉 Selects all `<p>` inside `<div>`

Purpose:

- More precise targeting
- Avoid unnecessary classes

### Q. CSS combinators

**Answer:**

Combinators define relationships between selectors.

1. Descendant combinator (`space`)

```css
div p {
  color: red;
}
```

Targets all `<p>` inside `<div>`

2. Child combinator (`>`)

```css
div > p {
  color: blue;
}
```

Targets direct child `<p>`

3. Adjacent sibling (`+`)

```css
h1 + p {
  color: green;
}
```

Targets first `<p>` immediately after `<h1>`

4. General sibling (`~`)

```css
h1 ~ p {
  color: orange;
}
```

Targets all sibling `<p>` after `<h1>`

### Q. How selectors are matched by browser?

**Answer:**

Browsers match selectors from right to left for performance optimization.

Example:

```css
div ul li a {
  color: red;
}
```

Browser checks:

1. Find all `<a>`
2. Check if inside `<li>`
3. Then inside `<ul>`
4. Then inside `<div>`

Why right-to-left?

- Faster matching
- Better rendering performance

### Q. Specificity & how to calculate it

**Answer:**

Specificity determines which CSS rule gets applied when multiple rules target the same element.

Specificity hierarchy:

| Selector Type                | Value |
| ---------------------------- | ----- |
| Inline style                 | 1000  |
| ID                           | 100   |
| Class/attribute/pseudo-class | 10    |
| Element/pseudo-element       | 1     |

Example:

```css
#header {
  color: blue;
}
.title {
  color: red;
}
```

👉 `#header` wins because ID specificity is higher.

Calculation example:

```css
div#box .text p
```

Specificity:

- `#box` → 100
- `.text` → 10
- `div`, `p` → 1 + 1

👉 Total = 112

### Q. `:root` pseudo-class

**Answer:**

`:root` selects the highest-level element in the document.

In HTML, `:root` refers to:

```html
<html></html>
```

Common use:

CSS variables

```css
:root {
  --primary-color: blue;
}
p {
  color: var(--primary-color);
}
```

Advantages:

- Global variables
- Easier theme management
- Reusable values

### Q. Difference between nth-child() vs nth-of-type()

**Answer:**

`:nth-child()`

Selects element based on child position among all siblings.

```css
p: nth-child(2);
```

👉 Selects `<p>` only if it is the second child.

`:nth-of-type()`

Selects based on element type only.

```css
p: nth-of-type(2);
```

👉 Selects second `<p>` regardless of other elements.

Example:

```html
<div>
  <h1>Title</h1>
  <p>Para 1</p>
  <p>Para 2</p>
</div>
```

- `p:nth-child(2)` → selects first `<p>`
- `p:nth-of-type(2)` → selects second `<p>`

### Q. Selector combinations (div p, div > p, etc.)

**Answer:**

1. `div p`

Descendant selector

```css
div p {
  color: red;
}
```

👉 Selects all `<p>` inside `<div>`

2. `div > p`

Child selector

```css
div > p {
  color: blue;
}
```

👉 Selects only direct child `<p>`

3. `div + p`

Adjacent sibling selector

```css
div + p {
  color: green;
}
```

👉 Selects first `<p>` immediately after `<div>`

4. `div ~ p`

General sibling selector

```css
div ~ p {
  color: orange;
}
```

👉 Selects all `<p>` siblings after `<div>`

Quick Summary

| Selector | Meaning                |
| -------- | ---------------------- |
| `A B`    | Descendant             |
| `A > B`  | Direct child           |
| `A + B`  | Immediate sibling      |
| `A ~ B`  | All following siblings |

## Box Model & Layout

### Q. What is CSS Box Model?

**Answer:**

The CSS Box Model describes how every HTML element is represented as a rectangular box.

It consists of:

1. Content
2. Padding
3. Border
4. Margin

Structure:

```
Margin
 └── Border
      └── Padding
           └── Content
```

Example:

```css
div {
  width: 200px;
  padding: 20px;
  border: 5px solid black;
  margin: 10px;
}
```

### Q. Properties in box model

**Answer:**

The CSS Box Model contains four main properties:

| Property | Purpose                   |
| -------- | ------------------------- |
| Content  | Actual text/image         |
| Padding  | Space inside border       |
| Border   | Surrounds padding/content |
| Margin   | Space outside border      |

Example:

```css
div {
  width: 100px;
  height: 50px;
  padding: 10px;
  border: 2px solid black;
  margin: 20px;
}
```

### Q. Margin vs padding

**Answer:**

| Feature             | Margin                           | Padding       |
| ------------------- | -------------------------------- | ------------- |
| Location            | Outside border                   | Inside border |
| Affects background? | ❌ No                            | ✅ Yes        |
| Collapses?          | ✅ Vertical margins can collapse | ❌ No         |
| Used for            | Space between elements           | Inner spacing |

Example:

```css
div {
  margin: 20px;
  padding: 20px;
}
```

### Q. Border vs outline

**Answer:**

| Feature            | Border | Outline |
| ------------------ | ------ | ------- |
| Takes space?       | ✅ Yes | ❌ No   |
| Part of box model? | ✅ Yes | ❌ No   |
| Affects layout?    | ✅ Yes | ❌ No   |
| Can be offset?     | ❌ No  | ✅ Yes  |

Example:

```css
div {
  border: 2px solid black;
  outline: 2px solid red;
}
```

### Q. Box-sizing (border-box vs content-box)

**Answer:**

The `box-sizing` property controls how element dimensions are calculated.

1. `content-box` (default)

```css
box-sizing: content-box;
```

Width/height apply only to content.

Formula:

```
Total width = width + padding + border
```

2. `border-box`

```css
box-sizing: border-box;
```

Width includes:

- Content
- Padding
- Border

Formula:

```
Total width = specified width
```

Common practice:

```css
* {
  box-sizing: border-box;
}
```

### Q. Which properties do NOT affect box model?

**Answer:**

Properties that do NOT affect box model dimensions include:

- outline
- box-shadow
- transform
- opacity
- visibility

Example:

```css
div {
  outline: 2px solid red;
  box-shadow: 0 0 10px black;
}
```

👉 Element size remains unchanged.

### Q. Block vs inline vs inline-block

**Answer:**

| Feature              | Block  | Inline | Inline-block |
| -------------------- | ------ | ------ | ------------ |
| Starts new line      | ✅ Yes | ❌ No  | ❌ No        |
| Width/height allowed | ✅ Yes | ❌ No  | ✅ Yes       |
| Takes full width     | ✅ Yes | ❌ No  | ❌ No        |

Block Example:

```css
display: block;
```

Examples:

```html
<div></div>
<p></p>
<section></section>
```

Inline Example:

```css
display: inline;
```

Examples:

```html
<span></span>
<a></a>
<strong></strong>
```

Inline-block Example:

```css
display: inline-block;
```

👉 Behaves inline but supports width/height.

### Q. Block Formatting Context (BFC)

**Answer:**

A Block Formatting Context (BFC) is a special layout context in CSS that controls how block elements are rendered.

BFC helps with:

- Containing floats
- Preventing margin collapse
- Isolating layouts

Create BFC using:

```css
overflow: hidden;
```

OR

```css
display: flow-root;
```

Example:

```css
.container {
  overflow: hidden;
}
```

### Q. Element dimensions (height, width, height:auto)

**Answer:**

CSS dimensions define the size of elements.

Width

```css
width: 200px;
```

Defines horizontal size.

Height

```css
height: 100px;
```

Defines vertical size.

`height: auto`

```css
height: auto;
```

Height automatically adjusts based on content.

Responsive example:

```css
img {
  width: 100%;
  height: auto;
}
```

Related properties:

- min-width
- max-width
- min-height
- max-height

## Positioning & Display

### Q. CSS positioning properties (static, relative, etc.)

**Answer:**

CSS provides different positioning methods for placing elements.

1. `static` (default)

```css
position: static;
```

- Normal document flow
- `top`, `left`, etc. do not work

2. `relative`

```css
position: relative;
top: 10px;
left: 20px;
```

- Moves relative to original position
- Space remains reserved

3. `absolute`

```css
position: absolute;
top: 0;
right: 0;
```

- Removed from normal flow
- Positioned relative to nearest positioned parent

4. `fixed`

```css
position: fixed;
bottom: 0;
```

- Relative to viewport
- Stays fixed during scrolling

5. `sticky`

```css
position: sticky;
top: 0;
```

- Behaves relative until scroll threshold
- Then acts fixed

### Q. z-index and stacking context

**Answer:**

`z-index` controls stacking order of overlapping elements.

```css
.box {
  position: absolute;
  z-index: 10;
}
```

Higher `z-index` appears above lower values.

Important:

`z-index` works only on:

- positioned elements
- flex/grid children

Stacking Context

A stacking context is an isolated layering environment.

Created by:

- position + z-index
- opacity < 1
- transform
- filter

### Q. Float property

**Answer:**

The `float` property moves elements left or right and allows surrounding content to wrap around them.

```css
img {
  float: left;
}
```

Values:

- left
- right
- none

Common use:

- Wrapping text around images

### Q. When to use float?

**Answer:**

Use `float` mainly for:

- Text wrapping around images
- Legacy layouts

Example:

```css
img {
  float: right;
  margin-left: 10px;
}
```

Modern layouts should prefer:

- Flexbox
- CSS Grid

Important:

Floated elements may require clearing:

```css
clear: both;
```

### Q. Ways to position elements

**Answer:**

Elements can be positioned using:

| Method               | Purpose              |
| -------------------- | -------------------- |
| Static positioning   | Default flow         |
| Relative positioning | Offset from original |
| Absolute positioning | Precise placement    |
| Fixed positioning    | Viewport-fixed       |
| Sticky positioning   | Scroll-based         |
| Float                | Text wrapping        |
| Flexbox              | 1D layouts           |
| Grid                 | 2D layouts           |

### Q. Sticky positioning

**Answer:**

`position: sticky` combines:

- relative positioning
- fixed positioning

Example:

```css
header {
  position: sticky;
  top: 0;
}
```

Behavior:

- Normal flow initially
- Sticks when reaching specified position

Common use:

- Sticky headers
- Sidebars
- Navigation bars

### Q. Center alignment techniques

**Answer:**

1. Text center

```css
text-align: center;
```

2. Block center

```css
margin: 0 auto;
width: 200px;
```

3. Flexbox center

```css
display: flex;
justify-content: center;
align-items: center;
```

4. Grid center

```css
display: grid;
place-items: center;
```

## Flexbox & Grid

### Q. What is Flexbox?

**Answer:**

Flexbox is a one-dimensional CSS layout system used to align and distribute items efficiently.

```css
.container {
  display: flex;
}
```

Features:

- Easy alignment
- Flexible sizing
- Responsive layouts

Axes:

- Main axis
- Cross axis

### Q. Flexbox properties (flex-grow, align-content, etc.)

**Answer:**

Container properties

| Property          | Purpose              |
| ----------------- | -------------------- |
| `display:flex`    | Enable flexbox       |
| `flex-direction`  | Row/column direction |
| `justify-content` | Main-axis alignment  |
| `align-items`     | Cross-axis alignment |
| `align-content`   | Multi-line alignment |
| `flex-wrap`       | Wrapping control     |

Item properties

| Property      | Purpose              |
| ------------- | -------------------- |
| `flex-grow`   | Expand item          |
| `flex-shrink` | Shrink item          |
| `flex-basis`  | Initial size         |
| `align-self`  | Individual alignment |
| `order`       | Change display order |

Example:

```css
.item {
  flex-grow: 1;
}
```

### Q. flex: 1

**Answer:**

`flex: 1` is shorthand for:

```css
flex: 1 1 0;
```

Meaning:

- flex-grow: 1
- flex-shrink: 1
- flex-basis: 0

Effect:

Item expands equally to fill available space.

Example:

```css
.item {
  flex: 1;
}
```

### Q. What is CSS Grid?

**Answer:**

CSS Grid is a two-dimensional layout system for rows and columns.

```css
.container {
  display: grid;
}
```

Features:

- Row + column control
- Complex layouts
- Precise placement

Example:

```css
.container {
  display: grid;
  grid-template-columns: 1fr 1fr;
}
```

### Q. Grid system

**Answer:**

A grid system divides a page into structured columns and rows.

Common example:

12-column layout

Used in:

- Responsive frameworks
- Dashboards
- Page layouts

### Q. Grid vs Flexbox differences

**Answer:**

| Feature   | Flexbox         | Grid              |
| --------- | --------------- | ----------------- |
| Dimension | One-dimensional | Two-dimensional   |
| Best for  | Components/UI   | Full layouts      |
| Direction | Row OR column   | Rows AND columns  |
| Alignment | Content flow    | Precise placement |

Use Flexbox for:

- Navigation bars
- Buttons
- Small layouts

Use Grid for:

- Full-page layouts
- Complex dashboards
- Multi-row structures

## Units & Dimensions

### Q. CSS units (px, %, em, rem)

**Answer:**

CSS units define the size of elements, text, spacing, and layouts.

Absolute Unit

`px` (Pixels)

```css
width: 200px;
font-size: 16px;
```

- Fixed size
- Most commonly used
- Does not scale relative to parent

Relative Units

`%`

```css
width: 50%;
```

Relative to parent element

`em`

```css
font-size: 2em;
```

Relative to parent's font size

`rem`

```css
font-size: 2rem;
```

Relative to root (`html`) font size

Quick Comparison

| Unit | Relative To      |
| ---- | ---------------- |
| px   | Fixed pixels     |
| %    | Parent element   |
| em   | Parent font size |
| rem  | Root font size   |

### Q. Difference between em vs rem

**Answer:**

| Feature        | em               | rem            |
| -------------- | ---------------- | -------------- |
| Relative to    | Parent font size | Root font size |
| Nested scaling | ✅ Yes           | ❌ No          |
| Predictability | Lower            | Higher         |

Example

```css
html {
  font-size: 16px;
}

.parent {
  font-size: 20px;
}

.child {
  font-size: 2em;
}
```

👉 Child = 40px

```css
.child {
  font-size: 2rem;
}
```

👉 Child = 32px

Interview Tip

- `em` scales based on parent
- `rem` scales based on root
- Most modern projects prefer `rem`

### Q. Viewport units (vh, vw)

**Answer:**

Viewport units are relative to browser window size.

Unit Meaning

| Unit | Meaning         |
| ---- | --------------- |
| vw   | Viewport width  |
| vh   | Viewport height |

Example

```css
width: 50vw;
height: 100vh;
```

Common Usage

Full-screen hero section:

```css
.hero {
  height: 100vh;
}
```

Examples

| Viewport Width | 50vw  |
| -------------- | ----- |
| 1000px         | 500px |

| Viewport Height | 100vh |
| --------------- | ----- |
| 800px           | 800px |

### Q. How to define element dimensions

**Answer:**

Element dimensions are controlled using sizing properties.

Width

```css
width: 300px;
```

Height

```css
height: 200px;
```

Min Width

```css
min-width: 200px;
```

Max Width

```css
max-width: 100%;
```

Min Height

```css
min-height: 100px;
```

Max Height

```css
max-height: 500px;
```

Responsive Example

```css
img {
  width: 100%;
  height: auto;
}
```

Important Interview Point

Dimensions are affected by:

- Width
- Height
- Padding
- Border
- `box-sizing`

## Colors & Backgrounds

### Q. Hex vs RGB color

**Answer:**

Both are used to define colors in CSS.

Hex Color

```css
color: #ff0000;
```

Format:

```
#RRGGBB
```

Example:

- `#ff0000` → Red
- `#00ff00` → Green
- `#0000ff` → Blue

RGB Color

```css
color: rgb(255, 0, 0);
```

Format:

```
rgb(red, green, blue)
```

Comparison

| Feature              | Hex         | RGB         |
| -------------------- | ----------- | ----------- |
| Readability          | Moderate    | High        |
| Transparency support | Via Hex8    | Via RGBA    |
| Common usage         | Very common | Very common |

### Q. Background vs color difference

**Answer:**

| Property   | Purpose            |
| ---------- | ------------------ |
| color      | Text color         |
| background | Element background |

Example

```css
p {
  color: white;
  background: blue;
}
```

Result

- Text = white
- Background = blue

### Q. Gradient in CSS (types)

**Answer:**

A gradient creates a smooth transition between colors.

1. Linear Gradient

```css
background: linear-gradient(red, blue);
```

Direction Example

```css
background: linear-gradient(to right, red, blue);
```

2. Radial Gradient

```css
background: radial-gradient(red, blue);
```

Creates circular color transition.

3. Conic Gradient

```css
background: conic-gradient(red, yellow, blue);
```

Creates pie-chart style gradient.

Gradient Types Summary

| Type   | Shape               |
| ------ | ------------------- |
| Linear | Straight line       |
| Radial | Circle/Ellipse      |
| Conic  | Around center point |

### Q. Transparent overlays

**Answer:**

Transparent overlays place a semi-transparent layer over content or images.

Using RGBA

```css
.overlay {
  background: rgba(0, 0, 0, 0.5);
}
```

Example

```css
.hero {
  background: linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)), url(hero.jpg);
}
```

Uses

- Improve text readability
- Hero sections
- Modal backgrounds

### Q. Responsive background images

**Answer:**

Responsive background images adapt to different screen sizes.

Common Technique

```css
.hero {
  background-image: url(hero.jpg);
  background-size: cover;
  background-position: center;
}
```

Important Properties

| Property                 | Purpose         |
| ------------------------ | --------------- |
| background-size: cover   | Fill container  |
| background-size: contain | Show full image |
| background-position      | Alignment       |
| background-repeat        | Prevent tiling  |

Example

```css
.hero {
  background-image: url(hero.jpg);
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
}
```

## Typography

### Q. Font-related properties

**Answer:**

Font-related CSS properties control the appearance of text.

Common Font Properties

| Property         | Purpose               |
| ---------------- | --------------------- |
| `font-family`    | Font type             |
| `font-size`      | Text size             |
| `font-weight`    | Thickness             |
| `font-style`     | Normal/italic         |
| `font-variant`   | Small caps            |
| `line-height`    | Line spacing          |
| `letter-spacing` | Space between letters |
| `word-spacing`   | Space between words   |

Example

```css
p {
  font-family: Arial, sans-serif;
  font-size: 16px;
  font-weight: bold;
  line-height: 1.5;
}
```

Font Shorthand

```css
font:
  italic bold 16px/1.5 Arial,
  sans-serif;
```

### Q. Font-face property

**Answer:**

`@font-face` allows custom fonts to be loaded and used on a website.

Example

```css
@font-face {
  font-family: "MyFont";
  src: url("MyFont.woff2") format("woff2");
}
```

Usage

```css
body {
  font-family: "MyFont", sans-serif;
}
```

Benefits

- Custom branding
- Consistent typography
- No dependency on user-installed fonts

Common Font Formats

| Format | Usage         |
| ------ | ------------- |
| WOFF2  | Recommended   |
| WOFF   | Good support  |
| TTF    | Larger files  |
| OTF    | Desktop fonts |

### Q. Text overflow (ellipsis)

**Answer:**

`text-overflow: ellipsis` truncates overflowing text and displays ....

Example

```css
.box {
  width: 200px;
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
}
```

Output

```
This is a very long text...
```

Requirements

Must use:

```css
overflow: hidden;
white-space: nowrap;
text-overflow: ellipsis;
```

Common Use Cases

- Card titles
- Product names
- Table columns

### Q. Multi-line ellipsis

**Answer:**

Multi-line truncation limits text to a specific number of lines.

Example

```css
.description {
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
}
```

Result

```
Line 1
Line 2
Line 3...
```

Common Use Cases

- Blog cards
- News previews
- Product descriptions

Important Interview Point

Single-line ellipsis:

```css
text-overflow: ellipsis;
```

Multi-line ellipsis:

```css
-webkit-line-clamp;
```

### Q. Explain clamp() function

## Transforms, Transitions & Animations

### Q. Transform property (2D & 3D)

**Answer:**

The `transform` property modifies an element's position, size, rotation, or shape without affecting document flow.

2D Transforms

Translate

```css
transform: translate(50px, 20px);
```

Scale

```css
transform: scale(1.5);
```

Rotate

```css
transform: rotate(45deg);
```

Skew

```
transform: skew(20deg);
```

3D Transforms

Rotate X

```css
transform: rotateX(45deg);
```

Rotate Y

```css
transform: rotateY(45deg);
```

Translate Z

```css
transform: translateZ(100px);
```

Combining Transforms

```css
transform: translateX(20px) rotate(30deg);
```

### Q. Translate vs absolute positioning

**Answer:**

| Feature                    | Translate | Absolute Positioning |
| -------------------------- | --------- | -------------------- |
| Layout affected            | ❌ No     | ❌ No                |
| Creates movement           | ✅ Yes    | ✅ Yes               |
| GPU acceleration           | ✅ Yes    | ❌ Usually No        |
| Animation performance      | Better    | Slower               |
| Original position retained | ✅ Yes    | ❌ No                |

Translate Example

```css
transform: translateX(100px);
```

Absolute Example

```css
position: absolute;
left: 100px;
```

Interview Tip

Use `transform: translate()` for animations whenever possible.

### Q. CSS transitions

**Answer:**

Transitions create smooth changes between CSS property values.

Example

```css
button {
  transition: background-color 0.3s;
}

button:hover {
  background-color: red;
}
```

Result

Background color changes smoothly instead of instantly.

Common Uses

- Hover effects
- Menus
- Buttons
- Cards

### Q. Transition property syntax

**Answer:**

Syntax:

```css
transition: property duration timing-function delay;
```

Example

```css
transition: all 0.3s ease;
```

Individual Properties

```css
transition-property: transform;
transition-duration: 0.3s;
transition-timing-function: ease;
transition-delay: 0s;
```

Example

```css
.card {
  transition: transform 0.3s ease-in-out;
}
```

### Q. CSS animations (example)

**Answer:**

Animations use `@keyframes` to define intermediate states.

Example

```css
@keyframes fadeIn {
  from {
    opacity: 0;
  }

  to {
    opacity: 1;
  }
}

.box {
  animation: fadeIn 1s ease;
}
```

Animation Shorthand

```css
animation: fadeIn 1s ease 0s 1 normal forwards;
```

Common Uses

- Loaders
- Banners
- UI effects
- Micro-interactions

### Q. Animation timing functions

**Answer:**

Timing functions control animation speed progression.

Common Values

| Function      | Behavior           |
| ------------- | ------------------ |
| `linear`      | Constant speed     |
| `ease`        | Slow → Fast → Slow |
| `ease-in`     | Slow start         |
| `ease-out`    | Slow end           |
| `ease-in-out` | Slow both ends     |

Example

```css
animation-timing-function: ease-in-out;
```

Custom Timing

```css
animation-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
```

### Q. Tweening in CSS

**Answer:**

Tweening (in-betweening) is the process of generating intermediate values between animation states.

Example

```css
@keyframes move {
  from {
    left: 0;
  }

  to {
    left: 200px;
  }
}
```

Browser automatically creates intermediate positions:

```
0px → 20px → 40px → 60px → ... → 200px
```

Why Important?

Without tweening:

```
0px → 200px
```

Instant jump

With tweening:

```
Smooth motion
```

## Responsive Design

### Q. Responsive vs adaptive design

**Answer:**

Both approaches aim to make websites work on different screen sizes.

Responsive Design

- Uses fluid layouts
- Uses flexible images
- Uses media queries
- Layout changes continuously

Example:

```css
.container {
  width: 100%;
}
```

Adaptive Design

- Uses predefined layouts
- Different layouts for specific screen sizes
- Layout changes at fixed breakpoints

Example:

```
320px → Mobile Layout
768px → Tablet Layout
1200px → Desktop Layout
```

Differences

| Feature        | Responsive | Adaptive             |
| -------------- | ---------- | -------------------- |
| Layout         | Fluid      | Fixed layouts        |
| Flexibility    | High       | Moderate             |
| Maintenance    | Easier     | Harder               |
| Device Support | Better     | Specific breakpoints |

### Q. Fluid vs adaptive design

**Answer:**

Fluid Design

Uses relative units:

```
width: 80%;
```

Layout continuously grows and shrinks.

Adaptive Design

Uses fixed breakpoints:

```
width: 960px;
```

Layout switches between predefined versions.

Differences

| Feature     | Fluid              | Adaptive         |
| ----------- | ------------------ | ---------------- |
| Units       | %, vw, rem         | Mostly px        |
| Behavior    | Continuous scaling | Layout switching |
| Flexibility | High               | Medium           |

### Q. Media queries & types

**Answer:**

Media queries allow CSS to apply styles based on device characteristics.

Syntax

```css
@media (max-width: 768px) {
  .menu {
    display: none;
  }
}
```

Common Media Types

| Type     | Purpose        |
| -------- | -------------- |
| `all`    | All devices    |
| `screen` | Screens        |
| `print`  | Printed pages  |
| `speech` | Screen readers |

Examples

Mobile

```css
@media (max-width: 768px) {
}
```

Tablet

```css
@media (min-width: 768px) and (max-width: 1024px) {
}
```

Desktop

```css
@media (min-width: 1025px) {
}
```

### Q. How to hide/show elements based on screen size

**Answer:**

Using media queries.

Hide on mobile

```css
@media (max-width: 768px) {
  .desktop-only {
    display: none;
  }
}
```

Show only on mobile

```css
.mobile-only {
  display: none;
}

@media (max-width: 768px) {
  .mobile-only {
    display: block;
  }
}
```

Alternative

```css
visibility: hidden;
```

Difference:

| Property          | Space Reserved? |
| ----------------- | --------------- |
| display:none      | ❌ No           |
| visibility:hidden | ✅ Yes          |

### Q. Responsive text techniques

**Answer:**

Responsive text adapts to screen size.

Using

```css
font-size: 1rem;
```

Using viewport units

```css
font-size: 3vw;
```

Using clamp()

```css
font-size: clamp(1rem, 2vw, 2rem);
```

Meaning:

```
Minimum → 1rem
Preferred → 2vw
Maximum → 2rem
```

Example

```css
h1 {
  font-size: clamp(2rem, 5vw, 4rem);
}
```

Interview Tip

`clamp()` is the preferred modern solution for responsive typography.

## Advanced Features

### Q. CSS variables (custom properties)

**Answer:**

CSS Variables store reusable values.

Declaration

```css
:root {
  --primary-color: blue;
}
```

Usage

```css
button {
  background: var(--primary-color);
}
```

Benefits

- Reusable values
- Easier maintenance
- Theme support

Example

```css
:root {
  --spacing: 16px;
}
```

### Q. CSS counters

**Answer:**

CSS Counters automatically generate numbering.

Example

```css
body {
  counter-reset: section;
}

h2::before {
  counter-increment: section;
  content: counter(section) ". ";
}
```

Output

```
1. Introduction
2. About
3. Contact
```

Common Uses

- Documentation
- Chapters
- FAQ numbering

### Q. Overflow (hidden, etc.)

**Answer:**

The overflow property controls content that exceeds element boundaries.

Values

| Value   | Behavior              |
| ------- | --------------------- |
| visible | Default               |
| hidden  | Hide overflow         |
| scroll  | Always show scrollbar |
| auto    | Scrollbar when needed |

Example

```css
.box {
  overflow: hidden;
}
```

Horizontal & Vertical

```
overflow-x: auto;
overflow-y: scroll;
```

### Q. inherit keyword

**Answer:**

`inherit` forces a property to inherit its parent's value.

Example

```css
.parent {
  color: blue;
}

.child {
  color: inherit;
}
```

Result

```
Child text becomes blue
```

Useful For

- Consistent theming
- Component styling

### Q. calc() function

**Answer:**

`calc()` performs calculations inside CSS.

Syntax

```css
width: calc(100% - 50px);
```

Example

```css
.sidebar {
  width: 250px;
}

.content {
  width: calc(100% - 250px);
}
```

Supports

- Addition (+)
- Subtraction (-)
- Multiplication (\*)
- Division (/)

### Q. Progressive rendering

**Answer:**

Progressive rendering improves perceived performance by displaying content as soon as possible.

Techniques

1. Critical CSS
2. Lazy loading
3. Skeleton screens
4. Code splitting
5. Resource prioritization

Example

```html
<img loading="lazy" src="image.jpg" />
```

Benefits

- Faster perceived load time
- Better user experience
- Improved Core Web Vitals

### Q. Feature detection in browsers

**Answer:**

Feature detection checks whether a browser supports a feature before using it.

CSS Feature Detection

Using `@supports`

```css
@supports (display: grid) {
  .container {
    display: grid;
  }
}
```

JavaScript Feature Detection

```js
if ("geolocation" in navigator) {
  console.log("Supported");
}
```

Why Important?

- Progressive enhancement
- Better compatibility
- Graceful degradation

Example

```css
@supports (backdrop-filter: blur(10px)) {
  .card {
    backdrop-filter: blur(10px);
  }
}
```

## Pseudo Classes & Elements

### Q. Pseudo-classes vs pseudo-elements

**Answer:**

Both allow styling without adding extra HTML.

Pseudo-class (`:`)

Targets a specific state of an element.

Examples:

```css
a:hover {
}
input:focus {
}
li:first-child {
}
```

Pseudo-element (`::`)

Targets a specific part of an element.

Examples:

```css
p::first-letter {
}
p::before {
}
p::after {
}
```

Differences

| Feature | Pseudo-class | Pseudo-element  |
| ------- | ------------ | --------------- |
| Syntax  | `:`          | `::`            |
| Targets | State        | Part of element |
| Example | `:hover`     | `::before`      |

### Q. :hover vs :focus

**Answer:**

`:hover`

Activated when mouse is over an element.

```css
button:hover {
  background: red;
}
```

`:focus`

Activated when element receives keyboard focus.

```css
input:focus {
  border-color: blue;
}
```

Differences

| Feature          | :hover | :focus |
| ---------------- | ------ | ------ |
| Mouse required   | ✅ Yes | ❌ No  |
| Keyboard support | ❌ No  | ✅ Yes |
| Accessibility    | Lower  | Higher |

Interview Tip

Always provide visible `:focus` styles for accessibility.

### Q. ::before and ::after

**Answer:**

Used to insert content before or after an element.

Example

```css
.btn::before {
  content: "★";
}

.btn::after {
  content: "→";
}
```

Requirements

```css
content: "";
```

is mandatory.

Common Uses

- Icons
- Decorative elements
- Badges
- Tooltips

### Q. ::first-letter, ::first-line, :first-child

**Answer:**

`::first-letter`

Styles first letter.

```css
p::first-letter {
  font-size: 2rem;
}
```

`::first-line`

Styles first line.

```css
p::first-line {
  font-weight: bold;
}
```

`:first-child`

Selects first child element.

```css
li:first-child {
  color: red;
}
```

Differences

| Selector         | Purpose             |
| ---------------- | ------------------- |
| `::first-letter` | First letter        |
| `::first-line`   | First line          |
| `:first-child`   | First child element |

## Performance & Optimization

### Q. CSS sprites

**Answer:**

CSS Sprites combine multiple images into a single image file.

Benefits

- Fewer HTTP requests
- Faster loading
- Better performance

Example

```css
.icon-home {
  background-position: 0 0;
}
```

### Q. File splitting

**Answer:**

File splitting organizes CSS into multiple files.

Example:

```
base.css
layout.css
components.css
utilities.css
```

Benefits

- Easier maintenance
- Better scalability
- Team collaboration

### Q. Fixing browser-specific issues

**Answer:**

Common techniques:

Vendor prefixes

```css
-webkit-transform: rotate(20deg);
transform: rotate(20deg);
```

Feature detection

```css
@supports (display: grid) {
}
```

CSS Reset/Normalize

Helps reduce browser inconsistencies.

### Q. Reset vs Normalize CSS

**Answer:**

Reset CSS

Removes browser default styles.

Example:

```css
* {
  margin: 0;
  padding: 0;
}
```

Normalize CSS

Keeps useful defaults while normalizing differences.

Differences

| Feature            | Reset | Normalize |
| ------------------ | ----- | --------- |
| Removes styles     | Yes   | No        |
| Preserves defaults | No    | Yes       |
| Aggressive         | Yes   | No        |

## Preprocessors & Architecture

### Q. What is CSS preprocessor?

**Answer:**

A CSS preprocessor extends CSS with programming-like features.

Examples:

- Sass
- Less
- Stylus

Features

- Variables
- Mixins
- Nesting
- Functions

Example

```css
$primary: blue;

button {
  color: $primary;
}
```

### Q. Sass, Less, Stylus

**Answer:**

Popular CSS preprocessors.

| Feature            | Sass    | Less   | Stylus   |
| ------------------ | ------- | ------ | -------- |
| Popularity         | Highest | High   | Moderate |
| Syntax flexibility | Medium  | Medium | High     |
| Ecosystem          | Large   | Medium | Smaller  |

Examples

Sass

```css
$color: blue;
```

Less

```css
@color: blue;
```

Stylus

```css
color = blue
```

### Q. Mixins / functions

**Answer:**

Mixins

Reusable blocks of styles.

```css
@mixin center {
  display: flex;
  justify-content: center;
  align-items: center;
}
```

Usage:

```css
.box {
  @include center;
}
```

Functions

Return calculated values.

```scss
@function double($size) {
  @return $size \* 2;
}
```

### Q. CSS variables vs preprocessor variables

**Answer:**

| Feature         | CSS Variables   | Sass Variables |
| --------------- | --------------- | -------------- |
| Runtime changes | ✅ Yes          | ❌ No          |
| Browser support | Modern browsers | Compiled away  |
| JS access       | ✅ Yes          | ❌ No          |

CSS Variable

```css
:root {
  --primary: blue;
}
```

Sass Variable

```css
$primary: blue;
```

## Miscellaneous

### Q. Accessibility (a11y)

**Answer:**

Accessibility ensures websites are usable by everyone.

Best Practices

- Semantic HTML
- Keyboard navigation
- Visible focus states
- Proper contrast ratios
- Alt text for images

Example

```html
<img src="logo.png" alt="Company Logo" />
```

### Q. DOM reflow

**Answer:**

Reflow occurs when browser recalculates layout.

Triggers:

- Width changes
- Height changes
- DOM updates

Expensive Operations

```js
element.style.width = "200px";
```

Optimization

- Batch DOM updates
- Prefer transforms

### Q. Image scroll control property

**Answer:**

The most common property is:

```css
background-attachment: fixed;
```

Values

| Value  | Behavior               |
| ------ | ---------------------- |
| scroll | Default                |
| fixed  | Fixed during scrolling |
| local  | Scroll with content    |

### Q. Underline removal in links

**Answer:**

```css
a {
  text-decoration: none;
}
```

Restore on hover

```css
a:hover {
  text-decoration: underline;
}
```

### Q. Pagination in CSS

**Answer:**

CSS alone does not create pagination logic.

However for print:

```css
.page {
  break-after: page;
}
```

For web pagination:

- CSS styles controls
- JavaScript/backend controls page changes

### Q. Automatic numbering using counters

**Answer:**

CSS Counters generate numbering automatically.

```css
body {
  counter-reset: section;
}

h2::before {
  counter-increment: section;
  content: counter(section) ". ";
}
```

Output

```
1. Introduction
2. Features
3. Contact
```

### Q. Why background & color are separate

**Answer:**

They control different parts of an element.

| Property   | Controls        |
| ---------- | --------------- |
| color      | Text            |
| background | Background area |

Example:

```css
p {
  color: white;
  background: black;
}
```

Benefits

- Independent control
- Better design flexibility
- Easier theming

### Q. CSS working under the hood

**Answer:**

When a page loads:

1. Browser downloads HTML
2. Browser downloads CSS
3. CSS is parsed into CSSOM
4. HTML becomes DOM
5. DOM + CSSOM → Render Tree
6. Layout (Reflow)
7. Paint
8. Composite

Rendering Pipeline

```
HTML → DOM
CSS → CSSOM

DOM + CSSOM
↓
Render Tree
↓
Layout
↓
Paint
↓
Composite
```
