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
