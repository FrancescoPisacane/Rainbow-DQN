# Rainbow-Ocean: Vectorized DQN Extensions

A modular implementation of Deep Q-Networks (DQN) built with [PufferLib Ocean](https://puffer.ai/ocean.html), focusing on performance-enhancing extensions inspired by the "Rainbow" architecture.
This project explores the impact of individual and combined algorithmic improvements on standard DQN agents.

**DQN Extensions:**
  - **Double DQN & Dueling DQN:** Architectural improvements to mitigate maximization bias and improve state-value estimation.
  - **Prioritized Experience Replay (PER):** Advanced sampling using a SumTree data structure to focus learning on high-information transitions.
  - **N-Step Returns:** Implementation of multi-step targets to balance bias and variance.
  - **Noisy Networks:** Integrated parameter-space noise for more robust, structured exploration.

## Environments
Benchmarking was conducted across three tiers of the PufferLib Ocean suite:
1. **Debug (Squared):** Rapid verification of algorithm correctness.
2. **Comparing (CartPole):** Used for extensive hyperparameter tuning and extension comparison.
3. **Challenge (Breakout):** High-dimensional visual observation task for scaling analysis.

## Key Findings & Empirical Analysis
Contrary to naive expectations, the "Rainbow-lite" agent (combining all extensions) did not immediately outperform individual components in simpler environments like CartPole.
- **Hyperparameter Conflict:** We identified critical interference between PER parameters ($\beta=0.8$) and reward clipping when combined with smaller buffer capacities.
- **Complexity Trade-off:** Added complexity proved detrimental in low-dimensional spaces, while showing higher late-stage potential in complex environments like Breakout (reaching evaluation returns of ~250-300).
