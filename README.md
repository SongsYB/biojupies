# BioJupies
Automated generation of Jupyter Notebooks for RNA-seq data analysis via user interface.

### Overview
1. [What is BioJupies?](#what-is-biojupies)
2. [How can I generate notebooks using BioJupies?](#how-can-i-generate-a-notebook-using-biojupies)
3. [How can I upload my own RNA-seq data to BioJupies?](#how-can-i-upload-my-rna-seq-data-to-biojupies)
4. [What analyses can BioJupies perform?](#what-analyses-can-biojupies-perform)
5. [Can I contribute my RNA-seq analysis tools?](#can-i-contribute-my-rna-seq-analysis-tools)
6. [How can I download and rerun my notebooks?](#how-can-i-download-and-rerun-my-notebooks)
7. [References](#references)

## What is BioJupies?
BioJupies is a web server which allows users to automatically generate Jupyter Notebooks from RNA-seq datasets through an intuitive interface, with no knowledge of coding required. The BioJupies can be accessed for free from http://biojupies.cloud.
![Screenshot of the BioJupies website landing page.](img/website.png)

## How can I generate a notebook using BioJupies?

Generating a notebook using BioJupies requires three steps:

![Screenshot of the BioJupies website landing page.](img/workflow.png)

1. First, **select an RNA-seq dataset** you with to analyze. You can upload FASTQ files, gene expression tables, or use a search engine to browse over 6,000 public datasets published in the [Gene Expression Omnibus](https://www.ncbi.nlm.nih.gov/geo/) and processed by [ARCHS4](https://amp.pharm.mssm.edu/archs4/).
2. Second, **add one or more computational tools** to analyze the data. BioJupies currently supports 14 plugins to perform exploratory data analysis, differential gene expression, enrichment analysis, and small molecule queries.
3. Third, **generate the notebook** with the desired settings. The notebook will be served to you through a URL, and can be easily downloaded and rerun on your local computer.

## How can I upload my RNA-seq data to BioJupies?
Users can upload their RNA-seq datasets for analysis at https://amp.pharm.mssm.edu/biojupies/upload. BioJupies currently supports uploading **RNA-seq datasets in the FASTQ format** or **tables of gene-level counts**.

![Screenshot of the BioJupies upload page.](img/upload.png)

**Note**: While the user may successfully generate a notebook from normalized gene expression counts or microarray data tables, the tools are **NOT** yet optimized to handle such data. Such results should be interpreted with caution.

The Enrichment Analysis and Small Molecule Query plugins currently support datasets uploaded with **gene symbols** as row identifiers. When uploading datasets with different identifiers (e.g. ENSEMBL IDs, Entrez IDs), please note that these plugins may return empty results.

## What analyses can BioJupies perform?
BioJupies currently provides **14 RNA-seq data analysis plugins**, divided 
into four categories.

For more information about the plugins and access to the source code, visit https://github.com/MaayanLab/biojupies-plugins.

![Screenshot of the BioJupies upload page.](img/tools.png)

## Can I contribute my RNA-seq analysis tools?
Developers are welcome to contribute their own RNA-seq data analysis plugins for integration in BioJupies.

Once integrated, the plugin will be made available to all users of BioJupies for generation of notebooks. Source code for all plugins is available at https://github.com/MaayanLab/biojupies-plugins.

To contribute your plug-in, please visit https://amp.pharm.mssm.edu/biojupies/contribute.

## How can I download and rerun my notebooks?
After generating a BioJupies notebook, users can download, execute and customize it locally using the `maayanlab/biojupies-notebooks` Docker container.

To achieve this, the following steps are required:
1. Pull the latest version of the Docker container from the console by running:

``` bash 
docker pull maayanlab/biojupies-notebooks
```

2. Identify the notebook's unique ID (a 9-character alphanumeric string) from its URL - e.g. `5DAHiejHN`.

![Screenshot of the a BioJupies notebook UID.](img/notebook_uid.png)

3. Launch the Docker container. **Note:** replace `5DAHiejHN` with the UID of the notebook you wish to rerun.

``` bash 
docker run -it -p 8888:8888 -e NOTEBOOK_UID=5DAHiejHN maayanlab/biojupies-notebooks
```

4. Access the local Jupyter Notebook server from your browser at port 8888.

![Screenshot of the a local Jupyter Server.](img/local_server.png)

5. Rerun the analysis and customize it by adding your code.

![Screenshot of the a local Jupyter Server.](img/local_notebook.png)

For more information about reusing notebooks, see https://amp.pharm.mssm.edu/biojupies/docker.

## References
BioJupies is currently published as a pre-print on **BioRxiv**:
[BioJupies: Automated Generation of Interactive Notebooks for RNA-seq Data Analysis in the Cloud](https://doi.org/10.1101/352476) Torre, D., Lachmann, A., and Ma’ayan, A. (2018)

## License
This project is licensed under the Apache-2.0 License - see the [LICENSE.md](LICENSE.md) file for details