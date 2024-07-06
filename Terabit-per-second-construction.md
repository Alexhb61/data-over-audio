# Intro
I'm willing to believe I made a mistake or misunderstood something, but I'm trying to learn something about physics or linear algebra.
I'm going to present the rest of the document as if it is error-free which it is up to my understanding. Please feel to mention errors to me.

### My Intuition
1. My intuition says that information can be sent through pulses other than the square pulses commonly used.
2. My intuition says that waves should be analyzed in 2 dimensions: dampening and frequency.

While I'd like to see a contradiction with these intuitions, I don't see a way to find a contradiction with those assumptions alone. Instead, I will find a contradiction in my understanding with more standard assumptions.
# Assumptions
These can be discussed as separate things which could be oversimplifications.
For conciseness, we will define the standard wave as follows:
 ``` StandardWave(a,d,w,p,t) = a * 2^(-d(t-p)) * sin(2 * pi * w * (t-p) ) * H(t-p) ```
 It is a dampened sine wave starting at time = 0 with four characteristics:
 1. amplitude a
 2. dampening rate d
 3. frequency w
 4. start time p.
