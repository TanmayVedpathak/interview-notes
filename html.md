# HTML (HyperText Markup Language)

## Basics & Fundamentals

### Q. What is HTML?

**Answer:**

Definition

HTML (HyperText Markup Language) is the standard language used to create and structure web pages.

Purpose

- Defines structure, not styling
- Works with CSS (design) + JS (behavior)

Example

```html
<!DOCTYPE html>
<html>
  <head>
    <title>My Page</title>
  </head>
  <body>
    <h1>Hello World</h1>
  </body>
</html>
```

🔥 Interview Line

HTML is a markup language used to structure content on the web using elements and tags.

### Q. What is the difference between HTML elements and tags?

**Answer:**

HTML Tag

The syntax used to mark content

```html
<p></p>
```

HTML Element

Complete structure → opening tag + content + closing tag

```html
<p>Hello</p>
```

Key Difference

| Feature          | Tag           | Element            |
| ---------------- | ------------- | ------------------ |
| Meaning          | Markup syntax | Complete structure |
| Includes content | ❌ No         | ✅ Yes             |

🔥 Interview Line

A tag is the syntax, while an element includes the tag along with its content.

### Q. Difference between tags, attributes, and elements

**Answer:**

Tag

```html
<a> </a>
```

Attribute

Provides additional information

```html
<a href="https://example.com">Link</a>
```

👉 `href` = attribute

Element

Full structure

```html
<a href="https://example.com">Link</a>
```

Summary

| Term      | Meaning               |
| --------- | --------------------- |
| Tag       | Markup syntax         |
| Attribute | Extra info inside tag |
| Element   | Tag + content         |

🔥 Interview Line

Tags define structure, attributes add extra information, and elements represent the complete unit.

### Q. Does `<!DOCTYPE html>` tag is a HTML tag?

**Answer:**

👉 ❌ No, it is NOT a tag

Definition

It is a declaration that tells the browser:

👉 “This document is HTML5”

Purpose

Ensures browser uses standards mode

🔥 Interview Line

`<!DOCTYPE html>` is a declaration, not an HTML tag, and it tells the browser to use HTML5 standards.

### Q. What are void elements in HTML?

**Answer:**
Definition

Elements that do not have closing tags

Examples

```html
<br />
<img src="image.jpg" />
<input type="text" />
<hr />
```

Key Points

- Cannot have content inside
- Self-closing by nature

🔥 Interview Line

Void elements are HTML elements that do not require closing tags and cannot contain content.

### Q. What are empty elements?

**Answer:**

Definition

Elements that have no content

Example

```html
<p></p>
```

Key Difference

| Feature     | Void Elements  | Empty Elements     |
| ----------- | -------------- | ------------------ |
| Closing Tag | ❌ No          | ✅ Yes             |
| Content     | ❌ Not allowed | ❌ Currently empty |

🔥 Interview Line

Empty elements have no content but may have closing tags, whereas void elements never have closing tags.

### Q. What happens if you overlap sets of tags?

**Answer:**

Example (Incorrect HTML)

```html
<b><i>Text</b></i>
```

Problem

Tags are not properly nested

Result

- Browser tries to fix it automatically
- Can lead to:
  - Unexpected layout ❌
  - Broken structure ❌
  - Styling issues ❌

Correct Way

```html
<b><i>Text</i></b>
```

Rule

👉 Always properly nest tags

🔥 Interview Line

Overlapping tags break proper nesting, leading to unpredictable rendering and potential layout issues.

🚀 Final Summary

- HTML → structure of web pages
- Tag vs Element → syntax vs full structure
- Attributes → extra info
- DOCTYPE → declaration, not tag
- Void elements → no closing tag
- Empty elements → no content
- Overlapping → invalid HTML

## Attributes & Metadata

### Q. What are HTML attributes?

**Answer:**

Definition

- Attributes provide additional information about HTML elements.
- They are always written in the opening tag.

Syntax

```html
<tag attribute="value">Content</tag>
```

Example

```html
<a href="https://example.com">Visit</a>
```

👉 href is an attribute

Common Attributes

| Attribute | Purpose           |
| --------- | ----------------- |
| `href`    | Link destination  |
| `src`     | Image source      |
| `alt`     | Image description |
| `id`      | Unique identifier |
| `class`   | Styling/grouping  |

🔥 Interview Line

HTML attributes provide additional information about elements and are defined inside opening tags.

### Q. Can attribute values be anything or are there specific values?

**Answer:**

👉 ❌ Not anything — depends on the attribute

Types of Attribute Values

1. Predefined Values

```html
<input type="text" />
```

👉 `type` must be specific (`text`, `password`, etc.)

2. Free Values

```html
<div id="header"></div>
```

👉 `id` can be any valid name

3. Boolean Attributes

```html
<input disabled />
```

👉 Presence = true

Key Insight

- Some attributes are restricted
- Some are flexible

🔥 Interview Line

Attribute values depend on the attribute type—some accept predefined values, while others allow custom values.

### Q. What is the role of the <meta> tag in HTML?

**Answer:**

Definition

Provides metadata about the webpage

Uses

- Character encoding
- SEO (description, keywords)
- Viewport (responsive design)
- Browser behavior

