# Two-Level Adaptive Branch Prediction

## Overview
As the issue rate and depth of pipelining in high-performance superscalar processors increase, the importance of an excellent branch predictor becomes vital to delivering the potential performance of wide-issue, deep-pipelined microarchitectures.

This project implements/explores the **Two-Level Adaptive Branch Prediction** scheme, which achieves substantially higher accuracy than traditional static or simple dynamic schemes. By utilizing two levels of history information, this mechanism achieves an average prediction accuracy of **97%**, compared to the 94.4% seen in contemporary literature.

---

## The Mechanism
The predictor uses two levels of branch history information to make predictions:
1.  **Level 1:** The history of the last $k$ branches encountered.
2.  **Level 2:** The branch behavior for the last $s$ occurrences of the specific pattern of those $k$ branches.

### Variations
We identify three variations of the Two-Level Adaptive Branch Prediction based on the resolution of history information:
* **GA (Global Adaptive):** Uses a single global history register.
* **PA (Per-address Adaptive):** Uses a branch history table (BHT) indexed by the branch address.
* **SA (Set Adaptive):** Groups branches into sets to share history information.

The most effective implementation utilizes a **per-address branch history table** and a **global pattern history table**.

---

## Pattern History Update Automata
The prediction is determined by Finite-State Moore Machines (FSMs) stored in the Pattern History Table (PHT). The following automata were evaluated:

| Automaton | Description | Bit Complexity |
| :--- | :--- | :--- |
| **Last-Time** | Stores only the outcome of the last execution. Predicts what happened last time. | 1-bit |
| **A1** | Records the last two outcomes. Predicts "Taken" if at least one of the last two was taken. | 2-bits |
| **A2** | A 2-bit saturating up-down counter (Smith Predictor style). | 2-bits |



---

## Performance Evaluation
The scheme was measured using trace-driven simulations of the **SPEC benchmarks**.

### Key Results
* **Accuracy:** Two-Level Adaptive Prediction averages **97%**.
* **Comparison:** Other known schemes achieve a maximum of **94.4%**.
* **Sensitivity:** Accuracy is highly sensitive to $k$ (length of history register) and $s$ (size of PHT entries).

---

## Future Work
While 97% accuracy is a significant improvement, future high-performance engines with deeper pipelines will require even lower miss rates. Current research is focused on:
* Characterizing the remaining 3% of mispredictions.
* Reducing the hardware overhead of per-address history tables.
* Analyzing the effects of context switching on branch history state.

---

## References
* Yeh, T.-Y., & Patt, Y. N. "Two-Level Adaptive Training Branch Prediction."
* Smith, J. E. "A Study of Branch Prediction Strategies."
