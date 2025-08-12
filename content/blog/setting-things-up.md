---
title: "Setting up the Project Repository"
description: "Documenting the first concrete step in the xavierroy.in redesign: creating the project repository and basic Eleventy configuration."
date: 2025-08-12
---

## Overview

This post covers the **very first hands-on step** in the redesign of xavierroy.in — setting up the project repository and getting Eleventy running locally.  

It may not be flashy, but this foundation is crucial. Everything else — from layouts to content — will build on this.

---

## Why this matters

Before writing a single line of HTML or designing a layout, it's important to start with a **clean, version-controlled foundation**. This ensures you can:
- Track every change as you progress  
- Collaborate smoothly if others get involved  
- Reproduce the setup consistently across machines and environments  

Think of this as **clearing your workbench before starting a project** — the prep work makes all the later steps easier and less stressful.

---

## What You’ll Need to Follow Along

If you want to try this yourself, here’s what you’ll need:

- [Node.js](https://nodejs.org/) (version 18 or newer recommended) installed on your machine 
- Basic familiarity with the command line  
- A GitHub account (or any Git remote hosting) to create the repository   


> For transparency and to capture the reasoning behind each choice, I’m maintaining a [Decision Log](/decisions/) that documents key decisions throughout this redesign. 


## How I Set Up the Project

### 1. Create the repository

I started by creating a **private GitHub repository** called `xavierroy.in-redesign`.  

Keeping it private for now allows me to experiment freely without worrying about public visibility. It will go public once the project stabilizes

```bash
git init
git remote add origin git@github.com:username/xavierroy.in-redesign.git
```

### 2. Initialize the Node.js project
Inside the newly cloned repo:
```bash
npm init -y
```
This generates a **`package.json`** file, which will track dependencies and scripts.

### 3. Install Eleventy

Add Eleventy as a development dependency:

```bash
npm install @11ty/eleventy --save-dev
```

### 4. Add a basic Eleventy config
At the project root, I created **`eleventy.config.cjs`** with:

```js
module.exports = function(eleventyConfig) {
  // Copy static assets directly
  eleventyConfig.addPassthroughCopy("assets");

  return {
    dir: {
      input: "src",
      output: "_site"
    }
  };
};

```
This sets :
- `src/` as the source folder for all site files  
- `_site/` as the output folder for the built site  
- Asset passthrough so CSS/images copy over without extra config


### 5. Create the initial content folder and homepage
Make a folder called `src` in the root, and inside it, add `index.md`:

```markdown
---
title: "Welcome to the xavierroy.in Redesign"
layout: default.njk
---

# Hello from the redesigned xavierroy.in!

This is the first content page of the redesign project, built with Eleventy.

```
### 6. Add a minimal layout template

Inside your includes directory (by default `_includes`), add `default.njk`:

```njk
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>{{ title }}</title>
</head>
<body>
  {{ content | safe }}
</body>
</html>
```

### 7. Verify the setup and serve the site
Run the dev server to check everything works:
```bash
npx eleventy --serve
```

If all is well, you’ll see your markdown content styled by the layout at http://localhost:8080 (or the port Eleventy chooses).

> You can view my site at [new.xavierroy.in](https://new.xavierroy.in/). {% lucide "rocket" %}

## Lessons & observations
- Even a minimal Eleventy setup benefits from an early defined directory structure.  
- Keeping the repo private during this phase reduces the pressure for “perfect commits.”  
- Eleventy’s minimal configuration approach lets you get started fast — you add complexity only as you need it.

## Next steps
In the upcoming post, I’ll:
- Expand the content folders with sample markdown posts  
- Build out the initial homepage layout  
- Continue this step-by-step, methodical approach to the redesign