Examples

```html
<meta name="description" content="Best website" /> <meta name="viewport" content="width=device-width, initial-scale=1.0" />
```

Key Point

Placed inside `<head>`

🔥 Interview Line

The `<meta>` tag provides metadata like character encoding, viewport settings, and SEO information.

### Q. How to indicate the character set in HTML?

**Answer:**

Using <meta charset="UTF-8">

Example

```html
<meta charset="UTF-8" />
```

Why Important

- Ensures correct display of text
- Supports multiple languages

🔥 Interview Line

The character set is defined using `<meta charset="UTF-8">` to ensure proper text rendering.

### Q. Why is a URL encoded in HTML?

**Answer:**

Reason

👉 URLs can only contain valid ASCII characters

Problem

- Special characters like:
  - space
  - `@`, `#`, `&`

👉 Can break URLs

Solution

Encode them into safe format

Example

```
Original: hello world
Encoded: hello%20world
```

🔥 Interview Line

URLs are encoded to ensure special characters are safely transmitted over the internet.

### Q. What is URL Encoding?

**Answer:**

Definition

Process of converting characters into a format that can be safely transmitted in URLs

How it Works

Replaces unsafe characters with % + hex value

Examples

| Character | Encoded |
| --------- | ------- |
| Space     | `%20`   |
| `@`       | `%40`   |
| `&`       | `%26`   |

Example

```
https://example.com/search?q=hello%20world
```

Key Points

- Also called percent encoding
- Used in query strings and URLs

🔥 Interview Line

URL encoding converts special characters into a safe format using percent encoding for reliable transmission.

🚀 Final Summary

- Attributes → extra info in tags
- Values → predefined or flexible
- `<meta>` → metadata (SEO, charset, viewport)
- Charset → UTF-8 for proper text
- URL encoding → safe URL transmission

## Semantic HTML

### Q. What is semantic HTML?

**Answer:**

Definition

Semantic HTML means using HTML elements that clearly describe their meaning and purpose.

Example

```html
<header>
  <h1>Website Title</h1>
</header>

<main>
  <article>Blog content</article>
</main>

<footer>Footer info</footer>
```

Why Important

- Better SEO ✅
- Improved accessibility ✅
- Cleaner, readable code ✅

🔥 Interview Line

Semantic HTML uses meaningful tags to describe content structure, improving SEO and accessibility.

### Q. What are semantic elements?

**Answer:**

Definition

Elements that describe their purpose clearly

Examples

| Element     | Purpose             |
| ----------- | ------------------- |
| `<header>`  | Top section         |
| `<nav>`     | Navigation          |
| `<main>`    | Main content        |
| `<section>` | Section of content  |
| `<article>` | Independent content |
| `<aside>`   | Sidebar             |
| `<footer>`  | Bottom section      |

Non-Semantic Elements

- `<div>`
- `<span>`

👉 Do not convey meaning

🔥 Interview Line

Semantic elements describe the role of content, unlike non-semantic elements like div and span.

### Q. What are logical and physical tags in HTML?

**Answer:**

Physical Tags

👉 Define appearance (visual style)

```html
<b>Bold</b> <i>Italic</i>
```

Logical Tags

👉 Define meaning (semantic importance)

```html
<strong>Important</strong> <em>Emphasized</em>
```

Key Difference

| Feature       | Physical Tags  | Logical Tags |
| ------------- | -------------- | ------------ |
| Focus         | Style          | Meaning      |
| SEO           | ❌ Not helpful | ✅ Helpful   |
| Accessibility | ❌ Poor        | ✅ Better    |

🔥 Interview Line

Physical tags control appearance, while logical tags convey meaning and improve accessibility.

### Q. Difference between `<strong>`, `<b>` and `<em>`, `<i>`

**Answer:**

`<b>` vs `<strong>`

| Feature  | `<b>`     | `<strong>`     |
| -------- | --------- | -------------- |
| Meaning  | Bold text | Important text |
| Semantic | ❌ No     | ✅ Yes         |
| SEO      | ❌ No     | ✅ Yes         |

Example

```html
<b>Bold text</b> <strong>Important text</strong>
```

`<i>` vs `<em>`

| Feature       | `<i>`  | `<em>`   |
| ------------- | ------ | -------- |
| Meaning       | Italic | Emphasis |
| Semantic      | ❌ No  | ✅ Yes   |
| Accessibility | ❌ No  | ✅ Yes   |

Example

```html
<i>Italic text</i> <em>Emphasized text</em>
```

Key Insight

👉 Browsers may render both similarly

👉 But semantics matter for SEO & screen readers

🔥 Interview Line

`<strong>` and `<em>` add semantic meaning, while `<b>` and `<i>` only affect appearance.

🚀 Final Summary

- Semantic HTML → meaningful structure
- Semantic elements → describe content role
- Logical tags → meaning
- Physical tags → styling
- Prefer `<strong>` / `<em>` over `<b>` / `<i>`

## Elements & Layout

### Q. Difference between `<div>` and `<span>`

**Answer:**

`<div>`

- It is a block-level element
- Takes full width of its parent container
- Always starts on a new line
- Used for structuring large sections/layout

