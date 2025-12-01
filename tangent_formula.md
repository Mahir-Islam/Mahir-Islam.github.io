01/12/2025

# Hassan's Tangent Formula

For a circle of the form $$(x - a)^2 + (y - b)^2 = r^2$$, what is the formula for the tangent around such circle at degree $$\theta$$?

TLDR; it's: $$y = \tan(\theta)(x - a) + \sec(\theta)r + b$$.
I couldn't find any information about this specific formula, so I'm claiming it for myself! I'll call it Hassan's formula. Now, why is that? Because I said so1 See for yourself at (here)[https://www.desmos.com/calculator/4215338557]. But I guess that's not good enough, so let's prove it!

First, let's set $$a, b = 0$$, so we start with the special case $$x^2 + y^2 = r^2$$, centered around the origin. To find the magnitude, we do $$\sqrt{x^2+y^2}$$, and for the angle it occupies relative to (0,0), we compute $$atan(\frac{x_1}{x_0})$$


We have a tangent line, which touches $$(x_0, x_1)$$. We know that the gradient is $$\frac{x_1}{x_0}$$.
