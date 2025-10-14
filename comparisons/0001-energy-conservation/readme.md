# SC-0001: Energy conservation in infinite media <!-- omit in toc -->

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
  - [2.7. Scoring](#27-scoring)
  - [2.8. Report](#28-report)

## 1. Overview

### 1.1. Purpose

Verify that Monte Carlo simulation correctly conserve energy during particle transport.

### 1.2. Scope

Verify energy conservation for monoenergetic electrons and photons (1 keV to 20 MeV) in infinite homogeneous media. Test matrix includes 13 materials: 12 representative elements spanning Z = 1 to 92 plus liquid water. Each software simulates 312 cases (2 particles × 12 materials × 13 energies) with the expected result that total deposited energy equals initial particle energy within floating-point precision. This benchmark tests internal algorithm consistency rather than agreement with experimental data.

### 1.3. Expectation

The total energy deposited per history is equal to the initial particle energy, within floating-point precision.

## 2. Specification

### 2.1. Particles

- Monoenergetic electrons
- Monoenergetic photons

### 2.2. Materials

- **Elements:** Z = 1, 6, 7, 8, 13, 26, 29, 47, 74, 82, 92 (representative sample of pure elements)
- **Compounds:** Water
- **State:** Natural state at room temperature (gas, liquid, solid)

### 2.3. Energies

- **Kinetic energies:** 2 keV, 5 keV, 10 keV, 20 keV, 50 keV, 100 keV, 200 keV, 500 keV, 1 MeV, 2 MeV, 5 MeV, 10 MeV, 20 MeV, 50 MeV

### 2.4. Geometry

- Infinite homogeneous medium (no boundaries)

- Particle starts at origin

- If the software cannot model an infinite medium space, the following should be used:

  - Sphere of radius 100 × CSDA range of particle, centred on the origin
  - Document actual sphere radius used for each case
  - Verification: < 0.001% of particles reach the sphere radius

### 2.5. Source

#### Type

- Isotropic point source at origin

#### Initial conditions

- Position: (0, 0, 0)
- Direction: Isotropic (4π)
- Energy: Monoenergetic
- Particle type: Single species per simulation

### 2.6. Physics

#### Transport

- Default or documented transport parameters and physical cross sections
- Default production thresholds and transport cutoffs
- No variance reduction techniques

### 2.7. Scoring

#### Measurand

- Total energy deposited in medium (keV)

#### Method

For each case:

- Run 1e9 independent incident particles
- Track until all particles are absorbed (or escape)
- Sum all energy deposition events, compute difference with incident energy
- Compute the root-mean-square difference between incident and deposited energy

### 2.8. Report

#### Input files

- Provide simulation input files for all cases
- Instructions to reproduce the simulations from a fresh installation of the software

#### Simulation results

- For each case, report the root-mean-square difference between incident and deposited energy
- No uncertainty is required since results should be exact within floating-point precision
- Provide the results as a .csv file according to the following template:

  ```csv
  software,material,keV,rms
  EGSnrc,H2O,10,1.34e-15
  ```
