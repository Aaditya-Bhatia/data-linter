# Data Linter

This is a fork of google brain's data linter [project](https://github.com/brain-research/data-linter), which was created by Nick Hynes (nhynes@berkeley.edu) during an
internship at Google, but is currently an archived project.

Its an amazing tool, which I have put into the lazarus pit and have revived it. However, this reviving has been a painful process (no documentation, conflicting dependencies, etc.), and I have made the demo work (and am using it for statistically cleaning some other files). However, maintenance is far from ideal and I would love to take PRs and hope y'all can help maintain this awesome project!

Its built on python2.7 and some other data pre-processing is built on python3.+ which would obviously drive anyone crazy. 
- I found non-conflicting dependecies and pinned them into 2 requirements.txt files. 
- Made the demo working, along with the corresponding data files in the `demo` folder.
- Extracted relevant code from super old dependencies and removed them in requirements.txt (eg. incompatible `facets` library which is depreciated and archived).

## Summary

This code accompanies the
[NIPS 2017 ML Systems Workshop](http://learningsys.org/nips17/) paper/poster,
"The Data Linter: Lightweight, Automated Sanity Checking for ML Data Sets."

The Data Linter uses statistical techniques to identify potential issues (lints) in your ML training data.

# Using the Data Linter

## Environment Setup

Create a python 2.7 virtual environment and install libraries using 

`pip install -r requirements.txt`


## Data Linter Demo

Navigate to the demo folder and run the python two files using instructions found in `demo/README.md` (NOTE: this works on python3.8).

## Running the Data Linter

Running the Data Linter requires the following steps:

1. Encoding your data in TFRecord format.
2. Generating summary statistics for those data, using Facets.
3. Running the Data Linter.
4. Using the Lint Explorer to produce the lint results.

The data preprocessing part of the project works on Python3.8 and the details are in the `demo` folder. Particularly, 

#### 1. Creating Data in the TFRecord Format
*[Part of Data Preprocessing at python3.8]*
Converts CSV files to the TFRecord format, look at the example code
in `demo/convert_to_tfrecord.py`.

#### 2. Summarizing Your Data Using Facets
*[Part of Data Preprocessing at python3.8]*
To see how to generate summary statistics for your data, see the example code in
`demo/summarize_data.py`.

### Executing the Data Linter
*[Part of Main Data Linter at python 2.7 ]*
Once you have both the data and summary statistics, you can run the Data Linter
as such:

```shell
python data_linter_main.py --dataset_path PATH_TO_TFRECORDS \
  --stats_path PATH_TO_FACETS_SUMMARIES --results_path PATH_FOR_SAVING_RESULTS
```

Specifically, to run the demo, 

```shell
python data_linter_main.py --dataset_path demo adult.tfrecords 
  --stats_path demo/adult_summary.bin 
  --results_path demo/adult_lints.bin
```

### Viewing Results with the Lint Explorer

After the Data Linter is done examining your data, you can view the results
using this command:

```shell
python lint_explorer_main.py --results_path PATH_TO_RESULTS
```

Specifically, for the demo files, 

```shell
python lint_explorer_main.py --results_path \
  demo/lint_results.bin
```

# Supplimentary Material

The code makes use of
[Google's protobuf format](https://developers.google.com/protocol-buffers/). The protos are defined in `protos/`.

The facets library is archived and is not installable due to package conflicts. Which is why, I placed the relevant [code](https://github.com/PAIR-code/facets/tree/master/facets_overview/python) is present in the `demo` folder. 