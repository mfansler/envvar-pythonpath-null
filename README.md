## Overview
[![Conda Build and Publish](https://github.com/mfansler/envvar-pythonpath-null/actions/workflows/conda-build.yml/badge.svg)](https://github.com/mfansler/envvar-pythonpath-null/actions/workflows/conda-build.yml)
[![Anaconda Cloud version](https://anaconda.org/merv/envvar-pythonpath-null/badges/version.svg)](https://anaconda.org/merv/envvar-pythonpath-null)
[![platforms](https://anaconda.org/merv/envvar-pythonpath-null/badges/platforms.svg)](https://anaconda.org/merv/envvar-pythonpath-null)
[![downloads](https://anaconda.org/merv/envvar-pythonpath-null/badges/downloads.svg)](https://anaconda.org/merv/envvar-pythonpath-null)
[![updated](https://anaconda.org/merv/envvar-pythonpath-null/badges/latest_release_date.svg)](https://anaconda.org/merv/envvar-pythonpath-null)

This Conda package uses activation/deactivation scripts to set the environment variable 
`PYTHONPATH=""` when activating a Conda environment, effectively insulating
the Conda environment from Python modules provided by this variable.

## Installation
The package is hosted on Anaconda Cloud. It can be installed with

```bash
conda install merv::envvar-pythonpath-null
```

Users wishing to have `PYTHONPATH=""` set for all environments by default can use

```bash
conda config --add create_default_packages merv::envvar-pythonpath-null
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
`ANACONDA_USER` variable in the [`conda-build.yml` workflow file](https://github.com/mfansler/envvar-pythonpath-null/blob/main/.github/workflows/conda-build.yml)
and need to set an `ANACONDA_TOKEN` [repository secret](https://docs.github.com/en/actions/security-guides/encrypted-secrets#creating-encrypted-secrets-for-a-repository) corresponding to [an access token](https://docs.anaconda.com/anacondaorg/user-guide/tasks/work-with-accounts/#creating-access-tokens) 
for their Anaconda Cloud account with the **"Allow all API operations"** permission.
