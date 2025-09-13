# Introduction:

# Questions:
Q1: Why doesn't the Shannon Hartley theorem discuss complex frequencies?
This question I have causes people to be confused,
so I have formulated it into the physics-engineering challenge as:
Q2: Can we send data parallel to real frequencies in the form of complex frequencies?
Producing complex frequencies doesn't sound difficult, 
but isolating frequencies of the same real component with different imaginary component sounds hard;
thus, I have formulated the question for this note:
Q3: Does there exist a pair of realizable filters which reliably separate ``` rect(t) ``` from ``` rect(t).e^(pt) ``` ?
# Claim:
Nonrigourously, there exist w, n such that the linear time invariant filter
with transfer function in the frequency domain ```F(s) = 1/((s/w)^2n + 1 )``` is good enough.
Rigorously, for all real epsilon1,epsilon2,epsilon3, epsilon4 > 0, 
there exists a real positive w, and a positive integer n,
``` distance(rect(t), F*rect(t) ) < epsilon1 ```
``` distance(0,F(s-2w)*(rect(t) ) ) < epsilon2 ```
``` distance(rect(t).e^(pt),F(s-2w)*(rect(t).e^2wt) ) < epsilon3 ```
```distance(0, F*(rect(t).e^2wt) ) < epsilon4 ```
By symmetry, We will break this into two limits:
For all n, ```lim w->infinity distance(rect(t), F*rect(t) ) = 0 ```
For all w, ```lim n->infinity distance( 0, F*(rect(t).e^2wt)) < epsilon ```
If we pick a w to satisfy the first equation,
we might need to pick a larger w to satisfy the second equation.

## Lemma 1:
For all n; ```lim w->infinity distance(rect(t), F*rect(t) ) = 0 ``` starting limit.
iff For all n, ```lim w->infinity sum_(t in C) |rect(t)-F*rect(T) |^2 dt = 0 ``` expanding out definition of function distance.
iff for all n, ```lim w->infinity sum_(s in C) |L{rect}(s)-L{F*rect}(s) |^2 ds = 0 ``` using the fact that there is a laplace transform which is unitary.
iff for all n, ```lim w->infinity sum_(s in C) |(F- 1). L{rect}(s) |^2  ds = 0 ``` using the convolution theroem and algebra.
iff for all n, ```lim w->infinity F = 1/((s/w)^2n + 1 ) ``` which holds by elementary limit laws.
However that might be mixing up the s and w which are going to infinity at the same time.

## lemma 2: 
For all w, ``` lim n->infinity distance( 0 , F*(rect(t).e^2wt) ) < epsilon```
iff (because L is unitary for some constants)
For all w,``` lim n->infintiy distance(0, F.(L{rect}*delta(s-2w) ) ) < epsilon ```
Playing with definitions:
For all w, ``` lim n ->infinity distance(0,F(s).sinc(s-2w) ) < epsilon```
Let the error inside the circle of radius w at center 0 be epsilon; then we can bound the remaining error to be 0 because:
For all w, ``` lim n ->infinity distance_(outside the circle of radius w at center 0) (0, F(s).sinc(s-2w) ) =0 ```
Expanding the definition of F:
For all w, ``` lim n ->infinity sum_(outside the circle of radius w at center 0 )(sinc(s-2w)^2).(1/[(s/w)^2n + 1) )^2 = 0 ```
Which should hold by limit laws.
CLEAR ERROR: THERE ARE Poles in F that lie on the edge of the circle

## Concern
Distance might be the wrong mechanism.
Or summing over the entire complex plane might be irrelevant.
Furthermore, its unclear to me how to deal with the poles of filters in this analysis.
