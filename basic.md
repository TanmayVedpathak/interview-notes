# BASIC

## Web Fundamentals

### Q. Full mental model of how a web page load

**Answer:**

#### 1️⃣ Big Picture: What happens when you open a website?

When you type:

```
https://example.com
```

Your browser doesn’t magically know where the site lives. A chain of systems work together:

```
Browser → DNS → CDN → Dispatcher → Web Server → App → Database
```

Let’s break every single piece of this chain.

#### 2️⃣ DNS (Domain Name System) – The Phonebook of the Internet

What DNS does

DNS converts:

```
example.com → 93.184.216.34
```

Steps

1. Browser checks cache
2. OS cache
3. ISP DNS
4. Root DNS → TLD → Authoritative DNS
5. IP address returned

💡 Important

DNS itself does not host content. It only points you to where to go (often a CDN).

#### 3️⃣ CDN (Content Delivery Network)

What is a CDN?

A global network of servers that:

- Cache your website content
- Serve users from the nearest location
- Reduce load on origin servers

Popular CDNs:

- Cloudflare
- Akamai
- AWS CloudFront

Why CDN is critical

Without CDN:

```
User in India → Server in US → Slow 😐
```

With CDN:

```
User in India → Mumbai edge server → Fast ⚡
```

What CDN caches

| Cached by CDN    | Not Cached           |
| ---------------- | -------------------- |
| Images           | Personalized data    |
| CSS              | Logged-in dashboards |
| JS               | Payment APIs         |
| HTML (sometimes) | WebSockets           |

CDN cache decision

CDN checks:

Cache-Control headers

- Expires
- ETag
- CDN rules

If cached → served instantly

If not → request forwarded to origin

#### 4️⃣ Publisher – Who publishes the website?

Publisher means:

The entity that owns and deploys the website

Examples:

- News site → Media company
- E-commerce → Amazon, Flipkart
- Corporate site → Company itself

Publisher responsibilities

- Write code
- Build assets
- Upload to servers
- Configure CDN
- Decide caching rules
- Push site live

💡 In CMS systems (like AEM, WordPress):

- Publisher = Author environment
- Live site = Publish environment

#### 5️⃣ Dispatcher (Very Important in Enterprise)

What is a Dispatcher?

A reverse proxy + cache layer between:

```
CDN ↔ Web Server ↔ Application
```

Most common in:

- Adobe Experience Manager (AEM)
- Enterprise CMS setups

Usually built on:

- Apache HTTP Server
- Nginx

Dispatcher responsibilities

1. Cache HTML pages
2. Filter allowed URLs
3. Block malicious requests
4. Route traffic to correct backend
5. Protect app servers

Dispatcher vs CDN

| CDN        | Dispatcher      |
| ---------- | --------------- |
| Global     | Inside infra    |
| Edge-level | Near origin     |
| Public     | Private         |
| Faster     | More controlled |

💡 Best practice:

CDN → Dispatcher → App

#### 6️⃣ Web Server

What it does

- Serves static files
- Handles HTTP requests
- Talks to app server

Common web servers:

- Apache
- Nginx

Example

```
GET /index.html
```

If static → served directly

If dynamic → forwarded to app server

#### 7️⃣ Application Server

This is where business logic runs.

Examples:

- Node.js (Express, Nest)
- Java (Spring)
- .NET
- PHP (Laravel)

What happens here

- Auth checks
- API calls
- Database queries
- Rendering HTML / JSON

#### 8️⃣ Database & APIs

Data sources

- SQL (MySQL, PostgreSQL)
- NoSQL (MongoDB)
- External APIs
- Cache layers (Redis)

#### 9️⃣ Caching – The Secret Sauce 🔥

Types of caching (Most important interview topic)

1. Browser Cache

- Stored in user’s browser
- Controlled by headers

```
Cache-Control: max-age=31536000
```

2. CDN Cache

- Edge-level
- Massive performance gain

3. Dispatcher Cache

- HTML page caching
- Protects app server

4. Application Cache

- Redis
- In-memory cache

5. Database Cache

- Query results
- Index caching

Cache Invalidation (Hard part)

Ways to refresh content:

- Cache purge
- Versioned URLs
- TTL expiry
- Webhook-based purge

💡 Interview gold line

“Caching is easy. Cache invalidation is the hardest problem.”

#### 🔟 How a Web Page Goes Live (End-to-End)

