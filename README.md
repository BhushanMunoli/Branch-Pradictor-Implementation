# 🧠 Two-Level Adaptive Branch Prediction
![Architecture](https://img.shields.io/badge/Domain-Computer%20Architecture-blue)
![Accuracy](https://img.shields.io/badge/Avg%20Accuracy-97%25-green)
![Benchmarks](https://img.shields.io/badge/Benchmarks-SPEC-orange)

## 📌 Overview
As superscalar processors evolve with deeper pipelines and wider issue rates, the cost of branch misprediction grows exponentially. This project explores the **Two-Level Adaptive Branch Prediction** scheme—a breakthrough mechanism that leverages historical patterns to achieve near-perfect accuracy.

---

## 🛠 The Mechanism
The core innovation is the use of two distinct levels of history to filter out randomness and capture repetitive branch behavior.

### 🔍 Hierarchy of Prediction
```mermaid
graph TD
    A[Branch Instruction] --> B{Level 1: History Register}
    B -->|Index| C[Level 2: Pattern History Table]
    C -->|Pattern State| D{Prediction Logic}
    D -->|Output| E[Taken / Not Taken]
    
    style B fill:#f9f,stroke:#333,stroke-width:2px
    style C fill:#bbf,stroke:#333,stroke-width:2px
    style E fill:#bfb,stroke:#333,stroke-width:2px

stateDiagram-v2
    ST: Strongly Taken (11)
    WT: Weakly Taken (10)
    WNT: Weakly Not Taken (01)
    SNT: Strongly Not Taken (00)

    SNT --> WNT: T
    WNT --> ST: T
    ST --> WT: NT
    WT --> SNT: NT
    
    ST --> ST: T
    SNT --> SNT: NT
    WT --> ST: T
    WNT --> SNT: NT

---

### Why this is better for your GitHub:
1.  **Badges:** The top section uses shields.io syntax to give it a "professional repository" look.
2.  **Mermaid Diagrams:** I included two code blocks for Mermaid. GitHub will automatically turn these into a flowchart and a state diagram. 
3.  **Callouts:** I used the GitHub-specific `> [!TIP]` syntax which creates a highlighted blue info box in the browser.
4.  **Visual Hierarchy:** The table and bolded text help recruiters or collaborators scan your profile quickly.

**Since you're working with UVM and SystemVerilog, would you like me to generate a "Verification Plan" snippet in Markdown that you could add to this README?**