```html
<div>This is a div</div>
<div>Another div</div>
```

`<span>`

- It is an inline element
- Takes only required width
- Does not start on a new line
- Used for styling small parts of text

```html
<p>This is a <span style="color:red;">red</span> word.</p>
```

Key Difference

| Feature    | `<div>`         | `<span>`      |
| ---------- | --------------- | ------------- |
| Type       | Block           | Inline        |
| Width      | Full width      | Content width |
| Line break | Yes             | No            |
| Use case   | Layout/sections | Text styling  |

### Q. Inline vs Block Elements

**Answer:**

Block Elements

- Take full width
- Start on a new line
- Can contain inline & block elements

Examples:

```html
<div></div>

<p></p>

<h1></h1>
to
<h6></h6>

<section></section>

<article></article>
```

Inline Elements

- Take only necessary width
- Stay in the same line
- Cannot contain block elements

Examples:

```html
<span></span>, <a></a>, <strong></strong>, <em></em>, <img />
```

Example:

```html
<p>This is <span>inline</span> and <span>text</span></p>

<div>Block 1</div>
<div>Block 2</div>
```

### Q. How to separate a section of text in HTML?

**Answer:**

There are multiple ways, depending on purpose:

1. Using `<p>` (Paragraph)

```html
<p>This is paragraph 1</p>
<p>This is paragraph 2</p>
```

2. Using `<br>` (Line Break)

```html
Line 1<br />
Line 2
```

3. Using `<hr>` (Horizontal Line)

```html
<hr />
```

4. Using semantic tags (BEST PRACTICE)

```html
<section>
  <h2>Title</h2>
  <p>Content here</p>
</section>
```

Other useful tags:

- `<article>`
- `<div>`
- `<section>`

5. Using CSS spacing

```html
<p style="margin-bottom:20px;">Text 1</p>
<p>Text 2</p>
```

### Q. How many ways can we position an HTML element?

**Answer:**

There are 5 main positioning types in CSS:

1. `static` (default)

```css
position: static;
```

- Normal flow
- No positioning applied

2. `relative`

```css
position: relative;
top: 10px;
```

Moves relative to itself

3. `absolute`

```css
position: absolute;
top: 0;
left: 0;
```

Positioned relative to nearest positioned parent

4. `fixed`

```css
position: fixed;
top: 0;
```

- Fixed relative to viewport
- Does not move on scroll

5. `sticky`

```css
position: sticky;
top: 0;
```

- Acts like relative + fixed
- Sticks when scrolling

### Q. How to redirect to a particular section of a page?

**Answer:**

You use anchor links with `id`.

Step 1: Create a target section

```html
<h2 id="about">About Section</h2>
```

Step 2: Link to it

```html
<a href="#about">Go to About</a>
```

How it works:

- `#about` refers to element with `id="about"`
- Browser scrolls to that section

Bonus: Smooth scrolling (CSS)

```css
html {
  scroll-behavior: smooth;
}
```

## Links & Navigation

### Q. Difference between `<link>` and `<a>` tag

**Answer:**

`<link>` tag

- Used to connect external resources to HTML
- Mostly used inside `<head>`
- Not visible to users
- Example: CSS, favicon

```html
<link rel="stylesheet" href="styles.css" />
```

`<a>` (anchor) tag

- Used to create clickable links
- Visible on the webpage
- Navigates to another page/section

```html
<a href="https://example.com">Visit Website</a>
```

Key Differences

| Feature     | `<link>`         | `<a>`      |
| ----------- | ---------------- | ---------- |
| Purpose     | Resource linking | Navigation |
| Visible     | ❌ No            | ✅ Yes     |
| Location    | `<head>`         | `<body>`   |
| Example use | CSS, favicon     | Hyperlinks |

### Q. Difference between Absolute and Relative URL

**Answer:**

Absolute URL

- Full path including protocol + domain
- Works from anywhere

```html
<a href="https://www.google.com">Google</a>
```

Relative URL

- Path based on current file location
- Used within the same website

```html
<a href="/about.html">About</a> <a href="contact.html">Contact</a>
```

Key Differences

| Feature         | Absolute URL   | Relative URL             |
| --------------- | -------------- | ------------------------ |
| Includes domain | ✅ Yes         | ❌ No                    |
| Use case        | External links | Internal navigation      |
| Flexibility     | Fixed          | Depends on file location |

### Q. How to create an email link in HTML?

**Answer:**

You use the `mailto:` protocol inside an anchor tag.

Basic Example

```html
<a href="mailto:example@gmail.com">Send Email</a>
```

With Subject & Body

```html
<a href="mailto:example@gmail.com?subject=Hello&body=How are you?"> Send Email </a>
```

What happens:

- Opens user's default email app
- Pre-fills email details

### Q. Active links vs Normal links

**Answer:**

Normal Link

- Default state (not clicked yet)
- Styled using:

```css
a {
  color: blue;
}
```

Active Link

- When user is clicking (pressing) the link
- Very short stat

```csss
a:active {
color: red;
}
```

Other Important States (Interview Bonus)