Step-by-step

1. Developer writes code
2. Code pushed to Git
3. CI builds assets
4. Files uploaded to server / CMS
5. Dispatcher cache cleared
6. CDN cache purged
7. DNS already pointing to CDN
8. Users see new page 🎉

#### 1️⃣1️⃣ Real-World Request Flow (Final Mental Model)

```
User Browser
↓
DNS
↓
CDN (cached? yes → return)
↓ no
Dispatcher (cached? yes → return)
↓ no
Web Server
↓
Application Server
↓
Database / APIs
↑
Response cached on way back
```

#### 1️⃣2️⃣ Why This Matters (Career Perspective)

If you understand this:

- You debug slow websites
- You answer system design questions
- You design scalable apps
- You speak like a senior engineer

### Q. List all HTTP status codes.

**Answer:**

HTTP status codes are grouped into five categories based on the first digit.

#### 1xx — Informational

| Code  | Meaning             |
| ----- | ------------------- |
| `100` | Continue            |
| `101` | Switching Protocols |
| `102` | Processing          |
| `103` | Early Hints         |

#### 2xx — Success

| Code  | Meaning                       |
| ----- | ----------------------------- |
| `200` | OK                            |
| `201` | Created                       |
| `202` | Accepted                      |
| `203` | Non-Authoritative Information |
| `204` | No Content                    |
| `205` | Reset Content                 |
| `206` | Partial Content               |
| `207` | Multi-Status                  |
| `208` | Already Reported              |
| `226` | IM Used                       |

Common examples:

```text
200 → request succeeded
201 → resource created
204 → success with no response body
```

#### 3xx — Redirection

| Code  | Meaning                |
| ----- | ---------------------- |
| `300` | Multiple Choices       |
| `301` | Moved Permanently      |
| `302` | Found                  |
| `303` | See Other              |
| `304` | Not Modified           |
| `305` | Use Proxy — deprecated |
| `306` | Unused                 |
| `307` | Temporary Redirect     |
| `308` | Permanent Redirect     |

`307` and `308` preserve the original HTTP method and body during redirection.

#### 4xx — Client Errors

| Code  | Meaning                         |
| ----- | ------------------------------- |
| `400` | Bad Request                     |
| `401` | Unauthorized                    |
| `402` | Payment Required                |
| `403` | Forbidden                       |
| `404` | Not Found                       |
| `405` | Method Not Allowed              |
| `406` | Not Acceptable                  |
| `407` | Proxy Authentication Required   |
| `408` | Request Timeout                 |
| `409` | Conflict                        |
| `410` | Gone                            |
| `411` | Length Required                 |
| `412` | Precondition Failed             |
| `413` | Content Too Large               |
| `414` | URI Too Long                    |
| `415` | Unsupported Media Type          |
| `416` | Range Not Satisfiable           |
| `417` | Expectation Failed              |
| `418` | I'm a Teapot                    |
| `421` | Misdirected Request             |
| `422` | Unprocessable Content           |
| `423` | Locked                          |
| `424` | Failed Dependency               |
| `425` | Too Early                       |
| `426` | Upgrade Required                |
| `428` | Precondition Required           |
| `429` | Too Many Requests               |
| `431` | Request Header Fields Too Large |
| `451` | Unavailable For Legal Reasons   |

Important commonly used codes:

```text
400 → invalid request
401 → authentication required or invalid
403 → authenticated but not allowed
404 → resource not found
409 → conflict with current server state
422 → syntactically valid request but invalid content
429 → rate limit exceeded
```

#### 5xx — Server Errors

| Code  | Meaning                         |
| ----- | ------------------------------- |
| `500` | Internal Server Error           |
| `501` | Not Implemented                 |
| `502` | Bad Gateway                     |
| `503` | Service Unavailable             |
| `504` | Gateway Timeout                 |
| `505` | HTTP Version Not Supported      |
| `506` | Variant Also Negotiates         |
| `507` | Insufficient Storage            |
| `508` | Loop Detected                   |
| `510` | Not Extended                    |
| `511` | Network Authentication Required |

Common examples:

```text
500 → unexpected server failure
502 → invalid response from upstream service
503 → server temporarily unavailable
504 → upstream service timed out
```

**Interview Line**

HTTP status codes are grouped as `1xx` informational, `2xx` success, `3xx` redirection, `4xx` client errors, and `5xx` server errors.

