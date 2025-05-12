# Computational Physics Projects

This repository contains Python implementations of two classic computational physics problems:

1. **Tacoma Bridge Collapse Simulation**
2. **Traveling Salesperson Problem Optimization**

## Overview

This project investigates two distinct optimization problems in computational physics:

- The **Tacoma Bridge collapse** is modeled using coupled differential equations, solved with both Taylor and Cromer numerical methods. The simulation explores how wind forces affect bridge oscillations and identifies the natural frequency that contributed to the bridge's catastrophic failure.

- The **Traveling Salesperson Problem (TSP)** is approached using simulated annealing to find optimal routes between American capital cities. The project demonstrates how this heuristic algorithm can efficiently find near-optimal solutions to an otherwise computationally intractable problem.

## Requirements

- Python 3.x
- NumPy
- Matplotlib
- JSON (for loading city data)

```bash
pip install numpy matplotlib
```

## Tacoma Bridge Simulation

The Tacoma Bridge collapsed in November 1940 due to resonance effects. This section models the oscillations using differential equations:

### Features
- Implementation of McKenna's model for cable tension forces
- Numerical solution using both Taylor and Cromer methods
- Simulation of bridge behavior with and without wind forces
- Determination of the bridge's natural frequency (found to be approximately 0.12Hz)
- Comparison with the historical value (0.2Hz)

### Usage
```python
# Run simulation without wind
times, θ, y = tacoma(dt=0.001, cromer=True, y0=0, θ0=0.01, z0=0, γ0=0)

# Run simulation with wind force
times, θ, y = wind_tacoma(dt=0.001, cromer=True, y0=0, θ0=0.01, z0=0, γ0=0, A=2, ω=0.73)
```

## Traveling Salesperson Problem

The TSP implementation uses simulated annealing to find the shortest route connecting 30 American capital cities.

### Features
- Random path generation for initialization
- Pairwise exchange function for path modification
- Temperature scheduling for controlled cooling
- Simulation of annealing process to find near-optimal paths
- Functions to find both shortest and longest possible paths
- Visualization of paths on a map of the USA

### Usage
```python
# Generate a random path with 8 cities
path = rand_path(8)
show_path(path, path[0])

# Find shortest path using simulated annealing
shortest_path(0.999, 10000, 8000, 20)  # Returns a path with distance of approximately 2194.65
```

## Results

- **Tacoma Bridge**: The simulation determined the natural frequency of the bridge to be 0.12Hz, compared to the historical value of 0.2Hz.
- **Traveling Salesperson**: The shortest path found connecting all capital cities was approximately 2194.65 units.

## Methodology

### Tacoma Bridge
The bridge is modeled using coupled differential equations representing vertical displacement and rotation:

```
d²y/dt² = -d × dy/dt - (K/ma)(e^a(y - lsin(θ)) + e^a(y + lsin(θ)) - 2)
d²θ/dt² = -d × dθ/dt + (3cos(θ)/l)(K/ma)(e^a(y - lsin(θ)) - e^a(y + lsin(θ)))
```

These equations are solved using numerical integration methods.

### TSP
The simulated annealing approach uses:
- Random initial path
- Gradual temperature reduction: T = αᵗ × t₀
- Probability of accepting worse solutions: P = e^(-dₙₑw/T) × e^(dₒₗₐ/T)
- Multiple runs to find global minimum

## Acknowledgments

This project was completed as part of a computational physics course, drawing on established mathematical models and optimization techniques.

## License

This project is available under the MIT License.
