# Gridworld Reinforcement Learning Simulator

A web-based simulator for comparative analysis of reinforcement learning algorithms in gridworld environments. This project provides an interactive platform for studying Q-Learning, SARSA, and Monte Carlo methods.

## Project Overview

This simulator enables empirical comparison of fundamental reinforcement learning algorithms on customizable gridworld tasks. The implementation provides:

- Interactive environment configuration (3×3 to 10×10 grids)
- Three classic RL algorithms: Q-Learning, SARSA, and Monte Carlo (first-visit)
- Real-time visualization of learning curves
- Comprehensive hyperparameter control
- Performance metrics and statistical analysis

## Quick Start

### Requirements
- Modern web browser (Chrome, Firefox, Edge, or Safari)
- No installation or dependencies required

### Running the Simulator
1. Open `index.html` in any web browser
2. The simulator will launch with a default 6×6 grid configuration
3. Configure environment, select algorithms, and begin training

Alternatively, use command line:
```bash
# Windows
start index.html

# macOS
open index.html

# Linux
xdg-open index.html
```

## Features

### Environment Configuration
- **Dynamic Grid Sizing**: Adjustable grid dimensions from 3×3 to 10×10
- **Interactive Obstacle Placement**: Click-to-toggle interface for adding/removing obstacles
- **Fixed Start and Goal**: Start position at (0,0), goal at (n-1, n-1)
- **Visual Feedback**: Color-coded cells for immediate state identification

### Algorithm Implementations

#### Q-Learning (Off-Policy TD)
**Update Rule:**
```
Q(s,a) ← Q(s,a) + α[r + γ max Q(s',a') - Q(s,a)]
```
- Off-policy temporal difference learning
- Learns optimal action-value function regardless of behavior policy
- Uses maximum Q-value over next state actions
- Typically faster convergence to optimal policy

#### SARSA (On-Policy TD)
**Update Rule:**
```
Q(s,a) ← Q(s,a) + α[r + γ Q(s',a') - Q(s,a)]
```
- On-policy temporal difference learning
- Learns value of the policy being followed
- Uses actual next action from ε-greedy policy
- More conservative behavior, considers exploration in learning

#### Monte Carlo (First-Visit)
**Update Rule:**
```
Q(s,a) ← Average of returns following first visits to (s,a)
```
- Episode-based learning approach
- No bootstrapping (waits for episode completion)
- Unbiased estimate of true value function
- Sample averaging or incremental mean updates

### Reward Structure
The environment implements the following reward function:
- **Goal reached**: +10
- **Normal move**: -0.1 (encourages path efficiency)
- **Collision** (obstacle/boundary): -1 (agent remains in current position)

### Visualization Components
- **Learning Curves**: Line graphs displaying steps per episode
- **Algorithm Comparison**: Multiple curves with distinct colors
- **Performance Metrics**: 
  - Average steps (final 10 episodes)
  - Best performance achieved
  - Convergence behavior

## Navigation Bar Features

### How to Use
Detailed instructions for:
- Environment configuration
- Algorithm selection
- Hyperparameter tuning
- Training execution
- Results interpretation

### Algorithms
Comprehensive documentation including:
- Mathematical formulations
- Update equations
- Algorithmic characteristics
- Comparative analysis table

### GitHub Repository
Direct link to the project source code and documentation.

## Usage Guidelines

### Hyperparameter Configuration
- **Learning Rate (α)**: Range [0, 1]. Recommended: 0.1
  - Higher values: Faster learning, potential instability
  - Lower values: Slower convergence, more stable
  
- **Discount Factor (γ)**: Range [0, 1]. Recommended: 0.9
  - Higher values: Prioritizes long-term rewards
  - Lower values: Emphasizes immediate rewards
  
- **Exploration (ε)**: Range [0, 1]. Recommended: 0.1
  - Higher values: More exploration, slower convergence
  - Lower values: More exploitation, risk of suboptimal convergence
  
- **Episodes**: Range [100, 10000]. Recommended: 1000-2000
  - Complex environments require more episodes
  - Simple paths converge in fewer episodes

## Technical Implementation

### Architecture
- **Technology Stack**: Pure HTML5, CSS3, and JavaScript (ES6)
- **No Dependencies**: No external libraries or frameworks required
- **Single File Design**: All components in one HTML file for portability
- **Canvas Rendering**: HTML5 Canvas API for chart visualization

### Environment Specifications
- **State Space**: All (row, col) grid positions
- **Action Space**: 4 discrete actions {up, down, left, right}
- **Deterministic Dynamics**: Actions produce consistent results
- **Episodic Task**: Terminates at goal or 200-step limit

### Performance Characteristics
- Training: Synchronous execution with asynchronous UI updates
- Scalability: Handles up to 10,000 episodes efficiently
- Typical execution time: 1-3 seconds for 1000 episodes on modern hardware

## Code Structure

```
index.html
├── HTML Structure
│   ├── Navigation Bar (fixed top)
│   ├── Modal Dialogs (How to Use, Algorithms)
│   ├── Environment Setup Panel
│   ├── Algorithm Selection Panel
│   └── Results Display Panel
├── CSS Styling
│   ├── Professional Typography
│   ├── Grid Layout System
│   ├── Modal Components
│   └── Responsive Design
└── JavaScript Implementation
    ├── Grid State Management
    ├── GridEnvironment Class
    ├── RL Algorithms
    │   ├── Q-Learning Implementation
    │   ├── SARSA Implementation
    │   └── Monte Carlo Implementation
    ├── Training Orchestration
    ├── Canvas Visualization
    └── UI Event Handlers
```

## Experimental Methodology

### Basic Experiment Workflow
1. Configure grid size and obstacle placement
2. Select algorithm(s) for comparison
3. Set hyperparameters based on environment complexity
4. Execute training
5. Analyze learning curves and performance metrics
6. Iterate with different configurations

### Suggested Experiments
- **Convergence Analysis**: Compare convergence rates across algorithms
- **Hyperparameter Sensitivity**: Systematic variation of α, γ, ε
- **Environment Complexity**: Test on grids of varying size and obstacle density
- **Policy Comparison**: Evaluate final policy quality

## References

- Sutton, R. S., & Barto, A. G. (2018). *Reinforcement Learning: An Introduction* (2nd ed.). MIT Press.
- Watkins, C. J. C. H. (1989). Learning from Delayed Rewards. PhD thesis, Cambridge University.
- Rummery, G. A., & Niranjan, M. (1994). On-line Q-learning using connectionist systems. Technical Report, Cambridge University Engineering Department.

## Project Information

**Repository**: [https://github.com/maverick-0215/Learning-Grid-Game-via-RL](https://github.com/maverick-0215/Learning-Grid-Game-via-RL)

**License**: Educational use

**Course Project**: Foundations of Artificial Intelligence

## Contact and Contributions

This project is developed as a course assignment. The implementation is available for educational purposes and academic use.