```css
a:link { color: blue; } /_ normal _/
a:visited { color: purple; } /_ after click _/
a:hover { color: green; } /_ mouse over _/
a:active { color: red; } /_ while clicking _/
```

Order Rule (Important!)

👉 LVHA order

- `:link`
- `:visited`
- `:hover`
- `:active`

## Lists

### Q. Types of lists in HTML

**Answer:**

HTML provides 3 main types of lists:

1. Ordered List (`<ol>`)

Displays items in a numbered format

```html
<ol>
  <li>Item 1</li>
  <li>Item 2</li>
</ol>
```

👉 Output: 1, 2, 3...

2. Unordered List (`<ul>`)

Displays items with bullets

```html
<ul>
  <li>Item A</li>
  <li>Item B</li>
</ul>
```

👉 Output: ●, ○, ■ etc.

3. Definition List (`<dl>`)

Used for terms and descriptions

```html
<dl>
  <dt>HTML</dt>
  <dd>Markup language</dd>
</dl>
```

Summary

| Type       | Tag    | Use case            |
| ---------- | ------ | ------------------- |
| Ordered    | `<ol>` | Steps, ranking      |
| Unordered  | `<ul>` | General lists       |
| Definition | `<dl>` | Terms & definitions |

### Q. How to change list number type mid-list?

**Answer:**

You can change numbering using:

Method 1: `type` attribute

```html
<ol type="1">
  <li>Item 1</li>
  <li>Item 2</li>
</ol>

<ol type="A">
  <li>Item 3</li>
</ol>
```

Method 2: `start` attribute

```html
<ol start="5">
  <li>Item 5</li>
</ol>
```

Method 3: CSS (list`-style-type`)

```html
<ol style="list-style-type: upper-roman;">
  <li>Item</li>
</ol>
```

Method 4: Nested lists (best for mixed styles)

```html
<ol>
  <li>
    Item 1
    <ol type="a">
      <li>Sub item</li>
    </ol>
  </li>
</ol>
```

### Q. What happens if list-style-type is used on non-list?

**Answer:**

By default:

👉 Nothing happens

```html
<div style="list-style-type: square;">Hello</div>
```

No bullets appear because `<div>` is not a list element

Why?

`list-style-type` works only on:

- `<ul>`
- `<ol>`
- `<li>`

Exception (advanced):

If you force element to behave like a list:

```html
<div style="display: list-item; list-style-type: square;">Hello</div>
```

👉 Now bullet will appear ✅

### Q. Difference between `<menu>`, `<dir>`, and `<ul>`

**Answer:**

`<ul>` (Unordered List)

- Standard, widely used
- Displays bullet points
- Recommended

```html
<ul>
  <li>Item</li>
</ul>
```

`<menu>`

- Originally for menus/toolbars
- Now behaves like `<ul>` in most browsers
- Rarely used

```html
<menu>
  <li>Item</li>
</menu>
```

`<dir>` (Deprecated ❌)

- Used in old HTML for directory lists
- Not supported in modern HTML

```html
<dir>
  <li>Item</li>
</dir>
```

Key Differences

| Tag      | Status        | Usage               |
| -------- | ------------- | ------------------- |
| `<ul>`   | ✅ Standard   | General lists       |
| `<menu>` | ⚠️ Rare       | Menus (limited use) |
| `<dir>`  | ❌ Deprecated | Avoid using         |

## Tables

### Q. What is a cell?

**Answer:**

A cell is the smallest unit inside a table—formed by the intersection of a row and a column.

Created using:

- `<td>` → data cell
- `<th>` → header cell

```html
<table border="1">
  <tr>
    <th>Name</th>
    <th>Age</th>
  </tr>
  <tr>
    <td>Tanmay</td>
    <td>25</td>
  </tr>
</table>
```

👉 Each box you see is a cell

### Q. Cellpadding vs Cellspacing

**Answer:**

`cellpadding`

Space inside a cell (between content and border)

```html
<table cellpadding="10"></table>
```

`cellspacing`

Space between cells

```html
<table cellspacing="10"></table>
```

Key Difference

| Feature        | Cellpadding             | Cellspacing                |
| -------------- | ----------------------- | -------------------------- |
| Space location | Inside cell             | Between cells              |
| Effect         | Increases inner spacing | Creates gaps between cells |

⚠️ Important (Modern HTML)

Both are deprecated in HTML5

👉 Use CSS instead:

```css
td {
  padding: 10px;
}

table {
  border-spacing: 10px;
}
```

### Q. How to merge rows/columns?

**Answer:**

Merge columns → `colspan`

```html
<td colspan="2">Merged Column</td>
```

Merge rows → `rowspan`

```html
<td rowspan="2">Merged Row</td>
```

Example:

```html
<table border="1">
  <tr>
    <td colspan="2">Header</td>
  </tr>
  <tr>
    <td rowspan="2">Side</td>
    <td>Data 1</td>
  </tr>
  <tr>
    <td>Data 2</td>
  </tr>
</table>
```

### Q. What happens if rows/cols ≠ 100%?

**Answer:**

This refers to table width or column widths.

Case 1: Total < 100%

- Extra space remains unused
- Browser may distribute remaining space automatically

Case 2: Total > 100%

- Table may overflow container
- Columns may shrink or break layout

