# Simple SISO OFDM over USRP

[![License: IEEE](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg)](http://creativecommons.org/licenses/by-nc-sa/4.0/)

This repository is going to run SISO OFDM with BPSK demodulation on USRP board by using the example code on [WARPLab](https://warpproject.org/trac/wiki/WARPLab/Examples/OFDM) `wl_example_siso_ofdm_txrx.m​`.
* The offical document of [USRP](https://www.ettus.com/content/files/07495_Ettus_N)
*Notice that this repository is NCTU CS course lab of "Wireless Communication Systems 2018". If you are taking this course, please do not duplicate from this repository. All rights reserved.*

## Introduction

The sample code `wl_example_siso_ofdm_txrx.m​` follows the following steps.
1. Generate OFDM transmit samples
2. Send samples via WARP or Simulation transmission
3. Decode the received samples
4. Calculate SNR / channels and plot

In the part of signal generation,
1. Generate preambles
2. Generate digital bits
3. Modulate digital bits to frequency-domain samples
4. Add pilot samples
5. Convert frequency sample to time samples via FFT
6. Insert CP (Cyclic Prefix)
7. Reshape symbols to 1D samples

In the part of decoding,
1. Packet detection
2. CFO correction (useless in simulation)
3. Channel estimation
4. Remove CP
5. Convert time samples to frequency samples via FFT
6. Decode frequency samples
7. SFO correction

* Notice: The most of works can follow by my another repository - [Simple_SISO_OFDM](https://github.com/yungshenglu/Simple_SISO_OFDM).
* USRP Driver (API)
    * About UHD
        * USRP Hardware Driver
        * C++ API
        * http://files.ettus.com/manual
        * https://github.com/EttusResearch/uhd
    * Locating devices
        * `host/build/utils/uhd_find_devices --args "addr=192.168.10.14"`
        * This program scans the network for supported devices and prints out a list of discovered devices and their IP addresses

---
## Environment

![](https://i.imgur.com/m7psyDI.png)

* How to Add a New File & Compile
    * File (Source) Directory
        * Use built in Makefile
        * Put your files in `~/uhd/host/examples/`
        * Add your filenames to the CmakeList.txt in `~/uhd/host/examples`
    * Compile (Binary) Directory
        * `cd ~/uhd/host/build/examples`
        * `make`
        * The executable bin file should be in this folder after compile
* USRP Server
    * `mkdir wcs_trace`
    * Transimitter: `./single_tx --f=2.49 --i=128`
    * Receiver: `./single_rx --f=2.49 --i=128`
    * Received data in `./wcs_trace/rx_signals.bin`

---
## BPSK OFDM over USRP

* Tx repetitively sends 50 symbols
* `USE_WARPLAB_TXRX = 0` to see the simulation result
* Set `MOD_ORDER = 2` to use BPSK modulation
* Rx receives at least one batch of 50 symbols
* Matlab offline decoding

---
## TODO

(Update soon.)

---
## Contributor

* [Yung-Sheng Lu](https://github.com/yungshenglu)

---
> Notice that this repository is NCTU CS course lab of "Wireless Communication Systems 2018". If you are taking this course, please do not duplicate from this repository. All rights reserved.

[![License: IEEE](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg)](http://creativecommons.org/licenses/by-nc-sa/4.0/)