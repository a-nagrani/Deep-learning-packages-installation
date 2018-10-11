# pytorch
Installing pytorch on a remote machine + all dependencies and useful libraries 

Assuming you have python3.6 or higher already. 

### Anaconda 

Conda is a package manager to manage virtual environment and install packages. [Anaconda cheat sheet](https://conda.io/docs/_downloads/conda-cheatsheet.pdf). First get Anaconda from [here](https://www.anaconda.com/download/#linux). 

Then run 
``` 
sh Anaconda3-5.2.0-Linux-x86_64.sh 
```

and follow the prompts. The defaults are generally good. By downloading Anaconda, you get conda, Python, Jupyter Notebook and hundreds of other open source packages. You can use either conda or pip for installation in an virtual environment created with conda.
Note: The differences between conda and pip 

conda install — installs any software package.

pip install — installs python packages only and it’s the defacto python package manager.


Some useful conda commands: 

```
# update conda in your default environment 
 conda upgrade conda
 conda upgrade --all

# create a new environment with conda
 conda create -n [my-env-name]

# activate the environment you created
 source activate [my-env-name]

# take a look at the environment you created
 conda info
 conda list

# install a package with conda and verify it's installed
 conda install numpy
 conda list

# take a look at the list of environments you currently have
 conda info -e

# remove an environment
 conda env remove --name [my-env-name]

```


To install python 

```
conda create --name py36 python=3.6
```

Otherwise if you already have python, you can create a virtual environment for pytorch 

```
conda create --name pytorch 
```
To activate this environment, use:

 ```
source activate pytorch
```

To deactivate an active environment, use:
 ```
 source deactivate
 ```
 
 ### Pytorch
 Now install pytorch in this environment. First activate your environment. Then run (for cuda 9) 
 
 ```
 conda install pytorch torchvision -c pytorch
 ``` 
 Change this based on the cuda version you have, using the command from the [pytorch page](https://pytorch.org/get-started/locally/#anaconda)
 
# Jupyter Notebooks 

Now setup a kernel for Jupyter Notebooks

```
conda install ipykernel
python -m ipykernel install --user --name pytorch --display-name "PyTorch"
```
You can start a notebook by running 

```
jupyter notebook
```

To access this notebook remotely over SSH, 

Check to see if you have a notebook configuration file, jupyter_notebook_config.py. The default location for this file is your Jupyter folder located in your home directory:

Windows: C:\Users\USERNAME\.jupyter\jupyter_notebook_config.py

OS X: /Users/USERNAME/.jupyter/jupyter_notebook_config.py

Linux: /home/USERNAME/.jupyter/jupyter_notebook_config.py

If you don’t already have a Jupyter folder, or if your Jupyter folder doesn’t contain a notebook configuration file, run the following command:

```
jupyter notebook --generate-config
```
Set a password using the command: 

```
jupyter notebook password
``` 

Then run: 

```
jupyter notebook --no-browser --port=8889
```

This runs a jupyter notebook server on the remote machine on port:8889 without opening a browser since we will use the browser on our local machine to connect to this.

In a new terminal window on your local machine, SSH into the remote machine again using the following options to setup port forwarding.

```
ssh -N -L localhost:8888:localhost:8889 user@remote_host
```

arsha@shallow12 

-N options tells SSH that no commands will be run and it’s useful for port forwarding, and -L lists the port forwarding configuration that we setup.

Access the remote jupyter server via your local browser. Open your browser and go to:
```
localhost:8888
```

# Installing TensorFlow with Keras 




# Useful python libraries 
## LibROSA
LibROSA is a great python package for audio and music processing. Here's a full [tutorial](https://librosa.github.io/librosa/tutorial.html). 
The simplest way to install librosa is 
``` 
pip install librosa 
```
