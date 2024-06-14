# Newtonian dynamics of a Lennard-Jones Fluid

A Lennard-Jones fluid is a system of particles interacting via the Lennard-Jones interaction, for which the potential energy between a pair of particles has the form

\[ u_{ij}(r_{ij}) = 4\epsilon \left[ \left( \frac{\sigma}{r_{ij}} \right)^{12} - \left( \frac{\sigma}{r_{ij}} \right)^{6} \right] \]

where $\epsilon$ is an energy scale (minimum value of the potential energy) and $\sigma$ is a length scale (equilibrium separation is $2^{1/6}\sigma$). Given this pair-potential energy function, the force exerted by the $i$th particle on the $j$th particle is

\[ \mathbf{F}_{i \rightarrow j} = \frac{48\epsilon}{r_{ij}^2} \left[ \left( \frac{\sigma}{r_{ij}} \right)^{12} - \frac{1}{2} \left( \frac{\sigma}{r_{ij}} \right)^{6} \right] \mathbf{r}_{ij} \]

where $\mathbf{r}_{ij} = \mathbf{r}_j - \mathbf{r}_i$. Clearly, this force is attractive for $r_{ij} > 2^{1/6}\sigma$ and repulsive for $r_{ij} < 2^{1/6}\sigma$. There are natural length ($\sigma$), energy ($\epsilon$), and mass ($m$) scales in this system. Therefore, it is natural to measure all lengths, energies, and masses in units of these scales. These natural scales further induce natural velocity and time scales

\[ v_0 = \sqrt{\frac{\epsilon}{m}}, \quad t_0 = \frac{\sigma}{v_0} = \sigma \sqrt{\frac{m}{\epsilon}} \]

The equation of motion for the $i$th particle is

\[ m \frac{d^2 \mathbf{r}_i}{dt^2} = \sum_{j \neq i} \mathbf{F}_{j \rightarrow i} = \sum_{j \neq i} \frac{48\epsilon}{r_{ij}^2} \left[ \left( \frac{\sigma}{r_{ij}} \right)^{12} - \frac{1}{2} \left( \frac{\sigma}{r_{ij}} \right)^{6} \right] \mathbf{r}_{ji} \]

Introduce dimensionless position and time variables

\[ \tilde{\mathbf{r}}_i = \frac{\mathbf{r}_i}{\sigma}, \quad \tau = \frac{t}{t_0} \]

In terms of these dimensionless variables, the equations reduce to

\[ \frac{d^2 \tilde{\mathbf{r}}_i}{d\tau^2} = \sum_{j \neq i} \frac{48}{\tilde{r}_{ij}^2} \left[ \left( \frac{1}{\tilde{r}_{ij}} \right)^{12} - \frac{1}{2} \left( \frac{1}{\tilde{r}_{ij}} \right)^{6} \right] \tilde{\mathbf{r}}_{ji} \]

The dimensionless pair potential energy function (pair potential energy measured in units of $\epsilon$) reduces to

\[ \tilde{u}_{ij}(\tilde{r}_{ij}) = 4 \left[ \left( \frac{1}{\tilde{r}_{ij}} \right)^{12} - \left( \frac{1}{\tilde{r}_{ij}} \right)^{6} \right] \]

We anticipate that in thermal equilibrium, the mean kinetic energy per particle of this system of particles is

\[ \bar{k} = \frac{1}{N} \bar{K} = k_B T \]

where

\[ K = \sum_{i=1}^N \frac{1}{2} mv_i^2 \]

and $v_i$ is the speed of the $i$th particle. Defining dimensionless velocities $\tilde{\mathbf{u}}_i$ as

\[ \tilde{\mathbf{u}}_i = \frac{\mathbf{v}_i}{v_0} \]

it follows

\[ \bar{k} = \frac{1}{N} \sum_{i=1}^N \frac{1}{2} mv_0^2 \tilde{u}_i^2 = \epsilon \tilde{k} \]

where

\[ \tilde{k} = \frac{1}{N} \sum_{i=1}^N \frac{1}{2} \tilde{u}_i^2 \]