Case 3: Not defined

- Browser auto-adjusts based on content

👉 Browsers use auto layout algorithm, so:

- Exact behavior may vary slightly
- Content plays a big role

### Q. Border vs Rules attributes

**Answer:**

`border`

Controls outer + inner borders

```html
<table border="1"></table>
```

👉 Adds full grid border

`rules`

Controls internal lines only

```html
<table border="1" rules="rows"></table>
```

`rules` values:

| Value  | Meaning               |
| ------ | --------------------- |
| none   | No inner borders      |
| rows   | Horizontal lines only |
| cols   | Vertical lines only   |
| all    | All inner borders     |
| groups | Between row groups    |

⚠️ Important

- rules is obsolete in HTML5
- Use CSS instead:

```CSS
table, td {
  border: 1px solid black;
  border-collapse: collapse;
}
```

🔥 Interview Tip

- Prefer CSS over old HTML attributes
- Know:
  - colspan, rowspan
  - padding vs spacing
  - Deprecated vs modern practices

## Forms

### Q. Types of input fields in HTML

**Answer:**

The `<input>` element supports many types via the type attribute.

Common input types

```html
<input type="text" />
<input type="password" />
<input type="radio" />
<input type="checkbox" />
<input type="submit" />
<input type="button" />
<input type="file" />
<input type="hidden" />
<input type="reset" />
```

Quick idea

- `text` → single-line text
- `password` → masked input
- `radio` → single choice (one option)
- `checkbox` → multiple choices
- `file` → upload files

### Q. Role of action attribute

**Answer:**

Defines where form data is sent after submission.

```html
<form action="/submit-form"></form>
```

👉 When user clicks submit:

Data goes to `/submit-form`

### Q. Role of method attribute

**Answer:**

Specifies how data is sent to the server.

Two main methods:

`GET`

```html
<form method="GET"></form>
```

- Data is visible in URL
- Used for fetching data

👉 Example:

```
/search?q=html
```

`POST`

```html
<form method="POST"></form>
```

- Data sent in request body
- More secure than GET
- Used for submitting data

### Q. HTML5 new input types

**Answer:**

HTML5 introduced smarter input types:

```html
<input type="email" />
<input type="number" />
<input type="date" />
<input type="range" />
<input type="color" />
<input type="url" />
<input type="tel" />
<input type="search" />
```

Benefits

- Built-in validation
- Better mobile keyboards
- Improved UX

### Q. What is `novalidate`?

**Answer:**

Disables browser’s default form validation

```html
<form novalidate></form>
```

👉 Even if fields have:

```html
<input type="email" required />
```

➡ Form will still submit without validation

### Q. Limits of text field size

**Answer:**

1. `maxlength`
   - Maximum number of characters

   ```html
   <input type="text" maxlength="10" />
   ```

2. `size`
   - Visible width of input box (not limit)

   ```html
   <input type="text" size="20" />
   ```

Key Difference

| Attribute | Purpose                |
| --------- | ---------------------- |
| maxlength | Limits characters      |
| size      | Controls display width |

### Q. Why group checkboxes?

**Answer:**

Checkboxes are grouped using the same `name` attribute.

```html
<input type="checkbox" name="hobby" value="cricket" /> Cricket <input type="checkbox" name="hobby" value="music" /> Music
```

Why?

- Allows multiple selections
- Sends grouped data to server

👉 Output (example):

```
hobby=cricket&hobby=music
```

Without grouping:

Each checkbox would be treated as separate data

🔥 Interview Tip

- `action` = WHERE
- `method` = HOW
- `GET` = visible, `POST` = hidden
- `maxlength ≠ size`
- Group checkboxes using same name

## Media & Graphics

### Q. What is <figure> tag?

**Answer:**

The `<figure>` tag is a semantic HTML5 element used to group media content (image, diagram, code, chart, etc.) along with an optional caption.

```html
<figure>
  <img src="image.jpg" alt="Sample" />
  <figcaption>This is a caption</figcaption>
</figure>
```

Key points

- Provides meaning/structure (semantic)
- Often used with `<figcaption>`
- Content can be moved independently without breaking the document flow

### Q. Difference between `<figure>` and `<img>`

**Answer:**

| Feature | `<figure>`              | `<img>`              |
| ------- | ----------------------- | -------------------- |
| Type    | Container (semantic)    | Media element        |
| Purpose | Group media + caption   | Display image only   |
| Caption | Supports `<figcaption>` | ❌ No                |
| Usage   | Structured content      | Simple image display |

👉 `<figure>` wraps `<img>` (it doesn’t replace it)

### Q. What are media elements in HTML5?

**Answer:**

HTML5 introduced built-in media elements:

Main ones:

```html
<audio controls src="audio.mp3"></audio>

<video controls src="video.mp4"></video>
```

Other related tags:

- `<source>` → multiple formats
- `<track>` → subtitles/captions
- `<embed>` / `<object>` → external media

### Q. What audio formats are supported?

**Answer:**

Common supported formats:

- MP3 → most widely supported ✅
- WAV → high quality, large size
- OGG → open-source format