### Q. Explain in detail IndexedDB.

**Answer:**

IndexedDB is a browser database designed for storing large amounts of structured data on the client.

Unlike `localStorage`, which stores only strings, IndexedDB can store structured values such as:

```text
objects
arrays
numbers
strings
dates
blobs
files
```

It is commonly used for:

- Offline-first applications
- Cached API data
- Large datasets
- Draft forms
- Local search data
- Files and images
- Progressive Web Apps

#### Main concepts

##### Database

Open a database using:

```js
const request = indexedDB.open("app-db", 1);
```

The second argument is the database version.

##### Object stores

An object store is similar to a table.

```js
request.onupgradeneeded = () => {
  const db = request.result;

  db.createObjectStore("users", {
    keyPath: "id",
  });
};
```

`keyPath` specifies which property acts as the primary key.

##### Keys

Keys can be:

```text
explicit
keyPath-based
auto-incremented
```

Example:

```js
db.createObjectStore("users", {
  keyPath: "id",
  autoIncrement: true,
});
```

##### Transactions

All reads and writes happen inside transactions.

Common modes are:

```text
readonly
readwrite
versionchange
```

Example:

```js
const transaction = db.transaction("users", "readwrite");

const store = transaction.objectStore("users");

store.put({
  id: 1,
  name: "John",
});
```

Transactions help preserve consistency.

##### Requests

The native IndexedDB API is event-based.

```js
const request = indexedDB.open("app-db", 1);

request.onsuccess = () => {
  const db = request.result;
};

request.onerror = () => {
  console.error(request.error);
};
```

Libraries such as `idb` provide Promise-based wrappers.

#### Reading data

```js
const transaction = db.transaction("users", "readonly");

const store = transaction.objectStore("users");

const request = store.get(1);

request.onsuccess = () => {
  console.log(request.result);
};
```

#### Indexes

Indexes allow efficient lookups by non-primary-key fields.

```js
store.createIndex("email", "email", {
  unique: true,
});
```

Then:

```js
const emailIndex = store.index("email");

emailIndex.get("john@example.com");
```

#### Cursors

Cursors iterate over many records.

```js
const request = store.openCursor();

request.onsuccess = () => {
  const cursor = request.result;

  if (cursor) {
    console.log(cursor.value);

    cursor.continue();
  }
};
```

#### IndexedDB vs localStorage

| IndexedDB                | localStorage          |
| ------------------------ | --------------------- |
| Structured data          | Strings only          |
| Asynchronous             | Synchronous           |
| Transactions             | No transactions       |
| Indexes                  | No indexes            |
| Good for larger datasets | Good for small values |
| Supports blobs/files     | String storage        |
| More complex             | Very simple           |

`localStorage` can block the main thread because it is synchronous.

IndexedDB is asynchronous and better suited for larger client-side datasets.

#### Schema upgrades

Schema changes happen when opening the database with a higher version.

```js
indexedDB.open("app-db", 2);
```

Then update stores/indexes inside:

```js
onupgradeneeded;
```

#### Multiple tabs

If another tab has an older connection open, an upgrade can be blocked.

Useful events include:

```text
blocked
versionchange
```

Applications should close outdated connections when a version change is requested.

#### IndexedDB and Web Workers

IndexedDB can be accessed from Web Workers, which is useful when storage and data processing should happen away from the UI thread.

#### Security consideration

IndexedDB is client-side storage.

Users can clear or modify browser storage, so it should not be treated as an authoritative or secure backend database.

**Interview Line**

IndexedDB is an asynchronous transactional browser database for structured client-side data with object stores, indexes, cursors, and versioned schema upgrades.

### Q. Explain in detail Shadow DOM.

**Answer:**

Shadow DOM is a browser feature that creates an encapsulated DOM subtree for a component.

It is commonly used with Web Components.

#### Shadow host and shadow root

Create a shadow root:

```js
const host = document.querySelector("#component");

const shadowRoot = host.attachShadow({
  mode: "open",
});
```

Conceptually:

```text
Document
└── component ← shadow host
    └── #shadow-root
        ├── style
        ├── h2
        └── button
```

The host belongs to the normal DOM.

The internal nodes belong to the shadow tree.

#### Style encapsulation

CSS inside the shadow root is scoped to that shadow tree.

