# Adaptive-Filtering
FPGA accelerated adaptive filtering (LMS filter design). 

---
## Project Context:
I've recently been introduced to the concepts regarding digital filter design, specifically in the world of Python. As reference, my DSP lab course had us consider some practical design trade-offs in creating effective filters for noisy signals (e.g. audio or image). Beyond traditional windowing, Hamming/Hanning, straightfoward high/low/band pass/stop filters, generalized linear phase, and many other mathematical concepts important to filter design, the laboratory assignment introduced the fundamental ideas behind adaptive filter and LMS filtering. "How can we learn the optimal filter 'on-the-fly'?". 

In conjunction with my exploration of hardware design basics and a (very) brief reading on simulated annealing, I've been thinking about utilizing my Fall break to create a rudimentary project that can combine all such concepts together. In fact, they mesh well nicely!

There are two sections of the project;
    - Offline: generate a price signal corrupted by some sort of noise, run simulated annealing to obtain a starting set of weights.
    - Online: stream noisy price samples into the board, run real-time LMS adaptation in hardware using the simulated annealing initial weights, and stream the filtered output back.

I hope to develop skills and knowledge in adaptive digital signal processing and SystemVerilog.

---

## Project Goals:
This project aims to build an adaptive signal processing pipeline on the Urbana FPGA board (Xilinx Spartan-7 xc7s50csga324-1) to recover a latent price signal from noisy financial observations using a Least Mean Squares adaptive filter implemented in synthesized hardware. 

Importantly, prior to any LMS adaptation, simulated annealing will find near-optimal initial weights (instead of zero initialization of our filter coefficients) and in real-time, the board will run the LMS adaptation loop on every new incoming sample (perhaps price data). Without the usage of simulated annealing, our LMS would struggling to settle on target weights before updating them in real-time. 