```html
<audio controls>
  <source src="audio.mp3" type="audio/mpeg" />
  <source src="audio.ogg" type="audio/ogg" />
</audio>
```

### Q. What is Canvas?

**Answer:**

The `<canvas>` element is used for drawing graphics using JavaScript.

```html
<canvas id="myCanvas"></canvas>

<script>
  const c = document.getElementById("myCanvas");
  const ctx = c.getContext("2d");
  ctx.fillRect(20, 20, 100, 50);
</script>
```

Key points

- Pixel-based
- Requires JavaScript
- Used for:
  - Games 🎮
  - Animations
  - Charts

### Q. What is SVG?

**Answer:**

SVG = Scalable Vector Graphics

- XML-based graphics format
- Defined using shapes like `<circle>`, `<rect>`

Key points

- Vector-based
- Scales without losing quality
- Can be styled with CSS & JS

### Q. Difference between SVG and Canvas

**Answer:**

| Feature     | SVG                       | Canvas                      |
| ----------- | ------------------------- | --------------------------- |
| Type        | Vector                    | Pixel (bitmap)              |
| Scalability | No quality loss           | Loses quality when scaled   |
| DOM access  | Yes (elements accessible) | No (drawn pixels only)      |
| Performance | Better for small graphics | Better for complex graphics |
| Use case    | Icons, UI, diagrams       | Games, animations           |

### Q. Explain HTML5 Graphics

**Answer:**

HTML5 provides two main ways to create graphics:

1. Canvas (Dynamic)
   - Script-based drawing
   - Pixel manipulation
   - Good for real-time graphics

2. SVG (Static + Interactive)

- Markup-based
- DOM elements
- Good for UI graphics

Summary

| Feature   | Canvas           | SVG           |
| --------- | ---------------- | ------------- |
| Rendering | JavaScript       | XML/HTML      |
| Best for  | Games, animation | Icons, charts |

🔥 Interview Tip

- `<figure>` = semantic wrapper
- `<img>` = actual image
- Canvas = pixel drawing (JS)
- SVG = vector graphics (DOM-based)
- MP3 = safest audio format

## HTML5 APIs & Features

### Q. What are Web Workers?

**Answer:**

Web Workers allow JavaScript to run in background threads, separate from the main UI thread.

Why needed?

JavaScript is single-threaded, so heavy tasks can freeze the UI. Workers solve this.

Example:

```js
// main.js
const worker = new Worker("worker.js");
worker.postMessage("start");

worker.onmessage = (e) => {
  console.log(e.data);
};
```

```js
// worker.js
onmessage = function () {
  postMessage("Task done");
};
```

Key points

- Runs in background
- No direct access to DOM
- Communicates via `postMessage()`

### Q. What is Geolocation API?

**Answer:**

The Geolocation API allows websites to get the user's location (latitude & longitude).

Example:

```html
<script>
  navigator.geolocation.getCurrentPosition((position) => {
    console.log(position.coords.latitude);
    console.log(position.coords.longitude);
  });
</script>
```

Key points

- Requires user permission
- Used in:
  - Maps
  - Food delivery apps
  - Ride booking

### Q. What is Data Transfer API?

**Answer:**

The Data Transfer API is used in drag-and-drop operations to store and transfer data.

Example:

```html
<div draggable="true" ondragstart="drag(event)">Drag me</div>
<div ondrop="drop(event)" ondragover="allowDrop(event)"></div>

<script>
  function drag(e) {
    e.dataTransfer.setData("text", "Hello");
  }

  function drop(e) {
    e.preventDefault();
    console.log(e.dataTransfer.getData("text"));
  }
</script>
```

Key points

- Used with Drag & Drop API
- Methods:
  - `setData()`
  - `getData()`

### Q. What are Server-Sent Events (SSE)?

**Answer:**

Server-Sent Events (SSE) allow the server to push updates to the browser automatically.

Example:

```js
const source = new EventSource("/events");

source.onmessage = (event) => {
  console.log(event.data);
};
```

Key points

- One-way communication (server → client)
- Uses `EventSource`
- Ideal for:
  - Live notifications
  - News feeds

### Q. What is Microdata?

**Answer:**

Microdata is a way to add structured data to HTML so search engines understand content better.

Example:

```html
<div itemscope itemtype="https://schema.org/Person">
  <span itemprop="name">Tanmay</span>
</div>
```

Key points

- Improves SEO
- Used for:
  - Rich search results
  - Product info
  - Reviews

### Q. What are Web Components?

**Answer:**

Web Components allow you to create reusable custom HTML elements.

Core technologies:

1. Custom Elements
2. Shadow DOM
3. HTML Templates

Example:

```js
class MyElement extends HTMLElement {
  connectedCallback() {
    this.innerHTML = "<p>Hello World</p>";
  }
}
customElements.define("my-element", MyElement);
```

```html
<my-element></my-element>
```

Key points

- Encapsulated (no CSS conflicts)
- Reusable components
- Works without frameworks

🔥 Interview Tip (Quick Revision)

- Web Workers → background JS threads
- Geolocation API → user location
- DataTransfer API → drag & drop data
- SSE → server → client updates
- Microdata → structured SEO data
- Web Components → reusable custom elements