```js
shadowRoot.innerHTML = `
  <style>
    button {
      color: red;
    }
  </style>

  <button>Save</button>
`;
```

That rule does not normally affect unrelated buttons outside the component.

Similarly, normal page selectors do not directly style internal shadow elements in the usual way.

#### `open` vs `closed`

```js
element.attachShadow({
  mode: "open",
});
```

allows:

```js
element.shadowRoot;
```

to return the shadow root.

With:

```js
mode: "closed";
```

external access through `element.shadowRoot` returns `null`.

Closed mode is not a security feature.

#### Slots

Slots let external content be projected into the component.

Shadow tree:

```html
<div>
  <slot name="title"> </slot>
</div>
```

Usage:

```html
<my-card>
  <h2 slot="title">Hello</h2>
</my-card>
```

A slot without a name is the default slot.

```html
<slot></slot>
```

#### Styling the host

Inside shadow CSS:

```css
:host {
  display: block;
}
```

You can also conditionally style the host:

```css
:host(.active) {
  border: 1px solid;
}
```

#### CSS custom properties

CSS variables can cross the shadow boundary and are useful for theming.

Outside:

```css
my-card {
  --title-color: blue;
}
```

Inside:

```css
h2 {
  color: var(--title-color, black);
}
```

#### Events and retargeting

Events may cross shadow boundaries, but the browser can retarget them.

If a button inside a shadow root is clicked, outside code may see the custom-element host as `event.target` instead of the internal button.

You can inspect the path with:

```js
event.composedPath();
```

Custom events that must cross the boundary often use:

```js
new CustomEvent("save", {
  bubbles: true,
  composed: true,
});
```

#### Shadow DOM vs normal DOM

| Normal DOM                        | Shadow DOM                                |
| --------------------------------- | ----------------------------------------- |
| Shared page tree                  | Encapsulated subtree                      |
| Global CSS can affect descendants | Styles are scoped                         |
| Easy selector traversal           | Shadow boundary limits selector traversal |
| General application markup        | Component encapsulation                   |

#### Shadow DOM vs iframe

An iframe creates a separate document and browsing context.

Shadow DOM stays in the same document and JavaScript environment.

So Shadow DOM is lighter and designed for component-level encapsulation.

#### Web Component example

```js
class UserCard extends HTMLElement {
  constructor() {
    super();

    const shadow = this.attachShadow({
      mode: "open",
    });

    shadow.innerHTML = `
      <style>
        h2 {
          color: purple;
        }
      </style>

      <h2>User Card</h2>
    `;
  }
}

customElements.define("user-card", UserCard);
```

Usage:

```html
<user-card> </user-card>
```

#### Important limitation

Shadow DOM provides encapsulation, not security.

Open roots can be accessed by page JavaScript, and browser developer tools can inspect shadow trees.

**Interview Line**

Shadow DOM creates an encapsulated component subtree with scoped styling, slots for content projection, and controlled event-boundary behavior.

## SEO

### Q. What is `robots.txt`?

**Answer:**

Definition

`robots.txt` is a text file placed in the root of a website that tells search engine crawlers (bots) which pages they are allowed or not allowed to crawl.

Example URL:

```
https://example.com/robots.txt
```

Why is it used?

It is used to control how search engines like Google, Bing, etc., crawl your website.

Main Purpose

1. Control Crawling
   - Prevent bots from accessing certain pages

2. Protect Sensitive Areas (Not secure, but helps)
   - Admin pages
   - Internal APIs
   - Temporary files

3. Optimize Crawl Budget
   - Search engines don’t waste time on irrelevant pages

4. Avoid Duplicate Content Issues
   - Block duplicate or unnecessary URLs

Basic Syntax

```
User-agent: _
Disallow: /admin/
Allow: /public/
```

Explanation

| Rule                | Meaning               |
| ------------------- | --------------------- |
| `User-agent: *`     | Applies to all bots   |
| `Disallow: /admin/` | Block `/admin` folder |
| `Allow: /public/`   | Allow `/public`       |

Example

```
User-agent: \*
Disallow: /private/
Disallow: /temp/
```

👉 Bots cannot crawl /private and /temp

Important Points ⚠️

- ❌ It does NOT secure data (just a guideline)
- ❌ Bots can ignore it (malicious bots)
- ✅ Only affects crawling, not indexing (in some cases)

robots.txt vs Meta Robots

