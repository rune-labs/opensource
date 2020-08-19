# Jupyter Notebook Templates

Here are some introductory materials to access and manipulate data using Rune's APIs.

## Rune's Stream API
The **Stream API** allows you to pull time series data, including RC+S and Apple Watch signals. Full documentation for this API can be found [here](https://docs.runelabs.io/).  Our Python package `runeq` enables streamlined use of this API. Documentation for our Python SDK can be found [here](https://runeq.readthedocs.io/en/latest/).

## Overview
First, set up your analysis environment in Python. Then, download/clone this repository and load up the .ipynb files in Jupyter Notebook. 

* [00_python_installation_instructions](./00_python_installation_instructions.md) 
details how to set up a Python analysis environment on a Mac. This notebook can be skipped if you already have the Anaconda distribution. However, you may want to install two additional packages: `runeq` for utilizing the Stream API and `gql` for using the Graph API.

* [01_download_neural_data](./01_download_neural_data.ipynb) 
walks through a simple example of pulling raw time series and spectrograms and saving those as CSV files.

* [02_download_watch_data](./02_download_watch_data.ipynb) 
provides functions for downloading accelerometry, rotation, tremor probability, and dyskinesia probability from the Apple Watch.

* [03_find_neural_and_watch_data](03_find_neural_and_watch_data.ipynb) 
highlights ways to find where there are concurrent neural and watch data.

* [04_advanced_neural_data_selection](04_advanced_neural_data_selection.ipynb) 
uses meta data such as stimulation, sensing, and adaptive parameters for advanced neural data querying.

* [05_check_data_gaps](05_check_data_gaps.ipynb) 
filters data to remove epochs with non-continuous time stamps and to remove epochs that are too short in duration.

* [06_inspect_rcs_data_quality](06_inspect_rcs_data_quality.ipynb) 
uses session meta data to quantify and visualize data quality.

## Appendix of Functions
Here is a list of major functions and where to find them in the notebooks.

**Function** | **Notebook**
--- | --- 
`check_accel_data_availability` | [03_find_neural_and_watch_data](03_find_neural_and_watch_data.ipynb) 
`check_gaps` | [05_check_data_gaps](05_check_data_gaps.ipynb)
`check_duration` | [05_check_data_gaps](05_check_data_gaps.ipynb)
`check_neural_data_availability` | [03_find_neural_and_watch_data](03_find_neural_and_watch_data.ipynb) 
`check_sampling_rate` | [05_check_data_gaps](05_check_data_gaps.ipynb)
`filter_by_epoch_duration` | [04_advanced_neural_data_selection](04_advanced_neural_data_selection.ipynb)
`find_epochs` | [04_advanced_neural_data_selection](04_advanced_neural_data_selection.ipynb)
`find_overlapping_epochs` | [04_advanced_neural_data_selection](04_advanced_neural_data_selection.ipynb)
`get_accel` | [02_download_watch_data](02_download_watch_data.ipynb)
`get_adaptive_meta_data` | [04_advanced_neural_data_selection](04_advanced_neural_data_selection.ipynb)
`get_dyskinesia` | [02_download_watch_data](02_download_watch_data.ipynb)
`get_neural_time_series` | [01_download_neural_data](01_download_neural_data.ipynb)
`get_rotation` | [02_download_watch_data](02_download_watch_data.ipynb)
`get_sensing_meta_data` | [04_advanced_neural_data_selection](04_advanced_neural_data_selection.ipynb)
`get_session_events` | [06_inspect_rcs_data_quality](06_inspect_rcs_data_quality.ipynb)
`get_spectrogram` | [01_download_neural_data](01_download_neural_data.ipynb)
`get_stimulation_meta_data` | [04_advanced_neural_data_selection](04_advanced_neural_data_selection.ipynb)
`get_tremor` | [02_download_watch_data](02_download_watch_data.ipynb)
`plot_epochs` | [04_advanced_neural_data_selection](04_advanced_neural_data_selection.ipynb)