## Storage & Offline Features

### Q. What is Web Storage in HTML5?

**Answer:**

Web Storage is a way to store key–value data in the browser (client-side), introduced in HTML5.

Types

- `localStorage` → persistent storage
- `sessionStorage` → temporary (per tab/session)

Basic usage

```html
<script>
  localStorage.setItem("name", "Tanmay");
  const value = localStorage.getItem("name");
  localStorage.removeItem("name");
  localStorage.clear();
</script>
```

Key points

- Stores data as strings (key–value)
- Larger capacity than cookies (~5–10MB)
- Not sent with every HTTP request (unlike cookies)

### Q. Difference between LocalStorage and SessionStorage

**Answer:**

| Feature     | `localStorage`                   | `sessionStorage`            |
| ----------- | -------------------------------- | --------------------------- |
| Lifetime    | Until manually cleared           | Until tab/browser is closed |
| Scope       | Shared across tabs (same origin) | Per tab/session             |
| Persistence | Persistent                       | Temporary                   |
| Use case    | Remember user settings           | Temporary form data         |

### Q. What is Application Cache?

**Answer:**

Application Cache (AppCache) was an HTML5 feature used to store website resources offline, so pages could load without internet.

Example (old usage)

```html
<html manifest="app.manifest"></html>
```

What it did

- Cached HTML, CSS, JS files
- Enabled offline access

⚠️ Important (Very Common Interview Point)

👉 Application Cache is deprecated and removed

Replacement

Use Service Workers instead (modern approach)

### Q. What is a manifest file?

**Answer:**

There are two contexts:

(A) Old AppCache Manifest (Deprecated)

A `.manifest` file that listed resources to cache:

```
CACHE MANIFEST
index.html
styles.css
script.js
```

(B) Modern Web App Manifest (PWA) ✅

A JSON file that defines how a web app behaves when installed.

```json
{
  "name": "My App",
  "short_name": "App",
  "start_url": "/",
  "display": "standalone",
  "icons": []
}
```

Used for:

- Add to home screen
- App-like experience
- Icons, theme, splash screen

🔥 Interview Tips (Very Important)

- Web Storage ≠ Cookies
- `localStorage` = permanent
- `sessionStorage` = per tab
- AppCache is deprecated ❌
- Use Service Workers + PWA manifest ✅

## Images & Responsive Design

### Q. What are raster vs vector images?

**Answer:**

Raster Images (Bitmap)

- Made of pixels
- Lose quality when zoomed (pixelated)
- Common formats:
  - JPEG, PNG, GIF

👉 Example: Photos

Vector Images

- Made of mathematical paths
- Scale without losing quality
- Common format:
  - SVG

👉 Example: Logos, icons

Key Differences

| Feature   | Raster                   | Vector             |
| --------- | ------------------------ | ------------------ |
| Structure | Pixels                   | Paths (math-based) |
| Scaling   | Loses quality            | No quality loss    |
| File size | Larger (high-res images) | Usually smaller    |
| Use case  | Photos                   | Logos, UI graphics |

### Q. How to make images responsive?

**Answer:**

Method 1: CSS (most common)

```css
img {
  max-width: 100%;
  height: auto;
}
```

👉 Image scales with container

Method 2: `srcset` (advanced)

```html
<img src="small.jpg" srcset="small.jpg 500w, large.jpg 1000w" sizes="(max-width: 600px) 100vw, 50vw" />
```

👉 Browser chooses best image

Method 3: Using responsive frameworks

Example: Bootstrap → `img-fluid`

### Q. Image Map in HTML

**Answer:**

An image map allows you to create clickable areas on an image.

Example:

```html
<img src="image.jpg" usemap="#map1" />

<map name="map1">
  <area shape="rect" coords="0,0,100,100" href="page1.html" />
  <area shape="circle" coords="200,100,50" href="page2.html" />
</map>
```

Shapes supported:

- `rect` → rectangle
- `circle` → circle
- `poly` → polygon

### Q. How to align images and wrap text?

**Answer:**

1. Wrap text using `float`

```css
img {
  float: left;
  margin-right: 10px;
}
```

```html
<img src="img.jpg" />
<p>Text wraps around image...</p>
```

2. Align image center

```css
img {
  display: block;
  margin: 0 auto;
}
```

3. Using Flexbox (modern approach)

```css
.container {
  display: flex;
  align-items: center;
}
```

⚠️ Note

- Old HTML attribute `align` is deprecated
- Use CSS instead

🔥 Interview Tips

Raster = pixels, Vector = scalable
Use `max-width: 100%` for responsive images
Image map = clickable regions
Use `float` or `flexbox` for alignment

## Performance & Optimization

### Q. How to optimize website assets loading?

**Answer:**

This is about when and how assets (CSS, JS, images, fonts) are loaded.

Key techniques

✅ 1. Minimize render-blocking resources

```html
<script src="app.js" defer></script>
<script src="analytics.js" async></script>
```

- `defer` → runs after HTML parsing
- `async` → loads independently

✅ 2. Lazy loading (load only when needed)

```html
<img src="image.jpg" loading="lazy" />
```

👉 Improves initial page load speed

✅ 3. Use Critical CSS

