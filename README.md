# Two-photon imaging and looming behavior analysis

MATLAB pipelines I wrote for my Ph.D. work in the Kerschensteiner Lab at Washington University in St. Louis. They process two-photon recordings of single-neuron dendrites and analyze mouse escape behavior to looming stimuli.

These are the imaging and behavior analysis code for:

> C.-I. Lin, A. Jo, P. Ramakrishna, X. Song, J. L. Morgan, and D. Kerschensteiner. *Inhibition confines dendritic integration to set behavior-specific sensory gain.* Under review (2026).

The code is also published with the study's full code release in [kerschensteinerd/Lin2026_gamma2-escape](https://github.com/kerschensteinerd/Lin2026_gamma2-escape), which additionally contains the compartmental model.

## Contents

| Folder | What it does | Details |
| --- | --- | --- |
| [`two_photon_imaging/`](two_photon_imaging/README.md) | Channel deinterleaving, translation-based motion correction, ROI preparation, interactive tdTomato-guided dendrite segmentation, stimulus-marker timing, and spot-size response analysis | [Inputs and execution order](two_photon_imaging/README.md) |
| [`behavior/`](behavior/README.md) | Speed heatmaps, reaction times, maximum speeds, and threshold-based escape probabilities from mouse speed traces | [Input format and analysis](behavior/README.md) |

## Two-photon imaging pipeline

Run the scripts in this order. Each step writes MAT files that the next step reads.

1. `deinterleave_channels` splits page-interleaved TIFF recordings into GCaMP, tdTomato, transmitted-light, and stimulus-marker channels.
2. `register_channels` estimates frame-by-frame translation on a reference channel and applies it to every channel.
3. `prepare_roi_projections` crops and builds projection images for segmentation.
4. `segment_tdtomato_dendrites` selects active dendritic pixels with an interactive threshold tool (`thresholdGUI`).
5. `extract_stimulus_timing` finds stimulus onsets from the marker channel.
6. `analyze_spot_size_responses` extracts and averages responses for each stimulus size.

## Requirements

- Imaging: MATLAB R2022b or later, Image Processing Toolbox, Signal Processing Toolbox, and a desktop session for interactive steps.
- Behavior: MATLAB R2018b or later, no extra toolboxes.

Experimental recordings and speed data are not included. Each folder README lists the exact inputs, settings, and outputs.

## Author

Chin-I Lin · [cilin6268.github.io](https://cilin6268.github.io) · [LinkedIn](https://www.linkedin.com/in/chin-i-lin)
