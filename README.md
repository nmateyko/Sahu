# Sahu
This repo contains scripts for processing and analyzing data from [Sahu et al. 2022](https://doi.org/10.1038/s41588-021-01009-4).

# Installing Snakemake on Sockeye

## Creating a Snakemake environment
To run the processing pipeline, you need a conda environment with Snakemake installed:

    conda create -c conda-forge -c bioconda -n snakemake snakemake
    conda activate snakemake

## Changing the Snakemake cache directory
Snakemake tries to save cache files to your home directory while running a job, but Sockeye jobs
can't write to your home directory. Create a cache directory in your scratch:

    cd /scratch/st-cdeboer-1/<your-name>
    mkdir .cache

Now you need to point Snakemake to this cache directory by defining XDG_CACHE_HOME in your .bashrc.
Open your .bashrc in vim:

    cd ~
    vim .bashrc

Add the following line to your .bashrc:

    export XDG_CACHE_HOME=/scratch/st-cdeboer-1/<your-name>/.cache/

# Running the Snakemake Workflow

From the workflow directory (e.g. enhancer_workflow), run the following:

    snakemake --profile config --use-conda --conda-frontend conda