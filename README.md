---
Name: Cancan Wang
Topic: QR Iteration
Title: The Efficacy of QR Iteration in Numerical Linear Algebra
---
# QR Iteration

## Table of Contents
- [Overview](#Overview)
- [Background](#Background)
- [How it is Worked](#How-it-is-Worked)
- [Why it is used](#Why-it-is-used)
- [Examples](#Examples)
- [Limitation](#Limitation)
- [Strength](#Strength)
- [Application](#Application)

## Overview
QR Iteration is a pivotal technique in numerical linear algebra, specifically employed for determining the eigenvalues of matrices. It is categorized under iterative methods due to its process of sequentially honing in on the solution via repeated computational cycles. The QR Iteration technique systematically decomposes a matrix into two components: an orthogonal matrix (Q) and an upper triangular matrix (R). Through successive iterations, it refines the approximation of a matrix's eigenvalues. The iterative aspect of the method highlights its procedural progression, which incrementally edges closer to the matrix’s actual eigenvalues. This iterative procedure is especially advantageous for full, dense matrices where alternative eigenvalue calculation methods may be ineffective or slow to converge. The QR Iteration method exemplifies the intricate synergy of linear algebra operations in the realm of numerical computations.

## Background
Eigenvalues are essential in the field of linear algebra, serving as a cornerstone for understanding linear transformations and their applications in stability analyses, physics, and engineering. Traditional approaches to computing eigenvalues, like power iteration or inverse iteration, are suitable for scenarios involving large sparse matrices or when targeting the extreme eigenvalues. Yet, these methods have limitations, especially when a full eigenvalue spectrum of a matrix is required [1].

Enter QR Iteration, an eigenvalue algorithm devised independently by John G. F. Francis and Vera N. Kublanovskaya in the late 1950s [2]. This method leverages the concept that similar matrices share identical eigenvalues and eigenvectors, forming the foundation of its iterative process. Currently, QR Iteration is the method of choice to obtain a complete set of eigenvalues, particularly for full, dense matrices [3].

The algorithm's computational efficiency is greatly enhanced by first reducing a matrix to Hessenberg form, which trims the operational complexity from cubic to quadratic relative to matrix size. This pre-processing step renders QR Iteration not just faster but also applicable to a broader range of matrices, including non-symmetric and non-positive definite ones [4].

Today, QR Iteration remains the most prevalent method for full eigenvalue computation, valued for its robustness and versatility. Its slow convergence rate for some matrices is often offset by its comprehensive applicability and the significant improvements it offers over traditional methods for dense matrices of modest size [5].

## How it is worked
The process involves two key steps:
1. **RQ-Factorization**: The initial matrix, denoted as $\(A - \kappa I\)$, undergoes RQ-factorization, resulting in $\(RQ\)$.
2. **QR-Factorization**: Subsequently, the matrix $\(A - \sigma I\)$ is multiplied by the conjugate transpose of $\(Q\)$ from the first step, leading to a QR-factorization.

This method stands out by leveraging the properties of the RQ-factorization of $\(A - \kappa I\)$ to intelligently compute the QR-factorization of the transformed matrix. The transformation that defines the QR step is based on the unitary factor $\(Q\)$ obtained in this process.

A significant aspect of this method is its convergence properties. By applying multiple QR iterations with strategically chosen shifts $\(\sigma\)$, the method converges to an upper triangular matrix, revealing the eigenvalues of the original matrix $\(A\)$. This approach combines the QR and RQ methods, ensuring convergence at both ends of the matrix through a carefully selected function $\(f(.)\)$ applied to $\(A\)$. The function $\(f(A) = (A - \sigma I)(A - \kappa I)^{-1}\)$ is identified as optimal for this purpose, avoiding the numerical challenges of inverting the factor $\(A - \kappa I\)$. [6]


## Why it is used
The QR iteration method is primarily used for its ability to compute eigenvalues and eigenvectors of a matrix efficiently. This method is particularly advantageous because it allows for convergence from both ends of the matrix, a feature not commonly found in standard eigenvalue algorithms. The process involves a two-step iteration, starting with an RQ-factorization followed by a QR-factorization. This approach is beneficial as it exploits the properties of the initial RQ-factorization to intelligently compute the subsequent QR-factorization.

One of the critical aspects of the QR iteration method is its stability and reliability in numerical computations. The method avoids the direct inversion of the matrix factor, which can be numerically unstable, especially when the shift chosen is close to an eigenvalue of the matrix, leading to near-singular scenarios. Instead, the method employs a rational function-driven iteration, which maintains numerical stability and enhances the convergence properties.

The convergence of the QR algorithm and its variants can be interpreted as subspace iteration, determined by polynomials in the matrices. This interpretation allows for the derivation of bounds on the convergence of these algorithms, making the QR iteration method a robust choice for eigenvalue computations. [6]

## Examples
- **Basic QR Iteration for a 2x2 Matrix**
1. **Matrix to Decompose**: Consider a 2x2 matrix \(A\).
  $A=  | a  b  |
       | c  d  |$

2. **Initial Decomposition**: Perform the QR decomposition of $A$ manually or using a standard algorithm to get $Q$ (an orthogonal matrix) and $R$ (an upper triangular matrix).

3. **Form New Matrix**: Multiply $R$ and $Q$ (in this order) to get a new matrix $A_1 = RQ$.

4. **Iterate**: Repeat the QR decomposition for $A_1$, and form a new matrix $A_2$ from the resulting $Q$ and $R$.

5. **Convergence**: Continue this process. The matrix $A_n$ will converge to an upper triangular matrix as $n$ goes to infinity. The diagonal elements of this matrix are the eigenvalues of $A$.

- **QR Iteration with Shifts for a 3x3 Matrix**
1. **Initial Matrix**: Start with a 3x3 matrix $A$.
   $
   A = \begin{pmatrix}
   a & b & c \\
   d & e & f \\
   g & h & i
   \end{pmatrix}
   $

2. **Choose a Shift**: Select a shift value, often the bottom-right element of $A$, say $\( \mu = i \)$.

3. **Shift and Decompose**: Subtract $mu I $ from $A$, and perform QR decomposition on $\( A - \mu I \)$.

4. **Update Matrix**: Form a new matrix $\( A_1 = RQ + \mu I \)$.

5. **Iterate with New Shifts**: Repeat the process with new shifts (usually the new bottom-right element) and updated matrices.

6. **Convergence**: The matrix will eventually converge to a diagonal or nearly-diagonal form, with the eigenvalues on the diagonal.



## Limitation
- **Memory Constraints**:
  
QR iteration methods, especially in subspace iterations like Jacobi-Davidson, often face memory constraints that necessitate periodic restarts to manage computational overhead, particularly when computing multiple eigenvalues. While these restarts help in keeping memory usage in check, they can adversely impact the convergence of the methods. Each restart may disrupt the iterative process, potentially eroding previously gained convergence progress and requiring additional iterations to recover. This trade-off between memory management and convergence efficiency poses a significant challenge, particularly in large-scale computational tasks where both aspects are crucial. [7]

- **Performance Issues with Large-Scale Matrices**:
  
Traditional QR iteration methods encounter significant performance challenges when applied to large-scale matrices. As the size of the matrix increases, the computational complexity of the QR decomposition escalates dramatically, leading to a substantial decrease in efficiency. This scaling issue is particularly problematic in handling vast datasets where the computational load can become overwhelming, resulting in prolonged processing times and increased resource consumption. The inherent algorithmic structure of the QR iteration, while effective for smaller matrices, does not scale as efficiently for larger ones, making it less suitable for applications involving big data or extensive computational tasks. This limitation is a critical consideration in the field of numerical analysis and data processing, where the ability to efficiently handle large-scale matrices is increasingly important. The performance bottleneck with larger matrices underscores the need for more scalable and efficient computational methods in handling extensive datasets.[8] 

- **Convergence Rate**:
  
The convergence rate of the QR iteration can be slow, especially for matrices with close or clustered eigenvalues. This slower convergence can result in increased computational time and resource utilization, posing challenges in scenarios where speed is crucial. In matrices where eigenvalues are tightly grouped, the QR iteration method may require a higher number of iterations to achieve the desired precision, thereby extending the computation process. This aspect can be particularly limiting in large-scale computations or in real-time systems where rapid processing is essential. While the QR iteration method offers high accuracy and stability, this trade-off in terms of convergence speed is a critical consideration, especially in applications where efficiency and fast processing are as important as the accuracy of the results.

- **Complexity in Generalized Eigenproblems**:
  
The QR iteration method, while robust in many scenarios, encounters limitations when addressing generalized eigenproblems. In these cases, the method often necessitates more sophisticated approaches or specific adaptations, adding layers of complexity to its implementation. This increased complexity can pose challenges, particularly in terms of the computational burden and the intricacy of algorithmic design. Generalized eigenproblems, which involve a pair of matrices rather than a single matrix, require a nuanced approach that the standard QR iteration method may not readily provide. Adapting the method to suit these problems often means integrating additional steps or modifying the algorithm, which can lead to increased computational resources and time, as well as a higher demand for technical expertise in its application. This limitation highlights a trade-off between the method's versatility and its complexity, especially in advanced computational scenarios involving generalized eigenproblems.

## Strength

- **Efficiency with Large and Sparse Data**:

QR iteration, especially in its higher-order forms, is efficient in handling large and sparse data tensors, avoiding intermediate memory explosion. [9] This is achieved through a streamlined orthogonalization process in each iteration, circumventing the need for memory-intensive operations like singular value decomposition. As a result, the QR iteration method is not only memory-efficient but also computationally faster, making it highly suitable for large-scale data analysis in fields such as big data analytics, scientific computing, and machine learning, where managing large, sparse matrices is essential. This efficiency in processing complex data structures positions the QR iteration as a valuable tool in numerical linear algebra and tensor computations.

- **Controlled Precision Computing**:

QR iteration is useful in controlled precision computing, particularly for small matrices, where it can compute eigenvalues with high accuracy [10]. This precision stems from the method's ability to perform iterative calculations with a high degree of numerical stability. By utilizing a systematic approach to convergence, the QR iteration method ensures that each step is calculated with controlled precision, minimizing computational errors. This aspect is crucial in applications where even minor inaccuracies can lead to significant deviations in results, such as in scientific simulations and financial modeling. The method's inherent stability and precision make it a preferred choice for scenarios demanding exactness and reliability in computations, underscoring its strength in applications where precision is paramount.

- **Maintaining Matrix Structure**:

The QR iteration method is highly regarded for its ability to maintain the structural properties of matrices, a feature particularly beneficial in cases involving companion matrices [11]. This capability ensures that the intrinsic structure of the original matrix is preserved throughout the iteration process, leading to more efficient computation steps. By retaining the matrix structure, the QR iteration method enhances computational efficiency and accuracy, especially in algorithms where the structural integrity of the matrix plays a critical role in the outcome. This attribute is particularly valuable in numerical methods and applications where the preservation of matrix characteristics, such as sparsity or symmetry, is essential for the accuracy and efficiency of the computational process. The QR iteration's proficiency in maintaining matrix structure makes it a robust and reliable tool in advanced numerical analysis and linear algebra.

## Application

- **Eigenvalue Problems in Scientific and Engineering Computations**:
  - In scientific and engineering domains, eigenvalue problems are fundamental in understanding the behavior of various systems and processes. The QR iteration method is a staple in these areas for its ability to accurately and efficiently compute eigenvalues and eigenvectors of matrices.

  - It is particularly useful in scenarios involving large, sparse matrices, where traditional eigenvalue computation methods may falter. The QR iteration method's ability to handle these matrices makes it invaluable in complex simulations, such as those encountered in quantum mechanics, vibration analysis, and structural engineering.
- **Analysis of Dynamic Systems and Structural Stability**:
  - The QR iteration method is instrumental in the analysis of dynamic systems, especially in control theory and systems engineering. It helps in determining the stability and response characteristics of systems modeled by differential equations.

  - In structural engineering, the method is used to assess the stability and vibrational modes of structures. This is crucial in designing buildings, bridges, and other structures to ensure they can withstand various forces and stresses.
- **Data Analysis and Principal Component Analysis (PCA)**:
  - In the realm of data analysis, the QR iteration method is employed in techniques like PCA, which is widely used for dimensionality reduction in machine learning and statistics. PCA involves the computation of eigenvectors and eigenvalues of data covariance matrices, a task well-suited for the QR iteration method. By efficiently computing these, it allows for the extraction of principal components, which are key in identifying patterns and reducing the complexity of data.

  - This application is particularly relevant in fields like bioinformatics, finance, and social sciences, where large datasets are common, and extracting meaningful information is critical.

## References

1.  Wikipedia contributors. QR algorithm. Wikipedia, The Free Encyclopedia. https://en.wikipedia.org/wiki/QR_algorithm.
2. Python Numerical Methods. The QR Method. Berkeley University. https://pythonnumericalmethods.berkeley.edu/notebooks/chapter24.03-The-QR-Method.html.
3. Stanford University. The Practical QR Algorithm. https://web.stanford.edu/class/cme335/lecture7.pdf.
4. SIAM Review. Understanding the QR Algorithm. https://epubs.siam.org/doi/abs/10.1137/1034116.
5. JSTOR. Understanding the QR Algorithm. https://www.jstor.org/stable/2032911.
6. Vandebril, R., Barel, M.V., & Mastronardi, N. (2008). Rational QR-iteration without inversion. Numerische Mathematik, 110, 561-575.
7. Fokkema, D.R., Sleijpen, G.L., & Vorst, H.A. (1998). Jacobi-Davidson Style QR and QZ Algorithms for the Reduction of Matrix Pencils. SIAM J. Sci. Comput., 20, 94-125.
8. Jalali, Z.S., Wang, C., Kearney, G., Yuan, G., Ding, C., Zhou, Y., Wang, Y., & Soundarajan, S. (2023). Memristor-Based Spectral Decomposition of Matrices and Its Applications. IEEE Transactions on Computers, 72, 1460-1472.
9. Sun, Y., & Huang, K. (2022). HOQRI: Higher-Order QR Iteration for Scalable Tucker Decomposition. In Proceedings of the 2022 IEEE International Conference on Acoustics, Speech and Signal Processing (ICASSP). https://dx.doi.org/10.1109/icassp43922.2022.9746726.
10. Banks, J. E., Garza-Vargas, J., & Srivastava, N. (2022). Global Convergence of Hessenberg Shifted QR III: Approximate Ritz Values via Shifted Inverse Iteration. arXiv preprint arXiv:2205.06804. https://dx.doi.org/10.48550/arXiv.2205.06804.
11. Bini, D., Daddi, F., & Gemignani, L. (2004). ON THE SHIFTED QR ITERATION APPLIED TO COMPANION MATRICES. Electronic Transactions on Numerical Analysis, 18, 137-152.
   
