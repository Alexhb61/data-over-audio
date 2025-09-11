# Introduction:

# Core question:
Why are fractional frequencies, complex frequencies and sampling rate not accounted for in the shannon-hartley theorem?
Do they not effect things? If so, why?

# Answer - Fractional Frequencies:
Given a signal f(t),
When we sample it evenly n times per second, 
we are multiplying it with the dirac comb of period 1/n
(this seems to be part of the standard understanding).
When we then analyze a limited duration of the signal,
we are multiplying it with the rectangle function of duration D
(this seems to be part of the standard understanding).
When we go to apply the discrete fourier transform to it (and treat it as looped time),
we are then convolving it with the dirac comb of period D
(this is my novel interpretation).
So our analyzed signal is ```(f . comb_1/n . rect_D ) * comb_D```
The ```comb_1/n``` causes aliasing by being a convolution in the frequency domain.
Whereas the ```comb_D``` causes discretization by being a multiplication in the frequency domain.
This discretization shows up in small packet analysis, 
but does not show up in channel analysis like the shannon-hartley theorem
because we want to analyze the channel's bit rate as the duration tends towards infinity.
This makes a sort of sense that when we send more and more bits down a channel,
all the seconds having different data causes more and more fractional frequencies to show up.
