# Jupyter Notebook Templates

Here are some introductory materials to access and manipulate data using Rune's API.

## Rune's Stream API
The **Stream API** allows you to pull time series data, including signals from DBS devices and the Apple Watch. Full documentation for this API can be found [here](https://docs.runelabs.io/).  Our Python package `runeq` enables streamlined use of this API. Documentation for our Python SDK can be found [here](https://runeq.readthedocs.io/en/latest/).

## Overview
First, set up your analysis environment in Python. Then, download/clone this repository and load up the .ipynb files in Jupyter Notebook. 

* [00_python_installation_instructions](./00_python_installation_instructions.md) 
details how to set up a Python analysis environment on a Mac. This notebook can be skipped if you already have the Anaconda distribution. However, you should install `runeq` for utilizing the Stream API.

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

* [07_explore_patient_events](07_explore_patient_events.ipynb)
explores and pulls patient reported data from the Event and Span endpoints.

* [08_explore_metadata_state](08_explore_metadata_state.ipynb)
explores all of the metadata available from the State endpoint, with examples from Medtronic Summit RC+S and Percept.

* [09_explore_healthkit_data](09_explore_healthkit_data.ipynb)
explores and pulls data gathered from Apple's Health ecosystem.

* [101_clinical_score_upload](101_clinical_score_upload.ipynb)
uploads clinical score data, using UPDRS as an example, to the Rune platform.

## Appendix of Functions
Here is a list of major functions and where to find them in the notebooks.

**Function** | **Notebook**
--- | --- 
`check_accel_data_availability` | [03_find_neural_and_watch_data](03_find_neural_and_watch_data.ipynb) 
`check_gaps` | [05_check_data_gaps](05_check_data_gaps.ipynb)
`check_duration` | [05_check_data_gaps](05_check_data_gaps.ipynb)
`check_neural_data_availability` | [03_find_neural_and_watch_data](03_find_neural_and_watch_data.ipynb) 
`check_sampling_rate` | [05_check_data_gaps](05_check_data_gaps.ipynb)
`create_event` | [101_clinical_score_upload](101_clinical_score_upload.ipynb)
`create_span` | [101_clinical_score_upload](101_clinical_score_upload.ipynb)
`data_format_check` | [101_clinical_score_upload](101_clinical_score_upload.ipynb)
`filter_by_epoch_duration` | [04_advanced_neural_data_selection](04_advanced_neural_data_selection.ipynb)
`find_epochs` | [04_advanced_neural_data_selection](04_advanced_neural_data_selection.ipynb)
`find_overlapping_epochs` | [04_advanced_neural_data_selection](04_advanced_neural_data_selection.ipynb)
`get_adaptive_meta_data` | [04_advanced_neural_data_selection](04_advanced_neural_data_selection.ipynb)
`get_events` | [07_explore_patient_events](07_explore_patient_events.ipynb)
`get_neural_time_series` | [01_download_neural_data](01_download_neural_data.ipynb)
`get_sensing_meta_data` | [04_advanced_neural_data_selection](04_advanced_neural_data_selection.ipynb)
`get_session_events` | [06_inspect_rcs_data_quality](06_inspect_rcs_data_quality.ipynb)
`get_spans` | [07_explore_patient_events](07_explore_patient_events.ipynb)
`get_spectrogram` | [01_download_neural_data](01_download_neural_data.ipynb)
`get_states` | [08_explore_metadata_state](08_explore_metadata_state.ipynb)
`get_stimulation_meta_data` | [04_advanced_neural_data_selection](04_advanced_neural_data_selection.ipynb)
`get_watch_data` | [02_download_watch_data](02_download_watch_data.ipynb)
`plot_epochs` | [04_advanced_neural_data_selection](04_advanced_neural_data_selection.ipynb)
