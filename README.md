### Goal:

This project is a simulation of a Lennard-Jones fluid, a system where particles interact via the Lennard-Jones potential. The main objective is to study the dynamics of this system using Newton's laws of motion and verify that the speed distribution of particles in thermal equilibrium conforms to the Maxwell-Boltzmann distribution.

### Implementation:
  #### Simulation Setup:

    Initialization: Particles are initially placed in a regular pattern within a two-dimensional box. Velocities are assigned using a Gaussian distribution with zero mean.
    
    Periodic Boundary Conditions: To avoid boundary effects, the box is treated as a torus by identifying opposite edges, allowing particles to move continuously without encountering walls.
    
    Verlet Algorithm: The Verlet algorithm is used to evolve the positions and velocities of particles over time. This algorithm ensures accurate computation of particle trajectories by considering forces exerted by other particles.
  
    Force Calculation: Forces between particles are computed using the Lennard-Jones potential, which includes both attractive and repulsive components. A cut-off distance is implemented to limit the range of interactions, enhancing computational efficiency.
    
    Equilibration and Measurement: The system is evolved until it reaches thermal equilibrium. The mean kinetic energy per particle is monitored to determine the equilibrium temperature. The speed distribution of particles is measured once equilibrium is established and compared with the theoretical Maxwell-Boltzmann distribution.


### Conclusions:

The simulation successfully demonstrates that the speed distribution of particles in a Lennard-Jones fluid, even with interactions, conforms to the Maxwell-Boltzmann distribution as predicted by statistical mechanics.
The implementation of periodic boundary conditions and the Verlet algorithm are effective in simulating the dynamics of the system accurately.
The study confirms the theoretical expectations about the behavior of a Lennard-Jones fluid, providing insights into the equilibrium properties of interacting particle systems.
