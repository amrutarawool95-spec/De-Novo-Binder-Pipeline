# 🧬 De Novo Miniprotein Binder Design Pipeline
### *Automated, Reproducible Workflow for RFdiffusion → ProteinMPNN → AlphaFold-Multimer*

![Pipeline Status](https://img.shields.io/badge/status-active-success)
![Snakemake](https://img.shields.io/badge/Workflow-Snakemake-blue)
![License](https://img.shields.io/badge/license-MIT-green)

---

## 📖 1. Executive Summary & Scientific Rationale
This repository contains a fully reproducible, containerized **Snakemake pipeline** designed to automate the *de novo* generation of miniprotein binders. 

Designing a functional binder requires three distinct computational phases:
1. **Backbone Generation (RFdiffusion):** Creating a novel 3D protein scaffold that geometrically complements a target binding site (e.g., a GPCR extracellular loop or an immune checkpoint interface).
2. **Sequence Design (ProteinMPNN):** Assigning the optimal amino acid sequence to the generated backbone to ensure thermodynamic stability and high expression yield.
3. **Structural Validation (AlphaFold-Multimer):** *In silico* verification of the binder-target complex to predict binding affinity and structural confidence before costly wet-lab synthesis.

By chaining these tools via Snakemake, this pipeline eliminates manual file-handling bottlenecks, ensures strict version control, and allows for the parallel generation of hundreds of designs.

---

## 🔄 2. High-Level Workflow Architecture

```mermaid
graph TD
    A[🎯 Target Protein PDB<br/>(e.g., GPCR, Immune Checkpoint)] --> B
    
    subgraph Phase 1: Generative Design
    B[<b>Rule 1: RFdiffusion</b><br/>Generates novel backbone scaffolds<br/>targeting specific hotspots]
    end
    
    B -->|Outputs .pdb backbones| C
    
    subgraph Phase 2: Sequence Optimization
    C[<b>Rule 2: ProteinMPNN</b><br/>Designs amino acid sequences<br/>conditioned on backbone structure]
    end
    
    C -->|Outputs .pdb with sequences| D
    
    subgraph Phase 3: In Silico Validation
    D[<b>Rule 3: AlphaFold-Multimer</b><br/>Predicts complex structure &<br/>calculates pTM/ipTM scores]
    end
    
    D -->|Outputs validated complexes| E[✅ Final Ranked Designs<br/>Ready for Wet-Lab Synthesis]
    
    style A fill:#f9f,stroke:#333,stroke-width:2px
    style E fill:#bbf,stroke:#333,stroke-width:2px
    style B fill:#f96,stroke:#333,stroke-width:1px,color:#fff
    style C fill:#33cc33,stroke:#333,stroke-width:1px,color:#fff
    style D fill:#3399ff,stroke:#333,stroke-width:1px,color:#fff