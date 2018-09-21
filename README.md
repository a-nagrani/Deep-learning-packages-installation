# pytorch-installation
Installing pytorch on a remote machine + all dependencies and useful libraries 

Assuming you have python3.6 or higher already. 

### Anaconda 

First get Anaconda from [here](https://www.anaconda.com/download/#linux). 
Then run 
``` 
sh Anaconda3-5.2.0-Linux-x86_64.sh 
```

and follow the prompts. The defaults are generally good.


To install python 

```
conda create --name py36 python=3.6
```

Otherwise create a virtual environment for pytorch 

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
 
### Jupyter Notebooks 

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
