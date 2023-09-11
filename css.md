# CSS

CSS stands for cascading style sheets, while HTML is the structure of our webpages, they won't look very appealing.

CSS1 was introduced in 1994, it's goal was to provide a declarative styling language that could be used by authors.

CSS2 was finalised in 1998, work on CSS3 directly started and was delivered in 2012.

## How CSS is rendered?

1. Browser loads HTML
2. Convert HTML to the DOM
3. Fetches Linked ressources
4. Browser parses CSS
5. Render tree is laid out
6. UI is painted

## Terminology, core concepts

> Elements: They are the basis of our document structure, they can be replaceable or not.

#### Replaceable

```html
<img src="hi.png" alt="a person waving" />
```

#### Non replaceable

```html
<h1>Hello</h1>
```

#### Block elements

```html
<h1>Hello</h1>
<p>Please read me carefully :)</p>
```

<h1>Hello</h1>
<p>Please read me carefully :)</p>

#### Inline elements

```html
<p><a href="https://unsplash.com">Click me</a> to go to our website</p>
```

<p><a href="https://unsplash.com">Click me</a> to go to our website</p>

### Rules based language

- Select one / multiple elements
- Apply rules to them.

#### Css declaration

```css
h1 {
	color: red;
}
```

### Type selectors

h1 is the selector.
It is followed by curly brackets
In the brackets you can add multiple rules as key-value pairs.

### Class selectors

```html
<div class="card">
	<h1>Hello</h1>
	<img src="maw.jpg" alt="cute cat" />
	<p><a href="https://unsplash.com">Click me</a> to go to our website</p>
</div>
```

```css
.card {
	background-color: green;
}
```

### ID Selectors

```html
<div class="card">
	<h1 id="title">Hello</h1>
	<img src="maw.jpg" alt="cute cat" />
	<p><a href="https://unsplash.com">Click me</a> to go to our website</p>
</div>
```

```css
#title {
	color: red;
}
```

### Universal selector

```css
* {
	color: dodgerblue;
}
```

## Combining CSS selectors

To be more specific about which element we want to select, we can combine selectors

<details markdown="1">

```css
.body p {
	color: blue;
}
```

<details markdown="1">

All `p` elements inside a parent with a **`body` class**

</details>

</details>

---

<details markdown="1">

```css
.body p#blue {
	color: blue;
}
```

</details>

## Inheritance and specificity

```html
<div class="card">
	<h2>Yellow !</h2>
</div>
```

```css
.card {
	color: brown;
}
```

<details>

  <h2 style="color: brown">Yellow</h2>

</details>

Some property (not all) are inherited!

```html
<div class="card">
	<h2>Yellow !</h2>
</div>
```

```css
h2 {
	color: dodgerblue;
}

.card {
	color: brown;
}
```

---

```html
<div class="card">
	<h2>Yellow !</h2>
</div>
```

```css
h2 {
	color: dodgerblue;
}

.card h2 {
	color: brown;
}
```

Specificity is used by a browser to determine which CSS should be applied.

- Id's give 1-0-0 points
- Classes give 0-1-0 points
- Type gives 0-0-1 points

It's pretty much like Judo
ID's are like Ippon
Classes are like Waza-Ari
Types are like Koka

If you prefer to see it that way.

It really comes into play when you're trying to style the same element using different selectors.

```css
.body p {
}
```

---

```css
.body p.text {
}
```

---

```css
#hero .subscription;
```

⚠️ Inline style will always be more specific than style written in a stylesheet.

<details markdown="1">

```html
<div>
	<p id="text" style="color: blue">Boum !</p>
</div>
```

```css
div p#text {
	color: orange;
}
```

</details>

⚠️ Style written with an `!important` will always overwrite any other style.

<details markdown="1">

```html
<div>
	<p id="text" style="color: blue">Boum !</p>
</div>
```

```css
p {
	color: orange !important;
}
```

</details>

⚠️ Both of those usages are typically not recommended.

## Cascading

<ul class="list">
	<li style="color: dodgerblue" class="list-item">
		<a href="#" id="link-1">Link 1</a>
	</li>
	<li style="color: dodgerblue" class="list-item">
		<a style="color: red" href="#" id="link-2">Link 2</a>
	</li>
	<li style="color: dodgerblue" class="list-item">
		<a href="#" id="link-3">Link 3</a>
	</li>
</ul>

```html
<ul class="list">
	<li class="list-item">
		<a href="#" id="link-1">Link 1</a>
	</li>
	<li class="list-item">
		<a href="#" id="link-2">Link 2</a>
	</li>
	<li class="list-item">
		<a href="#" id="link-3">Link 3</a>
	</li>
</ul>
```

```css
a {
	color: inherit;
}

ul {
	color: yellow;
}

li.list-item #link-2 {
	color: dodgerblue;
}

ul.list {
	color: dodgerblue;
}

li #link-2 {
	color: whitesmoke;
}

ul.list #link-2 {
	color: red;
}
```
