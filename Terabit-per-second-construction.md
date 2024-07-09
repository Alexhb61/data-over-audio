# Intro
Please Read Disclaimer in README.
Please feel to mention errors to me.

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
The 6 assumptions worth making are as follows:
1. Standard Wave Generation
2. Linearity of Electrical Cirucits
3. Linearity of Air at STP
4. The Inaudibility of distance in Air at STP
5. Linear Time invariant Filter for Standard Waves
6. Decoding scheme for Sequence of Standard Waves
7. Shannon-Hartley Theorem

## 1 Standard Wave Generation
## 2 Linearity of Electrical Circuits
## 3 Linearity of Air at STP
My basic understanding of sound is that waves of different frequencies don't interfere with one another.
Ignoring reflections for a moment, the sound at one point should be the sum of sources with some volume effects of sound dispersion.
Those reflections in a large enough space will be indistinguishable from background noise.
## 4 The Inaudibility of distance in Air at STP
I'm under the impression that you can't hear the distance of a pure note as separate from volume. I would really like to play with that sound effect if it exists, but if it doesn't, the contradiction is in one of the other assumptions.
## 5 Linear Time invariant Filter for Standard Waves
## 6 Decoding scheme for Sequence of Standard Waves
First we remove the repeated wave sections with a delay based filter:
Y(t) = X(t) - 2^(-d/w) *X(t-1/w) 
Then it should be simple to distinguish between a single wavelength being mostly present or not.
Is Y(t) from b/w to (b+1)/w closer to a single wavelength or zero -> bit_wdb
One way to do this is ask which has less mean absolute error. sum | Y(t) - signal(t) | vs sum |Y(t)| which is smaller over that wavelength would determine 1 vs 0.
## 7 Shannon-Hartley Theorem


# The Contradiction
Here is the signal we are making:
```
For w = 1000 to 11000
For d = w to 11000
For b = 0 to w
produce standardwave(1,d,w,b/w,t) if bit_wdb is true else: silence.
```
Setup with many mics and speakers:
For all frequencies w from 1000 to 11000;
For all dampening rates from the fr w to 11000;
All the standard waves generators of a single frequency and dampening rate need to be combined into a circuit and play on a speaker.
The waves combine in the air.
They travel 1 meter with low distortion.
For each frequency and dampening rate, a microphone picks up the whole signal, and a filter isolates the appropriate frequency and dampening rate which then are measured by a DAC and decoded.

Setup with 1 mic and 1 speaker:
Same thing but possibly more things in series.
Note you still need a bunch of generators and DACs.