- Load only above-the-fold CSS first
- Defer rest

✅ 4. Use CDN (Content Delivery Network)

- Serve assets from nearest location
- Reduces latency

Examples:

- Cloudflare
- Akamai Technologies

✅ 5. Preload important resources

```html
<link rel="preload" href="font.woff2" as="font" />
```

✅ 6. Reduce HTTP requests

- Combine files (CSS/JS)
- Use sprites or inline SVG

✅ 7. Use caching

```http
Cache-Control: max-age=31536000
```

### Q. How can website assets be optimized?

**Answer:**

This is about reducing asset size and improving efficiency.

✅ 1. Compress images

- Use modern formats:
  - WebP
  - AVIF
- Tools:
  - TinyPNG

✅ 2. Minify CSS, JS, HTML

Before:

```js
function test() {
  console.log("hello");
}
```

After:

```js
function test() {
  console.log("hello");
}
```

✅ 3. Enable compression (Gzip/Brotli)

Reduces file size over network

✅ 4. Use modern image techniques

```html
<img src="img.webp" alt="..." width="300" height="200" />
```

✅ 5. Tree shaking & code splitting

- Remove unused JS
- Load only required code

Tools:

- Webpack
- Vite

✅ 6. Optimize fonts

- Use `font-display: swap`
- Limit font weights
- Prefer `.woff2`

✅ 7. Avoid unused assets

- Remove unused CSS/JS
- Audit using browser DevTools

🔥 Key Difference (Important for interview)

| Aspect   | Asset Loading Optimization | Asset Optimization        |
| -------- | -------------------------- | ------------------------- |
| Focus    | When/how assets load       | File size & efficiency    |
| Goal     | Faster rendering           | Smaller payload           |
| Examples | Lazy loading, defer        | Compression, minification |

🚀 Interview Summary (1-liners)

- Loading optimization = load smarter
- Asset optimization = make files smaller
- Use lazy loading + CDN + caching
- Use compression + minification + modern formats

## Miscellaneous

### Q. What are HTML entities?

**Answer:**

HTML entities are special codes used to display reserved or special characters in HTML.

Why needed?

Some characters are used in HTML syntax (like <, >), so we use entities to display them.

Examples:

```html
&lt; → < &gt; → > &amp; → & &nbsp; → space
```

Usage:

```html
<p>5 &lt; 10</p>
```

### Q. Why named and numeric entities exist?

**Answer:**

There are two types:

1. Named entities

```html
&amp;
```

- Easy to remember
- Human-readable

2. Numeric entities

```html
&#38; (decimal) &#x26; (hex)
```

Why both exist?

- Named entities are limited
- Numeric entities support all Unicode characters

👉 Use numeric when:

- Character has no named version
- You need universal compatibility

### Q. What is favicon and how to add it?

**Answer:**

A favicon is a small icon shown in:

- Browser tabs
- Bookmarks
- Address bar

Add favicon:

```html
<link rel="icon" href="favicon.ico" type="image/x-icon" />
```

Modern format:

```html
<link rel="icon" href="favicon.png" type="image/png" />
```

### Q. What is HTML DOM?

**Answer:**

DOM (Document Object Model) represents HTML as a tree structure of objects.

Example:

```html
<html>
  <body>
    <p>Hello</p>
  </body>
</html>
```

👉 DOM Tree:

- `html`
  - `body`
    - `p`

Why important?

JavaScript can read & modify HTML using DOM

### Q. What is collapsing whitespace advantage?

**Answer:**

HTML collapses multiple spaces into one.

```html
<p>Hello World</p>
```

👉 Output:

```
Hello World
```

Advantages:

- Cleaner HTML
- Smaller file size
- Consistent rendering

### Q. Is drag and drop possible in HTML5?

**Answer:**

✅ Yes, HTML5 supports drag and drop.

Basic example:

```html
<div draggable="true">Drag me</div>
```

Uses:

- File uploads
- UI interactions
- Reordering items

### Q. Is it possible for text to appear outside browser?

**Answer:**

👉 Yes, using CSS positioning/overflow.

Example:

```css
div {
  position: absolute;
  left: -100px;
}
```

- Text can move outside visible area
- Can also use:
  - overflow: visible
  - Negative margins

### Q. What are applets?

**Answer:**

Applets were small Java programs embedded in web pages.

```html
<applet code="MyApp.class"></applet>
```

⚠️ Important

- Deprecated and removed
- Required Java plugin (no longer supported)

👉 Replaced by:

- JavaScript
- Web APIs

### Q. When to use frames?

**Answer:**

Frames (`<frame>`, `<frameset>`)

- Used to split page into sections

⚠️ Status

- Deprecated in HTML5

Modern alternative:

Use `<iframe>`

```html
<iframe src="https://example.com"></iframe>
```

When to use today?

Embedding:

- Videos
- Maps
- External content

🔥 Interview Tips (Quick Recap)

- Entities → display special characters
- Named vs Numeric → readability vs full Unicode
- DOM → tree structure of HTML
- Whitespace → auto-collapsed
- Drag & Drop → supported in HTML5
- Applets & Frames → ❌ deprecated
- Use `<iframe>` instead
