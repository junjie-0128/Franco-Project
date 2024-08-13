# Finding best pseudo-modes for HEOM from numerical spectral density - Franco Project

In this project, we use supervised machine learning as the method for decomposing the Bath
Correlation Function(BCF) between the open quantum system and the attached environment to
series of exponential terms. The neural network model in machine learning provides opportunity
of designing specific forms of the hidden layer, and focusing on the weight of the branches in the
hidden layers give the indication of the parameter we are interested. This parameter fitting method
allows approximating the bath correlation function efficient reduction of exponential terms, and so
that improving the calculation efficiency.

## Project Timeline

### 0. Preliminary Work
0.1. Attempted numerical integration for correlation functions (faced issues with complex numbers)
0.2. Calculated real and imaginary parts of the integration separately

### 1. Initial Model Development
We started with a hand-derived equation:
```latex
(s + ai)e^{(\eta + \omega i)t} = e^{\mathbf{\eta}\ t}\left(\mathbf{s}\cos{\mathbf{\omega}t}-\mathbf{a}\sin{\mathbf{\omega}t}\right)+ie^{\mathbf{\eta}\ t}\left(\mathbf{s}\sin{\mathbf{\omega}t}+\mathbf{a}\cos{\mathbf{\omega}t}\right)
```
(s + ai)e^((η + ωi)t) = e^(ηt)(s·cos(ωt) - a·sin(ωt)) + ie^(ηt)(s·sin(ωt) + a·cos(ωt))
1.0 Develop two model that serves fitting for the real part and the imagniary part seperately. Even though the model can fit well, but they does not make conceptual sense.

1.1 Merging two model together that they can fit together with higher efficiency.

1.2 Due to the special form and constrains of the equation, I further modified the model that let both real and imagnary part together with shared parameters.

### 2. Advanced Model Development
Shifted to a more general model using complex parameters and basis functions.

2.1. Implemented complex model using standard exponential basis functions:

```latex
C(t)= \sum_{i = 1}^k c_i e^{\eta_i t}+ \sum_{i = 1}^k \tilde{c_i} e^{\eta^\ast_i t}
```
C(t) = Σ(i=1 to k) [c_i·e^(η_i·t) + c̃_i·e^(η*_i·t)]
2.2. Utilized Lagrangian multipliers to characterize correlation functions:
```latex
\frac{\partial}{\partial t}
\begin{pmatrix}
  f_1 \\
  f_2 \\
  \vdots \\
  f_k \\  
\end{pmatrix}
-
\mathbb{M}
\begin{pmatrix}
  f_1 \\
  f_2 \\
  \vdots \\
  f_k \\  
\end{pmatrix}
=
\begin{pmatrix}
  G_1 \\
  G_2 \\
  \vdots \\
  G_k \\  
\end{pmatrix}
\rightarrow 0
```
∂/∂t [f_1, f_2, ..., f_k]^T - M·[f_1, f_2, ..., f_k]^T = [G_1, G_2, ..., G_k]^T → 0

2.3. Enhanced model with critical damping properties:
```latex
\left[C(t) - \sum_{i = 1}^k c_i f_i(t)\right] + \lambda_1 G_1 + \dots + \lambda_k G_k = \mathcal{L}\rightarrow 0
```
[C(t) - Σ(i=1 to k) c_i·f_i(t)] + λ_1·G_1 + ... + λ_k·G_k = L → 0
Due to the mathematical interpretation, besides the 2.2 model that may give more freedom on the basis function perspective, we also use the critical damping property to get the analytical solution function, and add them to the 2.1 model.
```latex
C(t)= \sum_{i = 1}^k c_i e^{\eta_i t}+ \sum_{i = 1}^k \tilde{c_i} e^{\eta^\ast_i t} + d_1\psi_1 + d_2\psi_2
```
Then, the project has progressed from basic hand-derived equations to more sophisticated models incorporating complex parameters, Lagrangian multipliers, and critical damping properties.

### 3. Further refinement of models
