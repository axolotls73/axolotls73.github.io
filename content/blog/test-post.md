+++
title = "Feature Test"
date = 2025-05-18
draft = true
math = true
+++

This is a normal paragraph. It sits in the main column, which is around 55% of the page width on desktop. Tufte CSS leaves generous space to the right for margin notes and figures.

Here is a sidenote.{{< sidenote >}}This is a **sidenote** with some `inline code` and [a link](https://example.com).{{< /sidenote >}} And here is a marginnote.{{< marginnote >}}This is a marginnote. It has no number in the text, just the indicator symbol.{{< /marginnote >}} Both should appear in the sidebar on desktop and as numbered footnotes on mobile.

## Typography

Paragraphs use IBM Plex Serif. *Italic text*, **bold text**, and ***bold italic***. `Inline code` uses IBM Plex Mono.

Here is a blockquote:

> The commonplace book is a way to build a personal library of ideas you can return to.
>
> It is both a store of knowledge and a thinking tool.

And a blockquote containing a code block:

> ```python
> def greet(name):
>     return f"Hello, {name}!"
> ```

## Lists

Unordered:

- First item
- Second item
    - Nested item
    - Another nested item
- Third item

Ordered:

1. First
2. Second
3. Third

## Code

Inline: `x = f(y)`. Block:

```python
def fibonacci(n):
    a, b = 0, 1
    for _ in range(n):
        yield a
        a, b = b, a + b

print(list(fibonacci(10)))
```

```bash
hugo server --themesDir /Users/etucker/hugo-projects --theme blog-theme
```

## Figures

Normal figure with sidebar caption:

{{< figure
  src="https://upload.wikimedia.org/wikipedia/commons/thumb/4/47/PNG_transparency_demonstration_1.png/280px-PNG_transparency_demonstration_1.png"
  caption="A normal figure. The caption sits in the sidebar on desktop and below the image on mobile."
  alt="Transparency demonstration"
>}}

Margin figure (image + caption together in the sidebar on desktop, footnote on mobile):

{{< figure
  src="https://upload.wikimedia.org/wikipedia/commons/thumb/4/47/PNG_transparency_demonstration_1.png/280px-PNG_transparency_demonstration_1.png"
  type="margin"
  caption="A margin figure. On mobile this becomes a footnote, image and all."
  alt="Transparency demonstration"
>}}
This paragraph follows the margin figure. On desktop the image and caption appear to the right. On mobile they become a numbered footnote at the bottom.

Full-width figure:

{{< figure
  src="https://upload.wikimedia.org/wikipedia/commons/thumb/4/47/PNG_transparency_demonstration_1.png/280px-PNG_transparency_demonstration_1.png"
  type="full"
  caption="A full-width figure with a figcaption below."
  alt="Transparency demonstration"
>}}

## Sidenotes mixed with marginnotes

A paragraph with multiple notes. Here is the first.{{< sidenote >}}First sidenote.{{< /sidenote >}} Some more text, then a second.{{< sidenote >}}Second sidenote — numbering should be sequential with marginnotes.{{< /sidenote >}} Then a marginnote.{{< marginnote >}}A marginnote between two sidenotes. On mobile it should be numbered in DOM order alongside the sidenotes.{{< /marginnote >}} End of paragraph.

## Long paragraph with mid-paragraph note

Sidenotes that appear mid-paragraph used to break the paragraph flow on mobile. Here is a long paragraph to test that.{{< marginnote >}}This note is in the middle of a long paragraph. On mobile it should appear as a footnote at the bottom, not break the paragraph.{{< /marginnote >}} The rest of the paragraph continues here after the note marker. It should read as a continuous block of text on both desktop and mobile, with the note relegated to the sidebar or footnote section respectively. This sentence is here to make the paragraph long enough to be meaningful.

## Math

Inline math: $E = mc^2$

Consider a probability space $(\Omega, \mathcal{F}, \mathbb{P})$ and a random variable $X : \Omega \to \mathbb{R}$. The expected value $\mathbb{E}[X] = \int_\Omega X \, d\mathbb{P}$ exists whenever $\mathbb{E}[|X|] < \infty$. For two random variables $X$ and $Y$ with joint density $f_{X,Y}(x, y)$, the covariance $\mathrm{Cov}(X, Y) = \mathbb{E}[XY] - \mathbb{E}[X]\mathbb{E}[Y]$ measures their linear dependence. By the Cauchy–Schwarz inequality, $|\mathrm{Cov}(X,Y)|^2 \leq \mathrm{Var}(X)\,\mathrm{Var}(Y)$, and the Pearson correlation $\rho = \mathrm{Cov}(X,Y) / \sqrt{\mathrm{Var}(X)\mathrm{Var}(Y)}$ satisfies $-1 \leq \rho \leq 1$. When $X \sim \mathcal{N}(\mu, \sigma^2)$, the moment generating function is $M_X(t) = e^{\mu t + \sigma^2 t^2 / 2}$ for all $t \in \mathbb{R}$.

Display math:

$$
\int_0^\infty e^{-x^2} dx = \frac{\sqrt{\pi}}{2}
$$

$$
\mathbf{F} = m\mathbf{a}
$$
