# Intro
Same Disclaimer as before:
I'm trying to learn why there is a contradiction in my understanding. 
I'm hoping to learn something through this project.
## My Intuition
I was able to isolate this intuition from the other piece of intuition about waves:
### Square Pulses are not the ideal way to send data; I think standard waves are better.
## Definition of Standard Wave
Maybe It should have its own document instead of being defined in each document, but anyway I mean a dampened cosine wave multiplied by the unit step function.
I'm referring to wave of amplitude a, half-life per second b, frequency f, and delay d.
# Assumptions
The laplace transform of the standard wave is (a * 2 * pi * f)/((s - b * (ln2) )+(2 * pi * f)^2)
1. This Function takes up more bandwidth in a logarithmic way according to frequency.
2. If b > f , via a sequence of standard waves (one wavelength apart) one should be able to send data proportional to frequency. With less noise as b increases.
3. The shannon heartly theorem predicts bandwidth in bits is proportional to bandwidth in frequencies
# Contradiction
O(log(n)) is eventually dominated by O(n) so a contradiction is reached.
