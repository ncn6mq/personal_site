---
layout: post
blog_title:  "Introducing a clean, versatile Markdown blog theme"
title: "Blog"
comments: true
description: "Markdown Cheatsheet Demo..."
keywords: "markdown, typography components, dummy content"
---

**I'm including a sample of the markdown styles I've adapted for this blog theme in case anyone else is interested in using them. A sample layout is provided below.**

**Styles:**
[https://github.com/Aerlinger/personal_site/blob/master/_sass/_posts.scss](https://github.com/Aerlinger/personal_site/blob/master/_sass/_posts.scss)

**Raw Markdown:**
[https://raw.githubusercontent.com/Aerlinger/personal_site/master/_posts/2017-02-10-markdown-cheatsheet-demo.md](https://raw.githubusercontent.com/Aerlinger/personal_site/master/_posts/2017-02-10-markdown-cheatsheet-demo.md)


#### Basic Typography

This is all simple markdown. **This text is bolded.** _This text is italic_ They can also be **_combined_** together. Or, we can highlight code: `ThisIsMyCode()`. Links work too [such as](#) or [http://www.example.com](http://www.example.com).

> I'm including a sample of the markdown styles I've adapted for this blog theme in case anyone else is interested in using them. A sample layout is provided below.

<div class="divider"></div>

## Headings H1 to H6

# H1 Heading

## H2 Heading

### H3 Heading

#### H4 Heading

##### H5 Heading

###### H6 Heading

<div class="divider"></div>

## Footnotes

Footnotes are also supported. This is an example for the footnote number one [[^1]]. You can even add more footnotes, with link! [[^2]]

<div class="divider"></div>

## Blockquote

> The problem with quotes found on the internet is that they are often not true. *-- Abraham Lincoln*

<div class="divider"></div>

## List Items

1. First order list item
2. Second item

* Unordered list can use asterisks
- Or minuses
+ Or pluses

**NOTE:** *`<ol>` list items are not current numbered*

<div class="divider"></div>

## Code Blocks

```javascript
var s = "JavaScript syntax highlighting";
alert(s);
```

```python
def myFunction():
  pass

s = "Python syntax highlighting"
print(s)
```

```
No language indicated, so no syntax highlighting.
But let's throw in a <b>tag</b>.
```

<div class="divider"></div>

## Tables

### Table 1: With Alignment

| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |

### Table 2: With Typography Elements

Markdown | Less | Pretty
--- | --- | ---
*Still* | `renders` | **nicely**
1 | 2 | 3

<div class="divider"></div>

## Horizontal Separator

We can insert HTML as well. The HTML `<hr>` element is for creating a "thematic break" between paragraph-level elements. In markdown, you can create a `<hr>` with any of the following:

* `___`: three consecutive underscores
* `---`: three consecutive dashes
* `***`: three consecutive asterisks

renders to:

___

---

***

<div class="divider"></div>

## Media

### Embedding a Youtube Video

<div class="video-container"><iframe width="1280" height="720" src="https://www.youtube.com/embed/Awf45u6zrP0" frameborder="0" allowfullscreen></iframe></div>

### Images

![Minion](http://i.imgur.com/lA91pOw.gif)

#### Acknowledgements:

The theme for this blog was inspired by some of the free templates from the Jekyll repository. I recommend checking them out here: [https://github.com/jekyll/jekyll/wiki/Themes](https://github.com/jekyll/jekyll/wiki/Themes).

---

#### Footnotes:

[^1]: 1: Footnote number one.

[^2]: 2: Links can also be included [click here!](#)



