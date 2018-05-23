# Theoretical Neuroscience Final Project Guidelines

These instructions will get you up and running on your local machine for the final project using pycog. 

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
# (Optional) if for some reason previous line failed or you encounter other errors downstream, use these
conda remove -n RNN --all
conda config --remove channels intel
conda create -n RNN python=2
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
(Optional). If you have a discrete GPU, like Nvidia GTX 750 or newer models, you could get better performance, follow the GPU setup guide in theano website, you'll also need to modify pycog source code a little bit, email me if you want to try

4. Test installations by running the S1Code.py file in this repo
```bash
cd ..
git clone https://github.com/Hanyu-Li/pycog-workshop.git
cd pycog-workshop/tutorial
python S1Code.py
```
you should see training progresses

### Frequently encountered problems:

- "MKL_THREADING_LAYER=GNU" error: (https://github.com/Theano/Theano/issues/6568)


### How pycog works
Don't worry if you are not that familiar with python, you won't need to read through the bulk of their source code or start from scratch. However, You do need to understand how to build a "trial" code snippet that is compatible with the framework.

There are several ways you could use pycog:
1. Like S1Code.py, an all-in-one .py file that defines a trial, its training configurations and running script, 

2. Define an experiment using files like in examples/models, and use their do.py script to interact with it.
```bash
(conda activate RNN) # assumed this is active
cd examples # assume you are in pycog directory
python do.py models/multisensory.py train # this is actually one of Dr.Matt Kaufman's papers!
```
3. (Recommended) Use a jupyter notebook, as shown in pycog-workshop/tutorial/pycog-workshop.ipynb, we will walk through it in the workshop
```bash
cd pycog-workshop/tutorial
jupyter notebook pycog-workshop.ipynb
```
You will need to build something like one of those "generate_trial" functions to define a behavioral task and write analytical functions for the simulation results.