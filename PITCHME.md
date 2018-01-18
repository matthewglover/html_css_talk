## HTML and CSS
**Building Web UIs**

---

### HTML and CSS

- UI layer for Web and more
- Often an afterthought
- Impact on User Experience

Note:
- Not "real programming"
- Historical context needed
	- old code bases
	- backward compatibility requirements
---

### Outline

1. Layout
2. Multiple devices (resolution and aspect ratio)
3. Problems with CSS
4. Web Components
5. Abstractions

Note:
- Layout: combo of HTML & CSS to deliver UIs
- Res/Aspect: How to deal with multi-platform delivery
- Pre-processors and other ideas to solve perceived CSS problems
- Web Components - look at the future & similarities with React etc
- Abstractions - can we hide from HTML/CSS like JQuery/React etc let us hide from DOM?

- Other trends - things not covered but which relate in

---

### 1. Layout

Note:
- Combo of HTML and CSS to create layouts
- Look back at how layout has been addressed over the last 20 years
- Whats changed but also whats stayed the same

---

## 1.1 Layout - The Beginning

- Building brands
- Rise of design
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

Notes:

Pros:
- Worked
- Cross-browser consistency

Cons:
- mixing structure and style
- lot of noise
- poor for accessiblity
- search engines didn't like them
- often combined with a lot of images

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

http://cssdeck.com/labs/nvdqnon3

Note:
- variable height columns
- "float" an element to push it as far as possible to the right or to the left, and allow text to wrap around it
- designed for images
clear: both -> push down rest of content

---

## 1.4 Layout - Clear Fix

http://cssdeck.com/labs/axzgb8bj

Note:
- Floats don't affect height of container
- leads to "collapsed" layouts
- Need clearfix hack

---

### 1.5 Layout - Flexbox

> way to lay out, align and distribute space among items in a container, even when their size is unknown and/or dynamic

Note:
- Modern layout
- First thing since tables to deal with vertical alignment
- Fixes vertical alignment

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
- justify-content -> primary axis
- align-items -> secondary axis

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

.grid-item {
	align-items: start | end | center | stretch;
	align-self: start | end | center | stretch;
}
```

Note:
- Reasonably new feature, but good browser support
- Two dimensions
- Similarities to Flexbox

---

### 1.6 Layout - Grid

http://cssdeck.com/labs/cwjdjnaa

---

## 2. Resolution and Aspect Ratio

---

## 2.1 - Units

- Fixed: px
- Relative: %, Em, Rem

Note:
- While em is relative to the font-size of its direct or nearest parent, rem is only relative to the html (root) font-size.
- https://css-tricks.com/confused-rem-em/
- Favour relative units to fixed
- Allows user to resize app whilst maintaining sizing relationships
- Minimises changes for different devices

---

## 2.2. - Media Queries

```css
@media [all | screen | projector | print] and (max-width: 500px) , (max-height: 200px) {
	/* css */
}
```

Note:
and - either
, - or
https://css-tricks.com/css-media-queries/
- use sparingly
- rely on relative sizing as much as possible
- media queries = global scope
- focus on up-front html/css structure
- split "layout" from "components"

---

# 3.0 - The Problem with CSS?

Note:
- deficiencies in CSS
- pre-processors
- React etc - JS in CSS

---

# 3.1 - SASS

- Variables
- @import: single file (CSS imports equal multiple HTTP Requests)
- colour functions: lighten, darken, rgba
- mixins: remove duplication
- extend: apply styles from one css class to another (e.g. base button class)
- nested css syntax

Note:
- LESS, Stylus, (PostCSS)
- Designed to address perceived deficiencies

---

## 3.1 - SASS vs Selectors

http://cssdeck.com/labs/iie5iw0t

Note:
- Pre-compile stage
- Non-optimised compilation
- Nesting
	- favour shallow hierarchies
	- use direct child: `.parent > .child`
	- use * for grandchild: `.parent * > .grandchild`
- child/grandchild - http://cssdeck.com/labs/iie5iw0t

---

## 3.2 - Post-CSS

- modular transforms
- autoprefixer, inline imports
- css-next (variables, functions etc)

Note:
- Misuse: just like SASS but more dependencies to manage
- Use: enable specific, minimal transformations

---

## 3.3 - Immutable CSS

- Analagous to immutable objects
- Simplicity

Note:
- https://csswizardry.com/2015/03/immutable-css/
- https://github.com/johnotander/immutable-css
- More build tooling

---

## 3.4 - CSS in JS

- Popularised by React
- Style isolation
- Style objects located with components
- Render as inline-styles

Note:
- addresses componentisation
- downsides: duplication, lose css-only features (pseudo-classes)

---

## 3.5 - JSS / Aphrodite / Styled components

- Similar to CSS in JS
- JS but compiles to CSS

Note:
- get css selectors etc
- no setting at runtime (still need to use style attribs to override
- complexity: no "winning strategy"

---

## 3.6 - Problems with CSS: Summary

- Architecture vs code solutions - shallow cascade
- CSS gaining new features: variables, functions etc
- HTTP 2 - more efficient multiple files
- Shallow cascade

Note:
- Don't override tags unless want global resets
- Don't over-specifiy (keep shallow cascade)
- Living style guides

---

# 4. Components

- React, Angular, Vue
- Web Components - Shadow DOM

Note:
- Similar principles to React, Angular, Vue
- Custom tags, which hide complex functionality
- Objects/functions - take only data they need
- Protected from page-level js/dom/css

---

# 5. Abstractions

- Bootstrap / Material UI

Note:
PROS:
- abstract away complexity
- language of objects and components
- themes

CONS:
- everything looks the same
- heavyweight (JQuery)
- more customised = less benefit




