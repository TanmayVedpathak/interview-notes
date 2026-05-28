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

🔥 Interview Line

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

🔥 Interview Line

`sitemap.xml` is a file that lists all important URLs of a website to help search engines discover and index content efficiently.

🚀 Quick Summary

- Lists all website URLs
- Helps search engines crawl smarter
- Improves SEO performance
- Works alongside robots.txt
