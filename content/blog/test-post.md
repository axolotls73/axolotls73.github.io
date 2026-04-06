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

```bash
hugo server --themesDir /Users/etucker/hugo-projects --theme blog-theme
```

### Python

```python
from typing import Iterator
import math

# Sieve of Eratosthenes
def primes(limit: int) -> Iterator[int]:
    """Yield all primes up to limit."""
    sieve = bytearray([1]) * (limit + 1)
    sieve[0] = sieve[1] = 0
    for i in range(2, math.isqrt(limit) + 1):
        if sieve[i]:
            sieve[i*i::i] = bytearray(len(sieve[i*i::i]))
    return (i for i, v in enumerate(sieve) if v)

class Polynomial:
    def __init__(self, coeffs: list[float]) -> None:
        self.coeffs = coeffs

    def __call__(self, x: float) -> float:
        return sum(c * x**i for i, c in enumerate(self.coeffs))

    def __repr__(self) -> str:
        terms = [f"{c}x^{i}" for i, c in enumerate(self.coeffs) if c != 0.0]
        return " + ".join(terms) or "0"

p = Polynomial([1.0, 0.0, -3.5, 2.0])
print(p(1.5))   # 0.875
```

### C

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX_NODES 1024

typedef struct Node {
    int key;
    struct Node *left, *right;
} Node;

/* Allocate and initialise a new BST node */
static Node *node_new(int key) {
    Node *n = malloc(sizeof *n);
    if (!n) { perror("malloc"); exit(EXIT_FAILURE); }
    n->key = key;
    n->left = n->right = NULL;
    return n;
}

Node *bst_insert(Node *root, int key) {
    if (!root) return node_new(key);
    if (key < root->key)      root->left  = bst_insert(root->left,  key);
    else if (key > root->key) root->right = bst_insert(root->right, key);
    return root;
}

int main(void) {
    int keys[] = {5, 3, 7, 1, 4, 6, 8};
    Node *root = NULL;
    for (size_t i = 0; i < sizeof keys / sizeof *keys; i++)
        root = bst_insert(root, keys[i]);
    return 0;
}
```

### C++

```cpp
#include <concepts>
#include <iostream>
#include <vector>
#include <algorithm>

template<std::totally_ordered T>
class SortedVec {
public:
    void insert(T val) {
        auto it = std::lower_bound(data_.begin(), data_.end(), val);
        data_.insert(it, std::move(val));
    }

    [[nodiscard]] bool contains(const T& val) const {
        return std::binary_search(data_.cbegin(), data_.cend(), val);
    }

    // Range-based for support
    auto begin() const { return data_.cbegin(); }
    auto end()   const { return data_.cend(); }

private:
    std::vector<T> data_;
};

int main() {
    SortedVec<int> sv;
    for (int x : {4, 1, 7, 2, 9, 3})
        sv.insert(x);
    std::cout << std::boolalpha << sv.contains(7) << '\n'; // true
}
```

### Rocq

```coq
Require Import List Arith.
Import ListNotations.

(* A simple intrinsically-typed expression language *)
Inductive ty : Type := Nat | Bool.

Inductive val : ty -> Type :=
  | VNat  : nat  -> val Nat
  | VBool : bool -> val Bool.

Inductive expr : ty -> Type :=
  | Lit    : forall t, val t -> expr t
  | Add    : expr Nat -> expr Nat -> expr Nat
  | IfThen : forall t, expr Bool -> expr t -> expr t -> expr t.

Fixpoint eval {t : ty} (e : expr t) : val t :=
  match e with
  | Lit _ v          => v
  | Add e1 e2        =>
      let (VNat n1) := eval e1 in
      let (VNat n2) := eval e2 in
      VNat (n1 + n2)
  | IfThen _ b e1 e2 =>
      let (VBool b') := eval b in
      if b' then eval e1 else eval e2
  end.

Lemma eval_add_comm : forall (e1 e2 : expr Nat),
    eval (Add e1 e2) = eval (Add e2 e1).
Proof.
  intros e1 e2.
  simpl. destruct (eval e1), (eval e2). simpl.
  rewrite Nat.add_comm. reflexivity.
Qed.
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
