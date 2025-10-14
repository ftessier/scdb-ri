# sc-ri-0001: Energy conservation in infinite media <!-- omit in toc -->

## Table of contents <!-- omit in toc -->

- [1. Overview](#1-overview)
  - [1.1. Purpose](#11-purpose)
  - [1.2. Scope](#12-scope)
  - [1.3. Expectation](#13-expectation)
- [2. Specification](#2-specification)
  - [2.1. Particles](#21-particles)
  - [2.2. Materials](#22-materials)
  - [2.3. Energies](#23-energies)
  - [2.4. Geometry](#24-geometry)
  - [2.5. Source](#25-source)
  - [2.6. Physics](#26-physics)
  - [2.7. Measurand](#27-measurand)
  - [2.8. Method](#28-method)
  - [2.9. Report](#29-report)

## 1. Overview

### 1.1. Purpose

Verify that Monte Carlo simulation correctly conserve energy during particle transport.

### 1.2. Scope

Verify energy conservation for monoenergetic electrons and photons (1 keV to 20 MeV) in infinite homogeneous media. Test matrix includes 13 materials: 12 representative elements spanning, plus air and liquid water. Each software simulates 72 cases (2 particles × 9 materials × 4 energies) with the expected result that total deposited energy equals initial particle energy within floating-point precision. This benchmark tests internal algorithm consistency and floating point precision, rather than agreement with experimental data.

### 1.3. Expectation

The total energy deposited per history is equal to the initial particle energy, within floating-point precision.

## 2. Specification

### 2.1. Particles

- Monoenergetic electrons
- Monoenergetic photons

### 2.2. Materials

- **Elements:** Z = 1, 6, 13, 27, 47, 74, 82 (representative sample of pure elements)
- **Compounds:** Air, Water
- **State:** Natural state at room temperature (gas, liquid, solid)

### 2.3. Energies

- **Kinetic energies:** 10 keV, 100 keV, 1 MeV, 10 MeV

### 2.4. Geometry

- Infinite homogeneous medium (no boundaries)

- Particle starts at origin

- If the software cannot model an infinite medium space, the following should be used:

  - Sphere of radius 100 × CSDA range of particle, centred on the origin
  - Document actual sphere radius used for each case
  - Verification: < 0.001% of particles reach the sphere radius

### 2.5. Source

- Position: (0, 0, 0)
- Direction: Isotropic (4π)
- Energy: Monoenergetic
- Particle type: Electron or Photon

### 2.6. Physics

- Default or documented transport parameters and physical cross sections
- Default production thresholds and transport cutoffs
- No variance reduction techniques

### 2.7. Measurand

- Energy deposited in medium, per history (keV)

### 2.8. Method

For each test case:

- Run 1e9 independent incident particles (histories)
- Track until all particles are absorbed (or escape)
- Sum all energy deposition events in history
- Compute the difference between deposited energy and source energy
- Track the maximum difference between incident and deposited energy

### 2.9. Report

#### Input

- Simulation input files for all cases (or a script to generate them from a template)
- Instructions to reproduce the simulations from a fresh installation of the software

#### Results

- For each case, report the maximum difference between incident and deposited energy, normalized to the incident energy.
- No uncertainty is recorded since results should be exact within floating-point precision.
- Provide the results as a .csv file according to the following template:

  ```csv
  software,material,keV,maximum
  EGSnrc,H2O,10,1.34e-15
  ```
