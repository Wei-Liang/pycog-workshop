# Theoretical Neuroscience Final Project Guidelines

These instructions will get you up and running on your local machine for RNN. 

### Prerequisites

**Python**: Install either Anaconda or Miniconda for your operating system, either 2 or 3

* Anaconda: https://www.anaconda.com/download/#linux

* Miniconda: https://conda.io/miniconda.html

**Git**: We will install from source code, you'll need git installed
https://git-scm.com/

### Installations

1. Start a fresh virtual environment with conda,
in terminal(or cmd.exe in Windows):
``` bash 
conda update conda
conda config --add channels intel
conda create -n RNN intelpython2_core python=2 # we use intel's distribution of python for better performance
(conda create -n RNN python=2) # if for some reason previous line failed, use this
```
2. Install various prerequisites for theano, w.r.t http://deeplearning.net/software/theano/install.html
``` bash 
conda activate RNN
conda install numpy scipy mkl nose sphinx pydot-ng
(conda install numpy scipy mkl-service libpython m2w64-toolchain nose sphinx pydot-ng) # for windows
conda install jupyter cython networkx matplotlib
conda install theano
```
3. Install [pycog](https://github.com/frsong/pycog.git) from source code
``` bash
git clone https://github.com/frsong/pycog.git
cd pycog
pip install -e .
```
download a sample file from the authors: https://ndownloader.figshare.com/files/6654750 and rename it to S1Code.py

4. Test installations
```bash
python S1Code.py
```

### Frequently encountered problems:

- "MKL_THREADING_LAYER=GNU" error: (https://github.com/Theano/Theano/issues/6568)


### How pycog works
Don't panic if you are not that familiar with python, you won't need to read through the bulk of their source code or start from scratch. However, You do need to understand how to build a "trial" code snippet that is compatible with the framework. :grin:

S1Code.py is an all-in-one demo file, while their recommended usage is shown in examples directory.
```bash
(conda activate RNN) # assumed this is active
cd examples
python do.py models/multisensory.py train # this is actually one of Dr.Matt Kaufman's papers!
```
You will need to build something like the "generate_trial" function in these files 