# CVRP (Capacitated Vehicle Routing Problem) using Artificial Immune System Algorithm

## About this Project

This repository contains a Jupyter Notebook implementation of the Capacitated Vehicle Routing Problem (CVRP) solved using an Artificial Immune System (AIS) algorithm. The approach is inspired by biological immune systems and applies evolutionary computation techniques to optimize vehicle routes.


---

## What is CVRP?

The **Capacitated Vehicle Routing Problem (CVRP)** is a classic combinatorial optimization problem and a generalization of the famous Traveling Salesman Problem (TSP).

**Objective:**

> Determine the optimal set of routes for a fleet of vehicles to deliver goods to a set of customers, minimizing the total distance (or cost) while respecting vehicle capacity constraints.

**Key Constraints:**

- **Single Depot:** All vehicles start and end at a central depot (Node 0).
- **Capacity Constraint ($Q$):** Each vehicle has a maximum carrying capacity. The total demand on a single route cannot exceed this capacity.
- **Demand:** Each customer has a specific demand for goods.
- **Optimization Goal:** Minimize the total distance traveled by all vehicles combined.

---

## What is the Artificial Immune System (AIS)?

**Artificial Immune Systems (AIS)** are adaptive systems inspired by theoretical immunology and observed immune functions, principles, and models, applied to problem solving.

This project implements the **Clonal Selection Principle (CLONALG)**:

> In nature, when an antigen (bacteria/virus) attacks, the immune system selects the B-Cells (antibodies) that best recognize (have high affinity with) that antigen. These cells then reproduce (clone) and undergo high rates of mutation (hypermutation) to evolve even better matches.

---

## Mapping Biology to Code

| Biological Concept   | CVRP Implementation                                      |
|---------------------|----------------------------------------------------------|
| **Antigen**         | The problem instance (coordinate points and demand list)  |
| **Antibody**        | A candidate solution (list of integers representing route)|
| **Affinity**        | Fitness of the solution: $1/(\text{Total Distance} + \text{Penalty})$ (higher is better) |
| **Clonal Expansion**| Duplicating the best routes in the current generation     |
| **Hypermutation**   | Randomly swapping or reversing nodes in a route          |

---

## Algorithm Process

The `AIS` class in this repository follows these evolutionary steps:

1. **Initialization:** Create a population of random `Antibody` objects.
2. **Selection:** Sort the population by affinity (distance).
3. **Cloning:** The best antibodies are cloned; better solutions produce more clones.
4. **Hypermutation:** Clones undergo mutation (swap and inversion operators applied to routes).
5. **Reselection:** Mutated clones are evaluated; if a clone is better than its parent, it survives.
6. **Replacement:** A percentage of the worst solutions are replaced by new random ones to maintain diversity and avoid local optima.

## Notebook Overview

The main notebook, `Sistema_Imunológico_CVRP.ipynb`, includes:

- **References and Data**: Links to the [CVRPLIB](http://vrp.galgos.inf.puc-rio.br/index.php/en/) dataset and the [PyVRP/VRPLIB](https://github.com/PyVRP/VRPLIB) library for reading problem instances.
- **Setup**: Installs required libraries and mounts Google Drive for data access (for Colab users).
- **Data Handling**: Defines a `Data` class to load and store CVRP instance data, including node coordinates, demands, and distance matrices.
- **AIS Components**:
	- `Antibody` class: Represents a candidate solution (route), with methods for route generation, affinity calculation (fitness), feasibility checks, and hypermutation (variation).
	- `AIS` class: Manages the population of antibodies, selection, cloning, mutation, and replacement over generations to evolve better solutions.
- **Execution**: Loads a sample CVRP instance, runs the AIS algorithm, and prints the best solution found, including truck routes and loads.
- **Utility Functions**: Functions to print truck routes and calculate truck loads for the best solution.

## Usage

To run the notebook:

1. Open `Sistema_Imunológico_CVRP.ipynb` in Jupyter or Google Colab.
3. Provide a valid CVRP instance file path (the example uses a file from Google Drive).
4. Execute all cells to see the algorithm in action and review the results.
