# CHILD_BN Atlas (Preadolescent Children)

This repository provides the **CHILD_BN atlas** for preadolescent children, including:
- Volumetric parcellations and template/tissue maps (**NIfTI**)
- Surface parcellations (**GIFTI label.gii**) in common surface spaces/densities
- A canonical label lookup table (**LUT**) for label names and RGBA colors
- Optional helper scripts and reference surfaces/spheres for resampling

> **Citation requirement**  
> If you use any file from this release (volumetric or surface), you must cite:  
> **“Li, W., Fan, L., Shi, W., Lu, Y., Li, J., Luo, N., ... & Jiang, T. (2023). Brainnetome atlas of preadolescent children based on anatomical connectivity profiles. _Cerebral Cortex_, _33_(9), 5264-5275.”**  


---

## Label LUT

### `CHILD_BN_Atlas_LUT.txt`
Canonical mapping between label key and (name, RGBA color).
- Two-line entries:
  1) label name
  2) `key R G B A` (0–255)

Surface `.label.gii` files already contain embedded label tables, but this LUT is provided as the canonical reference for consistent naming/colors across tools.

---

## Volumetric files (NIfTI) — `nifti/`

- `CHILD_BN_Atlas_nparc224.nii.gz`
  Volumetric parcellation with **224 parcels** (please see Brain_Atlas_Ontology_Nomenclature_Abbreviations.docx for the ontology, nomenclature, and abbreviations of brain areas in the Child Brainnetome Atlas.).

- `childbrain_template_1mm.nii.gz`
  1 mm isotropic child brain template

  
- `CHILD_ATLAS_template.nii.gz`  
  2 mm isotropic child brain template.

- `childbrain_gm_1mm.nii.gz`, `childbrain_wm_1mm.nii.gz`, `childbrain_csf_1mm.nii.gz`  
  Tissue probability/segmentation maps (GM/WM/CSF) aligned to `childbrain_template_1mm`.

- `childbrain_pdw_1mm.nii.gz`  
  PD-weighted (or PD-like) reference image in the same 1 mm template space.

---

## Surface files (GIFTI) — `surface/`

### Surface spaces and densities
- **fsaverage, den-10k**: lightweight surface representation for visualization / fsaverage-style workflows
- **fsLR, den-32k**: standard HCP-style surface for CIFTI/fsLR analyses
- **fsLR, den-164k**: high-resolution fsLR surface for detailed boundaries/visualization

### Surface parcellations
Each hemisphere is provided separately:
- Left hemisphere: `...L...`
- Right hemisphere: `...R...`

Main deliverables:
- `fsaverage.{L,R}.CHILD_BN_Atlas.den-10k.label.gii`
- `fsLR.{L,R}.CHILD_BN_Atlas.den-32k.label.gii`
- `fsLR.{L,R}.CHILD_BN_Atlas.den-164k.label.gii`

Auxiliary/intermediate:
- `surface/shape/`  
  Metric/shape files used during generation and/or optional processing steps.
- `surface/sphere/`  
  Spherical registration surfaces for resampling between densities/spaces.
- `surface/surf/`  
  Reference surfaces (e.g., white/midthickness) for visualization/resampling.

---

## Quick start

### 1) Visualize in Connectome Workbench
```bash
wb_view surface/fsLR.L.CHILD_BN_Atlas.den-32k.label.gii