is dimensionless mean kinetic energy (mean kinetic energy measured in units of natural energy scale $\epsilon$). This system has a natural temperature scale

\[ T_0 = \frac{\epsilon}{k_B} \]

It is natural to measure temperature in units of $T_0$. Then, we define a dimensionless temperature

\[ \tilde{T} = \frac{T}{T_0} \]

Then, it follows from (8) that

\[ \tilde{k} = \frac{\bar{k}}{\epsilon} = \frac{k_B T}{\epsilon} = \frac{T}{T_0} = \tilde{T} \]

We consider a two-dimensional system of $N$ particles interacting via this interaction. This computational exercise simulates the dynamics of this system using Newton’s Laws, which are implemented through the Verlet Algorithm. The Verlet algorithm evolves the (dimensionless) position and velocity of every particle according to

\[ 
\tilde{\mathbf{r}}_i(t+ \Delta t/2) = \tilde{\mathbf{r}}_i(t) + \frac{\Delta t}{2} \tilde{\mathbf{v}}_i(t) 
\]
\[ 
\tilde{\mathbf{v}}_i(t+ \Delta t) = \tilde{\mathbf{v}}_i(t) + \Delta t \tilde{\mathbf{a}}_i(t+ \Delta t/2) 
\]
\[ 
\tilde{\mathbf{r}}_i(t+ \Delta t) = \tilde{\mathbf{r}}_i(t+ \Delta t/2) + \frac{\Delta t}{2} \tilde{\mathbf{v}}_i(t+ \Delta t) 
\]

where $\tilde{\mathbf{a}}_i$ is the dimensionless acceleration of the $i$th particle, given by

\[ 
\tilde{\mathbf{a}}_i = \sum_{j \neq i} \frac{48}{\tilde{r}_{ij}^2} \left[ \left( \frac{1}{\tilde{r}_{ij}} \right)^{12} - \frac{1}{2} \left( \frac{1}{\tilde{r}_{ij}} \right)^{6} \right] \tilde{\mathbf{r}}_{ji} 
\]

This computational exercise involves giving initial positions and velocities to the system of particles, evolving it till equilibrium is attained, and then measuring the speed distribution of particles. Since the kinetic energy, and not the total energy is a measure of the temperature of the system (in equilibrium), it is not possible to predict what temperature the system will equilibrate to, since the kinetic energy will change with time. Then, as the state of the system evolves with time, its mean kinetic energy is to be monitored, till it reaches a steady value, apart from fluctuations about this mean value. Given this temperature, we will measure the speed distribution of the particles. Statistical mechanics predicts that this speed distribution is Maxwellian, even for an interacting system. For this two-dimensional system, the Maxwell speed distribution is given by

\[ 
P(v) dv = \frac{m}{k_B T} v e^{-\frac{mv^2}{2k_B T}} dv 
\]

where $P(v) dv$ is the probability that the speed of a particle lies between $v$ and $v + dv$. Expressing this in terms of dimensionless speed $\tilde{u} = \frac{v}{v_0}$, we get

\[ 
P(\tilde{u}) d\tilde{u} = \frac{1}{\tilde{T}} \tilde{u} e^{-\frac{\tilde{u}^2}{2\tilde{T}}} d\tilde{u} 
\]

where $\tilde{T}$ is the dimensionless temperature. Once the equilibrium is established and the equilibrium temperature $\tilde{T}$ computed, we check if the system satisfies the speed distribution given by (19).

## Computational Procedure

- Start the system with the positions of particles placed in a regular pattern in a two-dimensional box of length $L$ (measured in units of natural length scale $\sigma$). Generate the velocities using a normal (Gaussian) distribution with zero mean and unit standard deviation. What is the significance of this initial velocity distribution?

- When evolving the system through the Verlet algorithm, the acceleration of every particle needs to be computed. This will be a vector sum of contributions due to forces exerted by all the other particles. In principle, all particles will exert forces on each other. However, since the interaction between particles falls rapidly beyond length scale $\sigma$, it is useful to put a `cut-off` beyond a certain distance $r_c$. This cut-off can be a few times $\sigma$. Then, to determine the acceleration of any particle, loop over all the other particles. If the distance between a given pair is less than $r_c$, take account the effect of that particle on the acceleration. Else, ignore the contribution.

