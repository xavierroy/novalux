---
title: "Building the First Layout Structure"
description: "Continuing the xavierroy.in redesign: adding layout structure, placeholder content, and tackling our first Eleventy hiccup."
date: 2025-08-16
---


## Quick Recap

In the [previous redesign log](/blog/setting-things-up/), I got the basics in place:  
- A fresh GitHub repository for the project  
- Eleventy installed and running locally  
- A first `index.md` page wired to a very minimal `default.njk` layout  

That was enough to see a “*hello world*” page in the browser — a small but important milestone.  

Now it’s time to move forward. The goal for this step is to move from a barebones page to a **structured layout** that will serve as the foundation for all content going forward.

---

## Adding a Basic Layout Structure

The first `default.njk` file was intentionally simple — it only output the page title and content. That worked, but real websites need more structure.  

I refactored `src/_includes/layouts/default.njk` to use **semantic HTML elements**: a header, a main content area, and a footer. I also added the meta viewport tag so the page scales properly on mobile.  


{% raw %}
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>{{ title }}</title>
</head>
<body>
  <header>
    <h1>{{ title }}</h1>
  </header>

  <main>
    {{ content | safe }}
  </main>

  <footer>
    <p>&copy; {{ "now" | date: "%Y" }} Xavier Roy</p>
  </footer>
</body>
</html>
```
{% endraw %}

### Why structure it this way?
- `<header>` → introduces the page and provides context for the content.
- `<main>` → marks the primary content area for accessibility and screen readers.
- `<footer>` → anchors the page with ownership information (and later, useful links).
- Meta viewport → ensures the site is responsive out of the box on mobile.

Even though the page is still plain, this small change has a big impact. Instead of a generic wrapper, we now have a **semantic backbone**: accessible, responsive, and extensible.

---

## Adding Placeholder Content

To test the new layout properly, I updated the **`src/index.md`** file with some sample content. Instead of leaving it blank, I added headings, paragraphs, and a list — enough to check how different elements render:

```markdown
---
title: "Welcome to the xavierroy.in Redesign"
layout: default.njk
---

# Hello, World 👋

This is the redesigned **xavierroy.in** in progress.  
Right now, it’s just a skeleton — structure first, styling later.  


## What’s Next?
Over the coming weeks, this site will grow piece by piece:
- Layouts → refined structure and reusable components  
- Content → about page, blog, and portfolio entries  
- Design → typography, spacing, and theming  

Stay tuned as the build continues!

```
Running:
```bash
npx eleventy --serve
```
gives a structured page with a header, main content, and footer — all filled with actual text instead of an empty shell.

### Why bother with placeholder content?

Even though this isn’t final copy, it helps:
- **Testing layouts** → seeing how headings, lists, and paragraphs render.
- **Visual checkpoints** → immediate feedback on progress instead of staring at a blank screen.
- **Momentum** → placeholder text lowers the barrier to experimenting freely.


### The First Error (and Fix)

When I first added the footer, I wanted the copyright year to update automatically. My first attempt was:

{% raw %}
```njk
<footer>
  <p>&copy; {{ new Date().getFullYear() }} Xavier Roy. All rights reserved.</p>
</footer>
```
{% endraw %}

…but that failed. Nunjucks doesn’t allow inline JavaScript inside templates, so Eleventy threw an error.

#### The Fix: Global Data

Instead of forcing inline JavaScript, I used [Eleventy’s global data API](https://www.11ty.dev/docs/data-global-custom/). In `eleventy.config.cjs`, I added:

```js
const { DateTime } = require("luxon");

module.exports = function (eleventyConfig) {
  eleventyConfig.addFilter("date", (dateObj, format = "yyyy") => {
    return DateTime.fromJSDate(dateObj).toFormat(format);
  });
};
```
Now `currentYear` is available everywhere in the site, no imports needed. Updating the footer became as simple as: 
{% raw %}
```njk
<footer>
  <p>&copy; {{ currentYear }} Xavier Roy. All rights reserved.</p>
</footer>
```
{% endraw %}
This small tweak makes the year dynamic and reusable without extra clutter.

{% lucide "logs", { "stroke": "#7924f0ff"} %} [Decision 003: Global Data for Copyright Year](/decisions/#decision-003-use-eleventy-global-data-for-dynamic-copyright-year)


### Lessons Learned
- **Don’t fight the templating language.** Inline JavaScript in Nunjucks doesn’t work — but Eleventy has built-in tools (filters, shortcodes, and global data).
- **Semantic HTML pays off.** Even without styling, `<header>`, `<main>`, and `<footer>` give accessibility, structure, and clarity.
- **Placeholder content is powerful.** It turns an empty skeleton into something testable, which keeps momentum going.
- **Debugging is part of the process.** Every error is a chance to learn how the system really works.

## Next Steps

Now that the site has a working foundation, the next priorities are:
- **Flesh out the information architecture** → decide the sections that belong on the homepage (hero, cards, footer).
- **Add sample Markdown pages/sections** → About, Blog, Portfolio — to test navigation.
- **Start planning typography** → choosing fonts and defining hierarchy (but styling comes later).

One step at a time. Structure first, polish later.

> You can view my site at [new.xavierroy.in](https://new.xavierroy.in/). {% lucide "rocket" %}

