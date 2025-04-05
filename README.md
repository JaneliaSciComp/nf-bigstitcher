# nf-bigstitcher

[![GitHub Actions CI Status](https://github.com/JaneliaSciComp/nf-bigstitcher/actions/workflows/ci.yml/badge.svg)](https://github.com/JaneliaSciComp/nf-bigstitcher/actions/workflows/ci.yml)
[![GitHub Actions Linting Status](https://github.com/JaneliaSciComp/nf-bigstitcher/actions/workflows/linting.yml/badge.svg)](https://github.com/JaneliaSciComp/nf-bigstitcher/actions/workflows/linting.yml)[![AWS CI](https://img.shields.io/badge/CI%20tests-full%20size-FF9900?labelColor=000000&logo=Amazon%20AWS)](https://nf-co.re/bigstitcher/results)[![Cite with Zenodo](http://img.shields.io/badge/DOI-10.5281/zenodo.XXXXXXX-1073c8?labelColor=000000)](https://doi.org/10.5281/zenodo.XXXXXXX)
[![nf-test](https://img.shields.io/badge/unit_tests-nf--test-337ab7.svg)](https://www.nf-test.com)

[![Nextflow](https://img.shields.io/badge/nextflow%20DSL2-%E2%89%A524.04.2-23aa62.svg)](https://www.nextflow.io/)
[![run with conda](http://img.shields.io/badge/run%20with-conda-3EB049?labelColor=000000&logo=anaconda)](https://docs.conda.io/en/latest/)
[![run with docker](https://img.shields.io/badge/run%20with-docker-0db7ed?labelColor=000000&logo=docker)](https://www.docker.com/)
[![run with singularity](https://img.shields.io/badge/run%20with-singularity-1d355c.svg?labelColor=000000)](https://sylabs.io/docs/)


## Introduction

**JaneliaSciComp/nf-bigstitcher** is a Nextflow pipeline that allows you to run individual [BigStitcher-Spark](https://github.com/JaneliaSciComp/BigStitcher-Spark) modules. This means you can run the compute-intensive parts of [BigStitcher](https://imagej.net/plugins/bigstitcher/) on any compute infrastructure supported by Nextflow ([SGE, SLURM, AWS, etc.](https://www.nextflow.io/docs/latest/executor.html)). The pipeline starts up an Apache Spark cluster, runs the selected BigStitcher step, and then shuts down Spark. 


## Usage

> [!NOTE]
> If you are new to Nextflow and nf-core, please refer to [this page](https://nf-co.re/docs/usage/installation) on how to set-up Nextflow. Make sure to [test your setup](https://nf-co.re/docs/usage/introduction#how-to-run-a-pipeline) with `-profile test` before running the workflow on actual data.

Review the current [nf-core configs](https://nf-co.re/configs/) to see if your compute environment is already supported by nf-core. If so, you can specify the config using `-profile` when running the pipeline. If not, you may need to create a profile for your compute infrastructure.

To run the "resave" module:

```bash
nextflow run JaneliaSciComp/nf-bigstitcher \
   -profile <docker/singularity/.../institute> \
   --module resave \
   --xml /path/to/your/bigstitcher/project.xml \
   --outdir /path/to/your/output.zarr
```

> [!WARNING]
> Please provide pipeline parameters via the CLI or Nextflow `-params-file` option. Custom config files including those provided by the `-c` Nextflow option can be used to provide any configuration _**except for parameters**_; see [docs](https://nf-co.re/docs/usage/getting_started/configuration#custom-configuration-files).

For more details and further functionality, please refer to the [usage documentation](https://nf-co.re/bigstitcher/usage) and the [parameter documentation](https://nf-co.re/bigstitcher/parameters).

## Pipeline output

To see the results of an example test run with a full size dataset refer to the [results](https://nf-co.re/bigstitcher/results) tab on the nf-core website pipeline page.
For more details about the output files and reports, please refer to the
[output documentation](https://nf-co.re/bigstitcher/output).

## Credits

JaneliaSciComp/nf-bigstitcher was developed by Cristian Goina, Konrad Rokicki, and Stephan Preibisch (the author of BigStitcher). 

## Contributions and Support

If you would like to contribute to this pipeline, please see the [contributing guidelines](.github/CONTRIBUTING.md).

## Citations

If you use BigStitcher for your analysis, please cite it using the following DOI: [10.1038/s41592-019-0501-0](https://doi.org/10.1038/s41592-019-0501-0)

An extensive list of references for the tools used by the pipeline can be found in the [`CITATIONS.md`](CITATIONS.md) file.
