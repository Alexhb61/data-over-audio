# Intro
Please Read Disclaimer in README.
I'm trying to learn why there is a contradiction in my understanding. 
I'm hoping to learn something through this project.
## My Intuition
I was able to isolate this intuition from the other piece of intuition about waves:
### Square Pulses are not the ideal way to send data; I think standard waves are better.
## Definition of Standard Wave
Maybe It should have its own document instead of being defined in each document, but anyway I mean a dampened cosine wave multiplied by the unit step function.
I'm referring to wave of amplitude a, half-life per second b, frequency f, and delay d.
# Contradiction:
1. Let ```c(t)``` be a sequence of timestamped delta functions.
2. then ```ramp(t) * c(t)``` is a signal sent with unit time square pulses.
3. then ```(ramp(t x epsilon) x standard(1,1,1,0) ) * c(t) ``` is the same signal but sent with larger pulses which can overlap without communication failure because of the dampened sine wave but needs twice the SNR. Note epsilon depends on production details.
4. Taking the laplace transform, we get : ```( L{ramp(t x epsilon)}(s) * ( delta(s - ln2 + 2pi x i ) + delta(s - ln2 + 2pi x i) ) ) x L{c}(s)```
5. So the frequency distribution is arbitrarily small depending on production details.
6. So from k hz and b bitdepth we get to 2x k x epsilon hz and b+1 bitdepth.
## Specifics:
Let w be one wavelength and D is the dampening amount for one wavelength for the encoding scheme.
Let k be the number of positions per wavelength.
Y is the signal being sent. X is a middle step. Encoding is the dampened cosine wave for 1 wavelength.
Bit is the sequence of bits intended to be sent.
### Deconstruction filter
X[t] = Y[t] - Y[t-w] x D
bit[i] = if from X[i x k] to X[(i + 1) x k] is closer to Encoding than 0 return 1 rather than 0
by closer I mean any error measure such as Sum of square ERRORS or Total Absolute Deviation.
### Construction filter
X[t] = bit[t div k] x Encoding[t mod k ]
Y[t] = X[t] + Y[t-w] x D
by div I mean integer division. By mod I mean modular arithmetic ( computing the remainder in division).
# Questions and Assumptions:
What am I assuming here?
I'll check back at a later point.
## More Precision than Bandwidth
You need to have more precision in the sending device and receiving device than "bandwidth" in the channel. That situation might be weird.
But is important.
