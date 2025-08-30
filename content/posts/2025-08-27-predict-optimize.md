---
layout: post
title: "Sunshine, Smog, and Smart Choices: A Friendly Intro to Predict-then-Optimize"
subtitle: "How prediction errors can turn 'optimal' transport plans into fragile ones"
date: 2025-08-27 10:00:00 +0100
author: "Mikele Gajda"
cover-img: "/assets/img/blog_2.jpeg"    
thumbnail-img: "/assets/img/blog_2.jpeg"  
tags: [machine learning, sustainability, research, optimization]                                        
description: "Predict then optimize"
---

The idea of using mathematics to helps us make smarter and more efficient choices, is definitely fascinating to me. Recently, I tried to play with a simple yet intriguing problem that felt both interesting and practically meaningful. The problem tries to find an answer to the following question: **how many electric buses should a city deploy tomorrow to cut pollution?**  

At first, it sounds quite easy and straightforward to be hones. But as often happens, reality comes in and she always likes to complexify things: if the **predictions** we have for tomorrow’s demand are wrong, even the most “optimal” deployment plan can fail miserably… and that’s the magic (and frustration) of **predict-then-optimize** :)  

---

## The story: a city’s bus challenge  

Imagine a city that operates both electric buses (clean but limited in number) and diesel buses (polluting but higher in number).  
- Electric buses are great but the city only owns **6 of them**.  
- Diesel buses are polluting, so the city wants to minimize their use.  
- Each bus, regardless of type, can carry **50 passengers**.  

We will try to find a solution to: **how many passengers will actually need buses tomorrow?** If we predict wrong, our “optimal” allocation won’t really be optimal.  

---

## Step 1: Predict passenger demand  

We’ll use a toy example where tomorrow’s passenger demand depends on temperature (I know, that's super simplified, but it gives you the idea). Warmer days → more people ride. A tiny linear regression does our prediction trick:  

```python
import numpy as np
from sklearn.linear_model import LinearRegression

# Dummy historical data: temperature vs passengers
X = np.array([[10], [15], [20], [25], [30]])
y = np.array([300, 350, 400, 450, 480])  # passengers observed

# Train the model
model = LinearRegression().fit(X, y)

# Tomorrow’s forecast: 22°C
predicted_passengers = int(model.predict([[22]])[0])
print(f"Predicted passengers: {predicted_passengers}")
````

Let's say the model predicts **420 passengers** for tomorrow.

---

## Step 2: Optimize bus allocation with OR-Tools

Knowing this forecast, the city now wants to deploy buses. The goal: cover all predicted passengers while minimizing the number of diesel-powered buses use.

```python
from ortools.linear_solver import pywraplp

# Create solver
solver = pywraplp.Solver.CreateSolver('SCIP')

# Decision variables
electric_buses = solver.IntVar(0, 6, 'electric_buses')  # max 6 available
diesel_buses = solver.IntVar(0, 100, 'diesel_buses')    # can use many

# Constraint: cover predicted demand
solver.Add(50*electric_buses + 50*diesel_buses >= predicted_passengers)

# Objective: minimize diesel buses
solver.Minimize(diesel_buses)

solver.Solve()

print(f"Electric buses: {electric_buses.solution_value()}")
print(f"Diesel buses: {diesel_buses.solution_value()}")
```

For **420 passengers**, the solver finds:

* 6 electric buses (300 seats)
* 3 diesel buses (150 seats)

Total = 450 seats → enough to cover demand. Pollution minimized, resources respected. Looks “optimal” :)

---

## Step 3: Reality bites

But here’s where things get interesting…

### Case 1: Real demand is lower (350 passengers)

* We oversupplied buses. Some buses run half-empty.
* Worse, we ran **3 diesel buses unnecessarily**, adding pollution that wasn’t needed.

### Case 2: Real demand is higher (480 passengers)

* Suddenly, our “optimal” plan leaves **30 passengers unserved**.
* Some of them may switch to cars or taxis, ironically causing *more* pollution.

---

## The bigger lesson

This little bus story shows why **predict-then-optimize** is powerful but at the same time tricky:

* **Predictions drive everything** → if your forecast is wrong, the optimization only amplifies the error.
* **Optimality is fragile** → “optimal” only means optimal *under the assumptions*.
* **Robustness matters** → sometimes, it’s better to plan conservatively (maybe always keep a buffer bus) rather than chase a brittle optimum.

---

## To conclude

I love working through simple examples to explain complex ideas. It reminds me that optimization is never the full story… it’s a partner play with prediction. And when predictions fail (as they often do), the “perfect” plan can quickly collapse.

Simple examples like this make me see “optimal” less like a magic word and more like a careful balance between data, assumptions, and reality.

