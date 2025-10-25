# Combinatorial Optimization: Partial Set Cover Problem

This repository contains a college project focused on solving the Partial Set Cover problem using Integer Linear Programming (ILP). This project was developed as part of a Combinatorial Optimization course (CS-538).

## Overview

The Partial Set Cover problem is a variation of the classic Set Cover problem, where the goal is to cover at least `P` elements from a given set `E` using a sub-collection of subsets `S'` from a larger collection `S`, such that the total cost of the chosen subsets is minimized. Each element `e` in `E` has a covering requirement `re`, meaning it must be covered by at least `re` subsets in `S'`.

The project formulates this problem as an Integer Linear Program (ILP) and solves it using the `PuLP` library in Python.

## Problem Definition

**Given:**
- An element set `E`.
- A collection of subsets of `E`, `S ⊆ 2^E`, with `∪B∈S B = E`.
- A cost `cB` for each subset `B ∈ S`.
- A covering requirement `re` for each element `e ∈ E`.
- A non-negative integer `P`.

**Required Solution:**
- A sub-collection `S′ ⊆ S` such that at least `P` elements in `E` are fully covered by `S′`.
- An element `e ∈ E` is fully covered by `S′` if `|{B ∈ S′: e ∈ B}| ≥ re`.
- The sub-collection `S′` must have the minimum cost, where `c(S′) = ΣB∈S′ c(B)`.

**Integer Linear Program (IP) Formulation:**

Minimize `ΣB∈S cB xB` subject to:

1. `Σe∈E ye ≥ P`
2. `ΣB∈S : e∈B xB − re ye ≥ 0 ∀ e ∈ E`
3. `xB ≥ 0 ∀ B ∈ S`
4. `xB ≤ 1 ∀ B ∈ S`
5. `ye ≤ 1 ∀ e ∈ E`
6. `ye ≥ 0 ∀ e ∈ E`
7. `xB ∈ Z ∀ B ∈ S`
8. `ye ∈ Z ∀ e ∈ E`

Where `xB` are binary variables indicating if subset `B` is chosen, and `ye` are binary variables indicating if element `e` is chosen to be multi-covered.

## Project Structure

- `Project Part-3.ipynb`: Jupyter Notebook containing the problem description, ILP formulation, and Python implementation using `PuLP` to solve the Partial Set Cover problem.
- `Project Part-3-Copy1.ipynb`: A copy of the main Jupyter Notebook.
- `Verification.ipynb`: Jupyter Notebook for verifying the solution.
- `intance01.txt`: Example input file containing the problem instance (E, S, P, RE values, Costs, and Subsets).
- `solution01.txt`: Output file containing the solution for `intance01.txt`, including the number of chosen subsets, minimum cost, and indices of the chosen subsets.
- `Project Part-3 CS-538.pdf`: PDF document related to the project, possibly a report or presentation.
- `Project Part-3 CS-538.webarchive`: Web archive of a document related to the project.

## How to Run

1. **Install Dependencies**:
   Ensure you have Python and Jupyter Notebook installed. Install the `PuLP` library:
   ```bash
   pip install pulp
   ```
   You may also need `numpy` if not already installed:
   ```bash
   pip install numpy
   ```

2. **Open Jupyter Notebook**:
   Navigate to the project directory and start Jupyter Notebook:
   ```bash
   jupyter notebook
   ```

3. **Execute the Notebook**:
   Open `Project Part-3.ipynb` and run all cells. The notebook will read the `intance01.txt` file, solve the ILP, and write the solution to `solution01.txt`.

## Team Members

- Archi Dsouza
- Abhishek Bhardwaj
- Piyush Nath
