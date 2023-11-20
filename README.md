# MATH4640_Final_Project
---
Name: Cancan Wang
Topic: QR Iteration
Title: 
---
# QR Iteration

## Table of Contents
- [Overview](#Overview)
- [Background](#Background)
- [QR Iteration Overview](#QR-Iteration-Overview)
- [How it is Worked](#How-it-works)
- [Why it is used](#Why-it-is-used)
- [Limitation](#Limitation)
- [Strength](#Strength)
- [Application](#Application)

## Overview

### Basic Concept
- **Matrix Decomposition**: Involves decomposing a matrix `A` into an orthogonal matrix `Q` and an upper triangular matrix `R`.
- **Iteration Process**: The algorithm iteratively applies QR decomposition and then multiplies the resulting components in reverse order (forming `RQ`). This is repeated until the matrix converges to a nearly triangular form.

### Process
- **Initial Step**: Begin with a matrix `A_0`, often the original matrix or a modified form.
- **Iterative Steps**: For each iteration `k`, decompose `A_{k-1}` into `Q_kR_k` and form `A_k = R_kQ_k`. This gradually forces `A_k` to become upper triangular.
- **Convergence**: The diagonal elements of the converging matrix approximate the eigenvalues of the original matrix.

### Variants
- **Shift Strategies**: Incorporating shifts (like the Wilkinson shift) can improve convergence speed.
- **Implicit QR**: A variant that avoids explicit computation of QR decomposition in each iteration for efficiency.

### Applications
- **Eigenvalue Problems**: Commonly used in solving eigenvalue problems in scientific and engineering computations.
- **Dynamic Systems**: Useful for analyzing dynamic systems and assessing structural stability.
- **Data Analysis**: Employed in techniques like principal component analysis (PCA).

### Advantages and Limitations
- **Advantages**: Reliable and efficient for most matrices, especially effective for symmetric or nearly symmetric matrices.
- **Limitations**: Can be slow for large matrices and may require additional methods for certain matrix types.

### Modern Usage
- **Software Implementations**: Available in scientific computing libraries like MATLAB, NumPy in Python, etc.
- **Continued Relevance**: Remains a fundamental tool in numerical linear algebra with ongoing research for improvement.

## Background

## How it is worked

## Why it is used

## Limitation

## Strength

## Application
