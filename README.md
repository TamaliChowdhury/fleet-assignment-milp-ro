# Fleet Assignment Under Structural Shocks

## Project Overview
This project addresses the challenge short-haul carriers face when hit by **structural fleet shocks**—such as manufacturer-wide groundings or regulator-issued capacity caps—where standard stochastic distributions for aircraft availability do not apply. It utilizes a four-phase analytical framework to determine which routes to preserve and which to drop when fleet availability is uncertain



## The Four-Phase Framework
The project is executed in four distinct phases, integrated within a single Python environment:

1.  **Phase I: MILP Baseline**
    *   A **Mixed-Integer Linear Programme (MILP)** solves for the deterministic optimum of each specific disruption scenario.
    *   **Objective:** Minimize a priority-weighted cost function that protects high-demand "trunk routes" over secondary routes.
2.  **Phase II: Robust Optimisation**
    *   Implements **Minimax** and **Minimax Regret** formulations to find a single "committed plan" before the specific disruption is revealed.
    *   Results show that Minimax Regret achieves a regret value of $v=0$ for this specific nested scenario set.
3.  **Phase III: Multi-Objective Pareto Analysis**
    *   Explores the trade-off between **operating cost** and **network coverage**.
    *   Identifies non-dominated solutions across a weighting spectrum ($\alpha$) to assist carrier decision-making.
4.  **Phase IV: Monte Carlo Validation**
    *   Stress-tests the committed plan against **15,000 random grounding trials** across three regimes: Stable, Stressed, and Crisis.
    *   Includes a Python-based animation of the fleet assignment performance.

## Technical Implementation

### Prerequisites
*   **Python 3.x**
*   **Gurobi Optimizer 12.0** (Requires a valid license)
*   **NumPy:** For data handling and Monte Carlo sampling.
*   **Matplotlib:** For generating result visualizations and animations.

### Data Calibration
The model parameters are calibrated against **Indian DGCA traffic data (2021-22)**[cite: 3]. This specific period captures demand patterns under actual regulatory stress, ensuring the model's relevance to real-world disruptions[cite: 3].

### Fleet Configuration
The test instance involves a carrier with **12 aircraft** serving **15 priority routes**:
*   **Aircraft 1-6:** Boeing 737-800 (162 seats)[cite: 3].
*   **Aircraft 7-12:** Airbus A320 (180 seats)[cite: 3].



## Results Summary
*   **Trunk Protection:** The model consistently protects trunk routes (Tier 1) through the priority-weighted objective, only dropping them in extreme "Crisis" scenarios[cite: 3].
*   **Constraint Impact:** The "Big-M" technique successfully links capacity constraints, allowing for controlled spill rather than model infeasibility[cite: 3].
*   **Validation:** Monte Carlo results confirm the robust plan generalizes well in "Stable" and "Stressed" regimes, while identifying the "Crisis" regime as the boundary for scenario-based protection[cite: 3].

## Repository Contents
*   `Operationsanalyticsassign-2.ipynb`: The primary Jupyter notebook containing the full model implementation, Gurobi code, and visualization routines[cite: 3].
*   `Project_Report.pdf`: The detailed 2,000-word analytical report[cite: 3].
