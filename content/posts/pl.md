---
title: "Programming language"
date: 2024-03-15T13:12:47-06:00
tags: ["rants"]
draft: true
---

A programming language and its design has to balance many concerns, from general concerns like 'ergonomics'
and 'performance' to very specific ones like C-ABI compatibility, unicode, and strings.

A practical language which slots well into the current landscape of languages (Clojure, zig) makes a ton of
sense, but I'm most interested in solving the problem of creating the best language I can, unfettered by the
concerns of maintaining any semblance of compatibility to the past.

At a high level, I think a great language must handle the following concerns:

- Productive (fast to write)
- Expressive (easy to read)
- Fast (fast runtime characteristics)
- Robust (doesn't explode unexpectedly)
- Elegant (???)

A language is in some ways nothing more than cultivated patterns and idioms. An effective language designer
must choose the right idioms and enforce them the right way.

For one, the language designer must chose how to execute an idea. Designs can explicitly allow and disallow certain
behaviors, but at other times designs can simply nudge users in the right direction by making bad patterns the
more difficult path. This idea is far from being unique to languages, but the nuances specific to it are great.

The designs and patterns that a designer can choose, extend, and apply together are a topic too broad to
summarize neatly. Some ideas are declarative vs imperative, functional, linear and affine types, dependent
types, strong types, memory management model, implicit arguments, and well a whole lot more.

- Productive (fast to write)
- Expressive (easy to read)
- Fast (fast runtime characteristics)
- Robust (doesn't explode unexpectedly)
- Elegant (???)

Below is a list of questions and hypothesis about programming languages and potential improvements to them that I'd like to
eventually explore:

1. What would a language that's designed with an LSP/IDE in mind look like?
2. How do you make meta-programming/partial-evaluation ergonomic?
3. How do you make one language that's able to be used for both systems, scripting, and shell programs?
4. How do you make a language that is productive to use?
5. How do you make a language that can be easily read?
6. How do you enforce memory-safety?
7. Can you do the above without a GC?
8. And can you do it without making life too difficult?

---

```
> .cd hello
> .exec { .add 1 2 } // if the 
```
