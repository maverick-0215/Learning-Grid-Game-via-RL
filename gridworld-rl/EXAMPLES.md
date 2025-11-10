# 🎯 Example Scenarios for Gridworld RL Simulator

This file contains preset configurations you can try in the simulator to see different learning behaviors.

## 📘 Beginner Scenarios

### Scenario 1: Empty Grid - Optimal Path
**Purpose**: See algorithms learn the shortest Manhattan path

**Configuration**:
- Grid Size: 5×5
- Obstacles: None (empty grid)
- Algorithms: All three (Q-Learning, SARSA, Monte Carlo)
- Hyperparameters:
  - α (Learning Rate): 0.1
  - γ (Discount): 0.9
  - ε (Exploration): 0.1
  - Episodes: 500

**Expected Results**:
- All algorithms should converge to 8 steps (4 right + 4 down)
- Q-Learning typically converges fastest
- Very stable learning curves after ~100 episodes

**What to Observe**:
- How quickly each algorithm finds the optimal path
- The learning curve should show a clear downward trend
- Final performance should be identical for all three

---

### Scenario 2: Single Wall
**Purpose**: Learn to navigate around a simple obstacle

**Configuration**:
- Grid Size: 6×6
- Obstacles: Place a vertical line of rocks from (1,2) to (4,2)
  - Click cells at positions: (1,2), (2,2), (3,2), (4,2)
- Algorithms: All three
- Hyperparameters:
  - α: 0.1
  - γ: 0.9
  - ε: 0.15
  - Episodes: 1000

**Expected Results**:
- Optimal path: ~11-13 steps (detour around wall)
- SARSA may be slightly more cautious
- Q-Learning finds optimal path reliably

**What to Observe**:
- How agents learn to avoid the wall
- Initial episodes have many collisions (200 step limit hit)
- Convergence happens around episode 200-400

---

## 📗 Intermediate Scenarios

### Scenario 3: Corridor Challenge
**Purpose**: Test exploration in constrained spaces

**Configuration**:
- Grid Size: 7×7
- Obstacles: Create a corridor pattern
  - Top wall: (1,1), (1,2), (1,3), (1,4), (1,5)
  - Bottom wall: (5,1), (5,2), (5,3), (5,4), (5,5)
  - Create gaps for passage
- Algorithms: All three
- Hyperparameters:
  - α: 0.1
  - γ: 0.9
  - ε: 0.2 (higher exploration needed)
  - Episodes: 1500

**Expected Results**:
- Takes longer to find optimal path
- Monte Carlo may struggle initially
- Higher variance in early learning

**What to Observe**:
- Importance of exploration (ε)
- How long it takes to discover the passage
- Difference between on-policy (SARSA) and off-policy (Q-Learning)

---

### Scenario 4: Diagonal Maze
**Purpose**: Complex navigation requiring multiple decision points

**Configuration**:
- Grid Size: 8×8
- Obstacles: Diagonal pattern
  - (2,2), (2,3), (3,3), (4,4), (5,4), (5,5), (6,5)
- Algorithms: All three
- Hyperparameters:
  - α: 0.08
  - γ: 0.95 (higher to value long-term planning)
  - ε: 0.15
  - Episodes: 2000

**Expected Results**:
- Optimal path: ~15-18 steps
- Clear difference between algorithms emerges
- Q-Learning often outperforms others

**What to Observe**:
- How discount factor (γ) affects long-term planning
- SARSA's cautious behavior near obstacles
- Learning curve has multiple "improvement jumps"

---

## 📕 Advanced Scenarios

### Scenario 5: Sparse Exploration
**Purpose**: Test exploration in large sparse environment

**Configuration**:
- Grid Size: 10×10
- Obstacles: Randomly place 8-10 obstacles scattered across grid
  - Example: (2,3), (3,7), (4,4), (5,8), (6,2), (7,5), (8,7), (9,3)
- Algorithms: All three
- Hyperparameters:
  - α: 0.05 (slower, more stable)
  - γ: 0.95
  - ε: 0.1
  - Episodes: 3000

**Expected Results**:
- Optimal path: ~18-22 steps
- Slow convergence
- Monte Carlo may take longest

**What to Observe**:
- Effect of large state space
- Importance of sufficient episodes
- How sparse rewards affect learning speed

---

### Scenario 6: High Exploration Test
**Purpose**: See effect of exploration parameter

**Configuration**:
- Grid Size: 6×6
- Obstacles: Moderate (4-5 rocks)
  - Example: (2,2), (2,3), (3,4), (4,2)
