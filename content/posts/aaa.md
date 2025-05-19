---
title: "My First Post with Tufte CSS"
subtitle: "An exploration of elegant typography and layout"
date: 2025-05-18T10:00:00-06:00
draft: false
author: "John Doe"
tags: ["tufte", "hugo", "css", "typography"]
---


## Main Content Section

This is a paragraph of text in the main column. Tufte CSS is designed for readability and clarity, drawing inspiration from the work of Edward Tufte. The main content column is typically around 55% of the page width, with generous margins for notes and figures.

Here's a bit more text to see how paragraphs flow. We can also include lists:

* An item in an unordered list.
* Another item, demonstrating list styling.
    * A sub-item, indented.
* A final item.

And ordered lists:

1.  First item.
2.  Second item.
3.  Third item.

### A Subsection with Code

Let's look at some inline `code`. It should be styled with a monospace font. For code blocks, we use a `<pre>` tag, which Hugo's Markdown processor will generate from fenced code blocks:

```python
# This is a Python code block
def hello_tufte():
    print("Hello, Tufte CSS in Hugo!")

hello_tufte()
```

The Tufte CSS provides styling for these elements to be clear and distinct from the main prose.

## Figures and Captions

Tufte CSS has specific styling for figures and captions.
## Sidenotes and Margin Notes

Sidenotes and margin notes are a key feature of Tufte's style.
This paragraph demonstrates where a sidenote or margin note might appear. The CSS you provided includes styles for `.sidenote`, `.marginnote`, and `.sidenote-number`.

## Blockquotes

Blockquotes are also styled:


This concludes a brief tour of some elements. Remember to place the `et-book` fonts in your `static/et-book` directory for the typography to render correctly.
