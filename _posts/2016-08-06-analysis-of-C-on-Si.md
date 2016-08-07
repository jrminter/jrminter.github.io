---
layout: post
title: Analysis of C films on Si.
author: John Minter
published: true
status: publish
draft: false
tags: R Jekyll RStudio DTSA-II
---
 
I frequently need to coat samples for X-ray Energy Dispersive Spectroscopy (EDS) with carbon to obtain a conductive surface so that the specimen does not charge in the scanning electron microscope (SEM).
 
Especially when we run the analysis at low acceleration voltages, the carbon coating can attenuate the emitted X-rays, especially the low energy ones. I need a way to estimate the thickness of the C layer. Our vacuum evaporator does not have a thickness monitor located near the specimen. I decided to write Python scripts to run Monte Carlo simulations using the NIST DTSA-II software.
 
Six of the resulting spectra, after subtraction of the continuum,are shown below.
 
![spectra](/images/cOnSi5kV)
 
The script also computed the peak integrals, outputting the integral and an estimate of the uncertainty to a `.csv` file. I then used R to analyze the data (computed at 5 nm increments, even though the plots are at 20 nm increments). I computed a smooth curve using the `LOESS` algorithm. The predicted values may be used as a lookup table.
 
![calibration curve](/images/c-ctd-si-series-plt.png)
 
All the code in my [dtsa2Scripts](https://github.com/jrminter/dtsa2Scripts/tree/master/estThickC) repository.
 
 
 
