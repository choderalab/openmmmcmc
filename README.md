[![Build Status](https://travis-ci.org/choderalab/openmmmcmc.svg?branch=master)](https://travis-ci.org/choderalab/openmmmcmc)

# OpenMM MCMC
A general Markov chain Monte Carlo framework for OpenMM.

*WARNING: This is a work in progress. These functionalities will be moved shortly to the more comprehensive package [OpenMMTools](https://github.com/choderalab/openmmtools).*

## Installation
From source
```
python setup.py install
```
With conda
```
conda install -c omnia openmmmcmc-dev
```

## States
Classes to cache a maintain a consistent state of the simulation.
- `ThermodynamicState`: Represent and manipulate the thermodynamic state of OpenMM `System`s and `Context`s.
- `SamplerState`: Represent and cache the state of the simulation that changes when the `System` is integrated.
- `CompoundThermodynamicState`: Extend the `ThermodynamicState` to handle parameters other than temperature and pressure through the implementations of the `IComposableState` abstract class.

## Monte Carlo moves
An implementation of an `MCMCMove` encodes how to propagate an OpenMM `System` to generate a new sample. Different `MCMCMove`s can be combined for more advanced schemes.
- `LangevinDynamicsMove`: Langevin dynamics segment as a (pseudo) Monte Carlo move.
- `HMCMove`: Assigns velocities from the Maxwell-Boltzmann distribution and propagate through velocity Verlet steps.
- `GHMCMove`: Generalized hybrid Monte Carlo Markov chain Monte Carlo.
- `MonteCarloBarostatMove`: Attempts to update the box volume using Monte Carlo updates.
