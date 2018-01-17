### HTML and CSS
#### A Brief History

---

## Introduction

- UI layer for majority of applications we build and use
- Often an afterthought both for developers and designers
- Bad implementation can have real impact on User Experience

Note:
- Not "real programming"
- Historical context needed
	- old code bases
	- backward compatibility requirements
---

## Topics

1. Layout
2. Resoltion and Aspect Ratios
3. Problems with CSS
4. Abstracting away HTML and CSS
5. Web Components
6. Other trends

Note:


## Summary

1. How it all started - Tables
2. CSS for Layout - Key developments
3. The Rise of Mobile - Media Queries
4. Fixing CSS - Pre-processors
5. Web Components - the death of the "Page"


Note:
- How it all started for me (before this web was v basic)
- Addressing challenges
- Missing: JavaScript, the rise and fall of Flash

---

## In the beginning

- People get on line
- Making things look good - the rise of design
- Browser (in)compatibility


Note:
- Move from simple text files with basic formatting and links > Selling things
- Impact of print design
- Images for logos, rollover buttons
- Making things work - hacker mentality
- No dev tools, no console, no Google, MDN, StackOverflow, CSS Tricks or W3Schools (WebMonkey, ExpertsExchange)

---

## Tables for layout

```html
<table cellspacing="0" cellpadding="0" border="0">
<tr>
	<td colspan="2" bgcolor="#FF0000">Header</td>
</tr>
<tr>
	<td rowspan="2">Nav Bar</td>
	<td>Main content</td>
</tr>
<tr>
	<td>Footer</td>
</tr>
</table>
```

Note:
- Tables to set up complex layouts
- Nested tables for individual elements
- Lots of noise (hard to see content)
- Add comments to delineate sections

---

## Problems with Tables

- Noise: more markup than content
- Mixing style

> HTML (the Hypertext Markup Language) and CSS (Cascading Style Sheets) are two of the core technologies for building Web pages. HTML provides the structure of the page, CSS the (visual and aural) layout, for a variety of devices.
(W3.org)
