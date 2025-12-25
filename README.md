# actin_toxin_docking
![Reidispongiolide_A_6MGO](https://github.com/user-attachments/assets/3734491e-c9ea-44fa-bf01-aa51569917c8)

## Project Goals

Build and evaluate an end-to-end docking and analysis pipeline for actin-targeting toxins across different receptor conformational states.
Assess docking plausibility using steric clash metrics, protein–ligand contact recovery, and ligand physicochemical features, and explore their utility for predicting ligand potency via logistic regression.
Benchmark docking results against crystallographic G-actin–ligand complexes, using RMSD and interaction-based metrics to understand the limitations of rigid docking for large, flexible ligands.

## Pipeline Summary

### Ligand preparation
Natural barbed-end binding toxins and tail-only analogs were prepared using RDKit and Open Babel.
### Receptor preparation
Multiple actin receptor states were used, including G-actin monomers (crystal ground truth) and F-actin Cryo-EM–derived conformations (e.g., AMPPNP-bound).
### Docking
Docking was performed with AutoDock Vina using a barbed-end cleft–centred search box.
### Pose evaluation
Whole-ligand and tail-only RMSD vs crystal ground truth
Protein–ligand contact counts within 4 Å
Steric clashes with neighbouring F-actin protomers
### Potency modelling
Ligand descriptors and clash metrics were combined in a simple logistic regression model to explore structure–potency relationships.

## Key Findings

### Docking consistently identifies the barbed-end cleft for known barbed-end toxins, while negative controls bind nonspecifically.
### Whole-ligand RMSD remains high (≈8–12 Å) for large macrolides, reflecting limitations of rigid docking and macrocycle flexibility rather than complete pose failure.
### Receptor conformation strongly affects pose families:
docking into G-actin monomers recovers tail–pocket contact patterns closer to crystal ground truth than docking into F-actin–like conformations, even when RMSD values are similar.
Contact-based and clash-based metrics provide more discriminative insight than RMSD alone for evaluating docking plausibility in this system.
### A simple logistic regression model using ligand features and clash metrics achieved reasonable performance given the small dataset, suggesting steric compatibility with the polymerization interface contributes to potency.

## Limitations

Rigid-receptor docking does not capture induced fit, actin loop rearrangements, or polymerization dynamics.
RMSD is a blunt metric for large, flexible ligands and should be interpreted alongside interaction-based measures.
The dataset size limits statistical power for potency prediction.

## Takeaway
This project demonstrates how receptor state, ligand flexibility, and evaluation metrics jointly shape docking outcomes in a biologically complex system, and highlights why interaction-based analyses are essential complements to RMSD when modelling large, flexible ligands.

📄 A detailed analysis and full results are provided as a PDF in the results/ directory.

