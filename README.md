# FPGA Speech Recognition

Slides from my graduation project at Istanbul Technical University, Electronics and Communication Engineering: an end-to-end speech recognition pipeline designed for FPGA implementation. Advisor: Dr. Ibraheem Shayea.

## Pipeline

Audio acquisition takes 44.1 kHz, 16-bit mono input from a BRAM buffer. Preprocessing applies pre-emphasis (alpha 0.95), framing (512 samples, step 160) and a Hamming window. Feature extraction computes the FFT, per-frame energy, a mel filter bank, and a 14-value MFCC vector per frame (DCT, liftering, log energy, delta and delta-delta). The decoder is a three-layer neural network trained in Python on four Google Speech Commands words (yes, no, up, down), using 63 frames of 14 features per one-second clip, with the trained weights exported as header files and decoder logic in Verilog.

## Status

Functional verification was done in simulation. The presentation PDF in this repository walks through each stage and its simulation results. The design was not deployed as a complete system on hardware.
