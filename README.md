# Using Particle Swarm Optimizer to Optimize a Non-convex Function

## Introduction

This project focuses on implementing the Particle Swarm Optimization (PSO) algorithm to optimize a non-convex function. PSO, a bio-inspired optimization algorithm, mimics the social behavior observed in animal swarms such as fish and flies. This methodology is effective in finding the global minimum of complex optimization problems where the solution space is vast and filled with multiple local minima.

### Project Description

Particle Swarm Optimizer is an innovative approach that utilizes multiple agents, initially scattered randomly across the solution space, which gradually converge around the optimal solution. The essence of PSO lies in its ability to guide these agents towards the most promising areas of the solution space based on a combination of their individual knowledge and the swarm's collective experience.

The strength of PSO, especially in the context of a non-convex function, is its robustness against the pitfalls of local optimization algorithms like gradient descent, which may struggle due to dependency on the starting point. Non-convex functions, characterized by multiple local minima, present a challenging landscape for optimization, making PSO a suitable choice for such scenarios.

In this project, we implement PSO in Python, leveraging libraries such as `numpy` for numerical operations and `matplotlib` for visualizations. The algorithm is designed to iteratively improve a candidate solution with respect to a given measure of quality, utilizing swarm intelligence principles.

The mathematical foundation of PSO is based on updating the velocity and position of each particle in the swarm. The key formulas used in this algorithm are:

$$v_{i+1} = w \cdot v_i + c_1 \cdot rand() \cdot (pbest_i - x_i) + c_2 \cdot rand() \cdot (gbest - x_i)$$

$$x_{i+1} = x_i + v_{i+1}$$

Where:
- $v$ represents the particle velocity.
- $w$ is the inertia weight, balancing exploration and exploitation.
- $c_1$ and $c_2$ are cognitive and social scaling parameters, influencing personal and collective learning.
- $rand()$ is a random number between (0,1).
- $pbest$ and $gbest$ are the personal best and global best positions of the particles, guiding the swarm's movement.

This README offers a detailed overview of the project, encompassing theoretical insights, implementation details, and the achieved results, demonstrating the power and versatility of PSO in tackling complex optimization challenges.

## Theoretical Background

### Particle Swarm Optimization (PSO)
Particle Swarm Optimization (PSO) is a computational algorithm that simulates the social behavior of birds, fish, and other swarms in nature. The core concept of PSO lies in the collective intelligence of these swarms, where the movement and decision-making process of one individual is influenced by others in the group. 

#### Mathematical Model
In PSO, each 'particle' in the swarm represents a potential solution to the optimization problem. The position and velocity of each particle are updated based on their own experience and the experience of neighboring particles.

The position $x_i$ and velocity $v_i$ of the $i$-th particle are updated as follows:
$$v_{i+1} = w \cdot v_i + c_1 \cdot rand() \cdot (pbest_i - x_i) + c2 \cdot rand() \cdot (gbest - x_i)$$

$$x_{i+1} = x_i + v_{i+1}$$

Where:
- $v_i$ is the current velocity.
- $w$ is the inertia weight.
- $c_1$ and $c_2$ are acceleration coefficients.
- $pbest$ and $gbest$ are the personal and global best positions.

### Non-convex Functions
The project specifically focuses on non-convex functions, which are characterized by having multiple local minima. These functions pose a significant challenge in optimization, as traditional methods like gradient descent are prone to getting trapped in local minima.

#### Project Focus
The non-convex function optimized in this project is defined as a generic function `cost_func` that is passed to the PSO algorithm. A typical non-convex function may have multiple local minima and a complex landscape, making it an ideal candidate to demonstrate the effectiveness of PSO. For example, a non-convex function can be represented as:

$$f(x) = a \cdot x^4 + b \cdot x^3 + c \cdot x^2 + d \cdot x + e$$

Where:
- $x$ is the variable.
- $a$, $b$, $c$, $d$, and $e$ are coefficients that create a non-convex shape in the function.

This function was chosen due to its complex landscape, with multiple peaks and valleys, representing a challenging optimization problem for PSO.

## Implementation Details

### Overview of PSO Implementation
This project's implementation of Particle Swarm Optimization (PSO) involves creating a swarm of particles, where each particle represents a potential solution to the optimization problem. The algorithm iteratively updates the position and velocity of each particle in the swarm, guiding them towards the optimal solution.

### Key Components
1. **Particle Initialization**: Each particle is initialized with a random position and velocity within the defined solution space.

2. **Velocity and Position Update**: The core of PSO lies in the update of particle velocities and positions. The velocity update equation incorporates three key components:
   - Inertia: Preserves the particle's previous direction.
   - Cognitive Component: Guides the particle towards its personal best position.
   - Social Component: Steers the particle towards the global best position found by the swarm.

   The update equations are as follows:
$$v_{i+1} = w \cdot v_i + c_1 \cdot rand() \cdot (pbest_i - x_i) + c2 \cdot rand() \cdot (gbest - x_i)$$

$$x_{i+1} = x_i + v_{i+1}$$

3. **Evaluation and Update of Best Positions**: After each iteration, the cost of the current position of each particle is evaluated. If a particle discovers a better position (lower cost), it updates its personal best. Simultaneously, the global best is updated if any particle finds a position better than the current global best.

4. **Convergence Criteria**: The algorithm iterates until a stopping criterion is met. This could be a predefined number of iterations or a threshold for the change in global best position.

### Customizations and Enhancements
- **Dynamic Inertia Weight**: The inertia weight `w` is dynamically adjusted during the optimization process. It starts with a higher value for global exploration and gradually decreases to facilitate local exploitation.
- **Parameter Tuning**: Parameters like the number of particles, cognitive and social coefficients, and inertia weight range are carefully tuned to balance exploration and exploitation efficiently.

### Code Structure
The implementation is modular, with separate functions for initializing particles, updating velocities and positions, and evaluating the cost. This modularity enhances the readability and maintainability of the code.

