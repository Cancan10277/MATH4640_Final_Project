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

### Modern Usage
- **Software Implementations**: Available in scientific computing libraries like MATLAB, NumPy in Python, etc.
- **Continued Relevance**: Remains a fundamental tool in numerical linear algebra with ongoing research for improvement.

## Background

## How it is worked

## Why it is used

## Limitation
- **Memory Constraints**: QR iteration methods, particularly in subspace iteration methods like Jacobi-Davidson, often require restarts due to memory limitations. These restarts are necessary to restrict computational overhead and are especially crucial when computing several eigenvalues. However, restarting can negatively impact the convergence of these methods. [1]

- **Performance Issues with Large-Scale Matrices**: Traditional methods, including QR decomposition, face significant performance limitations when dealing with large-scale matrices. The computational complexity increases dramatically with the size of the matrix, making these methods less efficient for large datasets. [2]

- **Convergence Rate**: The convergence rate of the QR iteration can be slow, especially for matrices with close or clustered eigenvalues. This can lead to increased computational time and resources.

- **Complexity in Generalized Eigenproblems**: When dealing with generalized eigenproblems, the QR iteration method may require more sophisticated approaches or adaptations, which can complicate the implementation and increase the computational burden.

## Strength

- **Efficiency with Large and Sparse Data**: QR iteration, especially in its higher-order forms, is efficient in handling large and sparse data tensors, avoiding intermediate memory explosion. [3]

- **Controlled Precision Computing**: QR iteration is useful in controlled precision computing, particularly for small matrices, where it can compute eigenvalues with high accuracy. [4]

- **Maintaining Matrix Structure**: In certain cases, like with companion matrices, QR iteration can maintain the structural properties of matrices, allowing for efficient computation steps. [5]

## Application

- **Eigenvalue Problems**: Commonly used in solving eigenvalue problems in scientific and engineering computations.
- **Dynamic Systems**: Useful for analyzing dynamic systems and assessing structural stability.
- **Data Analysis**: Employed in techniques like principal component analysis (PCA).

## References

1. Fokkema, D.R., Sleijpen, G.L., & Vorst, H.A. (1998). Jacobi-Davidson Style QR and QZ Algorithms for the Reduction of Matrix Pencils. SIAM J. Sci. Comput., 20, 94-125.
2. Jalali, Z.S., Wang, C., Kearney, G., Yuan, G., Ding, C., Zhou, Y., Wang, Y., & Soundarajan, S. (2023). Memristor-Based Spectral Decomposition of Matrices and Its Applications. IEEE Transactions on Computers, 72, 1460-1472.
3. Sun, Y., & Huang, K. (2022). HOQRI: Higher-Order QR Iteration for Scalable Tucker Decomposition. In Proceedings of the 2022 IEEE International Conference on Acoustics, Speech and Signal Processing (ICASSP). https://dx.doi.org/10.1109/icassp43922.2022.9746726.
4. Banks, J. E., Garza-Vargas, J., & Srivastava, N. (2022). Global Convergence of Hessenberg Shifted QR III: Approximate Ritz Values via Shifted Inverse Iteration. arXiv preprint arXiv:2205.06804. https://dx.doi.org/10.48550/arXiv.2205.06804.
5. Bini, D., Daddi, F., & Gemignani, L. (2004). ON THE SHIFTED QR ITERATION APPLIED TO COMPANION MATRICES. Electronic Transactions on Numerical Analysis, 18, 137-152.
   
