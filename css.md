# CSS style guidelines

## General

Follow the [general guidelines](general.md).

These days there are a lot of approaches that suggest a particular style so
take these guidelines with a grain of salt. Styled components for example make
BEM redundant.

Avoid `@import`, instead use multiple `<link>` statements.

Prefer to use a build step if possible, this will allow to split the sources.

## Syntax

Include a single space between the colon value, but no space between the colon
and the property. Opening brace goes besides the selector, after a space.

```css
.sporty {
	display: flex;
	width: 100%;
}
```

Separate declaration blocks with an empty line. Indent the block contents.

```css
.sporty {
	display: flex;
	width: 100%;
}

.lazy {
	width: auto;
}
```

Put selectors on separate lines unless the length is trivial.

```css
li.sporty span,
li.lazy span {
	background: purple;
}

ul, ol {
	padding: 0;
	margin: 0;
}
```

If you have multiple declarations in a block, put each on a separate line and
end each line with a semicolon. It's ok to not do that for single-declaration
blocks.

```css
.sporty {
	display: flex;
	width: 100%;
}

.lazy { width: auto }
```

Omit leading zeros

```css
section {
	margin-top: .8rem;
}
```

## Naming

Use BEM to style elements. Reflect the purpose of the element in the name.

```css
.person {
	display: flex;
}

.person__name {
	font-weight: 500;
}

.person__name--tentative {
	font-weight: 300;
}
```

For utility classes reflect the purpose of the class. When in doubt, borrow
naming from a framework like Bulma, Bootstrap or Tailwind CSS.

```css
.mt-0 {
	margin-top: 0 !important;
}
```

Use special prefixes 

## Properties

Use shorthand properties when you are using a lot of values:

```css
aside {
	border: 1px black solid;
	font: 1.2rem/1.6 roboto, helvetica, sans-serif;
	margin-bottom: 0; /* but don't, when a single explicit value is enough */
}
```

## Constants

Try to put your constants as variables at the start of the component or the
main CSS file if applicable everywhere. Or a separate `_variables` file.

```css
:root {
	--spacing-xs: .2rem;
	--spacing-sm: .5rem;
	--spacing-base: 1rem;
	--spacing-lg: 1.8rem;
	--spacing-xl: 3.5rem;

	--border-light: .05rem;
	--border-base: .1rem;
	--border-thick: .18rem;

	--border-radius: .18rem;

	--text-sm: 1rem;
	--text-base: 1.15rem;
	--text-lg: 1.3rem;
	--text-xl: 1.5rem;

	--letter-spacing: .075em;

	--main-font: Montserrat, -apple-system, BlinkMacSystemFont, Segoe UI, Oxygen, Ubuntu, Cantarell, Droid Sans, Helvetica Neue, sans-serif;
	--alt-font: Raleway, Helvetica, sans-serif;
	
	--text-light: 300;
	--text-normal: 400;
	--text-strong: 500;
	--text-bold: 600;
	
	/*name     code         purpose            contrast			*/
	/*                                   on white   on --black	*/
	--black:   #101318;  /* text         18.61      1		  */
	--gray:    #00a3b3;  /* main         3.05       6.11      */
	--green:   #5fed5a;  /* interaction  1.53       12.18     */
}
```

Combine default values in a single variable.

```css
:root {
	--font: var(--text-base) var(--main-font);
	--border: var(--border-base) var(--black) solid;
}
```

### Colors

Prefer HSL over RGB, RGB over hex, hex over named colors.

Use lowercase hex and prefer shorhand hex (`#333` not `#333333`).

### Weights

Prefer numeric font weights instead of named ones.

## Units

Use appropriate units.

Use `rem` for on-screen typography and anything that should scale if the point
size changes:

```css
section {
	width: 40rem;
	font-size: 1.2rem;
}
```

Use metric units for print:

```css
@media print {
	.card {
		width: 8cm;
	}
}
```

Use `em` only for sizes that should depend on the current font size:

```css
title {
	letter-spacing: .07em;
}
```

Use `px` for purely visual things:

```css
.card {
	box-shadow:
		0 1.7px 3.6px rgba(0, 0, 0, 0.028),
		0 4.8px 10px rgba(0, 0, 0, 0.04),
		0 11.5px 24.1px rgba(0, 0, 0, 0.052),
		0 38px 80px rgba(0, 0, 0, 0.08);
}
```

Avoid leading and trailing zeros:

```css
section {
	margin-top: 2rem;
	margin-bottom: .5rem;
}
```

Leave zeros unitless (unless required otherwise):

```css
.card {
	padding: 0;
	flex: 0px;
}
```

## Attribute ordering

Prefer concentric ordering.

1. variables
2. external layout
	- position (top, left, z-index, flex/grid self positioning)
	- box model (display, float, margin, width, height)
3. borders
4. internal layout
	1. content
	2. padding
	3. layout (flex/grid internal rules, columns)
	4. alignment
	5. overflow, wrap
5. typography (font-, text-, line-height, letter-spacing, quotes, ...)
6. decorations (colors, shadows, cursor)
7. specials/misc (animations, transforms)

```css
h1 {
	padding-top: var(--spacing-lg);
	padding-bottom: var(--spacing-lg);
	
	text-align: center;
	
	font-size: var(--text-2xl);
	font-weight: var(--text-strong);
	text-transform: uppercase;
	
	color: var(--orange);
}
```

## Project structure

Use the [7-1 pattern](https://sass-guidelin.es/#the-7-1-pattern) if you have a
build step.

## Media queries

Think about your break point selection. 

https://www.freecodecamp.org/news/the-100-correct-way-to-do-css-breakpoints-88d6a5ba1862/

Place the media queries close to their relevant code blocks.

## Resets

Use resets appropriate to your tooling. When unsure, use minimal resets, like
this one:

```css
* {
	box-sizing: border-box;
	margin: 0;
	padding: 0;
}
```
