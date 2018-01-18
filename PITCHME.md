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
- Layout: combo of HTML & CSS to deliver UIs
- Res/Aspect: How to deal with multi-platform delivery
- Pre-processors and other ideas to solve perceived CSS problems
- Abstractions - can we hide from HTML/CSS like JQuery/React etc let us hide from DOM?
- Web Components - look at the future & similarities with React etc
- Other trends - things not covered but which relate in

---

# 1. Layout

Note:
- Combo of HTML and CSS to create layouts
- Look back at how layout has been addressed over the last 20 years
- Whats changed but also whats stayed the same

---

## 1.1 Layout - The Beginning

- Rise of design
- Influence of print and CD Rom design
- Browser wars

Note:
- People come on line - cost / permanent connections
- Establishing brands
- Web design emerges: layout, images, interactivity
- HTML not designed for purpose so people got creative

---

## 1.2 Layout - Tables

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
- cellspacing / padding / bgcolor

---

## 1.2 Layout - Tables

Pros:
- Worked
- Cross-browser consistency

Cons:
- mixing structure and style
- lot of noise
- poor for accessiblity
- search engines didn't like them
- often combined with a lot of images

Note:
- Rise of Google and web optimisation saw move away from tables
- Plus better CSS support

---

## 1.3 Layout - Positioning

- static (default)
- relative
- absolute
- relative + absolute

Note:
- static: element is not positioned and occurs where it normally would in the document
- relative: move the element relative to where it would normally occur (BUT still occupies space originally occupied before l/r/t/b)
- absolute: element is removed from the document and placed exactly where you tell it to go
- relative + absolute: position nested elements absolutely within container
(http://www.barelyfitz.com/screencast/html-training/css/positioning/)

---

## 1.3 Layout - Positioning: absolute + relative

http://cssdeck.com/labs/wqrad3vu

Note:
Require relative on parent to contain absolute children

---

## 1.3 Layout - Positioning: 2 columns

http://cssdeck.com/labs/ixvjoa8y

Note:
- Solves two columns
- But doesn't set height on container
- Need to set container height explicitly
- Doesn't work well for dynamic content / text resizing

---

## 1.4 Layout - Floats

- variable height columns
- "float" an element to push it as far as possible to the right or to the left, and allow text to wrap around it

Note:
designed for images

---

## 1.4 Layout - Floats

http://cssdeck.com/labs/nvdqnon3

Note:
clear: both -> push down rest of content

---

## 1.4 Layout - Clear Fix

- Floats don't affect height of container
- leads to "collapsed" layouts
- Need clearfix hack

---

## 1.4 Layout - Clear Fix

http://cssdeck.com/labs/axzgb8bj

Note:
Add clearfix to div-1

---

### 1.5 Layout - Flexbox

> way to lay out, align and distribute space among items in a container, even when their size is unknown and/or dynamic
- CSS Tricks https://css-tricks.com/snippets/css/a-guide-to-flexbox/

Note:
- Modern layout
- First thing since tables to deal with vertical alignment

---

### 1.5 Layout - Flexbox

```css

.flex-container {
	display: flex;
	flex-direction: row | row-reverse | column | column-reverse;
	flex-wrap: nowrap | wrap | wrap-reverse;
	flex-flow: <flex-direction> <flex-wrap>;
	justify-content: flex-start | flex-end | center | space-between | space-around | space-evenly;
	align-items: flex-start | flex-end | center | space-between | space-around | space-evenly;
}
```

Note:
- justify-content -> primary axis
- align-items -> secondary axis

---

### 1.5 Layout - Flexbox

```css

.flex-item {
	order: integer (default 0);
	align-self: auto | flex-start | flex-end | center | baseline | stretch;
	flex-grow: integer;
	flex-basis: length | auto;
}
```

Note:
- justify-content -> primary axis
- align-items -> secondary axis

---

### 1.6 Layout - Grid

- Reasonably new feature, but good browser support
- Two dimensions
- Similarities to Flexbox

---

### 1.6 Layout - Grid

```css
.grid {
	display: grid;
	grid-template-columns: 1fr 1fr 2fr; 
	grid-column-gap: length;
	grid-auto-rows: 100px / minmax(100px, auto)
	justify-items: start | end | center | stretch;
}
```

---

### 1.6 Layout - Grid

```css
.grid-item {
	align-items: start | end | center | stretch;
	align-self: start | end | center | stretch;
}
```

---

### 1.6 Layout - Grid

http://cssdeck.com/labs/cwjdjnaa


---

## 2 Resolution and Aspect Ratio

---

## 2.1 - Units

- Fixed: px
- Relative: %, Em, Eem

## 2.1 - Units

> While em is relative to the font-size of its direct or nearest parent, rem is only relative to the html (root) font-size.

Note:
https://css-tricks.com/confused-rem-em/

---

## 2.1 - Units

- Favour relative units to fixed
- Allows user to resize app whilst maintaining sizing relationships
- Minimises changes for different devices

---

# 2.2. - Media Queries

```css
@media [all | screen | projector | print] and (max-width: 500px) , (max-height: 200px) {
	/* css */
}

Note:
and - either
, - or
https://css-tricks.com/css-media-queries/

---

# 2.2. - Media Queries

- use sparingly
- rely on relative sizing as much as possible
- media queries = global scope

---


--------------------------------------------------------
1. How it all started - Tables
2. CSS for Layout - Key developments
3. The Rise of Mobile - Media Queries
4. Fixing CSS - Pre-processors
5. Web Components - the death of the "Page"



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
