# Intro
I'm working on this project to try and understand a contradiction in my understanding of physics and information theory.
I'm hoping to learn something about audio engineering, linear algebra, physics, or information theory through this project.
I'm aware the project is a little absurd. Please feel free to mention errors to me.
## My Intuition
I was able to isolate the following intuition which I think is strange: 
### Waves should be analyzed in 2 dimensions: dampening and frequency.
I have this intuition from the nature of the s-plane in analysis via the laplace transform.
## Definition of Standard Wave
Maybe it should have a better name, but anyway by StandardWave(a,b,f,d) I am referring to a dampened cosine wave of amplitude a, half-life per second b, frequency f, and delay d which has no signal before its start time.
# Assumptions for this contradiction source:
1. Generate a standard wave for a specific integer frequency and integer half-life-per-second as a voltage signal.
2. The Ideal speaker which translates a voltage signal to sound signal can be approximated.
3. Distance can not be heard. (The standard wave does not significantly distort over short distances (<10m) for normal frequencies (<101KHZ) and corresponding dampening rates )
4. Sounds of different frequencies and dampening rates add without causally changing eachother.
5. The Ideal microphone which translates a sound signal into a voltage signal can be approximated.
6. For all frequencies and half-life-per seconds which are integers, there exists a filter which can isolate them.
 NOTE: said filter should not merely remove other signals but be able to let through the intended signal.
7. The Shannon Hartley Theorem implies that less than 50 Megabits per second can be transmitted through the air in a single space under <110db SNR conditions at short distances(<10m).
# Contradiction Generation:
From 60 Hz to 100,059 Hz:
From 60 Hz to 100,059 Hz half life per second:
We will be sending 1 standard wave to send 1 bit over say 2 seconds.
This will send around 10 Gigabits in 2 seconds which will heartily contradict assumption 7.
We setup the 10 billion senders on one side of a hypothetical room and 10 billion recievers on the other side of the room.
Each sender should exist because of assumption 1 and 2.
The data should reach from one side of the room to the other by assumptions 3 and 4.
Each reciever should exist and easily detect its target frequency by assumptions 5 and 6.
It is worth arguing that assumption 7 applies because 10^10 devices emitting a X db noise leads to (X+100) db total noise at most. (assuming noises add in the not log signal domain). Thus, It should be less than 110 db SNR.
