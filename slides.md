---
# POMDP Explained
layout: cover
title: Partially Observable Markov Decision Processes
subtitle: Decision-making under uncertainty
author: Your Name

---

# What is a POMDP?

- **POMDP** stands for **Partially Observable Markov Decision Process**.
- It's a mathematical framework for decision-making in environments where:
  - **Uncertainty** exists about outcomes.
  - The agent has **incomplete information** about the current state.
  
- An extension of the **Markov Decision Process (MDP)**, with the added complexity of **partial observability**.

---

# Applications of POMDPs

- **Robotics**: Autonomous navigation with noisy sensors.
- **Healthcare**: Treatment planning under uncertain patient conditions.
- **Game AI**: Decision-making with incomplete information (e.g., Poker).
- **Speech recognition**: Handling noisy inputs in dialogue systems.

---

# POMDP Components

- **States ($S$)**: The possible situations of the environment.
- **Actions ($A$)**: Decisions the agent can make.
- **Transition Model ($T$)**: Probability of moving between states.
- **Observations ($O$)**: Noisy signals from the environment.
- **Observation Model ($O(o|s', a)$)**: Likelihood of receiving an observation.
- **Reward ($R$)**: Immediate feedback for actions.
- **Belief State ($b(s)$)**: Probability distribution over states.
- **Discount Factor ($\gamma$)**: Weighs short vs long-term rewards.

---

# States and Actions

- **States ($S$)**: All possible situations the environment can be in.
  - Example: A robot's position in a maze.

- **Actions ($A$)**: Choices the agent can make to influence the environment.
  - Example: Move forward, turn left, turn right.

---

# Transition Model ($T$)

- The **Transition Model** $T(s'|s, a)$ describes the probability of transitioning from state $s$ to state $s'$ after taking action $a$.
  
- **Stochastic Environment**: Actions may not lead to deterministic outcomes.
  
- Example: A robot might slip while trying to move, leading to a different position than expected.

---

# Observations and Observation Model

- **Observations ($O$)**: Sensory inputs that give partial information about the state.
  - Example: A robot’s sensors detecting walls.

- **Observation Model ($O(o|s', a)$)**: Defines the probability of receiving observation $o$ when in state $s'$ after action $a$.
  - Example: Sensor readings may be noisy or incomplete.

---

# Reward Function ($R$)

- **Reward Function** $R(s, a)$: The immediate reward the agent receives for taking action $a$ in state $s$.

- The agent’s goal is to **maximize cumulative rewards** over time.

- Example: Positive reward for reaching a goal, negative reward for hitting a wall.

---

# Belief State ($b(s)$)

- **Belief State** $b(s)$: A probability distribution over all possible states.
  
- Since the agent doesn't know the true state, it maintains a belief about which state it might be in.

- **Belief Update**: The belief state is updated after each action and observation using **Bayesian Inference**.

---

# Belief Update Formula

$$
b'(s') = \eta \, O(o|s', a) \sum_{s \in S} T(s'|s, a) b(s)
$$

Where:
- $b'(s')$ is the updated belief after receiving observation $o$.
- $T(s'|s, a)$ is the transition model.
- $O(o|s', a)$ is the observation model.
- $\eta$ is a normalization constant.

---

# Policy ($\pi$) and Value Function

- **Policy** $\pi(b)$: A mapping from belief states to actions.
  - The agent selects actions based on its current belief.
  
- **Value Function** $V(b)$: The expected cumulative reward from belief state $b$.
  
- The goal is to find the **optimal policy** $\pi^*$, maximizing long-term rewards.

---

# Value Function and Bellman Equation

The **Bellman Equation** for a POMDP value function is:

$$
V(b) = \max_{a \in A} \left[ \sum_{s \in S} b(s) R(s, a) + \gamma \sum_{o \in O} P(o|b, a) V(b') \right]
$$

- $P(o|b, a)$: Probability of observation $o$ given belief $b$ and action $a$.
- The agent plans in **belief space** to find the best action sequence.

---

# Solving POMDPs: Exact vs Approximate

### Exact Solutions:
- **Value Iteration**: Uses dynamic programming, but computationally expensive.
- **Incremental Pruning**: An optimized approach for small POMDPs.

### Approximate Solutions:
- **Point-Based Value Iteration (PBVI)**: Focuses on a subset of belief points.
- **Monte Carlo Methods**: Use random sampling to estimate value functions.
- **POMCP**: Combines Monte Carlo tree search with POMDP planning.

---

# Example: Robot in a Maze

1. **States**: Different positions in the maze.
2. **Actions**: Move forward, turn left, turn right.
3. **Observations**: Wall detected, no wall detected (noisy).
4. **Transition**: The robot might slip or miscalculate its move.
5. **Reward**: Positive for reaching the goal, negative for hitting walls.
6. **Belief State**: Probabilistic estimate of the robot’s position.

---

# Applications of POMDPs

- **Robotics**: Navigation in uncertain environments.
- **Medical Decision Making**: Optimizing treatments with uncertain patient states.
- **Game AI**: Decisions with hidden information (e.g., Poker).
- **Autonomous Systems**: Handling noisy sensor data.

---

# Conclusion

- POMDPs provide a framework for decision-making in environments with **uncertainty** and **partial observability**.
- Despite their complexity, POMDPs are useful for real-world applications like robotics, AI, and healthcare.
- Approximation techniques allow POMDPs to scale to larger problems.

---

# Questions?

Any questions on POMDPs?
