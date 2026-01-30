---
## Hashnode
slug: web-fundamentals-part-3
domain: hashnode.hudater.dev
subtitle: "Emmet: Write HTML at 10× Speed"
enableToc: true
saveAsDraft: false

# Cover Image URL of the post
# String | Optional
# Note: You must upload the image to Hashnode's CDN, before you can use it here.
# Ex: https://cdn.hashnode.com/res/hashnode/image/upload/v1681132538878/itnaYF1h-.png
# - To upload, Login to Hashnode and go to https://hashnode.com/uploader
#   Use the URL that is generated after the upload.
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1768907490094/TEkoHSA4S.jpg?auto=format

## Jekyll
title: "Emmet: Write HTML at 10× Speed (3/4)"
layout: post
date: 2026-01-30 06:20:00 +0530
categories: [chaicode, web-fundamentals-series]
comments: true
pin: false
# tags: [servers, proxmox, homelab, hybrid cloud, architecture diagram]
tags:
  - html
  - web-fundamentals
  - chaicode
image:
  path: "https://res.cloudinary.com/djsasyvfl/image/upload/v1769734418/77a267c2-ab77-455e-8b93-4e69b98a7f54.png"
  alt: "Emmet Cheatsheet"
---

> Are you still writing all the HTML manually?
>
> Do you too want to be a 10x Developer?
>
> Let's explore Emmet and hack NASA with our fast HTML!

This is going to be a quick one to keep up with the spirit of Emmet

Emmet is a tool which writes HTML for you when you supply it with certain short-codes. That's all Emmet is!

You type:

```html
p
```

and press tab, you get:

```html
<p></p>
```

Emmet works as an extension for your code editor, not the browser. So install Emmet, write shortcodes for Emmet and press tab


### Basic Emmet Syntax and Abbreviations


#### Simple tags

For a simple tag like `p` and `h1` you can:

```html
p
```

and press tab to get:

```html
<p> </p>
```

or 

```html
h1
```

and press tab to get:

```html
<h1> </h1>
```

#### Classes

To create an element with a class, write the tag name followed by a dot and class name

For example:
```html
div.box
```

press tab to get:
```html
<div class="box"></div>
```

#### ID

To create an element with an ID, write the tag name followed by a hash(#) and the ID name

For example:
```html
section#hero
```

press tab to get:
```html
<section id="hero"></section>
```

#### Attributes

Some elements support attributes like the `a` tag which can take a URI as attribute


To create an element with an attribute, write the tag name followed by attribute inside a square bracket.

For example:
```html
a[href="https://hudater.dev"]
```

press tab to get:
```html
<a href="https://hudater.dev"></a>
```

Another example with multiple attributes:

```html
img[src="cat.png"][alt="image"]
```

press tab to get:
```html
<img src="picture.png" alt="image">
```

### Nested Elements

You can create elements inside elements using `>` symbol

For example:

```html
div>p
```

tab to get:

```html
<div>
  <p></p>
</div>
```

### Sibling Elements

What about multiple elements at the same level or hierarchy?
<br>
We can do that too:

```html
h1+p
```

tab to get:
```html
<h1></h1>
<p></p>
```

### Repeating Elements

We can simply multiply by the number of times we want the element to be repeated.
Simply use the `*` symbol.

For example:

```html
ul>li*3
```

tab to get:
```html
<ul>
  <li></li>
  <li></li>
  <li></li>
</ul>
```

This one the most useful and powerful when used with Lists.

### Bonus

We can get whole boilerplate code with only 2 keystrokes!

Simply do:

```html
!
```

and press tab to see the magic!


### Conclusion

I would highly recommend you to try Emmet.

You can write HTML without Emmet.
But once you use it, going back will feel painfully slow.
