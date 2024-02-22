# ISSCC Circuit Insights, Feb 17th, 2024

***Written by Morris Fan***

## Fundamentals of Digital Circuit Design

*Prof. Jan M. Rabaey, University of California, Berkeley USA*

**Compute, Communicate, Acquire/Act**

In digital design and computing, we focused on complexity at low cost.

From the lower level to the top: Boolean (0 and 1), logic gate control, processor, and memories to software.

We use VOLTAGE representation for signals (current, flux can also but no). Voltage signals are not ideal since it is affected by the environment, couple, and noises. We define threshold range.

**Regeneration:** no accumulation of noise in complex circuits. 

- In contrast to analog circuits. Which allows you to stack up circuits.

In the digital world, we view transistors as switches. However, it is not ideal and determines speed (performance) and energy consumption, caused by parasitic caps and resistance (Cs, Cd, Ron, Roff).

Charge and discharge caps, delay

**Energy and power:**

- Switching (dynamic consumption) = $\text{C}_{2} * V^2 * f$

- Static consumption = $\frac{V^2}{{R}_{off}}$

**Modularity and hierarchy:**

- Combine Easy composability to get a modular design approach.
- Delay = D1+D2
- Hierarchy to handling complexity
- F = (F1, F2) functions

**Timing and Sequential Circuits:**

- Asynchronous design is not ideal

- The absolute, time reference, clock synchronizes Clk to ensure function completion and order execution steps to achieve that once the signal passes clk, the signal is stable. Clk can’t be too fast, **o.w. Clk edges subject to delay (skew) and noise (jitter)**

- Provide timing margins to offset worst-case scenarios

- Optimize clk distribution network

**Verification:**
- Functionality
- Signal noise margins
- Timing margins
- Optimize and repetition

**Jitter impact:** 2 wires too close to each other (coupling caps btw the wires), bad clk, minimize the variance, solve by adding buffers.

> Q: Asynchronous clk is not useful since it didn’t have great EDA, is it worth developed?
R: Only triggered when the signal is changing, so the time variance is large, and we are doing worst case circuits, so it’s hard to design timing margin.

- SPICE doesn’t scale in billions of transistors. 

**Design methodology:**
- Verification and design automation (freedom from component choice)
- To make a reliable circuit, **Always Stick to the design rules**.

Design productivity: transistor-level => gate level => register transfer level (RTL) => reuse => AI design tools? => AI designing computers? **(What’s the rule and the role of the designer?)**

**Verilog:**
- Structure: HOW
- Behavior: WHAT

**Reuse the block**
Raising the bar, start using Python, java, tensor flow => the generator (ex. RISC-V)

As we are approaching the physical limitation. The ingenuity of humans and the ingenuity of nature, are there any natural models (different aspects)?

> Q: Why don’t we redesign the gate levels to increase the performance? Since you also need to redesign the verifications. choose the now that WINS. Will AI do the verification faster? 
R: Cost time and efforts.

> Q: Any other physical materials other than silicon to push regeneration. Quantum? Neural?
R: Sometimes you are not able to consider worst case scenario, like Gaussian distribution? Put circuits for detection, error correction to assist design.

> Q: Ideas on Moore’s law? 
R: Increase density, CFet (PMOS over NMOS).


## CMOS Circuit for Biomedical Applications

*Prof. Carolina Mora Lopez, IMEC, Leuven, Belgium*

**The complexity of the human brain v.s. technology.**
Aiming to manage disease, ease pain……

How can we interface with technology?

- Sense: getting information from bio-electric signals
- Actuate: Drive a certain organ

**Problem 1: Electrical noise**

- Thermal noise
    - a.k.a. white noise (noise for static resistance generated by the random thermal motion of charge carriers)
    - $V_n(RMS) = \sqrt{4KTRB}$

- Flicker noise
    - a.k.a. white noise (1/f noise) in transistors is caused by imperfections in the crystalline structure of semiconductors

- Noise spectrum
    - avg noise power at each frequency

- Corner frequency
    - where two noises coincide
    - Biopotential signals are low-frequency signals
    - Must minimize Both noises

- Design Trade-offs
    - area v.s. noise and power v.s. noise

#### Interface with Biology

- Cell, electro-chemical reactions

- Electrode is the electrical interface between tissue and electronics.

**Problem 2: electrode DC offset (EDO)**
how you design your amplifier
Half-cell potential, might be positive or negative depends on material

Electrode impedance magnitude decreases as frequency gets higher.
Small VEDO = low Zin @DC, for AC is not that straight forward

Vin = vbio + VEDO, EDO should not be amplifier.

How to remove EDO? High pass filter, reject fc < 1Hz

Make zin > 10*Zele to reduce noise.

How to achieve high input impedance? 

Spec of bio-amp:
Low noise
Can reject EDO
High input impedance

Application spec requirement:
Small area
Low power
Good linearity
Low input leakage (BJT have input current which is deserted)

Complete biopotential readout
Recording electrode => low-noise amp (the one wants to optimized) + =>filter => programmable gain amplifier => ADC (determine signal quality, how many bits/levels required)(but not over designing, expensive, enough is enough, more bits => more power needs to compute)
Reference electrode => amp - => 

Pseudo-resistors
Diode-connected MOS biased in cut-off
The equivalent resistance values > 100G ohms
Small area, but non-linear

Differential amplifier:
Upper PMOS (Mpi) dominate the noise
To achieve low-noise, large gm in Mpi and small gm in Mnb (lower MOS in the right bottom)

Multi channel readout can enable high-density sensing

Neural readout ASIC: study brain behavior (SoC)

Summary:
Biopotential are small (uV-mV) and low-frequency (<10kHz) signals

===QA===
Neural link claimed they have implanted a ‘brain-reading’ device into a person. allowing a person with severe paralysis to control a computer, robotic arm, wheelchair or other device through thought alone. What do you think of the future of putting chips to normal human beings or it should stick with medical usage.

Yes, it might happened, this is not the first approach people claims to put chips into human brains. it is high risks procedures, some day it might be in customer electric such as gaming and daily lives.

Power supplies, when to charge the device and how often should you charge the device. Noise cancellation to decrease power consumption



## The Basic of Ratio Frequency (RF) Circuits
*Prof. Hossein Hashemi, University of Southern California, USA*



## The Basic of Silicon-Photonic Circuits
*Prof. Sudip Shehkar, University of British Columbia, Canada*