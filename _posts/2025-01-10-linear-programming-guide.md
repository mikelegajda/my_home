---
layout: post
title: "Coffee, Choices, and Constraints: A Friendly Dive into Linear Programming"
subtitle: "A practical guide to solving optimization problems with linear programming"
date: 2025-08-24 14:30:00 +0100
author: "Mikele Gajda"
cover-img: "/assets/img/blog_1.jpeg"
thumbnail-img: "/assets/img/blog_1.jpeg"
tags: [linear-programming, optimization, tutorial, mathematics]
description: "Learn the fundamentals of linear programming with practical examples. This comprehensive guide covers theory, implementation, and real-world applications."
---


When getting introduced to operations research, the first encounter with linear programming gives a sense of the powerful tools at our disposal. It's like discovering a compass that can navigate through the complexity of real-world decisions, turning what feels overwhelming into something more manageable and clear.

---

## A quick day-to-day story  
Imagine this. You’ve got €20 in your wallet. Coffee costs €4, muffins cost €2. You *love* both, but your goal this week is to maximize **happiness** (let’s say each coffee gives you 5 “joy points” and each muffin gives 3).  

You can’t spend more than €20 (budget constraint), you obviously can’t buy negative muffins (non-negativity constraint). So, what's your goal? Well, you'd like to find the best combo of coffees and muffins that gives you the most joy.  

This is *exactly* what linear programming does: it helps us optimize (maximize or minimize) something while respecting the limits (constraints) we face.  

---

## The mathematics (in plain words)  
Linear programming (LP) problems usually have three parts (we've seen those in a previous article):  

1. **Decision variables**  
   - In our case: number of coffees `x` and number of muffins `y`.  

2. **Objective function**  
   - Maximize joy → `5x + 3y`.  

3. **Constraints**  
   - Budget: `4x + 2y ≤ 20`.  
   - Non-negativity: `x ≥ 0`, `y ≥ 0`.  

That’s it. You’ve got yourself a linear programming problem!  

---

## Why it matters (way beyond coffee)  
When you explore deeper, you really find that LP is *everywhere*.  

Linear programming is an essential tool for decision-making in a world of limited resources. It provides a powerful mathematical framework for finding the optimal solution in an ocean of possibilities. In real life, its applications space from businesses using it to solve complex logistical puzzles, to manufacturers relying on it for production planning to maximize output, to financial institutions applying it to portfolio optimization to balance risk and return. 

Basically, whenever you’ve got limited resources and big goals... LP shows up invited (or not) to the party.  

---

## A tiny Python demo (because code makes it real)  
Here’s a little snippet with Google `OR-tools` (a useful optimization library in Python).  

```python
from ortools.linear_solver import pywraplp

# Create the linear solver with the SCIP backend.
solver = pywraplp.Solver.CreateSolver('SCIP')
if not solver:
    print("SCIP solver not available.")
    # Or handle the error appropriately
else:
    # Decision variables
    # x = number of coffees
    x = solver.IntVar(0, solver.infinity(), 'coffee')
    # y = number of muffins
    y = solver.IntVar(0, solver.infinity(), 'muffin')

    # Constraint: 4*x + 2*y <= 20 (Budget)
    solver.Add(4 * x + 2 * y <= 20)

    # Objective function: Maximize 5*x + 3*y
    solver.Maximize(5 * x + 3 * y)

    # Solve the problem
    status = solver.Solve()

    # Print the solution
    if status == pywraplp.Solver.OPTIMAL:
        print(f"Optimal coffees: {x.solution_value()}")
        print(f"Optimal muffins: {y.solution_value()}")
        print(f"Maximum joy: {solver.Objective().Value()}")
    else:
        print("The problem does not have an optimal solution.")
````

When you run this, it tells you the sweet spot between coffees and muffins to max out your joy. Pretty cute, right? :)

---

## To conclude

So, linear programming isn't just some abstract set of inequalities and equations, but really provides a structured way to tackle complex decisions. It’s a **beautiful mix of logic and practicality**, quietly working behind the scenes in supply chains, finance, healthcare… and yes, even in your morning snack decisions.


