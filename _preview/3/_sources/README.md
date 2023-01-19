<img src="thumbnail.png" alt="thumbnail" width="300"/>

# Kerchunk Cookbook

[![nightly-build](https://github.com/ProjectPythia/cookbook-template/actions/workflows/nightly-build.yaml/badge.svg)](https://github.com/ProjectPythia/cookbook-template/actions/workflows/nightly-build.yaml)
[![Binder](http://binder.mypythia.org/badge_logo.svg)](http://binder.mypythia.org/v2/gh/ProjectPythia/cookbook-template/main?labpath=notebooks)

This Project Pythia Cookbook covers using the [Kerchunk](https://fsspec.github.io/kerchunk/) library to access archival data formats as if they were ARCO (Alanysis-Ready-Cloud-Optimized) data.

## Motivation

The `Kerchunk` library allow you to access chunked and compressed data formats such as (NetCDF, GRIB2, TIFF & FITS), many which are the primary data formats for many data archives, as if they were in ARCO formats such as Zarr which allows you parallel, chunk specific access. Instead of creating a new copy of the dataset in the Zarr spec/format, `Kerchunk` reads through the data archive and extracts the byte range and compression information of each chunk, then writes that information to a .json file (For more details on how this process works please see this page on the [Kerchunk docs](https://fsspec.github.io/kerchunk/detail.html)).
These summary files can then be combined to generated a `Kerchunk` reference for that dataset, which can be read via Xarray.

## Authors

[Norland Raphael Hagen](@first-author).

Much of the content of this cookbook was inspired by Martin Durant, the creator of `Kerchunk` and the [Kerchunk documentation](https://fsspec.github.io/kerchunk/).

### Contributors

<a href="https://github.com/ProjectPythia/kerchunk-cookbook/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=ProjectPythia/kerchunk-cookbook" />
</a>

## Structure

This cookbook is broken up into two sections, Foundations and Example Notebooks.

### Section 1 Foundations

In the `Foundations` section we will demonstrate how to use `Kerchunk` to create datasets from single file sources, as well as to create multi-file datasets from collections of files.

### Section 2 Case Studies

The notebooks in the `Case Studies` section demonstrate how to use `Kerchunk` to create datasets for all the supported file formats. `Kerchunk` currently supports NetCDF/HDF, GRIB2, TIFF and FITS, but more file formats may be available in the future.

### Future Additions / Wishlist

This Pythia cookbook is a start, but there are many more details of `Kerchunk` that could be covered. If you have an idea of what to add or would like to contribute, please open up a PR or issue.

Some possible additions:

- Diving into the details: The nitty-gritty on how `Kerchunk` works.
- `Kerchunk` and `Dask`: How to use Dask to speed-up your `Kerchunk` dataset generation.
- `Kerchunk` and `Parquet`, what are the benefits of using parquet for reference file storage.
- Appending to a Kerchunk dataset: How to schedule processing of newly added data files and how to add them to a `Kerchunk` dataset.

## Running the Notebooks

You can either run the notebook using [Binder](https://mybinder.org/) or on your local machine.

### Running on Binder

The simplest way to interact with a Jupyter Notebook is through
[Binder](https://mybinder.org/), which enables the execution of a
[Jupyter Book](https://jupyterbook.org) in the cloud. The details of how this works are not
important for now. All you need to know is how to launch a Pythia
Cookbooks chapter via Binder. Simply navigate your mouse to
the top right corner of the book chapter you are viewing and click
on the rocket ship icon, (see figure below), and be sure to select
“launch Binder”. After a moment you should be presented with a
notebook that you can interact with. I.e. you’ll be able to execute
and even change the example programs. You’ll see that the code cells
have no output at first, until you execute them by pressing
{kbd}`Shift`\+{kbd}`Enter`. Complete details on how to interact with
a live Jupyter notebook are described in [Getting Started with
Jupyter](https://foundations.projectpythia.org/foundations/getting-started-jupyter.html).

### Running on Your Own Machine

If you are interested in running this material locally on your computer, you will need to follow this workflow:

1. Clone the `https://github.com/ProjectPythia/kerchunk-cookbook` repository:

   ```bash
    git clone https://github.com/ProjectPythia/kerchunk-cookbook.git
   ```

1. Move into the `kerchunk-cookbook` directory
   ```bash
   cd kerchunk-cookbook
   ```
1. Create and activate your conda environment from the `environment.yml` file
   ```bash
   conda env create -f environment.yml
   conda activate kerchunk-cookbook
   ```
1. Move into the `notebooks` directory and start up Jupyterlab
   ```bash
   cd notebooks/
   jupyter lab
   ```
