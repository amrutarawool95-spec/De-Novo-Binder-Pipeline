# 🧬 Pipeline Architecture & Workflow Visualization

> **Objective:** To automate and standardize the *de novo* miniprotein binder design workflow, ensuring reproducibility, scalability, and ease of onboarding for new lab members.

## 🔄 High-Level Workflow Diagram

```mermaid
graph TD
    A[🎯 Target Protein PDB] --> B[Step 1: RFdiffusion]
    B -->|Generates Novel Backbone| C[Step 2: ProteinMPNN]
    C -->|Designs Amino Acid Sequence| D[Step 3: AlphaFold-Multimer]
    D -->|Validates Binding & Structure| E[✅ Final Validated Binder PDB]
    
    style A fill:#f9f,stroke:#333,stroke-width:2px
    style E fill:#bbf,stroke:#333,stroke-width:2px