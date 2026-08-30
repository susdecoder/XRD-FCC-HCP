# XRD-FCC-HCP

Reproducibility code and datasets for FCC/HCP phase classification using a minimal, physics-informed XRD feature representation.

## Overview

This repository contains the computational materials associated with the AI4Mat 2026 workshop submission on automated XRD phase characterization.

The study investigates whether two XRD-derived features, `(d1/d2)^2` and `I2/I1`, can distinguish FCC and HCP phases when classifiers are trained on synthetic diffraction data and evaluated on chemically more complex synthetic structures and experimentally measured HEA XRD patterns.

## Data

Three datasets are used in the study:

- **Synthetic training set:** 120 FCC/HCP patterns generated from Materials Project structures.
- **Chemically diverse synthetic stress test:** 54 Materials Project structures containing 4–6 elements.
- **Experimental HEA test set:** 17 independently measured experimental XRD patterns obtained from published sources.

The experimental patterns are used only for independent evaluation and are not used to train or modify the classifiers.

## Models

The study evaluates three classical classifiers:

- Linear SVM
- RBF-kernel SVM
- Cosine-kernel SVM

A separate quantum-kernel SVM implementation using a two-qubit PennyLane simulation is also included. The quantum kernel is evaluated through classical simulation; no quantum hardware execution or quantum computational advantage is claimed.

## Computational Notebooks

The notebooks in this repository represent the initial/base implementations developed during the study.

Subsequent analyses involved modifications to the implementation and datasets used in the study, including removal of an earlier constraint involving `d2^2/d1^2`.

The notebooks are therefore provided as documentation of the computational development and analysis workflow rather than as three independent final implementations of the paper.

## Feature-Space Selection Diagnostic

An earlier analysis applied the restriction:

`(d1/d2)^2 <= 2.0`

This restricted analysis produced 100% accuracy on the 17 experimental patterns.

Subsequent auditing showed that the restriction removed 35 of the 120 synthetic samples:

- 29 of 60 FCC samples (48.3%)
- 6 of 60 HCP samples (10.0%)

The complete-data analysis was subsequently used for the principal results, providing a more conservative assessment of sensitivity to feature-space selection.

## Reproducibility

The computational workflow was developed and evaluated using Python and Google Colab.

The notebooks and associated datasets are provided to document the feature construction, classification analyses, and diagnostic experiments reported in the study.

## Scope

The reported results should be interpreted within the limitations described in the accompanying paper, particularly the limited experimental dataset and the distribution difference between synthetic training data and experimental HEA measurements.
