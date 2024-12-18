# CZII---CryoET-Object-Identification
Find small biological structures in large 3D volumes

3D Particle Detection in Tomograms

Dataset Description

This competition focuses on identifying points corresponding to particle centers in 3D tomograms. For testing, participants will process a list of 3D arrays called "experiments" and submit a CSV file containing particle locations for 5 particle types in all experiments.

The dataset includes 6 particle types, each with varying levels of prediction difficulty:

apo-ferritin (easy)

beta-amylase (impossible, not scored)

beta-galactosidase (hard)

ribosome (easy)

thyroglobulin (hard)

virus-like-particle (easy)

Note: The beta-amylase particle type is not scored as it is considered too difficult for accurate evaluation. Predictions for this particle type do not affect the final score.

File Information

Training Data

Path: train/static/ExperimentRuns/{experiment}/VoxelSpacing10.000/

denoised.zarr/: Zarr files containing tomograph data.

{3 other data filtered options}: Filtered options not included in the test dataset.

Ground Truth Data: overlay/ExperimentRuns/{experiment}/Picks/

{particle_type}.json: JSON files containing ground truth particle coordinates.

Test Data

Path: test/static/ExperimentRuns/{experiment}/VoxelSpacing10.000/

denoised.zarr/: Zarr files containing tomograph data.

Sample Submission: sample_submission.csv

A sample submission file in the correct format.

Note: The test dataset available for download is an example dataset copied from the training data. The actual rerun test dataset contains approximately 500 tomographs.

Tomograms

Tomograms are provided as multiscale 3D OME-NGFF Zarr arrays. These can be opened using libraries such as zarr, ome-zarr, and copick.

Training Tomogram Types

The training data includes four filtered versions of the tomograms. Only the denoised option is included in the test data.

denoised (included in test data)

wbp (weighted back projection)

ctfdeconvolved

isonetcorrected

These zarr files are available in the competition directory. Details about their methods can be found in the preprint mentioned in the pinned welcome post.

Note: These are multiscale zarr arrays, with level 0 corresponding to the highest resolution.

Particle Locations

Particle locations are stored in JSON files following the copick specification. These files provide:

Particle coordinates.

Utility functions (e.g., converting points into segmentation masks).

Using copick

If you intend to use copick:

Access tomograms and particle locations.

Convert points into segmentation masks.

Use the example notebooks for guidance on accessing tomograms and creating valid predictions.
