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
- [Hugo](https:/gohugo.io/) (fast but steeper learning curve)  
- [Eleventy](https://11ty.dev/) (simple, flexible, familiar with HTML/CSS)  

**Choice**: Eleventy  
**Reasoning**:  
- Lightweight and minimal JavaScript dependencies  
- Supports modular, content-focused architecture  
- Easier learning curve aligned with existing skills  

**Status**: ✅ Implemented  

---
<!--
## Decision #002: Content Structure  
**Date**: August 6, 2025  
**Context**: Organizing content to reflect online presence  
**Options Considered**:  
- Single page
- Modular pillars based on origin and content type  

**Choice**: Modular pillars: Projects (Experiments), Writing, Reading, Social (grouped by origin)  
**Reasoning**:  
- Reflects the diversity of content and platforms  
- Scales well over time  

**Status**: ⬜ Planned  

---

-->