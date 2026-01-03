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

---
