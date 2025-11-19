# Reinforcement Learning Simulations

**CS329 - Foundations of Artificial Intelligence**  
**Course Project**

A collection of interactive web-based reinforcement learning simulations demonstrating classical RL algorithms on various environments.

## 🚀 Live Demo

**[Try it now!](https://maverick-0215.github.io/CS329-FAI-Project/)**

Experience the simulations directly in your browser - no installation required!

---

## 📋 Table of Contents

- [Overview](#overview)
- [Environments](#environments)
  - [Gridworld](#gridworld)
  - [15-Puzzle](#15-puzzle)
  - [CartPole](#cartpole)
- [Algorithms Implemented](#algorithms-implemented)
- [Features](#features)
- [Getting Started](#getting-started)
- [Usage](#usage)
- [Technical Details](#technical-details)
- [Project Structure](#project-structure)

---

## 🎯 Overview

This project implements three classic reinforcement learning environments with multiple RL algorithms, all running entirely in the browser using vanilla JavaScript. Each simulation provides:

- **Interactive visualization** of the environment and agent behavior
- **Real-time training** with performance metrics
- **Algorithm comparison** through side-by-side charts
- **Adjustable hyperparameters** for experimentation
- **Educational guides** explaining the problem and algorithms

---

## 🎮 Environments

### Gridworld

A classic grid navigation problem where an agent learns to reach a goal state while avoiding obstacles.

**Problem Description:**
- Agent starts at a designated start position
- Goal: Navigate to the goal position
- Obstacles: Certain cells are blocked
- Actions: Move Up, Down, Left, Right
- Rewards: +10 for reaching goal, -1 per step, -10 for hitting obstacles

**State Space:** Discrete grid positions  
**Action Space:** 4 discrete actions  
**Difficulty:** Beginner-friendly

**Key Learning Objectives:**
- Understanding value iteration
- Exploring vs. exploiting trade-offs
- Policy convergence visualization

---

### 15-Puzzle

A sliding tile puzzle where the agent learns to solve the classic 15-puzzle game.

**Problem Description:**
- 4×4 grid with 15 numbered tiles and one empty space
- Goal: Arrange tiles in numerical order
- Actions: Slide adjacent tiles into the empty space
- Rewards: Negative reward per move (encourages shorter solutions)

**State Space:** Permutations of tile arrangements  
**Action Space:** 4 discrete actions (context-dependent)  
**Difficulty:** Intermediate (large state space)

**Key Learning Objectives:**
- Handling large state spaces
- Heuristic-guided learning
- Episode-based learning (Monte Carlo)

---

### CartPole

A control problem where an agent balances a pole on a moving cart.

**Problem Description:**
- Pole attached to a cart on a frictionless track
- Goal: Keep pole upright as long as possible
- Actions: Push cart left or right
- Termination: Pole falls >12° or cart moves >2.4 units from center
- Rewards: +1 for each timestep the pole remains balanced

**State Space:** Continuous (discretized into bins)
- Cart Position: 3 bins
- Cart Velocity: 3 bins  
- Pole Angle: 12 bins
- Pole Angular Velocity: 6 bins

**Action Space:** 2 discrete actions  
**Difficulty:** Intermediate (continuous state space)

**Key Learning Objectives:**
- State discretization techniques
- Temporal difference learning
- Epsilon decay strategies
- Eligibility traces (future enhancement)

---

## 🧠 Algorithms Implemented

### Q-Learning
**Type:** Off-policy Temporal Difference  
**Update Rule:**  
```
Q(s,a) ← Q(s,a) + α[r + γ max Q(s',a') - Q(s,a)]
```

**Characteristics:**
- Learns optimal policy regardless of behavior policy
- Fast convergence
- Can overestimate Q-values

**Best For:** Gridworld, CartPole

---

### SARSA
**Type:** On-policy Temporal Difference  
**Update Rule:**  
```
Q(s,a) ← Q(s,a) + α[r + γ Q(s',a') - Q(s,a)]
```

**Characteristics:**
- Learns policy being followed
- More conservative than Q-Learning
- Better for stochastic environments

**Best For:** Gridworld, CartPole

---

### Monte Carlo
**Type:** Episode-based learning  
**Update Rule:**  
```
Q(s,a) ← average of returns following (s,a)
```

**Characteristics:**
- Learns from complete episodes
- No bootstrapping
- Unbiased estimates
- Slower convergence

**Best For:** 15-Puzzle (episodic), CartPole

---

## ✨ Features

### 🎨 Interactive Visualization
- Real-time rendering of environment state
- Agent movement animation
- Visual feedback for rewards and termination

### 📊 Performance Metrics
- **Training Charts:** Steps per episode with moving average smoothing
- **Statistics Cards:** Average performance over last 100 episodes
- **Algorithm Comparison:** Side-by-side performance visualization

### ⚙️ Hyperparameter Control
- **Learning Rate (α):** Controls update step size (0.0 - 1.0)
- **Discount Factor (γ):** Balances immediate vs. future rewards (0.0 - 1.0)
- **Episodes:** Number of training iterations (100 - 5000)
- **Epsilon (ε):** Exploration rate with automatic decay

### 🎓 Educational Content
- Problem descriptions and objectives
- State/action space explanations
- Reward structure details
- Algorithm comparisons

### 🚀 Performance Optimizations
- **Epsilon Decay:** Linear decay from 1.0 → 0.01 over first 50% of episodes
- **Sparse Q-Tables:** Memory-efficient storage
- **Asynchronous Training:** Non-blocking UI during training
- **Moving Average:** Smoothed performance visualization

---

## 🚀 Getting Started

### Option 1: Live Demo (Recommended)

**Visit the live deployment:** [https://maverick-0215.github.io/CS329-FAI-Project/](https://maverick-0215.github.io/CS329-FAI-Project/)

No installation needed - just click and start exploring!

### Option 2: Run Locally

#### Prerequisites
- Modern web browser (Chrome, Firefox, Safari, Edge)
- No installation or dependencies required!

#### Running Locally

1. **Clone or download** this repository
2. **Open `index.html`** in your web browser
3. **Select** an environment to explore
4. **Adjust hyperparameters** as desired
5. **Click "Train Agents"** to begin learning
6. **Watch** the algorithms compete in real-time!

---

## 📖 Usage

### Training Workflow

1. **Select Algorithms**
   - Check/uncheck algorithms to compare
   - At least one algorithm must be selected

2. **Configure Hyperparameters**
   - Adjust learning rate, discount factor, and episode count
   - Default values work well for most cases

3. **Train**
   - Click "Train Agents" button
   - Training runs asynchronously (UI remains responsive)
   - Progress shown via loading indicator

4. **Analyze Results**
   - View training curves on the chart
   - Compare algorithm performance via statistics cards
   - Identify convergence patterns

5. **Simulate**
   - Click "Simulate Learned Policy" to watch the best agent
   - Or "Run Untrained" to see random behavior

### Tips for Best Results

**Gridworld:**
- Use higher learning rate (α = 0.3-0.5) for faster convergence
- Q-Learning typically outperforms SARSA
- 500-1000 episodes sufficient

**15-Puzzle:**
- Monte Carlo works best (episodic problem)
- Increase episodes to 2000-3000
- Lower learning rate (α = 0.05-0.1)

**CartPole:**
- All algorithms perform well with proper tuning
- Epsilon decay is critical for convergence
- 1000 episodes recommended
- Watch for cart position drift (now fixed with improved discretization)

---

## 🔧 Technical Details

### Architecture

**Frontend:** Pure HTML5, CSS3, JavaScript (ES6+)  
**Rendering:** HTML5 Canvas API  
**Charting:** Custom canvas-based visualization  
**State Management:** Vanilla JavaScript objects

### Key Design Decisions

1. **No External Dependencies**
   - Entire project runs in browser without libraries
   - Easy to understand, modify, and deploy
   - No build process required

2. **Sparse Q-Table Implementation**
   - Only stores visited state-action pairs
   - Dramatically reduces memory usage
   - Scales to large state spaces

3. **Epsilon Decay Strategy**
   - Linear decay over first 50% of training
   - Balances exploration and exploitation
   - Prevents premature convergence

4. **State Discretization (CartPole)**
   - Bins chosen based on problem dynamics
   - Finer resolution near critical values (e.g., θ ≈ 0)
   - Includes cart position to prevent drift

### Performance Characteristics

| Environment | State Space Size | Typical Training Time |
|-------------|------------------|----------------------|
| Gridworld   | ~100 states      | < 1 second           |
| 15-Puzzle   | ~10^13 states    | 5-10 seconds         |
| CartPole    | 1,296 states     | 2-5 seconds          |

*Times measured on modern desktop browser (Chrome/Firefox)*

---

## 📁 Project Structure

```
FAI_Proj/
├── index.html              # Landing page with project navigation
├── gridworld.html          # Gridworld RL simulation
├── fifteen_puzzle.html     # 15-Puzzle RL simulation
├── cartpole.html           # CartPole RL simulation
├── gridworld-rl/           # Alternative gridworld implementation
├── simple_grid.ipynb       # Jupyter notebook experiments
├── fifteen_puzzle.ipynb    # Jupyter notebook experiments
└── README.md               # This file
```

### File Descriptions

- **`index.html`**: Main landing page with links to all simulations
- **`gridworld.html`**: Complete gridworld environment with Q-Learning, SARSA, and Monte Carlo
- **`fifteen_puzzle.html`**: 15-Puzzle solver using Monte Carlo learning
- **`cartpole.html`**: CartPole balancing task with improved discretization and epsilon decay
- **`*.ipynb`**: Python notebooks for algorithm prototyping and analysis

---

## 🔮 Future Enhancements

- SARSA(λ) with eligibility traces
- Deep Q-Network (DQN) using TensorFlow.js
- Additional environments (Mountain Car, Lunar Lander)
- Q-value heatmaps and policy visualization

---

## Authors
A V S Manoj (23110025)

N Eshwar Karthikeya (23110215)

O Akash (23110225)

M Aniruddh Reddy (23110195)

**Live Demo:** [maverick-0215.github.io/CS329-FAI-Project](https://maverick-0215.github.io/CS329-FAI-Project/)  
**Semester:** Fall 2025

---

## Acknowledgments

- **Sutton & Barto** for the foundational RL textbook
- **OpenAI Gym/Gymnasium** for environment inspiration
- **Andrej Karpathy** for REINFORCEjs inspiration
- Course instructors and TAs for guidance

---