#  De Novo Binder Design Pipeline (RFdiffusion → ProteinMPNN → AF2)

## 📌 Overview
A fully reproducible, containerized Snakemake pipeline for designing de novo miniprotein binders. This workflow automates the generation, sequence design, and structural validation of protein binders targeting specific protein-protein interfaces (e.g., GPCRs, immune checkpoints). 

*Designed to streamline the workflow described in Lee et al., Nature 2026 (Miniproteins targeting GPCRs) and Jumper et al., Nature Methods 2023 (LigandMPNN).*

## 🏗️ Pipeline Architecture
1. **Target Input:** User provides a target PDB structure (e.g., a GPCR).
2. **RFdiffusion:** Generates novel backbone scaffolds targeting a specific binding hotspot (defined by a contig map).
3. **ProteinMPNN:** Designs optimal amino acid sequences for the generated backbones, conditioned on the target structure.
4. **AlphaFold-Multimer:** Validates the physical binding affinity and structural confidence (pLDDT/pTM) of the designed binder against the target.

## 🚀 Quick Start

### Prerequisites
- Docker or Singularity (for containerization)
- Conda/Mamba

### Installation