| Feature  | robots.txt | Meta Robots   |
| -------- | ---------- | ------------- |
| Scope    | Whole site | Specific page |
| Location | Root file  | HTML `<head>` |
| Control  | Crawl      | Indexing      |

Real Insight

👉 Even if blocked in robots.txt, a page can still appear in search results if:

Other sites link to it

**Interview Line**

`robots.txt` is a file used to guide search engine crawlers on which parts of a website should or should not be crawled, helping optimize indexing and crawl efficiency.

🚀 Quick Summary

- File in root → /robots.txt
- Controls crawler access
- Improves SEO performance
- Not a security feature

### Q. What is `sitemap.xml`?

**Answer:**

Definition

`sitemap.xml` is a file that lists all important URLs of a website, helping search engines understand:

- What pages exist
- How they are structured
- When they were last updated

Why is it used?

It helps search engines like Google and Bing discover and index pages more efficiently.

Main Purpose

1. Improve Indexing
   - Ensures all important pages are found

2. Help Large Websites
   - Useful for sites with many pages or deep structure

3. Faster Discovery of New Content
   - Newly added pages get indexed quicker

4. Provide Metadata

   Includes:
   - Last modified date
   - Priority
   - Change frequency

Basic Structure

```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">

  <url>
    <loc>https://example.com/</loc>
    <lastmod>2026-04-16</lastmod>
    <changefreq>daily</changefreq>
    <priority>1.0</priority>
  </url>

</urlset>
```

Tags Explained

| Tag            | Meaning           |
| -------------- | ----------------- |
| `<loc>`        | Page URL          |
| `<lastmod>`    | Last updated date |
| `<changefreq>` | Update frequency  |
| `<priority>`   | Importance (0–1)  |

Example URL

```
https://example.com/sitemap.xml
```

Types of Sitemaps

1. XML Sitemap
   - For search engines (most common)
2. HTML Sitemap
   - For users (navigation page)

sitemap.xml vs robots.txt

| Feature | sitemap.xml   | robots.txt        |
| ------- | ------------- | ----------------- |
| Purpose | List pages    | Control crawling  |
| Type    | XML file      | Text file         |
| Role    | Help indexing | Restrict crawling |

Best Practices

- Include only important pages
- Keep it updated
- Submit to Google Search Console
- Avoid broken links

Important Notes ⚠️

- Not mandatory but highly recommended
- Does NOT guarantee indexing
- Works best when combined with good SEO

**Interview Line**

`sitemap.xml` is a file that lists all important URLs of a website to help search engines discover and index content efficiently.

🚀 Quick Summary

- Lists all website URLs
- Helps search engines crawl smarter
- Improves SEO performance
- Works alongside robots.txt

## Package manager

### Q. `npm ci` vs `npm install`

**Answer:**

Both commands install dependencies, but they are intended for different workflows.

#### `npm install`

Use `npm install` mainly for normal development and dependency management.

```bash
npm install
```

It reads:

```text
package.json
package-lock.json
```

and installs compatible dependencies.

When adding a package:

```bash
npm install axios
```

it normally updates:

```text
package.json
package-lock.json
```

#### `npm ci`

`npm ci` is designed for clean and reproducible installs.

It is commonly used in:

```text
CI/CD
Docker builds
deployment pipelines
automated environments
```

It requires an existing lock file.

```bash
npm ci
```

Important characteristics:

- Installs the exact dependency tree from the lock file
- Fails if `package.json` and the lock file are inconsistent
- Does not update the lock file
- Removes existing `node_modules` before installing
- Is not used to add new dependencies

#### Comparison

| `npm install`                              | `npm ci`                     |
| ------------------------------------------ | ---------------------------- |
| Local development                          | CI/CD and clean builds       |
| Can update lock file                       | Does not update lock file    |
| Can add dependencies                       | Not for adding dependencies  |
| Can work without an existing lock file     | Requires lock file           |
| Resolves dependency changes                | Uses locked dependency tree  |
| Does not always clean `node_modules` first | Removes `node_modules` first |

#### Typical workflow

Local development:

```bash
npm install axios
```

Commit:

```text
package.json
package-lock.json
```

CI:

```bash
npm ci
```

This helps keep the dependency tree reproducible between machines.

**Interview Line**

Use `npm install` for local dependency management and `npm ci` for clean, deterministic installations in CI/CD and deployment environments.
