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
