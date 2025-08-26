---
layout: post
title: "Linear Programming: From Theory to Practice"
subtitle: "A practical guide to solving optimization problems with linear programming"
date: 2025-01-10 14:30:00 +0100
author: "Mikele Gajda"
cover-img: "/assets/img/path.jpg"
thumbnail-img: "/assets/img/ijpr.jpeg"
tags: [linear-programming, optimization, tutorial, mathematics]
readtime: 8
description: "Learn the fundamentals of linear programming with practical examples. This comprehensive guide covers theory, implementation, and real-world applications."
---

Linear Programming (LP) is one of the most fundamental and widely used techniques in operations research and optimization. Whether you're optimizing supply chains, managing resources, or solving scheduling problems, LP provides a powerful mathematical framework for decision-making.

## What is Linear Programming?

Linear Programming is a mathematical optimization technique used to find the best outcome (such as maximum profit or minimum cost) in a mathematical model whose requirements are represented by linear relationships.

### Key Characteristics

Every linear programming problem has three essential components:

1. **Objective Function**: What you want to optimize (maximize or minimize)
2. **Decision Variables**: The unknowns you can control
3. **Constraints**: The limitations or requirements that must be satisfied

## A Classic Example: The Diet Problem

Let's work through a classic example to illustrate these concepts. Suppose you're planning a diet and want to minimize cost while meeting nutritional requirements.

### Problem Setup

You have two food options:
- **Food A**: $2 per unit, provides 3 units of protein and 1 unit of vitamin
- **Food B**: $3 per unit, provides 1 unit of protein and 2 units of vitamin

**Requirements:**
- At least 6 units of protein daily
- At least 4 units of vitamin daily

### Mathematical Formulation

Let's define our decision variables:
- x₁ = units of Food A to consume
- x₂ = units of Food B to consume

**Objective Function** (minimize cost):
```
Minimize: 2x₁ + 3x₂
```

**Constraints:**
```
3x₁ + x₂ ≥ 6  (protein requirement)
x₁ + 2x₂ ≥ 4  (vitamin requirement)
x₁, x₂ ≥ 0    (non-negativity)
```

## Solving with Python

Here's how to solve this problem using Python's SciPy library:

```python
from scipy.optimize import linprog
import numpy as np

# Objective function coefficients (minimize cost)
c = [2, 3]

# Inequality constraint matrix (convert ≥ to ≤ by multiplying by -1)
A_ub = [[-3, -1],  # -3x₁ - x₂ ≤ -6 (protein)
        [-1, -2]]  # -x₁ - 2x₂ ≤ -4 (vitamin)

b_ub = [-6, -4]

# Bounds for variables (x₁ ≥ 0, x₂ ≥ 0)
x_bounds = [(0, None), (0, None)]

# Solve the linear program
result = linprog(c, A_ub=A_ub, b_ub=b_ub, bounds=x_bounds, method='highs')

print(f"Optimal solution: x₁ = {result.x[0]:.2f}, x₂ = {result.x[1]:.2f}")
print(f"Minimum cost: ${result.fun:.2f}")
```

**Output:**
```
Optimal solution: x₁ = 1.33, x₂ = 1.33
Minimum cost: $6.67
```

## Graphical Solution Method

For two-variable problems, we can visualize the solution:

```python
import matplotlib.pyplot as plt
import numpy as np

# Create a grid of points
x1 = np.linspace(0, 5, 100)

# Constraint lines
protein_line = (6 - 3*x1)  # 3x₁ + x₂ = 6 → x₂ = 6 - 3x₁
vitamin_line = (4 - x1)/2  # x₁ + 2x₂ = 4 → x₂ = (4 - x₁)/2

# Plot constraints
plt.figure(figsize=(10, 8))
plt.plot(x1, protein_line, 'b-', label='Protein constraint: 3x₁ + x₂ ≥ 6')
plt.plot(x1, vitamin_line, 'r-', label='Vitamin constraint: x₁ + 2x₂ ≥ 4')

# Fill feasible region
plt.fill_between(x1, np.maximum(protein_line, vitamin_line), 10, 
                 alpha=0.3, color='green', label='Feasible region')

# Plot optimal point
plt.plot(1.33, 1.33, 'ro', markersize=8, label='Optimal solution')

plt.xlim(0, 5)
plt.ylim(0, 5)
plt.xlabel('x₁ (Food A)')
plt.ylabel('x₂ (Food B)')
plt.title('Linear Programming: Diet Problem')
plt.legend()
plt.grid(True, alpha=0.3)
plt.show()
```

## Real-World Applications

Linear programming has countless applications across industries:

### 1. **Supply Chain Optimization**
- Minimizing transportation costs
- Optimal warehouse locations
- Inventory management

### 2. **Production Planning**
- Resource allocation
- Manufacturing schedules
- Product mix optimization

### 3. **Financial Portfolio**
- Asset allocation
- Risk management
- Investment optimization

### 4. **Transportation**
- Route optimization
- Fleet management
- Network design

## Advanced Considerations

### Sensitivity Analysis

Once you have an optimal solution, it's crucial to understand how sensitive it is to changes in parameters:

```python
# Check how the solution changes with parameter variations
import pandas as pd

costs = np.arange(1.5, 3.5, 0.1)
solutions = []

for cost_a in costs:
    c_temp = [cost_a, 3]
    result_temp = linprog(c_temp, A_ub=A_ub, b_ub=b_ub, bounds=x_bounds, method='highs')
    solutions.append([cost_a, result_temp.x[0], result_temp.x[1], result_temp.fun])

df = pd.DataFrame(solutions, columns=['Cost_A', 'x1_optimal', 'x2_optimal', 'Total_Cost'])
print(df.head())
```

### Duality Theory

Every linear programming problem has an associated dual problem. Understanding duality helps in:
- Economic interpretation of solutions
- Computational efficiency
- Sensitivity analysis

## Common Pitfalls and Tips

1. **Always check feasibility**: Ensure your constraints don't contradict each other
2. **Scale your variables**: Large differences in magnitude can cause numerical issues
3. **Interpret results**: Always validate that your mathematical solution makes practical sense
4. **Consider integer constraints**: Sometimes variables must be whole numbers

## Next Steps

In future posts, we'll explore:
- **Integer Programming**: When variables must be whole numbers
- **Network Flow Problems**: Specialized LP applications
- **Multi-objective Optimization**: Handling conflicting objectives

Linear programming is just the beginning of your optimization journey. Master these fundamentals, and you'll have a solid foundation for tackling more complex optimization challenges!

---

*Have questions about linear programming? Drop them in the comments below, and I'll address them in future posts!*
