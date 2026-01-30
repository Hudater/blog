---
## Hashnode
slug: web-fundamentals-part-2
domain: hashnode.hudater.dev
subtitle: "HTML Basics: Tags, Elements, and Structure Explained"
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
title: "HTML Basics: Tags, Elements, and Structure Explained (2/4)"
layout: post
date: 2026-01-30 04:40:00 +0530
categories: [chaicode, web-fundamentals-series]
comments: true
pin: false
# tags: [servers, proxmox, homelab, hybrid cloud, architecture diagram]
tags:
  - html
  - web-fundamentals
  - chaicode
image:
  path: "https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Display/Block_and_inline_layout/mdn-horizontal.png"
  alt: "Credit: MDN"
---

> You most probably know what tags are
>
> But what about elements?
>
> Okay, you know that too but let's just go through a primer!


### HTML

As you might already know, HTML stands for HyperText Markup Language.

HTML is the language which we use to give structure to a webpage. It is not a programming language, just a special way to write plain old text plus some commands for the browser (or any other HTML reader/client)

### Tags

What primarily makes HTML different from just Plain text are **Tags**

A Tag is the label inside brackets which specifies the type of content to the browser

For example:

```html
<p> I am a Paragraph </p>
<h1> I am a big heading </h1>
```

#### Opening and Closing tag

You might have noticed that we are writing same tag two times but the second time has a slash with it.

That slashed  tag is called a closing tag

| Tag  | Type         |
|------|--------------|
| <p>  |  Opening Tag |
| </p> |  Closing Tag |

Whatever is wrapped inside these tags is the content.

In general, all tags that are opened should be closed.

HTML being so forgiving, or more accurately: HTML Parser being so forgiving, we don't always need to close tags but it is still a good practice to close your tags.

### Elements

Tags and Elements are two distinct identities.

Tags, as we know, just the part with the bracket like `<p>` and `</h1`

Elements are the full structure including **the tags and the content**

From our example:

| Entity                        | Type    |
|-------------------------------|---------|
| <p>                           |  Tag    |
| </p>                          |  Tag    |
| <p> I am a Paragraph </p>     | Element |
| <h1> I am a big heading </h1> | Element |



#### Void Elements

While most elements wrap some content inside them, there are few which don't.

These elements are known as Void Elements or **Self Closing Elements**

Since these elements don't wrap anything inside them, they **don't need a closing tag**

For example:

```html
<img src="picture.png">
<br>
<link>
```

### Display Specifications/Types

Every element occupies certain amount of space on the page.

Block and Inline are two most common layout types.

#### Block-Level Elements

Block level elements start at a new line and occupies the whole width of the browser. Anything after it gets pushed down to a new line

Block level elements don't care if they have the content to occupy the whole width. They scale to the width with or without the need of the space.

This code snippet

```html
<h1> I am a big heading </h1>
<p> I am a Paragraph </p>
<footer>
  <p> I am a Paragraph inside footer </p>
</footer>
```

Could be visualized like this:

```
┌──────────────────────────────────────┐
│ <h1>                                 │
│   I am a big heading                 │
└──────────────────────────────────────┘

┌──────────────────────────────────────┐
│ <p>                                  │
│   I am a Paragraph                   │
└──────────────────────────────────────┘

┌──────────────────────────────────────┐
│ <footer>                             │
│                                      │
│   ┌──────────────────────────────┐   │
│   │ <p>                          │   │
│   │   I am a Paragraph inside    │   │
│   │   footer                     │   │
│   └──────────────────────────────┘   │
│                                      │
└──────────────────────────────────────┘
```

Some common block level elements are:

```html
<div>
<h1>
<p>
<section>
<ul>
<li>
```

#### Inline Elements

Inline elements behave like words. They just take the width they require.

Inline elements do not start on a new line

For example, this code snippet

```html
<p>This is <span>important</span> text.</p>
```

Could be visualized like this:

```html
This is important text.
```

Notice how the word "important" didn't start at a new line. This is because `span` is an inline element.

Some common inline elements are:

```html
<span>
<a>
<strong>
<em>
<img>
```

### Common Tags

Some common tags to explore at this point are:

| Tag           | Purpose                  |
| --------------|--------------------------|
| `<h1>`        | Main heading             |
| `<p>`         | Paragraph                |
| `<a>`         | Link                     |
| `<img>`       | Image                    |
| `<div>`       | Generic block container  |
| `<span>`      | Generic inline container |
| `<ul>` `<li>` | Lists                    |
| `<button>`    | Button                   |

### Conclusion

At this point, you understand the basics of HTML and that's enough to get started.

Best thing to do, for a beginner, would be start looking at HTML code of random websites.

You can do that by simply opening up any website, Right-click and Inspect (or view source)
