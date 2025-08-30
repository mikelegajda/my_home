---
layout: post
title: "The Secret Map to Better Decisions: My Love Affair with Operations Research"
subtitle: "From bakery optimization to life-changing math"
date: 2025-08-21 10:00:00 +0100
author: "Mikele Gajda"
cover-img: "/assets/img/blog_3.jpeg"
thumbnail-img: "/assets/img/blog_3.jpeg"
tags: [operations-research, optimization, academia]
mathjax: true
description: "operations research and optimization"
---


# Finding my way into OR

I didn’t fall in love with *Operations Research* (OR) in a single moment. It was more of a slow, steady realization, project by project, that these tools could bring clarity to messy, real-world decisions. 

Little by little I was building trust in OR’s ability to help me give a try to solve seriously complex problems.


---

## OR in plain words

So, what is Operations Research? In the most simple terms I can put it: it’s using mathematics to make better choices. It’s like having a smart friend who can suggest you, *“try this plan, it will probably save time, money, and a few headaches.”*

At its core, OR is about optimization: finding the best option among many (sometimes definitely TOO MANY). Whether it’s scheduling flights, routing delivery trucks, or deciding how much inventory to keep, OR uses mathematical models to add clarity to the noise.

---

## The mathematics behind

I'm not going to show heavy formulas here (I don't even like heavy formulas) but something needs to be mentioned: **Linear Programming (LP)**, the foundation of many OR problems. LP helps us find the best solution when we have:

1. A goal to maximize or minimize (like profit)
2. Variables we can control (like production quantities)
3. Constraints that limit our choices (like available resources)

Let's check a simple example that everyone can understand.

Imagine you run a small bakery 🍞. You sell bread and cake. Both use flour and yeast, just in different amounts. You want to maximize profit, but your pantry is limited.

* Variables:
  $x_1 =$ number of bread loaves
  $x_2 =$ number of cakes

* Objective (maximize profit):

  $$
  \text{Maximize } 3x_1 + 5x_2
  $$

  (bread earns 3€ each, cake earns 5€ each)

* Constraints (limited resources):

  $$
  2x_1 + 4x_2 \le 100 \quad \text{(flour)}
  $$

  $$
  3x_1 + 2x_2 \le 90 \quad \text{(yeast)}
  $$

  $$
  x_1, x_2 \ge 0
  $$

That’s OR in action on a practical, structured, and a little creative problem.

---

## Let’s code it (with Google OR-Tools)

Here’s the same problem in Python using **Google OR-Tools**:

```python
from ortools.linear_solver import pywraplp

# Create the solver: use GLOP for continuous LP, or switch to "CBC" if you need integers later.
solver = pywraplp.Solver.CreateSolver("GLOP")

# Decision variables (continuous, nonnegative)
x1 = solver.NumVar(0.0, solver.infinity(), "Bread")  # number of bread loaves
x2 = solver.NumVar(0.0, solver.infinity(), "Cake")   # number of cakes

# Objective: maximize 3*x1 + 5*x2
objective = solver.Objective()
objective.SetCoefficient(x1, 3.0)
objective.SetCoefficient(x2, 5.0)
objective.SetMaximization()

# Constraints
# 2*x1 + 4*x2 <= 100  (Flour)
c1 = solver.Constraint(-solver.infinity(), 100.0, "Flour")
c1.SetCoefficient(x1, 2.0)
c1.SetCoefficient(x2, 4.0)

# 3*x1 + 2*x2 <= 90   (yeast)
c2 = solver.Constraint(-solver.infinity(), 90.0, "yeast")
c2.SetCoefficient(x1, 3.0)
c2.SetCoefficient(x2, 2.0)

# Solve
status = solver.Solve()

if status == pywraplp.Solver.OPTIMAL:
    print(f"Bread loaves: {x1.solution_value():.2f}")
    print(f"Cakes: {x2.solution_value():.2f}")
    print(f"Maximum Profit: {objective.Value():.2f} €")
else:
    print("No optimal solution found.")
```

The solver doesn’t guess a solution, it computes the best mix of bread and cake given your resources. That’s the amazing superpower of OR: turning “what should I do?” into a clear plan to follow.

---

## Why this matters

Operations Research is not ‘just math’; it builds on strong mathematical foundations and, through specific algorithms, finds applications across many aspects of society:

* Airlines design crew schedules that are efficient *and* humane.
* Hospitals match staffing to patient needs while keeping workloads fair.
* Tech teams place servers across regions to keep apps fast for everyone.


These are just examples of the many optimization problems that we can solve using OR-based approaches.


---

## A personal reflection

OR taught me that math isn’t only elegant, it’s useful. It helps communities and businesses run a little smoother.

And the best part? OR isn’t just for big organizations. With open-source tools, anyone, from students to founders, can model a problem, test ideas, and make better decisions.

