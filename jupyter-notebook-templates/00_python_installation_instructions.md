# Python Installation and Setup

These instructions detail how to set up a Python analysis environment using the Anaconda distribution.

## Introduction

Python is an open-source programming language with a number of packages to facilitate data analysis. A Python **module** is a single .py file that contains functions, and a **package** is a collection of modules. These packages are analogous to toolboxes in MATLAB. Common packages and their uses for data analysis include:

* **Pandas**: data reading/writing, manipulation, analysis
* **Numpy**: handling multi-dimensional array data
* **SciPy**: scientific computing, including support for signal processing and statistics
* **Matplotlib**: data plotting and visualization
* **Scikit Learn**: machine learning
* **Jupyter Notebook**: Python integrated development environment

Rather than installing each of these packages individually, a simplified way to install and manage packages is with a Python distribution, such as **Anaconda**. In addition to simplifying package installation and management, Anaconda also manages **virtual environments**. A virtual environment is an independent copy of Python, which can be tailored with specific versions of packages. Virtual environments will help you maintain dependencies across different projects.

## Installing Python

The Mac operating system comes pre-installed with Python. To check your version of Python, enter the following command in Terminal:

```
python --version
```

If you have Python 2.x, we recommend installing Python 3.6 or greater. First, we will set up command line tools and a package manager. Then we will install Python 3.

* Download **Xcode** from the Mac App Store: https://apps.apple.com/us/app/xcode/id497799835?mt=12. Then add the command line tools by entering the following in Terminal:

```
xcode-select --install
```

* Next, install **Homebrew**, a package manager for Mac, by entering the following in Terminal:

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```

* Install Python 3 using the Terminal command:

```
brew install python
```

* Once you have Python 3, install Anaconda using either the graphical installer or the command line installer: https://www.anaconda.com/distribution/.

* To install our Python SDK `runeq`, which simplifies use of our API:
```
pip install --upgrade pip
pip install runeq
```
* In order to use our Graph API, you will also need the gql package, which is not included in the Anaconda distribution. 

```
conda install -c conda-forge gql
```

## Setting up a Virtual Environment

To make sure that Anaconda installed correctly, enter the following command in Terminal:

```
conda list
```

This should print a list of the packages you now have in Python. Note that these packages are currently in your “base” environment. To start a new virtual environment, enter:

```
conda create -n <your_environment_name>
```

To open up a virtual environment, enter:

```
conda activate <your_environment_name>
```

Next, add packages to this environment with:

```
conda install pandas numpy scipy matplotlib scikit-learn jupyter requests 
```

To close out your virtual environment and return to the base environment, enter:

```
conda deactivate
```

## Using Jupyter Notebook

Jupyter Notebook is an open source integrated development environment that runs off of your web browser. It is a space to write and execute Python code, generate visualizations, and add data narratives in mark-down cells. To start up a Jupyter Notebook, first activate your virtual environment. Then enter the following in Terminal:

```
jupyter notebook
```

This should open up a new browser page, where you can navigate to your directory of interest and start a new notebook or load up an existing one.

Jupyter Notebook also has a number of (unofficial) extensions for added functionality (https://github.com/ipython-contrib/jupyter_contrib_nbextensions). These extensions are optional, but some may be useful for analyses, such as Variable Inspector and ExecuteTime.
