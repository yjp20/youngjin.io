---
title: How linear algebra should be taught
date: 2024-03-29T13:12:47-06:00
tags: ["math"]
---

When I first learned matrix multiplication in high school, my teacher said that matricies are "really
important", but that it's complicated and we didn't have time to go into it. And I really didn't get the point
back then; to me it was just a funky way to write equations.

Later, I learned that he was right. Linear algebra, which studies the linear systems matricies describe,
is arguably the most important field of mathematics. It's the foundation for every flavor of engineering,
including mechanical engineering, computer graphics, AI, robotics, and the list goes on.

And how universally practical linear algebra is might be surprising until you realize how simple and elegant
of an idea it is.

But not only is it really useful, linear algebra is really beautiful. Concepts in linear algebra have a
surprisingly visual and intuitive interpretation that isn't always taught, and I think that's a tragedy.

So I'm going to fix that --- I'm going to introduce linear algebra, like I always felt like it should have.

---

Linear algebra is so powerful is because it analyzes linear systems, and linear systems can describe _a lot_
of things.

One of the simplest of such a system is the Fibonacci sequence. I'm sure you've seen it, or heard about it:

$$
1, 1, 2, 3, 5, 8, 13, 21…
$$

Each new term in the Fibonacci sequence is the sum of the last two numbers before it.

Now, there are a lot of remarkable things to say about the Fibonacci sequence, but one of them is the fact
that each term is grows by the "golden ratio" which is defined to be \\({ 1+\sqrt{5} \over 2 } = 1.618… \\)

And that's remarkable, because the golden ratio appears in a ton of different places in nature (such as
sunflower seeds, shells, hurricanes, trees) as well as in art and proportions (like your monitor or a credit
card). Mathematically it's quite interesting as well; you can for example show that the golden ratio is the
"most irrational" number and the hardest number to approximate using a fraction of integers.

That aside, this raises a couple of questions:

- How do we know that the Fibonacci sequence increases according to the golden ratio?
- Do the starting two numbers matter? If it changes, what is the new ratio?
- How can we calculate the 100th number in the Fibonacci sequence, without adding together a hundred numbers?

Linear algebra answers all of these questions.

---

OK, so I said that it's a "system", but this is a sequence. To apply linear algebra, we need to define it as a
linear system.

How do we describe it as a system?

First, note that if we're trying to find the next number in the Fibonacci sequence, only the last two numbers matter. That gives the intuition that one reasonable way to define a system is to map the last two numbers before and after we add a new term:

<p>
$$
\begin{align*}
\text{new\_last} & = \text{last} + \text{second} \\
\text{new\_second} & = \text{last}
\end{align*}
$$
</p>

Or with symbols:

<p>
$$
\begin{align*}
\text{a} & = \text{x} + \text{y} \\
\text{b} & = \text{x}
\end{align*}
$$
</p>

This is a linear system, since all variables are expressed in linear, single-variable combinations. And
that means it can be written as a matrix:

<p>
$$
\begin{bmatrix}
a \\
b
\end{bmatrix}
=
\begin{bmatrix}
1 & 1 \\
1 & 0
\end{bmatrix}
\begin{bmatrix}
x \\
y
\end{bmatrix}
$$
</p>

Now the middle matrix, the one with the numbers, is what is called a "linear map", because it maps a pair of
numbers \\((x, y)\\) to another pair of numbers \\((a, b)\\). _And that means it can be represented on a
graph_.

<!-- todo interactible -->

The red arrow is the point that corresponds to \\((x,y)\\), while the blue arrow corresponds to \\((a,b)\\).
Try moving it around! Play with it until you get a good sense of how the transformation "looks" like.

<!-- todo animation of circle and square -->

---

We're still a little lost when it comes to being able to analyze the Fibonacci system. But here's something
you could have noticed while playing around with the animation. There are 4 different directions of arrows
that do not change direction after the transformation. And two of them are the mirror of each other.

Unlike other directions, the transformation of arrows along these two directions are quite simple: it just
multiplies the length of the arrow by a certain amount. We have one fewer thing to worry about since the
direction never changes, and that's going to help us break this system apart.

If you carefully measure how much the length of the arrow changes along these two directions, you'll see that
in one direction it scales by a factor of about \\(1.618\\)x times, and in the other direction, it scales by
\\(0.618\\)x times and _flips_ in the opposite direction.

If you are keen, you may have noticed that \\(1.618\\) _is the golden ratio_.

---

We're tantalizingly close to understanding why it is that the Fibonacci sequence increases by the golden
ratio, but we're still missing a logical step. Let's try graphing the Fibonacci sequence on a graph. We can do
this by making pairs of two terms, like \\((1,1)\\), \\((1,2)\\), \\((2,3)\\), \\((3,5)\\), \\((5,8)\\), and
plotting them on the 2D plane.

If we overlay these points on top of the two stable directions, we see an interesting pattern, it keeps
increasing in one direction by 1.618, and being squished and flipped in the other direction by 1.618.

As we keep increasing the number of terms in the Fibonacci sequence, the arrow gets closer and closer to the
direction of \\(1.618\\), and so it will get closer and closer to the behavior of arrows in that direction,
which increase by \\(1.618\\).

This effect can be seen even more clearly if we break apart each arrow into two arrows, in each direction:

<!-- animation of scale by 1.618, scale by 0.618, flip, and it slots directly into the new term -->

Now, you can see that that we've broken the transformation into these steps, but in the end it's exactly the
same linear map as the one we started with.

And this effect can be seen EVEN more clearly if we remove the coordinates in the background, and rotate the
plane so that the stable direction becomes the new axes.

<!-- animation of rotate coordinate axis, scale by 1.618, scale by 0.618, flip, and it slots directly into the new term -->

Now it's in a new coordinate space, where the transformation can be represented by two scaling operators in
these two directions.

---

It may not look like it, but we've done something really significant. We've completely separated the original
transformation into just a rotation and a stretch in the \\(x\\) and \\(y\\) axes, and a rotation back into
the original coordinate space.


