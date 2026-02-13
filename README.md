# Child-Brainnetome-Atlas
CHILD_BN atlas for preadolescent children 
(NIfTI + GIFTI label.gii; fsaverage 10k, fsLR 32k/164k)
README.txt
==========

Child Brainnetome (CHILD_BN) Atlas Release
-----------------------------------------
This folder contains the released volumetric and surface versions of the CHILD_BN atlas for preadolescent children, including
label lookup tables, NIfTI volumes in template/MNI space, and GIFTI surface label files in common surface coordinate systems.

If you use any file from this release, you must cite:
  "Brainnetome atlas of preadolescent children based on anatomical connectivity profiles"
(and any accompanying paper or resource description provided with the atlas release).


Directory Overview
------------------

1) CHILD_ATLAS_LUT.txt
   - Lookup table (LUT) for atlas labels and colors.
   - Format: two-line entries (label name; then "key R G B A" with 0–255 RGBA).

2) freesurfer/
   - FreeSurfer-formatted distribution and working structure.
   - Subfolders may include:
     label/   mri/   scripts/   stats/   surf/   tmp/   touch/   trash/
   - Intended for users who want to integrate the atlas into FreeSurfer workflows.

3) nifti/
   Volumetric atlas and tissue maps:
   - CHILD_ATLAS_224.nii.gz
       Volumetric parcellation (atlas) at 224-label granularity.
   - CHILD_ATLAS_template.nii.gz
       Volumetric atlas in the provided child template space.
   - childbrain_template_1mm.nii.gz
       1 mm isotropic child brain template.
   - childbrain_gm_1mm.nii.gz
       Gray matter tissue probability/segmentation volume (1 mm).
   - childbrain_wm_1mm.nii.gz
       White matter tissue probability/segmentation volume (1 mm).
   - childbrain_csf_1mm.nii.gz
       CSF tissue probability/segmentation volume (1 mm).
   - childbrain_pdw_1mm.nii.gz
       PD-weighted (or PD-like) reference volume in the same 1 mm template space.

4) Surface/
   Surface atlas files and processing helpers.

   Surface label GIFTI files (left/right hemispheres):
   - MNI.L.CHILD_BN_Atlas.10k.label.gii
   - MNI.R.CHILD_BN_Atlas.10k.label.gii
       Surface space: fsaverage (10k density).

   - MNI.L.CHILD_BN_Atlas.32k.label.gii
   - MNI.R.CHILD_BN_Atlas.32k.label.gii
       Surface space: fsLR (32k density).

   - MNI.L.CHILD_BN_Atlas.164k.label.gii
   - MNI.R.CHILD_BN_Atlas.164k.label.gii
       Surface space: fsLR (164k density).

   Additional contents:
   - sphere/
       Spherical registration surfaces used for resampling between densities/spaces.
   - surf/
       Reference surfaces (e.g., sphere, midthickness) for visualization and/or resampling.
   - shape/
       Auxiliary metric/shape files used during processing (intermediate or optional).
   - process.sh
       Example/utility script used to generate or convert surface atlas files.
   - read.txt
       Notes and provenance for the surface processing pipeline.


Recommended Usage Notes
-----------------------

A) Choosing a surface version
   - Use 10k (fsaverage) for lightweight visualization or workflows already in fsaverage space.
   - Use 32k (fsLR) for standard HCP-style surface analyses in CIFTI/fsLR space.
   - Use 164k (fsLR) for high-resolution surface analyses and precise boundary visualization.

B) Color table / label table consistency
   - Surface label files are distributed as .label.gii with embedded label tables.
   - CHILD_ATLAS_LUT.txt is provided as the canonical LUT for consistent label names and RGBA colors across tools.

C) Citation requirement
   - Any use (analysis, figures, redistribution of derivatives) must cite:
       "Brainnetome atlas of preadolescent children based on anatomical connectivity profiles"


Contact / Issues
----------------
For questions, bug reports, or requests for additional formats, please contact the atlas maintainers at liwen2016@ia.ac.cn.
