# Simulation Comparison Database — Rayonnements Ionisants

**Metrological traceability for simulations of ionizing radiation transport**

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)

## Overview

The **Simulation Comparison Database (SCDB)** provides a systematic framework for verifying Monte Carlo radiation transport software through rigorous inter-comparisons, modelled after the BIPM Key Comparison Database (KCDB). This SCDB-RI repository pertains to Monte Carlo simulations for ionizing radiation (RI, for *Rayonnement Ionisant*).

Just as the KCDB establishes equivalence between measurement standards maintained by National Metrology Institutes (NMIs), the SCDB establishes equivalence between simulation results produced by different Monte Carlo software, creating a traceable foundation for computational ionizing radiation transport.

## The problem

Monte Carlo simulations are essential for radiation dosimetry, treatment planning, industrial radiation processing, and radiation protection. Yet unlike experimental measurements, simulations lack:

- **Systematic software comparisons** with quantified degrees of equivalence
- **Reference values** calculated from first principles
- **Certified simulation capabilities** analogous to Calibration and Measurement Capabilities (CMCs)
- **Public database** of validated simulation accuracy and efficiency
- **Traceability chain** to verified simulation results

Current practice relies on ad-hoc literature comparisons and uncoordinated validation studies. Each research group validates independently, making results difficult to compare and trust difficult to establish.

## The solution

SCDB implements the KCDB model for simulations:

| **KCDB Concept**                   | **SCDB Implementation**                           |
| ---------------------------------- | ------------------------------------------------- |
| Key Comparison (KC)                | Simulation Comparison (SC)                        |
| Pilot Laboratory                   | Pilot Coordinator                                 |
| Transfer Standard                  | Shared geometry and source specifications         |
| Reference Value (KCRV)             | Simulation reference value (SCRV)                 |
| Degrees of Equivalence             | Quantified deviation from SCRV with uncertainties |
| Certified Measurement Capabilities | Certified Simulation Capabilities                 |
| Participating NMIs                 | Participating MC Software                         |
| Public KCDB Database               | Public github.com Repository                      |
