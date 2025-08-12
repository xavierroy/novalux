---
title: "Decision Log"
description: "A chronological record of key decisions made during the Novalux rebuild, with reasoning and outcomes."
permalink: /decisions/
---

# Decision Log

This page documents the key decisions made during the Novalux rebuild of <em>xavierroy.in</em>. Each entry captures the context, options considered, reasoning, and eventual outcomes.

---

## Decision #001: Static Site Generator Choice  
**Date**: August 5, 2025  
**Context**: [Selecting the foundation technology for the rebuild](blog/intro-to-novalux.md)

**Options Considered**:  
- [Gatsby](https://www.gatsbyjs.com/) , [Astro](https://astro.build/) & [Next.js](https://nextjs.org/) (modern but requires JavaScript knowledge)  
- [Hugo](https://gohugo.io/) (fast but steeper learning curve)  
- [Eleventy](https://11ty.dev/) (simple, flexible, familiar with HTML/CSS)  

**Choice**: Eleventy  
**Reasoning**:  
- Lightweight and minimal JavaScript dependencies  
- Supports modular, content-focused architecture  
- Easier learning curve aligned with existing skills  

**Status**: ✅ Implemented  

---

## Decision #002: Site Structure – Single Page  
**Date**: August 12, 2025  
**Context**: Defining the scope and user experience for the redesign  

**Options Considered**:  
- **Multi-page site** – clear separation of content, but more navigation overhead  
- **Single-page site** – all core sections on one scrollable page  

**Choice**: **Single-page site**  
**Reasoning**:  
- Minimalist approach with reduced complexity  
- Faster performance and easier maintenance  
- Clearer and more direct user journey  

**Impact**:  
- All core information (hero, featured work, latest writing, about, contact) presented on one scrollable page  
- No multi-page navigation required  

**Status**: ✅ Approved  

---
