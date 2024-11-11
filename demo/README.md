# Data Linter Demo

The demo uses [UCI
Census dataset](https://archive.ics.uci.edu/ml/datasets/Census+Income), which is also downloaded as `adult.data` file. 

## Environment Setup

To keep this separate than the main data linter environment. Create a new virtual environment. This generation uses python 3.8, whereas the parent data linter uses python 2.7

1. Python (The main repo is python 2.7, this one needs to be 3.8+) NOTE: After Installing a virtual env with python 3.8, you can use the requirements.txt to install the below. 
2. [Apache Beam](https://beam.apache.org/)
3. [TensorFlow](https://www.tensorflow.org/)
4. [Facets](https://github.com/PAIR-code/facets)

## [Optional] Download the dataset

The dataset is already downloaded at the demo directory, alternatively you can download the dataset at this location using:

```shell
wget https://archive.ics.uci.edu/ml/machine-learning-databases/adult/adult.data
```

## Convert the data to TFRecords

[1-3 are Optional]
1. Open `convert_to_tfrecord.py` (in this directory).
2. Set the `DATA_FILE` variable to the location of `adult.data` (which you just
   downloaded).
3. Set the `OUTPUT_FILE` variable to the location of where you would like to
   store the dataset once converted to TFRecords.
4. Run `python convert_to_tfrecord.py` 

## Create summary statistics

[1-3 are optional]
1. Open `summarize_data.py` (in this directory).
2. Set `DATASET_PATH` to the location of `OUTPUT_FILE` in the previous step.
3. Set `OUTPUT_PATH` to the location of where you wish to store the summary
   statistics.
4. Run `python summarize_data.py`.

## Go back to the parent Data Linter folder, and follow the readme instructions there!