- In addition to inter-particle interaction, we need to consider the interaction of each particle with the walls of the enclosing area. As before, we could make a particle elastically `bounce off` the walls. However, it is useful to avoid walls altogether, since they introduce additional, entropic interactions, whereas in this exercise we are interested in the effect of interactions between particles on their aggregate, macroscopic behavior. So, we get rid of the walls altogether. First, we put the particles in a square box of side $L$. Next, we turn the square (which has boundaries) into a torus (which does not). This is achieved by first `rolling` the square into a cylinder, and then joining the opposite ends of the cylinder to form a torus. Mathematically, this is the same as `identifying` the opposite edges of the square. That is, if we set up a coordinate system $(x, y)$ at one corner, the edge $x = L$ is identified as $x = 0$ (rolling into a cylinder) and the edge $y = L$ identified as $y = 0$ (joining the opposite circular faces of the cylinder). The way this is enforced on the particles is as follows: given coordinates $(x, y)$ of a particle, if say $x$ is such that $x > L$, force it to become $x \rightarrow x - L$. If, on the other hand $x < 0$, force it to become $x \rightarrow x + L$. Same for coordinate $y$. This is sometimes referred to as imposing `periodic boundary conditions`, though visualizing on a torus is more useful. The particles will then move around and interact on a torus which does not have boundaries.

- The distance between a pair of particles is affected after imposing periodic boundary conditions. For instance, consider two particles with coordinates $(L/10, y)$ and $(9L/10, y)$ for any $y$ within the box. Naively, one will compute the distance between them to be $8L/10$. But, given they are on a torus, the correct distance is $2L/10$ (why?). The separation between the particles is thus non-trivial in this topology. To evaluate the correct separation (used to determine accelerations), implement the following: say, the displacement between two particles is evaluated to be $\mathbf{r} = x\hat{i} + y\hat{j}$. Then, if $|x| > 0.5L$, then implement $x \rightarrow x - L \times \text{sgn}(x)$ where $\text{sgn}(x) = 1$ if $x > 0$ and $-1$ if $x < 0$ (`sign` function). Same for $y$. Try to understand the significance of this transformation. This is to be implemented when the accelerations are being evaluated.

- Generating the velocities according to a Gaussian distribution with zero mean does not guarantee that the total momentum of the system is precisely zero (because of the finite sample size). To ensure it is, calculate the total momentum of the particles after the velocity initialization, calculate the center of mass velocity and subtract it from the velocity of each particle so that the total momentum is forced to be zero (if it is not, the particles will experience a net drift since there are no walls to `kill` the momentum).

- To check for accuracy, monitor the conservation of the total energy of the system. This will involve computing the potential energy of the system at every step. The total (dimensionless) potential energy of the system is

\[ \tilde{U} = \sum_{i=1}^N \sum_{j>i} \tilde{u}_{ij}(\tilde{r}_{ij}) \]

Computing this will also involve calculating the distances between particles. As before, only distances less than $r_c$ are to be considered. However, to avoid generating singular forces arising due to abruptly `chopping off` the potential energy for any pair beyond $r_c$, a new pair potential energy function is introduced

\[ \tilde{u}_c(\tilde{r}_{ij}) = \tilde{u}_{ij}(\tilde{r}_{ij}) - \tilde{u}_{ij}(\tilde{r}_c) \]

which involves subtracting the contribution at $r = r_c$. This will make the potential energy function continuous at $r = r_c$, avoiding singular forces.

- Plot the mean kinetic energy per particle as a function of time and observe the time after it becomes steady (apart from fluctuations). To measure this steady temperature, calculate the mean kinetic energy at every time step (or every few time steps) after this equilibration time has been reached and calculate the average of these values.

- After equilibration time, gather data at every time step (or every few time steps) of the speeds of the particles. Plot a histogram of this data and check if it agrees with (19) where $\tilde{T}$ is the equilibrium temperature (measured above).
