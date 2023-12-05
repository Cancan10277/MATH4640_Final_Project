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
The QR iteration method, as innovatively developed by Vandebril, Barel, and Mastronardi, introduces a novel approach to eigenvalue computation. This method uniquely employs a QR iteration with a rational function, allowing for convergence at both the top and bottom of the matrix. 

### Basic Concept
- **Matrix Decomposition**: Involves decomposing a matrix `A` into an orthogonal matrix `Q` and an upper triangular matrix `R`.
- **Iteration Process**: The algorithm iteratively applies QR decomposition and then multiplies the resulting components in reverse order (forming `RQ`). This is repeated until the matrix converges to a nearly triangular form.

### Process
- **Initial Step**: Begin with a matrix $A_0$, often the original matrix or a modified form.
- **Iterative Steps**: For each iteration `k`, decompose $A_{k-1}$ into $Q_kR_k$ and form $A_k = R_kQ_k$. This gradually forces $A_k$ to become upper triangular.
- **Convergence**: The diagonal elements of the converging matrix approximate the eigenvalues of the original matrix.

### Variants
- **Shift Strategies**: Incorporating shifts (like the Wilkinson shift) can improve convergence speed.
- **Implicit QR**: A variant that avoids explicit computation of QR decomposition in each iteration for efficiency.

### Modern Usage
- **Software Implementations**: Available in scientific computing libraries like MATLAB, NumPy in Python, etc.
- **Continued Relevance**: Remains a fundamental tool in numerical linear algebra with ongoing research for improvement.

## Background

## How it is worked
The process involves two key steps:
1. **RQ-Factorization**: The initial matrix, denoted as \(A - \kappa I\), undergoes RQ-factorization, resulting in \(RQ\).
2. **QR-Factorization**: Subsequently, the matrix \(A - \sigma I\) is multiplied by the conjugate transpose of \(Q\) from the first step, leading to a QR-factorization.

This method stands out by leveraging the properties of the RQ-factorization of \(A - \kappa I\) to intelligently compute the QR-factorization of the transformed matrix. The transformation that defines the QR step is based on the unitary factor \(Q\) obtained in this process.

A significant aspect of this method is its convergence properties. By applying multiple QR iterations with strategically chosen shifts (\(\sigma\)), the method converges to an upper triangular matrix, revealing the eigenvalues of the original matrix \(A\). This approach combines the QR and RQ methods, ensuring convergence at both ends of the matrix through a carefully selected function \(f(.)\) applied to \(A\). The function \(f(A) = (A - \sigma I)(A - \kappa I)^{-1}\) is identified as optimal for this purpose, avoiding the numerical challenges of inverting the factor \(A - \kappa I\). [1]


## Why it is used

## Limitation
- **Memory Constraints**: QR iteration methods, particularly in subspace iteration methods like Jacobi-Davidson, often require restarts due to memory limitations. These restarts are necessary to restrict computational overhead and are especially crucial when computing several eigenvalues. However, restarting can negatively impact the convergence of these methods. [2]

- **Performance Issues with Large-Scale Matrices**: Traditional methods, including QR decomposition, face significant performance limitations when dealing with large-scale matrices. The computational complexity increases dramatically with the size of the matrix, making these methods less efficient for large datasets. [3]

- **Convergence Rate**: The convergence rate of the QR iteration can be slow, especially for matrices with close or clustered eigenvalues. This can lead to increased computational time and resources.

- **Complexity in Generalized Eigenproblems**: When dealing with generalized eigenproblems, the QR iteration method may require more sophisticated approaches or adaptations, which can complicate the implementation and increase the computational burden.

## Strength

- **Efficiency with Large and Sparse Data**: QR iteration, especially in its higher-order forms, is efficient in handling large and sparse data tensors, avoiding intermediate memory explosion. [4]

- **Controlled Precision Computing**: QR iteration is useful in controlled precision computing, particularly for small matrices, where it can compute eigenvalues with high accuracy. [5]

- **Maintaining Matrix Structure**: In certain cases, like with companion matrices, QR iteration can maintain the structural properties of matrices, allowing for efficient computation steps. [6]

## Application

- **Eigenvalue Problems**: Commonly used in solving eigenvalue problems in scientific and engineering computations.
- **Dynamic Systems**: Useful for analyzing dynamic systems and assessing structural stability.
- **Data Analysis**: Employed in techniques like principal component analysis (PCA).

## References

1. Vandebril, R., Barel, M.V., & Mastronardi, N. (2008). Rational QR-iteration without inversion. Numerische Mathematik, 110, 561-575.
2. Fokkema, D.R., Sleijpen, G.L., & Vorst, H.A. (1998). Jacobi-Davidson Style QR and QZ Algorithms for the Reduction of Matrix Pencils. SIAM J. Sci. Comput., 20, 94-125.
3. Jalali, Z.S., Wang, C., Kearney, G., Yuan, G., Ding, C., Zhou, Y., Wang, Y., & Soundarajan, S. (2023). Memristor-Based Spectral Decomposition of Matrices and Its Applications. IEEE Transactions on Computers, 72, 1460-1472.
4. Sun, Y., & Huang, K. (2022). HOQRI: Higher-Order QR Iteration for Scalable Tucker Decomposition. In Proceedings of the 2022 IEEE International Conference on Acoustics, Speech and Signal Processing (ICASSP). https://dx.doi.org/10.1109/icassp43922.2022.9746726.
5. Banks, J. E., Garza-Vargas, J., & Srivastava, N. (2022). Global Convergence of Hessenberg Shifted QR III: Approximate Ritz Values via Shifted Inverse Iteration. arXiv preprint arXiv:2205.06804. https://dx.doi.org/10.48550/arXiv.2205.06804.
6. Bini, D., Daddi, F., & Gemignani, L. (2004). ON THE SHIFTED QR ITERATION APPLIED TO COMPANION MATRICES. Electronic Transactions on Numerical Analysis, 18, 137-152.
   
