# Introduction
This note attempts to articulate my confusion with fractional frequencies.
# Question:
For any epsilon > 0, Given an Ideal 1+epsilon Hz bandpass filter with linear phase response and Finite Impulse Response, 
What is the maximum amount of data that can be put through two channels for a given Signal to Noise Ratio in voltz squared?
# Standard answer:
According to the shannon-hartley theorem, the answer should be AT MOST log_2(1+ SNR) bits per second, because the bandwidth is 1.
# My current answer:
At least 2SNR bits per second, proof:
We will model the channel as an affine function: ```F(s)+ n = m ```.
```m``` is a vector representing the measured result over time.
```s``` is a vector representing the signal over time.
```n``` is a noise vector representing the noise over time.
```F``` is a matrix capturing the filter, and because of linear phase response, it is nearly symmetric (not symmetric at the corners).
#### Note:
The signal to noise ratio being k means that for any contiguous duration of the transmission,
with more than 2/3 chance, ```sTs/nTn < k``` where those are dot products of column vectors.
I believe this definition roughly but not exactly matches gaussian noise model.
## Construction:
We will send 2SNR bits in a burst of 1 second over both channels.
Let k be the SNR in volts squared. Let the signal have 2-norm ```sqrt(k)```
When the noise vector has 2-norm less than ```1```, the process will have successfully sent 2k bits.
```V``` is the unitary discrete fourier transform of dimension k,
but column ```j``` of ```V^-1``` can also be viewed as the complex sinusoid of frequency ```f = j/(n-1)```
(j ranging from 0 to n-1 inclusive)
(T ranging from ```0/n``` to ```(n-1)/n``` inclusive )
with ```e^(-2pi*T*F)```` being the thing being powered.
We encode our 2k bits as a vector of +/-1+/-i instead of zeros and 1s.
1. V^(-1)d = s #encode signal into frequencies between 0 and 1.
2. signal_0 = s + s* ; signal_1 = i(s - s*) Now we have two real signals
3. Shift signal_i to the appropriate frequency to be going through the filter: message_i
4. m_i = F(message_i)+ n_i
5. Shift m_i back to the frequencies between 0 and 1  r_i
6. Let r = (r_0 - i*r_1)/2
7. Vr = b Decode the signal.
8. If b_i > 0 assume the input at that position was 1 and likewise for less than zero and negative 1 . Similarly for the imaginary units.

When the 2-norm of the noise is less than 1;
the 2-norm of V(n_0 -i*n_1)/2 is less than 1;
therefore the max-norm of V(n_0 -n_1)/2 is less than 1;
therefore, no +1 in the input can be turned into a -1 in the output.
The ideal filter should have no effect because (VFV^-1)^T = V^-TFV^T = V^-TV^T = I .

# Concerns:
The construction uses two channels.
Maybe it could have used 2 seconds?
The construction adds noise after the filter not before.
Are they distinctly different?

# Conclusion:
I have presented a rough argument that ```B*lg(1+SNR)``` can be exceeded.
Could this be tested? Could the argument be refined? Can the argument be refuted?
