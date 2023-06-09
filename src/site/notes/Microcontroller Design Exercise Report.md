---
{"dg-publish":true,"permalink":"/microcontroller-design-exercise-report/"}
---

Hamish Burke || 07-06-2023
Lab Partner: Seb Collis
***

# Design Exercise Report

1. Describe the behaviour and relative performance of the two convertors you have implemented.  

In order to test the performance of the Staircase ADC, our circuit was connected to a multimeter, with the input voltage being varied. The 'Staircase V' column in the table below represents the voltages read off the LCD display and the 'V' column lists the output voltages of the potentiometer, which were varied to test the Staircase ADC. The following results were obtained:

| V     | Staircase V                   |
| ----- | --------------------------- |
| 4.92  | 252 (goes blank any higher) |
| 4     | 227                         |
| 2     | 177                         |
| 0     | 129                         |
| -2    | 77                          |
| -4    | 28                          |
| -4.92 | 3 (drops to 1 at any lower) |

As the data above illustrates, the voltages that measured over 5V on the multimeter weren't appearing on the LCD display, and similarly for voltages below -5V. Given that the outputted voltages deviate significantly from the voltage on the potentiometer, we opted to modify the code by multiplying the returned value by $0.0196$. We discovered this adjustment brought us closer to the correct voltages. Although it's not an exact match, the modification brought the voltage read by the Staircase ADC much closer to the correct values.

Unfortunately, we were unable to get the Successive Approximation ADC (SAC) to be fully functional, hence we couldn't record any output voltages from it. However, it is important to note that the SAC is inherently faster than the Staircase ADC due to its binary search algorithm. This means it doesn't go through every voltage until the comparator changes state (like the Staircase ADC does), instead it eliminates half of the voltage options at every step. This design allows it to find the correct voltage a lot faster than the Staircase ADC. Therefore, if we were to successfully implement the SAC, it would have been faster than the Staircase ADC, albeit at a slightly higher cost.

<br>

2. Discuss the advantages of using “C” rather than assembler

There are several key advantages to using C over assembly language, primarily due to C being a higher-level language.

Firstly, C is generally considered easier to learn and understand than assembly. It uses a more human-readable syntax with well-defined operators and control structures, which makes the coding process less arduous for the programmer. Writing, reading, and maintaining code in C is typically much simpler and faster than in assembly. This also makes debugging and error handling more straightforward in C.

Secondly, C offers portability across different hardware platforms. While assembly is machine-specific, meaning that a program written in assembly for one type of hardware will likely not work on another, a program written in C can be compiled and run on a variety of different hardware systems with little to no modification. This makes C a more versatile choice for cross-platform development.

Finally, C has a rich set of preexisting libraries and frameworks. Using these libraries can drastically reduce the amount of code that a programmer has to write from scratch, thereby improving the speed of development and iteration. By contrast, assembly language has fewer libraries available, and those that do exist are often much less powerful and flexible than those in C.

# Additional Questions

## 1. Data Acquisition System

### A. I ADC Operation

A data acquisition system starts with a transducer converting a physical variable into an electrical signal. This analogue signal is sampled at regular intervals by a sample-and-hold circuit. Each sample is then converted into a digital value by an analogue-to-digital converter (ADC). The ADC outputs a binary number representing the sampled signal. The resulting digital signal can be processed or stored for later analysis, effectively transforming the original physical variable into a digital format.

### A. II ADC Resolution

The resolution of the ADC is calculated by dividing the total voltage range by the number of possible values the ADC can output. For an 8-bit ADC, there are $2^8 = 256$ possible values. So the resolution is $5V / 256 \approx 0.01953$ volts, or about 19.53 millivolts.

### A. III ADC Conversion Time

The conversion time for a full-scale input signal is the time it takes for the ADC to go through all of its possible output values. For an 8-bit ADC, there are $2^8 = 256$ possible values. If each step takes 2 µs, then the total conversion time is 512 µs. 

### B. I Sample-and-Hold Device

The sample-and-hold (S/H) circuit samples the input analog signal and holds onto its value while the ADC converts this sample to a digital value. This is necessary because the conversion process takes a certain amount of time, and we need to prevent the input signal from changing during this time.

### B. II Highest Frequency Component

The highest frequency that can be accurately sampled is given by the Nyquist-Shannon sampling theorem, which states that it must be less than half of the sampling rate. The sampling rate is the inverse of the sample period. So, to get the highest frequency, we first calculate the sampling rate and then divide it by 2. The calculation is as follows: $(1 / (25 \mu s)) / 2 = 20,000$ Hz or 20 kHz.

## 2. Multi-Channel Data Acquisition

A multiplexer can be added to the data acquisition system to digitise multiple input channels using a single ADC. The multiplexer switches between the input channels, connecting one channel at a time to the ADC.

## 3. ADC Output Code

The output code of an ADC is calculated by dividing the input voltage by the resolution of the ADC, and then rounding to the nearest integer. The resolution of the ADC is the voltage range divided by the number of possible output values. For an 8-bit ADC, there are $2^8 = 256$ possible output values, so the resolution is $10V / 256$. The output code for an input voltage of 3.293V is $\text{round}(3.293V / (10V / 256)) = 84$ in decimal, which corresponds to 1010100. 

## 4. Memory Requirement

A 16 bit ADC system with a sample period of $20 \mu s$ is used to record a song  
that lasts for 5 minutes. Calculate how much memory is required to store the  
song

The memory required to store the song can be calculated by multiplying the number of samples by the size of each sample. The number of samples is the duration of the song divided by the sample period, and the size of each sample is determined by the bit depth of the ADC. 
The calculation is $(5 * 60) / (20 \mu s) * (16 / 8) = 30,000,000$ bytes, which is equivalent to 30 megabytes.

## 5. SRAM Vs DRAM

SRAM (Static Random Access Memory) is a type of semiconductor memory that retains the stored data as long as power is supplied, without the need for refreshing. In contrast, DRAM (Dynamic Random Access Memory) requires constant refreshing of its data. DRAM offers high capacity and low power usage but at a moderate speed. SRAM, on the other hand, has lower capacity and higher power usage, but provides higher speed than DRAM.

## 6. SDR Vs DDR DRAM

SDR (Single Data Rate) and DDR (Double Data Rate) represent two different types of DRAM technology. DDR provides a speed advantage over SDR as it transfers data on both the rising and falling edges of the clock signal, doubling the rate of data transfer compared to SDR, which only transfers data on the rising edge. However, DDR also has higher power consumption due to the increased data transfer rate.




