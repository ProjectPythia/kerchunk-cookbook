<img src="thumbnail.png" alt="thumbnail" width="300"/>

# Kerchunk Cookbook

[![nightly-build](https://github.com/ProjectPythia/kerchunk-cookbook/actions/workflows/nightly-build.yaml/badge.svg)](https://github.com/ProjectPythia/kerchunk-cookbook/actions/workflows/nightly-build.yaml)
[![Binder](https://binder.projectpythia.org/badge_logo.svg)](https://binder.projectpythia.org/v2/gh/ProjectPythia/kerchunk-cookbook/main?labpath=notebooks)
[![DOI](https://zenodo.org/badge/588661659.svg)](https://zenodo.org/badge/latestdoi/588661659)

This Project Pythia Cookbook covers using the [Kerchunk](https://fsspec.github.io/kerchunk/)
library to access archival data formats as if they were
ARCO (Analysis-Ready-Cloud-Optimized) data.

## Motivation

The `Kerchunk` library allows you to access chunked and compressed
data formats (such as NetCDF3. HDF5, GRIB2, TIFF & FITS), many of
which are the primary data formats for many data archives, as if
they were in ARCO formats such as Zarr which allows for parallel,
chunk-specific access. Instead of creating a new copy of the dataset
in the Zarr spec/format, `Kerchunk` reads through the data archive
and extracts the byte range and compression information of each
chunk, then writes that information to a .json file (or alternate
backends in future releases). For more details on how this process
works please see this page on the
[Kerchunk docs](https://fsspec.github.io/kerchunk/detail.html)).
These summary files can then be combined to generated a `Kerchunk`
reference for that dataset, which can be read via
[Zarr](https://zarr.readthedocs.io) and
[Xarray](https://docs.xarray.dev/en/stable/).

## Authors

[Raphael Hagen](https://github.com/norlandrhagen)

Much of the content of this cookbook was inspired by
[Martin Durant](https://github.com/martindurant),
the creator of `Kerchunk` and the
[Kerchunk documentation](https://fsspec.github.io/kerchunk/).

### Contributors

<a href="https://github.com/ProjectPythia/kerchunk-cookbook/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=ProjectPythia/kerchunk-cookbook" />
</a>

## Structure

This cookbook is broken up into two sections,
Foundations and Example Notebooks.

### Section 1 Foundations

In the `Foundations` section we will demonstrate
how to use `Kerchunk` to create reference sets
from single file sources, as well as to create
multi-file virtual datasets from collections of files.

### Section 2 Generating Reference Files

The notebooks in the `Generating Reference Files` section
demonstrate how to use `Kerchunk` to create
datasets for all the supported file formats.
`Kerchunk` currently supports NetCDF3,
NetCDF4/HDF5, GRIB2, TIFF (including CoG).

### Section 3 Using Pre-Generated References

The `Pre-Generated References` section contains notebooks demonstrating how to load existing references into `Xarray` and `Xarray-Datatree`, generated coordinates for GeoTiffs using `xrefcoord` and plotting using `Hvplot Datashader`.

## Running the Notebooks

You can either run the notebook using [![Binder](https://binder.projectpythia.org/badge_logo.svg)](https://binder.projectpythia.org/v2/gh/ProjectPythia/kerchunk-cookbook/main?labpath=notebooks)
or on your local machine.

### Running on Binder

The simplest way to interact with a Jupyter Notebook is through
[Binder](https://binder.projectpythia.org), which enables the execution of a
[Jupyter Book](https://jupyterbook.org) in the cloud. The details of how this works are not
important for now. All you need to know is how to launch a Pythia
Cookbooks chapter via Binder. Simply navigate your mouse to
the top right corner of the book chapter you are viewing and click
on the rocket ship icon and be sure to select
“launch Binder”. After a moment you should be presented with a
notebook that you can interact with. You’ll be able to execute
and even change the example programs. The code cells
have no output at first, until you execute them by pressing
{kbd}`Shift`\+{kbd}`Enter`. Complete details on how to interact with
a live Jupyter notebook are described in [Getting Started with
Jupyter](https://foundations.projectpythia.org/foundations/getting-started-jupyter.html).

### Running on Your Own Machine

If you are interested in running this material locally on your computer,
you will need to follow this workflow:

1. Install [mambaforge/mamba](https://mamba.readthedocs.io/en/latest/installation.html)

1. Clone the `https://github.com/ProjectPythia/kerchunk-cookbook` repository:

   ```bash
    git clone https://github.com/ProjectPythia/kerchunk-cookbook.git
   ```

1. Move into the `kerchunk-cookbook` directory
   ```bash
   cd kerchunk-cookbook
   ```
1. Create and activate your conda environment from the `environment.yml` file.
   Note: In the `environment.yml` file, Kerchunk` is currently being installed from source as development is happening rapidly.

   ```bash
   mamba env create -f environment.yml
   mamba activate kerchunk-cookbook
   ```

1. Move into the `notebooks` directory and start up Jupyterlab
   ```bash
   cd notebooks/
   jupyter lab
   ```
