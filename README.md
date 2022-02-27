## Overview
[![Conda Build and Publish](https://github.com/mfansler/envvar-pythonnousersite-true/actions/workflows/conda-build.yml/badge.svg)](https://github.com/mfansler/envvar-pythonnousersite-true/actions/workflows/conda-build.yml)
[![Anaconda Cloud version](https://anaconda.org/merv/envvar-pythonnousersite-true/badges/version.svg)](https://anaconda.org/merv/envvar-pythonnousersite-true)
[![platforms](https://anaconda.org/merv/envvar-pythonnousersite-true/badges/platforms.svg)](https://anaconda.org/merv/envvar-pythonnousersite-true)
[![downloads](https://anaconda.org/merv/envvar-pythonnousersite-true/badges/downloads.svg)](https://anaconda.org/merv/envvar-pythonnousersite-true)
[![updated](https://anaconda.org/merv/envvar-pythonnousersite-true/badges/latest_release_date.svg)](https://anaconda.org/merv/envvar-pythonnousersite-true)

This Conda package uses activation/deactivation scripts to set the environment variable 
`PYTHONNOUSERSITE=1` when activating a Conda environment, effectively insulating
the Conda environment from Python packages installed at user-level.

## Installation
The package is hosted on Anaconda Cloud. It can be installed with

```bash
conda install merv::envvar-pythonnousersite-true
```

Users wishing to have `PYTHONNOUSERSITE=1` set for all environments by default can use

```bash
conda config --add create_default_packages merv::envvar-pythonnousersite-true
```

which will include this package automatically in all future environments at environment creation.

## Reuse and Repurposing
This package is a proof-of-concept to demonstrate managing environment variables
in Conda environments through the "unit of computation" of Conda, which is the 
Conda package. It is released under a CC0 license (i.e., public domain). Feel free 
to use this repository as an outline for similar packages.

The environment variables are set/unset in the `recipe/[de]activate.{bat,sh}` files. 
While there is not a standing convention for packages managing environment variables,
this uses the template `envvar-<variable_name>-<value>`.

The repository includes a GitHub Workflow that builds and uploads the package to 
Anaconda Cloud. For the uploading portion to work, users should adjust the 
`ANACONDA_USER` variable in the [`conda-build.yml` workflow file](https://github.com/mfansler/envvar-pythonnousersite-true/blob/main/.github/workflows/conda-build.yml)
and need to set an `ANACONDA_TOKEN` [repository secret](https://docs.github.com/en/actions/security-guides/encrypted-secrets#creating-encrypted-secrets-for-a-repository) corresponding to [an access token](https://docs.anaconda.com/anacondaorg/user-guide/tasks/work-with-accounts/#creating-access-tokens) 
for their Anaconda Cloud account with the **"Allow all API operations"** permission.
