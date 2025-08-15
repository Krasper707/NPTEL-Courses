## Week 1 notes (lecture-wise)

### Lec-1
#### Intro to LinearAlgebra(LA)

- Given an $nxn$ non-singular matrix A and an n-vector b, the problem is to find an n-vector X such that:
  - $AX=b$
- Practical variation of problem requires solution of several linear systems with same matrix A on left side , problem is to find matrix X such that $AX=b$

#### Least Square Problem:
- Given an $m x n$ matrix A and an m-vector b, find an n-vector X such that the norm of residual vector $||AX-b||_2$ is as small as possible. ; Used in engineering applications such as signals, image processing, weather prediciton and so on.

#### Eigenvalue Problem:
- Given an $n x n$ matrix A, problem is to find n numbers $\lambda_i$ and n vectors $x_i$ such that $Ax_i = \lambda_i x_i$ ; i =1,2,3,...,n


#### The generalized and quadratic eigenvalue problem:
- Given the $n$ x $n$ matrices A,B,C ,  problem is to find $\lambda_i$  and $x_i$ such that:
  - ($\lambda_i ^2 A + \lambda_i C +B)x_i$ =0 ; i=1,2,3,..,n
- Known as the quadratic eigenvalue problem. In special case when C is zero matrix, problem reduces to generalized eigenvalue problem.


#### Singular Value Decomposition
- Given an $m x n$ matrix A , the problem is to find unitary matrices U and V and a diagonal matrix $\Sigma$ such that $A= U (\sigma)V*$ ;

- Computational Difficulties:
  - Cramer's rule: Large system takes too long.
  - Matrix Inversion: Not practical all the time
  - Least squares by normal equations: Having difficulty for sensitivity to pertubation, corrupts the accuracy.
  - Computing eigenvalues by characteristic polynomial is not suitable approach as round-off errors block up
  - Solving generalized inverses ; $Ax=MBx => B^{-1}Ax =Mx$ ; computing inverse is costly.
  - Finding the singular values of $A^T A$, explicity formation of matrix product  $A^T A$ might lead to less of significant relevant information.



Infinity Norm:
<pre> ‖x‖∞ = max₍₁ ≤ i ≤ n₎ |xᵢ| , x ∈ ℝⁿ </pre>




### Stability in Numerical Analysis:
-  A number of maths problems are prone / sensitive to small computation errors(like rounding errors). A stable problem will be called `well-posed` and an unstable one will be called an `ill-posed` problem
-  **Stable** : If the solution x depends in a continuous way on the variable $y=f(x)$ else unstable.
-  Unstable problems are difficult to solve.
-  Condition number attempts to tmeasure the worst possible effect on the solution x of F(x,y)=0 when variable y is perturbed/changed by a small amount.

  ## Muller's Method:
  - For obtaining  both real and complex roots of a function. It is a generalization of the approach that led to the secant method.


---