- Algorithms: All three
- Hyperparameters:
  - α: 0.1
  - γ: 0.9
  - ε: 0.3 (high exploration!)
  - Episodes: 1500

**Expected Results**:
- Slower convergence due to high exploration
- More erratic learning curves
- Eventually finds good policy

**What to Observe**:
- Trade-off between exploration and exploitation
- Learning curves remain noisy throughout
- Compare with same scenario but ε=0.1

---

### Scenario 7: Near-Optimal Comparison
**Purpose**: Fine-tune to see subtle algorithm differences

**Configuration**:
- Grid Size: 6×6
- Obstacles: Strategic placement
  - (1,1), (1,2), (1,3), (2,3), (3,5), (4,5)
- Algorithms: All three
- Hyperparameters:
  - α: 0.1
  - γ: 0.9
  - ε: 0.1
  - Episodes: 2000

**Expected Results**:
- All converge to similar performance
- Q-Learning slightly faster
- SARSA more stable curve

**What to Observe**:
- Final performance (last 100 episodes)
- Variance in performance
- Which algorithm is most consistent

---

## 🔬 Experimental Scenarios

### Scenario 8: Learning Rate Comparison
**Purpose**: Understand impact of learning rate

**Configuration**:
- Grid Size: 6×6
- Obstacles: Medium complexity (5-6 rocks)
- Algorithms: Run Q-Learning three times with different α
  
**Test 1**: α=0.01, episodes=3000
**Test 2**: α=0.1, episodes=1500  
**Test 3**: α=0.5, episodes=1000

**What to Observe**:
- Low α: Slow but very stable
- Medium α: Good balance
- High α: Fast but may oscillate

---

### Scenario 9: Discount Factor Test
**Purpose**: See how discount factor affects learning

**Configuration**:
- Grid Size: 8×8
- Obstacles: Sparse (5-6 rocks)
- Algorithms: Q-Learning only
  
**Test 1**: γ=0.5, episodes=1500
**Test 2**: γ=0.9, episodes=1500
**Test 3**: γ=0.99, episodes=1500

**What to Observe**:
- Low γ: Prefers immediate rewards, may take suboptimal path
- Medium γ: Balanced
- High γ: Values long-term rewards, finds optimal path

---

### Scenario 10: Algorithm Behavior Near Obstacles
**Purpose**: Compare risk-taking behavior

**Configuration**:
- Grid Size: 6×6
- Obstacles: Create a "dangerous corridor"
  - Place rocks to create a narrow path with penalties on sides
  - Example: Two parallel walls with 1-cell gap
- Algorithms: Q-Learning vs SARSA (compare directly)
- Hyperparameters:
  - α: 0.1
  - γ: 0.9
  - ε: 0.15
  - Episodes: 2000

**Expected Results**:
- SARSA takes safer, longer path
- Q-Learning takes risky, shorter path
- Clear behavioral difference

**What to Observe**:
- On-policy (SARSA) vs off-policy (Q-Learning)
- SARSA learns value of *actual* behavior
- Q-Learning learns value of *optimal* behavior

---

## 💡 Tips for Creating Your Own Scenarios

1. **Start Simple**: Begin with small grids and few obstacles
2. **Increase Gradually**: Add complexity step by step
3. **Control Variables**: Change one hyperparameter at a time
4. **Run Multiple Times**: RL has variance; run same config 3-5 times
5. **Document Results**: Take notes on what you observe
6. **Share Interesting Configs**: Create challenging scenarios for others

## 📊 Metrics to Track

When running experiments, pay attention to:

- **Convergence Speed**: Episode number when learning stabilizes
- **Final Performance**: Average steps in last 50-100 episodes
- **Stability**: Variance in final performance
- **Best Performance**: Minimum steps achieved
- **Learning Curve Shape**: Smooth vs erratic

## 🎓 Educational Exercise Ideas

### Exercise 1: Hyperparameter Sweep
- Keep environment same
- Systematically vary one hyperparameter
- Plot convergence episode vs parameter value

### Exercise 2: Algorithm Ranking
- Create 5 different environments
- Run all 3 algorithms on each
- Rank algorithms by performance in each environment

### Exercise 3: Exploration Analysis
- Run same environment with ε = 0.0, 0.1, 0.2, 0.3, 0.5
- Observe convergence speed and final performance
- Find optimal exploration rate

### Exercise 4: Scale Analysis
- Test same obstacle pattern at scales 4×4, 6×6, 8×8, 10×10
- How does grid size affect learning?
- Do you need more episodes for larger grids?

---

**Have fun experimenting! 🎮🤖**

Remember: Reinforcement learning has inherent randomness (ε-greedy policy), so results may vary between runs. This is normal and expected!
