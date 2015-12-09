EXISTING PROBLEM: NUMERICAL INTEGRATION

Definite integrals arise in many different areas and the Fundamental Theorem
of Calculus is a powerful tool for evaluating definite integrals. However, it
cannot always be applied. There are some functions which do not have an
antiderivative which can be expressed in terms of familiar functions such as
polynomials, exponentials and trigonometric functions.
One such example is E<sup>(-X</sup>2). Of course, this is an important function since
it is the probability density function for the normal distribution.
Moreover, we sometimes only have information about a function by making
observations at a certain number of points. In that case, we do not have a
nice formula for the function we are integrating, but only some data points.
One of the current solution to the above problem is the Trapezoidal Rule.

EXISTING SOLUTION: THE TRAPEZOIDAL RULE

The trapezoidal rule uses trapezoids instead of rectangles to approximate the
definite interval over a closed bounded interval. By using points on the
graph of the function determined by a uniform width partition of the interval
the upper boundary of the trapezoid is formed.
Of course the more subintervals, (or said another way: the more trapezoids)
the more accuracy of the estimation. And here lies the biggest challenge in
the implementation of the Trapezoidal Rule - the sheer computational
complexity involved - particularly when high levels of accuracy are required.

SOLUTION PROPOSED USING CUDA / PROJECT OBJECTIVE

We have proposed a parallel algorithm for the Trapezoidal Rule, which
exploits the poer of CUDA. Running 4 blocks of 256 threads each, per call -
subject to a maximum limit of 2^27 calls (after this the function starts
making approximations).

CODE BRIEF

On execution, the user is asked to choose a mode for computation - Quick,
Standard or Extended - depending on which the relevant function is called.
In the Quick or the Default Mode, the Integration is performed over <X^2>
from 0 to 1. The accuracy is two decimal places. In the Standard and Extended
modes, the user gets to choose one out of the 5 common types of functions:
Inverse, Logarithmic, Algebraic, Trigonometric and Exponential. The accuracy
is three decimal places in Standard, while it increases to 6 decimal places
in Extended Mode. In addition, the Extended Mode also allows the user to
control the main kernel function. He can specify the Depth of Recursion at
which the function should start making serial calls, as well as the Depth of
recursion at which it should quit.